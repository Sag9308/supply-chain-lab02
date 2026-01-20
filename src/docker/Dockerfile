# Vulnerable Dockerfile with 2 key security issues
FROM python:3.12-slim
#fix aus CI/CD libc-bin und libc6(aus Debian-OS-layer)
RUN apt-get update \
 && apt-get -y upgrade \
 && apt-get -y dist-upgrade \
 && apt-get -y autoremove --purge \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
COPY app/ /app/
WORKDIR /app
RUN pip install flask requests
EXPOSE 5000
RUN useradd -m -u 1000 appuser && \
    chown -R appuser:appuser /app
USER appuser
CMD ["python", "main.py"]
