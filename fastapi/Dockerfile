# Etapa 1: builder
FROM python:3.12-slim AS builder

WORKDIR /app

# Dependências necessárias para compilar pacotes Python
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    gcc \
    && rm -rf /var/lib/apt/lists/*

COPY ./app/requirements.txt .

# Instala dependências em um diretório separado
RUN pip install --no-cache-dir --prefix=/install -r requirements.txt

# Etapa 2: runtimeg
FROM python:3.12-slim AS runtime

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Copia dependências instaladas
COPY --from=builder /install /usr/local

# Copia aplicação
COPY ./app .

EXPOSE 8000

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]