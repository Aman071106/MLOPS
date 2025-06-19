FROM python:3.8-slim
COPY . /app
WORKDIR /app
RUN pip install --upgrade pip && pip install --no-cache-dir -r requirements.txt
CMD ["python", "app.py"]