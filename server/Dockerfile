    FROM python:3.12.0-slim-bookworm

    ENV PYTHONUNBUFFERED=1
    ENV PYTHONDONTWRITEBYTECODE=1

    WORKDIR /app

# Copiar e instalar las dependencias
    COPY requirements.txt /app/requirements.txt
    RUN pip install --no-cache-dir -r requirements.txt

# Copiar el resto del proyecto
    COPY . /app/

# Exponer el puerto de Gunicorn
    EXPOSE 8000

# Dar permisos al script de inicio
    RUN chmod +x /app/entrypoint.sh

    ENTRYPOINT ["/bin/bash", "/app/entrypoint.sh"]

    CMD ["gunicorn", "--bind", "0.0.0.0:8000", "--workers", "3", "djangoproj.wsgi:application"]
