FROM ubuntu:16.04
LABEL maintainer=alice_k106@naver.com

# Install Python 3
RUN sed -i 's/archive.ubuntu.com/ftp.daum.net/g' /etc/apt/sources.list
RUN apt update && \
  apt install python3 python3-pip -y && \ 
  apt clean autoclean && \
  apt autoremove --yes && \
  rm -rf /var/lib/{apt,dpkg,cache,log}


WORKDIR /root
ADD ["requirements.txt", "app.py", "/root/"]

RUN pip3 install --trusted-host pypi.python.org -r requirements.txt
RUN pip3 install ptvsd

# Run app.py when the container launches
ENTRYPOINT ["python3", "-m", "ptvsd", "--port", "3000", "--host", "0.0.0.0", "/root/app.py"]