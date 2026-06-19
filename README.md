## Características

- **Subida de archivos:** Soporte para WAV, MP3, FLAC, OGG, M4A, WEBM.
- **Conversión de audio:** Cambio de frecuencia de muestreo y profundidad de bits.
- **Análisis de audio:** Visualización de forma de onda y espectro de frecuencia.
- **Descarga de archivos procesados.**
- **API REST.**

## Estructura del proyecto

```text
TP-COMUNICACION/
├── app.py                  # Punto de entrada principal
├── backend/                # Backend FastAPI
│   ├── aplicacion.py       # Aplicacion principal
│   ├── configuracion/      # Configuracion
│   │   ├── __init__.py
│   │   └── config.py
│   ├── controlador/        # Routers
│   │   ├── __init__.py
│   │   ├── rutas_audio.py  # Endpoints de audio
│   │   └── rutas_web.py    # Endpoints web
│   ├── modelo/             # Modelos y esquemas
│   │   ├── __init__.py
│   │   └── esquemas.py     # Esquemas Pydantic
│   └── servicios/          # Logica de negocio
│       ├── __init__.py
│       └── servicio_audio.py
├── frontend/               # Frontend (HTML/JS)
│   ├── estaticos/
│   │   └── js/
│   │       └── visualizacion.js
│   └── plantillas/
│       └── principal.html
├── uploads/                # Archivos subidos (se crea automaticamente)
├── temp/                   # Archivos temporales (se crea automaticamente)
├── requirements.txt        # Dependencias Python
└── README.md
```

## Requisitos previos

- Version de python: 3.8 a 3.13
   **Verificar tu version de python.**

   ```bash
   python --version
   ```

   **En caso de no tener una version compatible, por favor instalarla.**

- Gestior de paquetes: pip

## Instalacion

1. Clona el repositorio.

   ```bash
   git clone <url-del-repositorio>
   cd TP-COMUNICACION
   ```

2. Instalacion de FFmpeg.
   Python no sabe leer por sí solo audios web o formatos modernos comprimidos (como .webm). FFmpeg entra en acción para descomprimir y transformar esos datos binarios en un flujo que las librerías científicas puedan procesar.

   Dependiendo de tu sistema operativo, ejecutá uno de los siguientes comandos en tu terminal:

   - `En Windows (PowerShell):`
   ```powershell
   winget install "FFmpeg (Essentials Build)"
   ```
   (Nota: Una vez instalado, es necesario reiniciar VS Code para que aplique los cambios del PATH).

   - `En Mac (Homebrew):`
   ```bash
   brew install ffmpeg
   ```

   - `En Ubuntu/Debian:`
   ```bash
   sudo apt install ffmpeg
   ```

3. Instalar las dependencias de Python dependiendo de la version.
   **Dependiendo de la version que tengas hacer lo siguiente:**

   - `Version de Python 3.13:`
      ```bash
      pip install -r requirements_3.13.txt
      ```

   - `Version de Python 3.8 a 3.12:`
      ```bash
         pip install -r requirements.txt
      ```

4. Iniciar el servidor.

   ```bash
   python app.py
   ```

5. Acceder a la aplicación.
   - Frontend Web: http://localhost:8000

## Configuración

Edita `backend/configuracion/config.py` para personalizar:
- Puerto del servidor.
- Formatos de audio soportados.
- Tamaño máximo de archivo permitido.

## Endpoints principales

- `POST /api/audio/subir` - Subir archivo de audio
- `POST /api/audio/convertir` - Convertir archivo de audio
- `GET /api/audio/forma-onda/{archivo_id}` - Obtener forma de onda
- `GET /api/audio/espectro/{archivo_id}` - Obtener espectro de frecuencia
- `GET /api/audio/descargar/{archivo_id}` - Descargar archivo procesado
- `DELETE /api/audio/limpiar/{archivo_id}` - Limpiar archivos temporales
- `GET /` - Página principal
- `GET /salud` - Verificar estado del servidor

## Tecnologías utilizadas

- FastAPI
- Uvicorn
- soundfile, numpy, scipy, pydub
- FFmpeg
- HTML5, JavaScript