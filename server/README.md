Copy `secrets_example.json` to `data/secrets.json` and add a Gemini API key to `gemini_accounts`.

Start the backend with Docker Compose:

```sh
docker compose -f docker-compose.production.yml up --build -d
```

The handler uses Google's `gemini-3.5-flash-lite` model by default. Set `GEMINI_MODEL` on the `handler` service to use another model that is currently available to your Gemini API key.

The HTTP API listens on port 80. Redis data and server secrets are stored in `./data`.
