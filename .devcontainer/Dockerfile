FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

RUN apt-get -q update &&\
  apt-get -qy install software-properties-common vim unzip jq

USER vscode

RUN sudo mkdir /workspace

RUN echo 'export PROMPT_COMMAND="history -a"' >> ~/.bashrc &&\
  echo 'HISTFILE=/home/vscode/.history/bash_history' >> ~/.bashrc &&\
  echo 'HISTSIZE=-1' >> ~/.bashrc &&\
  echo 'HISTFILESIZE=-1' >> ~/.bashrc &&\
  echo 'HISTTIMEFORMAT="%F, %T "' >> ~/.bashrc

RUN echo 'HISTFILE=/home/vscode/.history/zsh_history' >> ~/.zshrc &&\
  echo 'HISTSIZE=1000000000' >> ~/.zshrc &&\
  echo 'HISTFILESIZE=1000000000' >> ~/.zshrc &&\
  echo 'setopt HIST_IGNORE_ALL_DUPS' >> ~/.zshrc &&\
  echo 'setopt INC_APPEND_HISTORY' >> ~/.zshrc &&\
  echo 'HISTTIMEFORMAT="%F, %T "' >> ~/.zshrc
