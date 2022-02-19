FROM alpine:latest
USER root
RUN apk update && apk upgrade && \
    apk add --no-cache bash git openssh wget
RUN adduser -s /bin/bash -h /home/dennis -D dennis 

USER dennis
RUN ssh-keygen -P "" -f ~/.ssh/id_rsa
RUN mkdir ~/git-prompt
RUN wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -P ~/git-prompt
RUN wget https://raw.githubusercontent.com/dennisyau1885/git/master/contrib/completion/git-prompt.sh -P ~/git-prompt
RUN wget https://raw.githubusercontent.com/dennisyau1885/git/master/contrib/completion/git_ps1 -P ~/git-prompt
RUN echo 'for f in ~/git-prompt/*; do . $f ; done' >>~/.bashrc
RUN git config --global color.status.added yellow
RUN git config --global color.status.updated yellow
RUN git config --global color.status.untracked dim
