FROM python:3.9.10-bullseye
#FROM python:3.8
#LABEL maintainer="Udacity"

WORKDIR /app
COPY . /app


RUN pip install --upgrade pip &&\
    pip install --trusted-host pypi.python.org -r requirements.txt

EXPOSE 80
# RUN pip install -r requirements.txt

# command to run on container start
CMD [ "python", "app.py" ]
