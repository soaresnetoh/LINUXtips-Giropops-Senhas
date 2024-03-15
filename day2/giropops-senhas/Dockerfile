FROM python:3.13.0a5-alpine3.19

WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt

ENV REDIS_HOST=redis

EXPOSE 5000

ENTRYPOINT ["python", "-m", "flask", "run", "--host=0.0.0.0"]