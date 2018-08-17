FROM debian:9

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV TZ=Asia/Shanghai
ENV PATH=/opt/conda/bin:$PATH

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update --fix-missing && \
    apt-get install -y bzip2 ca-certificates curl git vim build-essential && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN curl https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda3-4.2.11-Linux-x86_64.sh -o ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy

RUN conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/ && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/ && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/ && \
    conda config --set show_channel_urls yes

COPY pip.conf .

RUN mkdir -p ~/.config/pip && mv pip.conf ~/.config/pip/pip.conf

CMD [ "/bin/bash" ]
