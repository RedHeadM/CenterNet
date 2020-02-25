FROM pytorch/pytorch:latest
# install

RUN apt-get update --fix-missing
RUN apt install -y build-essential
RUN apt-get install -y manpages-dev
RUN apt-get install -y protobuf-compiler python-pil python-lxml git wget unzip screen vim libgtk2.0-dev

#USER app
WORKDIR /app/

#RUN mkdir /app



# Make RUN commands use `bash --login`:
#SHELL ["/bin/bash", "--login", "-c"]

# Anaconda installing
#RUN wget https://repo.continuum.io/archive/Anaconda3-5.0.1-Linux-x86_64.sh
#RUN bash Anaconda3-5.0.1-Linux-x86_64.sh -b
#RUN rm Anaconda3-5.0.1-Linux-x86_64.sh
#RUN conda update -n base -c defaults conda
# Set path to conda
#ENV PATH /root/anaconda3/bin:$PATH
#ENV PATH /home/app/anaconda3/bin:$PATH
#RUN conda create --name CenterNet python=3.6
#RUN conda init bash
#RUN conda activate CenterNet
#RUN ls ~/anaconda3/
#ENV PYTORCH ~/anaconda3/envs/CenterNet/lib/python3.6/site-packages/
RUN pip install torch==0.4.1 torchvision 
RUN python -c "import torch; print(torch.__version__)"
RUN python -c "import torch; import os; print(os.path.abspath(torch.__file__))"
RUN sed -i "1254s/torch\.backends\.cudnn\.enabled/False/g" /opt/conda/lib/python3.7/site-packages/torch/nn/functional.py

COPY ./requirements.txt /tmp/requirements.txt
#COPY . /tmp/
ENV CenterNet_ROOT /app
RUN git clone https://github.com/xingyizhou/CenterNet /app
RUN pip install -r /tmp/requirements.txt
RUN pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI
#WORKDIR /app/src/lib/models/networks/DCNv2
#RUN ./make.sh
#WORKDIR APP


#WORKDIR /tmp
#RUN python load_pretrained.py
#WORKDIR /app
ENTRYPOINT ["/bin/bash"]

