FROM ubuntu
MAINTAINER nikowek@gmail.com

RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    libncurses5-dev \
    libncursesw5-dev

RUN groupadd -r player && useradd -m -g player player
USER player

# Cache buster
ADD https://api.github.com/repos/CleverRaven/Cataclysm-DDA/commits/0.A uuid

RUN cd /home/player && \
    git clone --depth 1 --single-branch --branch 0.A https://github.com/CleverRaven/Cataclysm-DDA.git && \
    cd Cataclysm-DDA/ && \
    make RELEASE=1 LOCALIZE=1 USE_HOME_DIR=1 && \
    rm -rf .git

CMD cd /home/player/Cataclysm-DDA && ./cataclysm

