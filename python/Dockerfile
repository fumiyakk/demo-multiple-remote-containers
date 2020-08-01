FROM python:buster

WORKDIR /

RUN apt-get update \
    && apt-get install -y --no-install-recommends vim \
    && rm -rf /var/lib/apt/lists/*

COPY .config/flake8 /root/.config/flake8

# git
RUN wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -O ~/.git-completion.bash
RUN chmod a+x ~/.git-completion.bash
RUN echo "source ~/.git-completion.bash" >> ~/.bashrc
RUN wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh -O ~/.git-prompt.sh
RUN chmod a+x ~/.git-prompt.sh
RUN echo "source ~/.git-prompt.sh" >> ~/.bashrc

# poetry
RUN curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python
ENV PATH="${PATH}:/root/.poetry/bin"
RUN poetry config virtualenvs.create false
RUN poetry completions bash > /etc/bash_completion.d/poetry.bash-completion

COPY pyproject.toml poetry.loc* /

RUN poetry install --no-root