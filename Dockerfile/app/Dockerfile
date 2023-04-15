#pulling rokylinux with specific version (cannot download latest image at the moment)
FROM rockylinux:9.1.20230215
#install java jdk
RUN dnf install java-11-openjdk-devel -y
#install git
RUN dnf install git -y
#change workdir to /app folder
WORKDIR /app
#clone code of java app console
RUN git clone https://github.com/qtanit87/JavaApp.git
#change workdir to java app console directory
WORKDIR  /app/JavaApp
#compile code
RUN javac app.java
#run command "java app" when starting container
ENTRYPOINT ["java", "app"]