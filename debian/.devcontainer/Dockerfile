# pull official base image
FROM debian:latest

# set working directory
WORKDIR /app

RUN apt update -y
RUN apt install -y git ssh curl zsh 

# Change Shell
RUN sed -i 's#^root.*#root:x:0:0:root:/root:/bin/zsh#' /etc/passwd

# Install OMZ
RUN sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Install P10K
RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git /root/.oh-my-zsh/custom/themes/powerlevel10k

# Install ZSH Auto Suggestions
RUN git clone https://github.com/zsh-users/zsh-autosuggestions /root/.oh-my-zsh/custom/plugins/zsh-autosuggestions

# Copy Configurations
COPY .devcontainer/zshrc /root/.zshrc
COPY .devcontainer/p10k.zsh /root/.p10k.zsh

# add app
COPY . ./
