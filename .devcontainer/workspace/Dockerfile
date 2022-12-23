FROM ubuntu:latest

#shをBashに変更
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

RUN apt-get -y update && apt-get -y upgrade
RUN apt-get install sudo

#ユーザー作成
ARG user_name=ubuntu
ARG user_id=1942
ARG group_name=ubuntu
ARG group_id=1942

RUN groupadd -g ${group_id} ${group_name} && \
    useradd -u ${user_id} -g ${group_id} -d /home/${user_name} --create-home --shell /bin/bash ${user_name} && \
    mkdir /home/${user_name}/src
RUN echo "${user_name} ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers && chown -R ${user_name}:${group_name} /home/${user_name}

USER ${user_name}
WORKDIR /home/${user_name}
ENV HOME /home/${user_name}

# Python3
#RUN sudo apt-get install -y python3 python3-pip && pip3 install --upgrade pip

# Rust
#ENV PATH ${HOME}/.cargo/bin:$PATH
#RUN sudo apt-get install curl lldb gcc -y && \
#    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs -o rust.sh && \
#    chmod +x rust.sh && \
#    ./rust.sh -y --default-toolchain stable
