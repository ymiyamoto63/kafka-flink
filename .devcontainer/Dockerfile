FROM mcr.microsoft.com/devcontainers/python:1-3.11-bullseye

ENV PYTHONUNBUFFERED 1

# [Optional] If your requirements rarely change, uncomment this section to add them to the image.
COPY ../requirements.txt /tmp/pip-tmp/
RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
   && rm -rf /tmp/pip-tmp

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# Docker CLIのインストール
RUN apt-get update && apt-get install -y docker.io

# Docker Composeのインストール
RUN DOCKER_CONFIG=${DOCKER_CONFIG:-/usr/local/lib/docker} \
    && mkdir -p $DOCKER_CONFIG/cli-plugins \
    && curl -SL https://github.com/docker/compose/releases/download/v2.4.1/docker-compose-linux-x86_64 -o $DOCKER_CONFIG/cli-plugins/docker-compose \
    && sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose

# PostgreSQLのクライアントpsqlのインストール
RUN apt-get update && apt-get install -y postgresql-client