FROM registry.eng.hortonworks.com/hortonworks/hdp-centos7:3.0.0.0-829

MAINTAINER Yanbo Liang "yliang@hortonworks.com"

RUN pip install --upgrade pip
RUN pip uninstall --yes protobuf; exit 0
RUN pip install tensorflow keras
RUN pip install Pillow
RUN pip install pandas
RUN pip install h5py
