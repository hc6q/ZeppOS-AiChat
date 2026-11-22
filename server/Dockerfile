FROM python:3.12-slim

WORKDIR /app

RUN apt-get update \
    && apt-get install --no-install-recommends -y curl libopus0 \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt /app
RUN --mount=type=cache,target=/root/.cache/pip \
    pip3 install -r requirements.txt

COPY . /app/
ENV PYTHONPATH=/app

CMD ["gunicorn", "-b", "0.0.0.0:80", "--worker-class", "gevent", "ai_chat_backend:app"]
