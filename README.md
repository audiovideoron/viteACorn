# viteAcorn

Orchestrate and unify Vite (frontend) + Uvicorn (FastAPI backend) with synchronized logging, port-management, and hot-reload support.

---

## Features

1. **Single-command startup** of both servers with `--reload`.  
2. **Structured JSON logging** for easy parsing and integration.  
3. **Port-availability checks** (5173 & 8000) before launch.  
4. Graceful shutdown on SIGINT, or manual kill by port.  
5. Configurable log directory, file name, and debug level.

---

## Prerequisites

- Python 3.10+  
- Node.js & npm  
- Vite-based frontend project in `./frontend`  
- FastAPI backend entry in `run_servers.py`

---

## Installation

1. **Clone repo**  
   ```bash
   git clone https://github.com/<your-org>/viteAcorn.git
   cd viteAcorn
   ```  
2. **Install Python deps**  
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   ```  
3. **Install frontend deps**  
   ```bash
   cd frontend
   npm install
   cd ..
   ```

---

## Usage

1. **Start both servers** (with auto-reload for backend):  
   ```bash
   python run_servers.py --reload
   ```  
2. **Verify processes**  
   ```bash
   lsof -t -i:8000 | cat   # backend
   lsof -t -i:5173 | cat   # frontend
   ```  
3. **Stop gracefully**: Ctrl +C in terminal.  
4. **Force-kill by port**:  
   ```bash
   kill $(lsof -t -i:8000)
   kill $(lsof -t -i:5173)
   ```

---

## Configuration

| Flag            | Default       | Description                             |
| --------------- | ------------- | --------------------------------------- |
| `--reload`      | false         | Enable Uvicorn auto-reload              |
| `--log-dir`     | `logs/`       | Directory for `.log` files              |
| `--log-name`    | `server`      | Base name for log files                 |
| `--no-log-file` | false         | Disable writing to log file             |
| `--debug`       | false         | Set log level to DEBUG                  |

---

## Contributing

1. Fork the repo.  
2. Create a branch: `git checkout -b feature/xyz`.  
3. Commit changes with clear message.  
4. Open a PR against `main`.

---

## License

This project is licensed under the **MIT License**.  
See [LICENSE](LICENSE) for full text.


