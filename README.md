# Ollama + Open WebUI with GPU Support (Docker Compose)

This project sets up a local AI model serving stack using [Ollama](https://ollama.com/) and [Open WebUI](https://github.com/open-webui/open-webui) with Docker Compose. It includes support for NVIDIA GPUs and persistent volumes with custom names.

## Features

- **Ollama**: Efficient local LLM runtime with GPU acceleration (via NVIDIA Docker).
- **Open WebUI**: A sleek, powerful web-based interface for interacting with your models.
- **Custom Volumes**: Named volumes for persistent data storage.
- **Cross-Origin Access**: Configured with permissive CORS for local development.
- **Bridge Network**: Isolated network for inter-container communication.

## Requirements

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- NVIDIA GPU drivers and [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/dzieciolowski/ollama-openwebui-docker.git
   cd ollama-openwebui-docker
   ```

2. Start the services:

   ```bash
   docker compose up -d
   ```

3. Access the Web UI:

   - Ollama API: [http://localhost:11434](http://localhost:11434)
   - Open WebUI: [http://localhost:3000](http://localhost:3000)

## Volume Info

| Volume Name       | Path Inside Container         | Description                    |
|-------------------|-------------------------------|--------------------------------|
| `ollama-data`     | `/root/.ollama`               | Ollama model and config data   |
| `open-webui-data` | `/app/backend/data`           | Open WebUI user data           |

## GPU Support

This setup includes a deployment section to enable NVIDIA GPU access. Make sure your system is properly configured with:

```bash
docker run --rm --gpus all nvidia/cuda:12.8.1-base-ubuntu22.04 nvidia-smi
```

You should see your GPU listed.

## Notes

- This setup allows `CORS` from any origin (`*`) for easier testing. Adjust as needed for production use.
- `extra_hosts` is configured for Docker Desktop compatibility.

## License

MIT License. See `LICENSE` for details.
