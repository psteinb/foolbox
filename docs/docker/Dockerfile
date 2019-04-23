FROM ubuntu:trusty
ENV THEANO_FLAGS='floatX=float32'
ENV KERAS_BACKEND=tensorflow

RUN python3 --version
RUN pip3 install -U pip \
    && pip3 install --upgrade numpy \
    && pip3 install --upgrade scipy

COPY ../../requirements-dev-py3.txt .
COPY ../../requirements-dev.txt .

RUN pip3 install -r requirements-dev-py3.txt \
 && pip3 install -r requirements-dev.txt

#CMD python /app/app.py