# Redflix Streaming

## Descripción

Este programa implementa el sistema de streaming adaptativo para **Redflix**, un servicio de transmisión de video que se adapta a diferentes calidades de conexión. Los usuarios pueden seleccionar entre tres tipos de bitrate para ajustar la calidad de la transmisión de video: **Low Definition (LD)**, **Medium Definition (MD)** y **High Definition (HD)**. El sistema maneja múltiples clientes simultáneamente, cada uno con su propio "Streamer", y adapta el envío de frames de acuerdo al bitrate seleccionado.

## Requisitos

1. **Concurrencia**: El sistema permite manejar múltiples clientes, cada uno con su propio "Streamer", para una transmisión de video concurrente.
2. **Bitrate adaptativo**: El usuario puede seleccionar el bitrate de transmisión en cualquier momento. Existen tres opciones:
   - **LD (Low Definition)**: Envía 1 frame a la vez con una pausa pequeña entre ellos.
   - **MD (Medium Definition)**: Envía bloques de 10 frames a la vez con una pausa moderada.
   - **HD (High Definition)**: Envía bloques de 100 frames a la vez con una pausa larga.
3. **Simulación de video**: El contenido del video es simulado desde un archivo de texto (`video.txt`), donde cada número representa un frame del video.
4. **Terminación automática**: El sistema termina automáticamente cuando se han transmitido todos los frames del archivo de video.

## Uso

### Compilación

1. Asegúrate de tener un compilador de C disponible (por ejemplo, GCC).

2. Compila el código fuente con el siguiente comando:

   `gcc -o redflix redflix.c -lpthread`

## Ejecución
Para ejecutar el programa, utiliza el siguiente comando:

`./redflix <bitrate>`

## Parámetros:

- `<bitrate>`: Especifica el bitrate de transmisión. Puede ser uno de los siguientes:
- `LD`: Low Definition (baja calidad, 1 frame a la vez).
- `MD`: Medium Definition (calidad media, 10 frames a la vez).
- `HD`: High Definition (alta calidad, 100 frames a la vez).

Si no se proporciona el parámetro, el sistema no podrá iniciar.

Ejemplo de uso:

`./redflix LD`

Esto comenzará a transmitir los frames con el bitrate de Low Definition.

## Archivos Requeridos

video.txt: Un archivo de texto que simula el contenido del video. Cada número en el archivo representa un frame del video.

## Detalles de Ejecución

El programa lee el archivo video.txt para cargar los frames.
Según el bitrate seleccionado, los frames se envían de forma adaptativa:

- LD: Se envía 1 frame a la vez con una pequeña pausa.
- MD: Se envían bloques de 10 frames con una pausa moderada.
- HD: Se envían bloques de 100 frames con una pausa larga.

El programa finaliza automáticamente una vez que se hayan transmitido todos los frames del archivo de video.

## Consideraciones
- Concurrencia: El sistema permite manejar múltiples clientes de manera simultánea.
- Escalabilidad: Puede ajustarse para soportar más clientes y diferentes calidades de streaming.
- Finalización automática: Una vez que todos los frames del archivo de video hayan sido transmitidos, el programa terminará sin requerir intervención adicional.
