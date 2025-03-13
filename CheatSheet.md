# Docker Cheat Sheet

## 📦 **Comandos Básicos do Docker**

### Gerenciamento de Containers

- **Listar containers em execução:**
  ```bash
  docker ps
  ```
- **Listar todos os containers (incluindo parados):**
  ```bash
  docker ps -a
  ```
- **Iniciar um container:**
  ```bash
  docker start <container_id|nome>
  ```
- **Parar um container:**
  ```bash
  docker stop <container_id|nome>
  ```
- **Remover um container parado:**
  ```bash
  docker rm <container_id|nome>
  ```
- **Executar um container interativamente:**
  ```bash
  docker run -it <imagem> bash
  ```
- **Executar um comando em um container em execução:**
  ```bash
  docker exec -it <container_id|nome> bash
  ```

### Gerenciamento de Imagens

- **Listar imagens locais:**
  ```bash
  docker images
  ```
- **Remover uma imagem:**
  ```bash
  docker rmi <imagem_id|nome>
  ```
- **Baixar uma imagem do Docker Hub:**
  ```bash
  docker pull <imagem>:<tag>
  ```
- **Criar uma imagem a partir de um Dockerfile:**
  ```bash
  docker build -t <nome_imagem>:<tag> .
  ```

### Redes Docker

- **Listar redes Docker:**
  ```bash
  docker network ls
  ```
- **Criar uma rede Docker:**
  ```bash
  docker network create <nome_rede>
  ```
- **Conectar um container a uma rede:**
  ```bash
  docker network connect <nome_rede> <container_id|nome>
  ```

### Limpeza de Recursos

- **Remover containers parados, imagens não utilizadas e volumes:**
  ```bash
  docker system prune
  ```

## 📄 **Comandos Básicos de Dockerfile**

### Instruções Comuns

```Dockerfile
# Define a imagem base
FROM <imagem>:<tag>

# Define diretório de trabalho
WORKDIR /app

# Copia arquivos para a imagem
COPY . /app

# Executa comandos durante a construção
RUN apt-get update && apt-get install -y python3

# Define variáveis de ambiente
ENV VARIAVEL=valor

# Porta exposta pelo container
EXPOSE 8080

# Comando padrão ao iniciar o container
CMD ["python3", "app.py"]

# Alternativa: usa uma instrução de entrada
ENTRYPOINT ["python3", "app.py"]
```

## 🗂️ **Comandos Básicos de Docker Volume**

### Criar e Gerenciar Volumes

- **Listar volumes existentes:**
  ```bash
  docker volume ls
  ```
- **Criar um volume:**
  ```bash
  docker volume create <nome_volume>
  ```
- **Inspecionar um volume:**
  ```bash
  docker volume inspect <nome_volume>
  ```
- **Remover um volume:**
  ```bash
  docker volume rm <nome_volume>
  ```

### Usar Volumes em Containers

- **Montar um volume em um container:**
  ```bash
  docker run -v <nome_volume>:/caminho/no/container <imagem>
  ```

- **Montar um diretório local como volume:**
  ```bash
  docker run -v /caminho/local:/caminho/container <imagem>
  ```

