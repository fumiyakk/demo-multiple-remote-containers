FROM golang:buster

WORKDIR /

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      git \
      openssh-client \
      procps \
      ca-certificates \
      curl \
      unzip \
      gnupg \
      vim \
      wget \
 && rm -rf /var/lib/apt/lists/*

# git
RUN wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -O ~/.git-completion.bash
RUN chmod a+x ~/.git-completion.bash
RUN echo "source ~/.git-completion.bash" >> ~/.bashrc
RUN wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh -O ~/.git-prompt.sh
RUN chmod a+x ~/.git-prompt.sh
RUN echo "source ~/.git-prompt.sh" >> ~/.bashrc
