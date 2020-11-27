# python image.
# https://hub.docker.com/_/python
FROM python:3.9-slim

# allow statements and log messages to immediately appear in the knative logs.
ENV PYTHONUNBUFFERED True

# copy local code to the container image.
ENV APP_HOME /app
WORKDIR $APP_HOME
COPY . ./

# install dependencies.
RUN pip install Flask gunicorn

# run the web service on container startup. 
# use gunicorn webserver.
#     1 worker process. 
#     8 threads.
# for environments with multiple CPU cores, increase the number of workers
# to be equal to the cores available.
CMD exec gunicorn --bind :$PORT --workers 1 --threads 8 --timeout 0 main:app