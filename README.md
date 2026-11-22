# Releases de Impulso Financiero para Android

La APK consulta `latest.json` para saber si hay una versión más nueva. El manifiesto se publica en la rama `main` y cada APK se adjunta a un GitHub Release de este repositorio.

## Publicar una actualización

1. Aumenta `version` y `buildNumber` en `pubspec.yaml`; el número de build debe ser mayor que el anterior.
2. Genera la APK release firmada con la misma llave de publicación que se usará en futuras actualizaciones.
3. Crea un GitHub Release con una etiqueta como `v1.0.1` y adjunta el APK.
4. Calcula SHA-256 del archivo publicado: `Get-FileHash .\app-release.apk -Algorithm SHA256`.
5. Actualiza `latest.json` con la versión, el build, la URL exacta del APK, su SHA-256 y las notas de versión.
6. Confirma y publica el cambio de `latest.json` en `main`.

La APK solo ofrece la actualización cuando `buildNumber` supera al instalado. Verifica que cada release mantenga el mismo `applicationId` y la misma firma para que Android permita actualizar la instalación existente.

El manifiesto inicial es una plantilla sin actualización publicable. Debe reemplazarse al crear el primer release de Impulso Financiero.
