FROM mcr.microsoft.com/devcontainers/java:1-21-bullseye

# Variáveis definidas no devcontainer.json
ARG USUARIO_WILDFLY_NOME
ARG USUARIO_WILDFLY_SENHA

COPY sdkman_config /usr/local/sdkman/etc/config

WORKDIR /opt/jboss

# from https://github.com/jboss-dockerfiles/wildfly/blob/master/Dockerfile
ENV WILDFLY_VERSION 30.0.1.Final
ENV WILDFLY_SHA1 d6827219672cabfd4eca47e5b64699727bb61f0b
ENV JBOSS_HOME /opt/jboss/wildfly

USER root

# Add the WildFly distribution to /opt, and make wildfly the owner of the extracted tar content
# Make sure the distribution is available from a well-known place
RUN cd $HOME \
    && curl -L -O https://github.com/wildfly/wildfly/releases/download/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz \
    && sha1sum wildfly-$WILDFLY_VERSION.tar.gz | grep $WILDFLY_SHA1 \
    && tar xf wildfly-$WILDFLY_VERSION.tar.gz \
    && mv $HOME/wildfly-$WILDFLY_VERSION $JBOSS_HOME \
    && rm wildfly-$WILDFLY_VERSION.tar.gz \
    && chown -R vscode:vscode ${JBOSS_HOME} \
    && chmod -R g+rw ${JBOSS_HOME}

# Adiciona o usuário que vai ser usado pra fazer os deploys
RUN $JBOSS_HOME/bin/add-user.sh -u $USUARIO_WILDFLY_NOME -p $USUARIO_WILDFLY_SENHA
