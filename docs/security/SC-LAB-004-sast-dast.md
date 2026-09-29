# SC-LAB-004 SAST + DAST

## Objetivo

Analizar vulnerabilidades mediante técnicas SAST y DAST.

## Entorno

- Windows
- Python 3.14.7
- Flask 3.1.3
- Docker Desktop
- Semgrep
- OWASP ZAP

## Análisis humano

### ¿Qué dato controla el usuario?

El parámetro nombre.

### ¿A dónde llega ese dato?

A una consulta SQL y a una respuesta HTML.

### ¿Qué riesgo observas?

SQL Injection y XSS reflejado.

### ¿Qué control propondrías?

Consultas parametrizadas y escape de salida.

## Evidencia SAST

Semgrep detectó SQL Injection en `src/app.py` debido a la concatenación directa de datos del usuario en una consulta SQL.

## Corrección SQL

Se modificó la consulta para usar parámetros:

```python
cursor.execute(consulta, (nombre,))
```