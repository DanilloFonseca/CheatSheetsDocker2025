# Docker Network Cheat Sheet

## 🌐 **Tipos de Redes no Docker**

### 1. **Bridge (Padrão)**

- **Descrição:**
  - Rede isolada criada pelo Docker.
  - Containers na mesma bridge podem se comunicar entre si.
  - Ideal para ambientes onde os containers devem se comunicar apenas entre si e com o host.

- **Comandos:**

  - **Listar redes Docker:**
    ```bash
    docker network ls
    ```

  - **Criar uma rede bridge personalizada:**
    ```bash
    docker network create -d bridge minha_bridge
    ```

  - **Executar um container conectado a uma rede bridge:**
    ```bash
    docker run -d --network minha_bridge nginx
    ```

  - **Inspecionar detalhes de uma rede:**
    ```bash
    docker network inspect minha_bridge
    ```

  - **Conectar um container a uma rede existente:**
    ```bash
    docker network connect minha_bridge <container_id|nome>
    ```

  - **Desconectar um container de uma rede:**
    ```bash
    docker network disconnect minha_bridge <container_id|nome>
    ```

  - **Remover uma rede:**
    ```bash
    docker network rm minha_bridge
    ```

---

### 2. **Host**

- **Descrição:**
  - O container compartilha diretamente a interface de rede do host.
  - Sem isolamento de rede.
  - Útil para casos que exigem alto desempenho em comunicação de rede.

- **Comandos:**

  - **Executar um container usando a rede do host:**
    ```bash
    docker run -d --network host nginx
    ```

  - **Verificar containers em rede host:**
    ```bash
    docker network inspect host
    ```

> **Nota:** No modo `host`, as portas do container não são mapeadas, pois ele compartilha as interfaces do host diretamente.

---

### 3. **Macvlan**

- **Descrição:**
  - Permite atribuir um endereço IP diretamente à interface de rede do container.
  - Útil para integração com redes físicas.
  - Cada container pode ter seu próprio IP na mesma sub-rede do host.

- **Comandos:**

  - **Criar uma rede macvlan:**
    ```bash
    docker network create -d macvlan \
      --subnet=192.168.1.0/24 \
      --gateway=192.168.1.1 \
      -o parent=eth0 minha_macvlan
    ```

  - **Executar um container em uma rede macvlan:**
    ```bash
    docker run -d --network minha_macvlan --ip 192.168.1.100 nginx
    ```

  - **Inspecionar uma rede macvlan:**
    ```bash
    docker network inspect minha_macvlan
    ```

  - **Remover uma rede macvlan:**
    ```bash
    docker network rm minha_macvlan
    ```

> **Nota:** Certifique-se de que a interface (`parent`) especificada está ativa no host e na mesma sub-rede.

---

## 📊 **Resumo de Redes Docker**

| Tipo de Rede | Isolamento | Comunicação com Host | Uso Principal                          |
|--------------|------------|-----------------------|----------------------------------------|
| **bridge**   | Sim        | Via mapeamento de portas | Containers isolados com comunicação interna |
| **host**     | Não        | Direta                 | Máximo desempenho e acesso direto ao host |
| **macvlan**  | Sim        | Direta com IP próprio  | Containers com IPs próprios na rede física |
