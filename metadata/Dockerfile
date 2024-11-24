FROM ghcr.io/compbiocore/ccv_bootcamp_scrna:jul_15_04-31-00_2024

RUN apt-get update && \
	      apt-get -y --no-install-recommends install --fix-missing \
        wget \
        software-properties-common \
        gcc gfortran build-essential \
        libcurl4-openssl-dev \
        zlib1g zlib1g-dev libbz2-dev liblzma-dev libpcre++-dev libpango1.0-dev \
        xorg-dev \
        libglpk-dev \
        libreadline-dev && \
        apt-get clean && rm -rf /var/lib/apt/lists/*
