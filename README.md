# Dockerizing a FastAPI Application

1. Build the image:

```bash
docker build -t my-fastapi-app .
```

2. Run the container:

```bash
docker run -p 8000:8000 my-fastapi-app
```