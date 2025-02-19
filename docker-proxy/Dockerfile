FROM debian:buster

RUN apt-get update -y -q && apt-get install -y -q \
    sudo nano git curl wget build-essential python2 python2-dev python3-pip

RUN curl -k -sS https://bootstrap.pypa.io/pip/2.7/get-pip.py -o /tmp/get-pip.py \
    && python2 /tmp/get-pip.py \
    && rm /tmp/get-pip.py 

RUN python2 -m pip install --upgrade pip setuptools wheel \
    && python2 -m pip install distorm3 pycryptodome yara-python pillow openpyxl ujson pytz

RUN git clone https://github.com/volatilityfoundation/volatility.git /volatility \
    && cd /volatility && python2 setup.py install

RUN echo '#!/bin/bash\npython2 /volatility/vol.py "$@"' > /usr/local/bin/volatility \
    && chmod +x /usr/local/bin/volatility

# make work dir
RUN mkdir -p /workspace/
VOLUME /workspace/
WORKDIR /workspace/

CMD ["/bin/bash"]

