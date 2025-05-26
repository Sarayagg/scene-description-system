# scene-description-system
Sistema modular de asistencia visual con IA (ResNet50, YOLOv11, MiDaS)

# Sistema de Descripción Automática de Escenas para Personas con Discapacidad Visual

Este repositorio contiene el código y documentación del Proyecto Fin de Grado titulado "Descripción automática de escenas para personas con discapacidad visual basada en el reconocimiento de imágenes", desarrollado por Sara Yagüe Rubio en la Universidad Politécnica de Madrid.

El sistema permite interpretar entornos interiores mediante visión por computador y generar descripciones orales comprensibles, ofreciendo una herramienta de asistencia para personas con discapacidad visual.

## Descripción general del sistema

El sistema está compuesto por cinco módulos principales:

- Clasificación de escenas: Utiliza una red neuronal ResNet50 para identificar el tipo de entorno (cocina, oficina, dormitorio, etc.).
- Detección de objetos: Utiliza YOLOv11 para localizar y clasificar objetos presentes en la imagen.
- Estimación de profundidad: Utiliza el modelo MiDaS para generar mapas de profundidad monocular.
- Automatización de descripciones: Genera frases contextualizadas priorizando los objetos más relevantes por cercanía y tipo, a partir de los datos anteriores.
- Conversión texto a voz: Convierte las descripciones generadas en audio mediante la librería gTTS.

El sistema está diseñado para ejecutarse de forma local, sin necesidad de conexión a Internet, garantizando privacidad y personalización.

## Estructura del repositorio

scene-description-system/
├── src/
│ ├── classification/ # Clasificación de escena (ResNet50)
│ ├── detection/ # Detección de objetos (YOLOv11)
│ ├── depth_estimation/ # Estimación de profundidad (MiDaS)
│ ├── automation/ # Generación de descripciones
│ │ ├── procesar_detecciones.py
│ │ ├── generar_frases.py
│ │ └── describir_entorno.py
│ └── tts/ # Conversión texto a voz
│ └── sintetizar_audio.py
├── models/ # Modelos entrenados
├── examples/ # Imágenes de entrada y resultados generados
├── requirements.txt # Dependencias del proyecto
├── README.md # Este archivo
├── .gitignore # Exclusiones para Git
└── LICENSE # Licencia del proyecto




## Instalación y uso

1. Clonar el repositorio

git clone https://github.com/tu-usuario/scene-description-system.git
cd scene-description-system



2. Instalar dependencias

Es recomendable utilizar un entorno virtual.
pip install -r requirements.txt




3. Ejecutar el sistema

Ejemplo de uso:python src/automation/describir_entorno.py --input imagen.jpg


Este comando genera:
- Un archivo JSON con los resultados de clasificación, detección y profundidad
- Una frase descriptiva del entorno
- Un archivo de audio (.mp3) con la descripción

## Descripción de módulos

**Clasificación de escena (ResNet50)**  
Modelo reentrenado con transfer learning sobre el dataset MIT Indoor Scenes.  
Precisión alcanzada: 76.4%.

**Detección de objetos (YOLOv11)**  
Entrenado sobre un subconjunto etiquetado de escenas interiores.  
Precisión mAP@0.5: 0.529.

**Estimación de profundidad (MiDaS)**  
Modelo preentrenado de Intel Labs. Produce mapas de profundidad precisos en variedad de entornos.

**Automatización de descripciones**  
Este módulo integra los datos anteriores para generar frases en lenguaje natural. Incluye:
- Priorización de objetos según tipo, posición y contexto
- Adaptación del contenido a cada tipo de escena
- Posibilidad de ajustar el nivel de detalle

**Conversión texto a voz**  
Se utiliza gTTS para transformar las descripciones generadas en archivos de audio accesibles.

## Resultados

El sistema fue probado en diferentes entornos interiores, obteniendo resultados coherentes y relevantes tanto en precisión técnica como en utilidad práctica.

| Módulo            | Métrica              | Resultado   |
|-------------------|----------------------|-------------|
| Clasificación     | Precisión top-1      | 76.4 %      |
| Detección         | mAP@0.5              | 0.529       |
| Profundidad       | Evaluación cualitativa | Alta precisión visual |
| Descripciones     | Coherencia contextual| Alta        |

## Futuras mejoras

- Inclusión de entrada por voz para uso bajo demanda
- Incorporación de salida háptica para navegación sin audio
- Funcionamiento en tiempo real con cámaras conectadas
- Ajuste dinámico del nivel de detalle según usuario

## Contribuciones

El proyecto es de código abierto. Se aceptan contribuciones en forma de:
- Código nuevo o mejoras
- Corrección de errores
- Traducciones o mejoras en la documentación

Para colaborar, puedes abrir un "pull request" o sugerencia en este repositorio.

## Licencia

Este proyecto está distribuido bajo la Licencia MIT. Consulta el archivo LICENSE para más detalles.

## Autora

Sara Yagüe Rubio  
Grado en Ingeniería de Sonido e Imagen  
Universidad Politécnica de Madrid  
Año de presentación: 2025
