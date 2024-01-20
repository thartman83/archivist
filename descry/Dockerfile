FROM python:3.11-slim-bullseye

WORKDIR /

RUN apt-get update && apt-get install -y \
    sane \
    sane-utils \
    libsane-dev \
    gcc \
    git \
    sane-airscan \
    curl \
    iputils-ping \
    && rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 --branch main https://github.com/thartman83/archivist-descry.git /app

RUN pip3 install -r /app/requirements.txt

EXPOSE 5000

CMD [ "python3", "/app/run.py" ]
