
# Chatbot utilizando DialoGPT
 *Autor: Carlos Vergara*

### Introducción
En este mini proyecto, utilicé el modelo de lenguaje DialoGPT para crear un chatbot conversacional. El caso de uso principal fue explorar las capacidades de una API de modelo de lenguaje mediante la implementación de un sistema de diálogo interactivo. Mi objetivo fue entender cómo el modelo genera respuestas en función de las entradas del usuario y experimentar con diferentes configuraciones para optimizar la interacción.

## Instalación
1. Clona el repositorio.
2. Instala las dependencias ejecutando el siguiente comando:
   ```bash
   conda env create -f ironhack-llm.yml
   ```
3. Activa el entorno:
   ```bash
   conda activate <nombre_del_entorno>
   ```

## Uso
1. Ejecuta el script `chatbot.ipynb`.
2. Introduce un mensaje y presiona Enter.
3. Para salir, escribe `exit` o `quit`.


### Integración de la API
Elegí la biblioteca Transformers de Hugging Face para la integración de la API, utilizando específicamente el modelo DialoGPT. El proceso implicó los siguientes pasos:
1. **Instalación**: Preparé el entorno instalando las dependencias utilizando el archivo `ironhack.llm.yml`.
2. **Carga del modelo**: Cargué el modelo y el tokenizador utilizando las clases `AutoModelForCausalLM` y `AutoTokenizer` de la biblioteca Transformers.
3. **Envío de solicitudes**: Las entradas del usuario se codificaron y concatenaron con el historial de la conversación antes de generar respuestas del modelo.
4. **Manejo de respuestas**: La salida generada se decodificó y se imprimió de nuevo al usuario.

### Explicación del código
La funcionalidad principal del chatbot se encapsuló en una función `chat_with_dialoGPT`. Aquí hay algunas secciones clave del código:
- **Manejo de entradas**: La entrada del usuario se codifica, y si hay un historial de chat existente, se concatena con la nueva entrada.
- **Generación de respuestas**: Se utiliza el método `model.generate()` para crear respuestas, siendo parámetros como `max_length`, `temperature`, `top_k` y `top_p` cruciales para ajustar la aleatoriedad y calidad de la respuesta.
- **Bucle de conversación**: El programa solicita continuamente al usuario que ingrese datos hasta que decidan salir escribiendo 'exit' o 'quit'.

### Resultados y Hallazgos
A través de mi experimentación, descubrí que ajustar los parámetros afectaba significativamente la naturaleza de las respuestas. Valores más altos para `temperature` llevaban a respuestas más creativas pero menos coherentes, mientras que valores más bajos producían respuestas más predecibles. El chatbot mantuvo exitosamente el contexto durante la conversación, mejorando la interacción del usuario.

### Lecciones Aprendidas
Durante este proyecto, enfrenté varios desafíos, incluyendo:
- **Limitaciones del modelo**: Me di cuenta de que, aunque el modelo es capaz de generar respuestas relevantes, a veces se desvía del contexto si la conversación se vuelve demasiado larga.
- **Ajuste de parámetros**: La optimización de los parámetros es esencial para mejorar el rendimiento del chatbot. Aprendí que la experimentación sistemática con estos valores es necesaria para lograr la calidad de conversación deseada.
- **Experiencia del usuario**: Se hizo evidente que la experiencia del usuario podría mejorarse con un mejor manejo de entradas ambiguas y la preservación del contexto.

En general, este proyecto proporcionó valiosas perspectivas sobre el uso práctico de los modelos de lenguaje y destacó la importancia de una cuidadosa selección de parámetros y un diseño de interacción con el usuario.

### Retroalimentación y Reflexión
Después de presentar mis hallazgos, discutí las oportunidades y desafíos de integrar APIs de modelos de lenguaje en el desarrollo de aplicaciones. Las conclusiones clave incluyeron la necesidad de formación continua para mejorar el rendimiento del modelo y las consideraciones éticas relacionadas con el contenido generado por la IA.
