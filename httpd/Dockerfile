FROM ubuntu:xenial
RUN apt-get update && \
  apt-get install -y --no-install-recommends apache2 && \
  rm -rf /var/lib/apt/lists/*
EXPOSE 80
CMD ["/bin/bash"]
