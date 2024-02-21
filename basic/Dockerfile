FROM debian

RUN apt update

RUN apt install bat jq fzf tree neofetch lsd unzip wget curl htop ncdu vim postgresql postgresql-client tmux git make python3 python3-pip python3-venv nodejs npm zsh neovim -y

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
  unzip awscliv2.zip && \
  ./aws/install && \
  rm awscliv2.zip && \
  rm -rf aws

RUN sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v1.1.5/zsh-in-docker.sh)"

RUN wget https://raw.githubusercontent.com/Ruivalim/dotfiles/main/dot_config/zsh/alias.zsh -P /root
RUN wget https://raw.githubusercontent.com/Ruivalim/dotfiles/main/dot_config/zsh/config.zsh -P /root
RUN wget https://raw.githubusercontent.com/Ruivalim/dotfiles/main/dot_config/zsh/fzf.zsh -P /root

RUN echo "source /root/alias.zsh" >> "$HOME"/.zshrc
RUN echo "source /root/config.zsh" >> "$HOME"/.zshrc
RUN echo "source /root/fzf.zsh" >> "$HOME"/.zshrc

RUN apt autoremove -y \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["sleep", "infinity"]
