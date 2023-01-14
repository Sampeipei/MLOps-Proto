FROM python:3.9
USER root

RUN apt-get update
RUN apt-get -y install --no-install-recommends \
    locales \
    vim less \
    libgl1-mesa-dev

RUN localedef -f UTF-8 -i ja_JP ja_JP.UTF-8

ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL ja_JP.UTF-8
ENV TZ JST-9
ENV TERM xterm

RUN pip install --upgrade pip
RUN pip install --upgrade setuptools

COPY ./env/requirements.txt .
RUN  pip install -r requirements.txt

# path
RUN mkdir /workspace
RUN mkdir /workspace/data
RUN mkdir /workspace/notebook
RUN mkdir /workspace/logs
WORKDIR /workspace

# run
ENTRYPOINT ["jupyter-lab", "--NotebookApp.token=''", "--allow-root", "--no-browser", "--port", "8888", "--ip=0.0.0.0"]