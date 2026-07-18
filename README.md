# Multi-Stage Python & Nginx Proxy

Este projeto demonstra a criação de uma API em Python (FastAPI) otimizada utilizando **Multi-Stage Builds** no Docker, com o Nginx atuando como servidor de proxy reverso. 

O objetivo principal do Multi-Stage Build aqui é reduzir drasticamente o tamanho final da imagem de produção, deixando de fora ferramentas de compilação (como `gcc` e `build-essential`) que só são necessárias durante a instalação das dependências.

## 🚀 Tecnologias Utilizadas

* **Python 3.12-slim** (Base da aplicação)
* **FastAPI** (Framework web de alta performance)
* **Nginx** (Proxy reverso e servidor web)
* **Docker & Docker Compose** (Containerização e orquestração)

## 📁 Estrutura do Projeto

```text
MULTI-STAGES-PYTHON/
├── fastapi/
│   ├── app/
│   │   └── main.py
│   ├── Dockerfile
│   └── requirements.txt
├── nginx/
│   └── default.conf
└── docker-compose.yml