# Agente Respaldo — Releases

Este repositorio contiene **solo binarios firmados** de la edición "actualizable" del
Agente Respaldo y su manifiesto de versión (`ultima_version.json`). El código fuente del
programa vive en un repositorio privado aparte.

## Qué hay acá

- `AgenteRespaldo-<version>-actualizable.exe` — el instalador de cada versión publicada.
- `AgenteRespaldo-<version>-actualizable.exe.sha256` — su hash, para verificación manual.
- `ultima_version.json` — manifiesto firmado (Ed25519) que consulta el propio programa para
  saber si hay una versión más nueva. Cada Agente Respaldo instalado valida la firma de este
  archivo contra una clave pública embebida en el propio ejecutable antes de aceptar
  cualquier actualización — un manifiesto editado a mano, sin la clave privada correspondiente,
  es rechazado automáticamente.

## Cómo se publica una versión nueva

1. `python scripts/distribucion/build.py actualizable` en el repo privado.
2. `python scripts/distribucion/firmar_release.py <exe> --url-exe <url-final-en-este-repo>`.
3. Crear un release en este repo, subiendo el `.exe`, el `.sha256` y el `ultima_version.json`
   firmado.
