**Proyecto integrador: Chatbot en Python con Docker y Docker Compose**



*📌 Descripción del proyecto*



*Este proyecto consiste en un chatbot sencillo desarrollado en Python que utiliza un archivo JSON como base de datos de preguntas y respuestas.*

*El objetivo es demostrar:*



&#x20;   *Control de versiones con Git y GitHub*



&#x20;   *Contenerización con Docker*



&#x20;   *Orquestación con Docker Compose*



*La aplicación funciona por terminal y permite realizar preguntas simples definidas en el archivo base\_datos.json.*



**🚀 Instalación y despliegue**



*1. Clonar el repositorio*

*bash*



*git clone https://github.com/CarJavierFer/proyecto-integrador-chatbot.git*



*2. Construir la imagen Docker*

*bash*



*docker build -t chatbot .*



*3. Ejecutar el contenedor con Docker Compose*

*bash*



*docker compose up*



*4. Acceder a la aplicación*



*El chatbot funciona directamente por terminal.*

*Al iniciar el contenedor, se mostrará:*

*Código*



*Chatbot iniciado. Escribe 'salir' para terminar.*



**🐳 Explicación del Dockerfile**



*El Dockerfile utilizado es:*

*Dockerfile*



*FROM python:3.11-slim*

*WORKDIR /app*

*COPY base\_datos.json .*

*COPY chatbot.py .*

*CMD \["python", "chatbot.py"]*



*Explicación:*



&#x20;   *FROM python:3.11-slim → imagen base ligera.*



&#x20;   *WORKDIR /app → define el directorio de trabajo.*



&#x20;   *COPY → copia los archivos necesarios al contenedor.*



&#x20;   *CMD → ejecuta automáticamente el chatbot al iniciar el contenedor.*



**🧩 Explicación del docker-compose.yml**



*yaml*

*services:*

&#x20; *chatbot:*

&#x20;   *build: .*

&#x20;   *container\_name: chatbot*

&#x20;   *volumes:*

&#x20;     *- ./base\_datos.json:/app/base\_datos.json*

&#x20;   *stdin\_open: true*

&#x20;   *tty: true*

&#x20;   *command: \["python", "chatbot.py"]*



Explicación:



&#x20;   *Define el servicio chatbot.*



&#x20;   *Construye la imagen desde el Dockerfile.*



&#x20;   *Monta el archivo JSON como volumen para persistencia.*



&#x20;   *Permite entrada por teclado (stdin\_open + tty).*



&#x20;   *Ejecuta automáticamente python chatbot.py.*



**🔧 Posibles problemas y soluciones**

*❗ No se ve lo que escribo al usar Docker Compose*



*En Windows + Git Bash, la entrada por teclado no se muestra, aunque el contenedor sí la recibe.*



*Solución:*  

*Usar:*

*bash*



*winpty docker run -it chatbot*



*❗ Problemas con permisos de Docker Desktop*



*Puede ser necesario ajustar permisos en:*

*Código*



*C:\\ProgramData\\DockerDesktop*

*Antes de reinstalar Docker Desktop.*



**✨ Contribuciones y organización del repositorio**



*El repositorio utiliza varias ramas:*



&#x20;   *main → rama estable*



&#x20;   *documentacion → documentación del proyecto*



&#x20;   *dockerizacion → Dockerfile y Compose*



&#x20;   *desarrollo-chatbot → desarrollo del chatbot*



*Se ha creado un Pull Request desde documentacion hacia main, cumpliendo el enunciado.*



**🌐 Exposición de puertos**



*Este proyecto no expone puertos, ya que el chatbot funciona por terminal dentro del contenedor.*

*No utiliza HTTP ni interfaz web, por lo que no es necesario mapear puertos.*



