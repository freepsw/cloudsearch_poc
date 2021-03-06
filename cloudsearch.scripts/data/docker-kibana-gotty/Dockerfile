# This Dockerfile was generated from the template at templates/Dockerfile.j2
FROM centos:7
LABEL maintainer "Elastic Docker Team <docker@elastic.co>"
EXPOSE 5601 8088

# Add Reporting dependencies.
RUN yum update -y && yum install -y fontconfig freetype && yum clean all

WORKDIR /usr/share/kibana
RUN curl -Ls https://artifacts.elastic.co/downloads/kibana/kibana-6.2.4-linux-x86_64.tar.gz | tar --strip-components=1 -zxf - && \
    ln -s /usr/share/kibana /opt/kibana

ENV ELASTIC_CONTAINER true
ENV PATH=/usr/share/kibana/bin:$PATH

# Set some Kibana configuration defaults.
COPY config/kibana-oss.yml /usr/share/kibana/config/kibana.yml

# Add the launcher/wrapper script. It knows how to interpret environment
# variables and translate them to Kibana CLI options.
COPY bin/kibana-docker /usr/local/bin/

# Add a self-signed SSL certificate for use in examples.
COPY ssl/kibana.example.org.* /usr/share/kibana/config/

# Install gotty 
RUN curl -o /etc/yum.repos.d/home_radiorabe_misc.repo http://download.opensuse.org/repositories/home:/radiorabe:/misc/CentOS_7/home:radiorabe:misc.repo

RUN yum install -y gotty-bin

# Provide a non-root user to run the process.
RUN groupadd --gid 1000 kibana && \
    useradd --uid 1000 --gid 1000 \
      --home-dir /usr/share/kibana --no-create-home \
      kibana
USER kibana


CMD ["/bin/bash", "/usr/local/bin/kibana-docker"]
