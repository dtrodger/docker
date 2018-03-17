FROM python:3.6.1
RUN groupadd flaskgroup && \
   useradd -m -g flaskgroup -s /bin/bash flask && \
   mkdir -p /home/app/web
WORKDIR /home/app/web
COPY setup/requirements.txt /home/app/web
COPY gitkey /root/.ssh/id_rsa
RUN chmod 700 ~/.ssh && chmod 600 ~/.ssh/id_rsa && \
    ssh-keyscan -t rsa bitbucket.org >> ~/.ssh/known_hosts && \
    pip install --no-cache-dir -r requirements.txt
COPY . /home/app/web
RUN chown -R flask:flaskgroup /home
USER flask
