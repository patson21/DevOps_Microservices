FROM python:3.9.10-bullseye

WORKDIR /app

COPY . flask_app/web.py /app
COPY . nlib /app

RUN pip install --upgrade pip &&\
    pip install --trusted-host pypi.python.org -r requirements.txt

EXPOSE 80

CMD ["python", "web.py"]