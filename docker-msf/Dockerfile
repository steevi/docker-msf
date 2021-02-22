FROM debian:10

RUN apt update && \
    apt -y upgrade && \
    apt install -y curl gnupg2 && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*


WORKDIR /root

RUN curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && \
    chmod +x msfinstall && \
    ./msfinstall && \
    rm msfinstall

RUN groupadd -r user && useradd -r -g user user
RUN mkdir /home/user && \
    chown -R user:user /home/user

USER user

WORKDIR /home/user

EXPOSE 5443