FROM jenkins/ssh-agent:latest-debian-jdk17

RUN apt-get update && apt-get install curl unzip -y && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /opt/maven &&\
	cd /opt/maven &&\
	curl https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz -o maven.tar.gz &&\
	tar -zxvf maven.tar.gz --strip-components 1 &&\
	rm -rf maven.tar.gz

RUN mkdir -p /opt/gradle &&\
	cd /opt/gradle &&\
	curl -L https://services.gradle.org/distributions/gradle-8.6-bin.zip -o gradle.zip &&\
	unzip gradle.zip &&\
	rm -rf gradle.zip &&\
	cd gradle* &&\
	mv * ../ &&\
	cd .. &&\
	rm -rf gradle*

RUN PATH="$PATH:/opt/maven/bin:/opt/gradle/bin" && sed -i "s|PATH=.*|PATH=$PATH|g" /etc/environment
