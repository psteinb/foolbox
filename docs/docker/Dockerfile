FROM ubuntu:trusty
ENV THEANO_FLAGS='floatX=float32'
ENV KERAS_BACKEND=tensorflow

RUN apt update && apt purge -y python3 && apt install -y python3.5 python3.5-dev wget curl git

RUN python3.5 --version && python3 --version

RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python3.5 ./get-pip.py && pip3 --version && ls -lrth `which pip3` `which pip`

RUN pip3 install -U pip \
    && pip3 install --upgrade numpy \
    && pip3 install --upgrade scipy

RUN git clone https://github.com/bethgelab/foolbox.git /repo
RUN pip3 install -r /repo/requirements-dev-py3.txt \
 && pip3 install -r /repo/requirements-dev.txt

RUN pip3 install --upgrade tensorflow \
    && python3.5 -c 'import tensorflow; print(tensorflow.__version__)'

RUN pip3 install --upgrade theano \
    && python3.5 -c 'import theano; print(theano.__version__)'

RUN pip3 install --upgrade https://github.com/Lasagne/Lasagne/archive/master.zip \
    && python3.5 -c 'import lasagne; print(lasagne.__version__)'

RUN pip3 install http://download.pytorch.org/whl/cpu/torch-1.0.1.post2-cp35-cp35m-linux_x86_64.whl \
    && python3.5 -c 'import torch; print(torch.__version__)'

RUN pip3 install --upgrade keras>=2.1.5 \
    && python3.5 -c 'import keras; print(keras.__version__)'

RUN pip3 install --upgrade mxnet>=1.1.0 \
    && python3.5 -c 'import mxnet; print(mxnet.__version__)'

RUN apt update \
    && apt install -y unzip dpkg \
    && mkdir /tmp/openmpi \
    && cd /tmp/openmpi \
    && wget http://cntk.ai/PythonWheel/ForKeras/depends/openmpi_1.10-3.zip \
    && unzip ./openmpi_1.10-3.zip \
    && dpkg -i openmpi_1.10-3.deb \
    && cd \
    && rm -rf /tmp/openmpi

RUN pip3 install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.3-cp35-cp35m-linux_x86_64.whl \
    && python3.5 -c 'import cntk; print(cntk.__version__)'

RUN pip3 install pytest-faulthandler && pip3 install --upgrade numpy
#CMD python /app/app.py
