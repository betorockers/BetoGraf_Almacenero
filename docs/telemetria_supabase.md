# Telemetría y Monitoreo de Salud — BetoGraf Almacenero POS

Este módulo permite la supervisión remota continua del estado de los terminales POS que operan en redes locales aisladas (detrás de NAT/firewalls), utilizando **Supabase** como bus de salida y puente hacia el dashboard central de monitoreo.

---

## 1. Arquitectura Técnica

```
[ Terminal Local BetoGraf POS ]
  ├── /health/extended/            <-- Endpoint HTTP local (inspección directa en la máquina)
  ├── TelemetryService             <-- Recolección nativa (RAM via ctypes, Disco via shutil, DB SQLite, Periféricos)
  └── HealthTelemetryWorker (60s)  <-- Subproceso daemon en segundo plano
        │
        └── HTTPS REST POST (apikey)
              │
              ▼
   [ Supabase Cloud (pos_health_metrics) ]
              │
              ▼
    [ Dashboard Central de Monitoreo ]
```

---

## 2. Endpoints Locales Disponibles

* `GET /health/extended/`
* `GET /pos/api/health/extended/`

### Ejemplo de Respuesta JSON:
```json
{
  "status": "ok",
  "reported_at": "2026-10-13T16:14:04.290235+00:00",
  "uptime_seconds": 3600,
  "serial": "POS-AN-7NL2-7BHZ-38HW",
  "hw_id": "F4B3-991A-002C",
  "license_mode": "full",
  "supabase_configured": true,
  "system": {
    "hostname": "CAJA-01",
    "os_name": "Windows 11",
    "os_version": "10.0.26100",
    "architecture": "AMD64",
    "python_version": "3.13.13",
    "ram": {
      "total_mb": 16384.0,
      "avail_mb": 9840.5,
      "used_mb": 6543.5,
      "used_pct": 40
    },
    "disk": {
      "total_gb": 240.0,
      "used_gb": 85.0,
      "free_gb": 155.0,
      "used_pct": 35.4
    }
  },
  "database": {
    "status": "ok",
    "productos_count": 1250,
    "ventas_count": 4820,
    "pedidos_count": 12,
    "error": null
  },
  "hardware": {
    "printer_connected": true,
    "scanner_connected": true,
    "selected_printer": "XP-80"
  },
  "telemetry": {
    "last_push_at": "2026-10-13T16:14:00.000000+00:00",
    "last_push_status": "ok"
  }
}
```

---

## 3. Esquema SQL para Supabase (`pos_health_metrics`)

Ejecutar en el SQL Editor de tu proyecto Supabase:

```sql
CREATE TABLE IF NOT EXISTS public.pos_health_metrics (
    id BIGSERIAL PRIMARY KEY,
    serial TEXT NOT NULL,
    hw_id TEXT,
    hostname TEXT,
    app_version TEXT,
    license_mode TEXT,
    status TEXT DEFAULT 'ok',
    uptime_seconds BIGINT DEFAULT 0,
    ram_used_pct INTEGER,
    ram_used_mb NUMERIC(10,2),
    ram_total_mb NUMERIC(10,2),
    disk_free_gb NUMERIC(10,2),
    disk_total_gb NUMERIC(10,2),
    disk_used_pct NUMERIC(5,2),
    db_status TEXT,
    productos_count INTEGER DEFAULT 0,
    ventas_count INTEGER DEFAULT 0,
    pedidos_count INTEGER DEFAULT 0,
    printer_connected BOOLEAN DEFAULT FALSE,
    scanner_connected BOOLEAN DEFAULT FALSE,
    reported_at TIMESTAMPTZ DEFAULT NOW(),
    metadata JSONB,
    created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Índices recomendados para consultas del Dashboard
CREATE INDEX IF NOT EXISTS idx_pos_health_serial ON public.pos_health_metrics(serial);
CREATE INDEX IF NOT EXISTS idx_pos_health_reported_at ON public.pos_health_metrics(reported_at DESC);
```

---

## 4. Consulta Típica para Dashboard Central (Último Estado de Cada Máquina)

```sql
SELECT DISTINCT ON (serial)
    serial,
    hostname,
    status,
    ram_used_pct,
    disk_free_gb,
    printer_connected,
    scanner_connected,
    reported_at,
    NOW() - reported_at AS tiempo_desde_reporte
FROM public.pos_health_metrics
ORDER BY serial, reported_at DESC;
```
