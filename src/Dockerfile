# Imagem de execução, utilizada para executar o que estara no virtualenv
FROM python:3.12.10-slim-bullseye

# Instala as dependencias do sistema
RUN apt-get update && apt-get upgrade -y && apt-get install openjdk-11-jdk procps -y

# Definie as variaveis do JAVA
ENV JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
ENV PATH="$JAVA_HOME/bin:$PATH"

# Prepara o ambiente
WORKDIR /app

# Habilitando o Virtualenv
COPY utils/requirements.txt .

RUN python -m venv venv && . venv/bin/activate && pip install -r requirements.txt

# Copia dos arquivos e pastas para o workdir
COPY data/ .
COPY notebooks/ .

# Executa um comando no CMD para rodar o JupyterLab ao iniciar o container
CMD ["jupyter-lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]