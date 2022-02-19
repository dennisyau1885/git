FROM alpine:latest
USER root
RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash git openssh wget \
    && adduser -s /bin/bash -h /home/gptest -D gptest

USER gptest
RUN ssh-keygen -P "" -f ~/.ssh/id_rsa \
    && mkdir ~/git-prompt \
    && echo 'for f in ~/git-prompt/*; do . $f ; done' >>~/.bashrc \
    && git config --global color.status.branch green \
    && git config --global color.status.added yellow \
    && git config --global color.status.updated yellow \
    && git config --global color.status.untracked dim
COPY git-completion.bash git-prompt.sh git_ps1 /home/gptest/git-prompt
