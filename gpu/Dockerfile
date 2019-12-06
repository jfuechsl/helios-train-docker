FROM tensorflow/tensorflow:2.0.0-gpu-py3

COPY requirements.in /build/requirements.in
RUN \
  cd /build && \
  curl -L http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz -o ta-lib-0.4.0-src.tar.gz && \
  tar -xzf ta-lib-0.4.0-src.tar.gz && \
  cd ta-lib/ && \
  ./configure && \
  make && \
  make install && \
  cd /build && \
  rm -rf ta-lib* && \
  pip install --upgrade pip-tools && \
  pip-compile --upgrade --build-isolation --generate-hashes \
  --output-file /build/requirements.txt /build/requirements.in && \
  pip install --upgrade -r /build/requirements.txt
