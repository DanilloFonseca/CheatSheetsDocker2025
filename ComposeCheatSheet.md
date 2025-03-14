# 🐳 Docker Compose Cheat Sheet

Docker Compose é uma ferramenta que simplifica a execução de múltiplos containers Docker usando um único arquivo (`docker-compose.yml`). Com ele, você pode gerenciar serviços (bancos de dados, APIs, etc.) de forma organizada.

---

## 📂 1. Comandos Básicos do Docker Compose

### ✅ **Iniciar os containers**
```bash
docker-compose up
```
- **O que faz?**: Inicia todos os serviços definidos no `docker-compose.yml`.
- **Opção útil:**
    ```bash
    docker-compose up -d
    ```
    - `-d`: Executa em segundo plano (modo "detached").

### ⏹️ **Parar os containers**
```bash
docker-compose down
```
- **O que faz?**: Para e remove todos os containers, redes e volumes criados.

### 🔍 **Verificar o status dos containers**
```bash
docker-compose ps
```
- **O que faz?**: Lista os containers em execução.

### 📜 **Ver os logs em tempo real**
```bash
docker-compose logs
```
- **O que faz?**: Exibe os logs de todos os serviços.
- **Opção útil:**
    ```bash
    docker-compose logs -f
    ```
    - `-f`: Segue os logs em tempo real.

### 🛠️ **Executar um comando em um container**
```bash
docker-compose exec <serviço> <comando>
```
- **O que faz?**: Permite executar comandos dentro de um container em execução.
- **Exemplo:**
    ```bash
    docker-compose exec app bash
    ```
    - Abre um terminal dentro do serviço chamado `app`.

### 🔄 **Reiniciar um serviço específico**
```bash
docker-compose restart <serviço>
```
- **O que faz?**: Reinicia um container específico.

---

## 📊 2. Gerenciamento de Imagens e Volumes

### 📦 **Remover containers, volumes e redes órfãos**
```bash
docker-compose down -v
```
- **O que faz?**: Remove tudo, incluindo os volumes associados.


## 📋 3. Comandos Avançados e Úteis

### 🧹 **Limpar containers e recursos não utilizados**
```bash
docker system prune -f
```
- **O que faz?**: Remove containers, redes, imagens e caches que não estão em uso.

### 🏗️ **Recriar containers após modificar o `docker-compose.yml`**
```bash
docker-compose up -d --build
```
- **O que faz?**: Recria os containers aplicando as alterações do arquivo.

### 🔢 **Ver a estrutura de redes Docker Compose**
```bash
docker network ls
```
- **O que faz?**: Lista todas as redes Docker disponíveis, incluindo as criadas pelo Compose.

---

 **Dica Importante:** Sempre que tu fizer alterações no `docker-compose.yml`, use:

```bash
docker-compose up -d --build
```
Para garantir que as mudanças sejam aplicadas.
