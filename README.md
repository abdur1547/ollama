# Ollama + Open WebUI (GPU Support)

This project runs [Ollama](https://ollama.ai) with GPU acceleration and [Open WebUI](https://github.com/open-webui/open-webui) inside Docker containers.  
It gives you a local API for running LLM models and a web interface to interact with them.

---

## Features

- GPU support using NVIDIA runtime
- Persistent storage for both Ollama and Open WebUI
- Easy access via REST API and browser UI
- Ready-to-use with a single `docker compose up`

---

## Requirements

- Docker and Docker Compose installed
- NVIDIA GPU drivers installed on the host
- [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) installed

---

## Getting Started

### Clone the Repository

```bash
git clone git@github.com:abdur1547/ollama.git
cd ollama
```

---

## Basic Commands

### Start the Containers

```bash
docker compose up -d
```

### Stop the Containers

```bash
docker compose down
```

### Restart the Containers

```bash
docker compose restart
```

### View Logs

```bash
docker compose logs -f
```

---

## Access Points

- **Ollama API:** [http://localhost:11434](http://localhost:11434)  
  You can send requests using `curl` or any HTTP client.

- **Open WebUI:** [http://localhost:8090](http://localhost:8090)

  A graphical web interface for interacting with models.

---

## Running Commands Inside Ollama

- **Run a model interactively:**

  ```bash
  docker compose exec ollama ollama run llama3.2
  ```

- **Pull a model:**

  ```bash
  docker compose exec ollama ollama pull llama3.2
  ```

- **List all available models:**
  ```bash
  docker compose exec ollama ollama list
  ```

---

## Example API Request

Send a prompt to Ollama via API:

```bash
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2",
  "prompt": "Write a short poem about the sea."
}'
```

---

## Persistent Data

- **Ollama data:** stored in `./ollama_data`
- **Open WebUI data:** stored in `./open_webui_data`

These volumes ensure models and settings persist across container restarts.

---

## Useful Commands

- **List running containers:**

  ```bash
  docker ps
  ```

- **Check logs for a specific service:**

  ```bash
  docker compose logs -f ollama
  docker compose logs -f open-webui
  ```

- **Verify GPU availability inside Docker:**
  ```bash
  docker run --rm --gpus all nvidia/cuda:12.2.0-base nvidia-smi
  ```
