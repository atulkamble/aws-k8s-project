FROM python:3.9-slim
WORKDIR /app
COPY . . 
RUN pip install --no-cache-dir -r requirements.txt
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "--workers", "2", "app:app"]
EXPOSE 5000