# Verificación de la estación meteorológica CYD

Fecha: 2026-10-30. Spec Kit aplicado manualmente con plantillas oficiales y constitución existente, sobre copias respaldadas y commits de especificación previos a la incorporación. No se instalaron extensiones ni se grabó firmware.

| Criterio | Evidencia y resultado |
|---|---|
| AC1 · Fuentes y privacidad | Los tres fuentes y dos referencias coinciden byte a byte con los originales respaldados; SHA-256 en docs/weather-source-manifest.json. README público adaptado y referencia histórica redactada. Certificado raíz público, sin clave privada. No se incluyen brutos, credenciales, perfiles, backups o binarios de firmware. |
| AC2 · Descarga y catálogo | ZIP de cinco archivos: carpeta WeatherStationCYD con principal Arduino, dos cabeceras, README y licencia. Hash e inventario en downloads/weather-manifest.json; catálogo con dos proyectos únicos. Descarga del radar conservada. |
| AC3 · Compilación y contrato | Compilación completa finalizada con salida 0: 1.206.308 bytes de programa (92 %), 52.896 bytes de RAM estática (16 %). Dos pruebas HTTPS reales desde PC: correctas en 0,674 s, con la raíz del firmware; Sevilla y localidad inexistente. La comprobación original de backups privados se omite explícitamente de la distribución. |
| AC4/AC5 · Evidencia física | Portal HTTP 200 al guardar Madrid/ES; conexión habitual del PC restaurada y perfil temporal eliminado. Confirmación del autor seguida de foto y vídeo con Madrid, WIFI OK, 14,6 °C y previsión. Seis PNG: foto y cinco cuadros reales, recorte rectangular exacto, sin recreación de píxeles ni metadatos privados; procedencia/hashes en su manifiesto. |
| AC6 · Entrega multimedia | MP4 H.264/AAC, 1080×1920, 30 fps, 36 s. Voz sintética española, música original, rótulos y SRT; QR del vídeo codificado comprobado hacia el catálogo público. Se excluye completamente el portal visible en el bruto. Revisión visual de capturas y muestras del montaje; decodificación completa y comprobaciones de integridad documentadas antes del commit de contenido. |

## Límites

La exportación original compiled_only se conserva como registro histórico. La nueva foto/vídeo demuestra la visualización física de datos, pero no identifica el hash del binario instalado. Las pruebas desde PC no ejecutan el parser C++, radio o LCD del ESP32. No se afirma validación exhaustiva de persistencia tras reinicio, todas las ciudades, recuperación prolongada ni todas las ramas de error.

Madrid es la ubicación pública de ejemplo solicitada. Open-Meteo aporta datos de modelo por Internet; no son mediciones de sensores locales. Código MIT y condiciones de API/datos diferenciados en la guía.

## Publicación

El commit de contenido y su árbol se contrastan por HTTPS anónimo con GitHub. El cierre de publicación se registra después de verificar remoto, descarga ZIP y ausencia de releases, sin publicar automáticamente en TikTok.
