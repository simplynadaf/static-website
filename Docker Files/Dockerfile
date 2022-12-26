FROM amazonlinux:latest

#Install Dependencies 
RUN yum update -y && \
    yum install -y httpd && \
    yum search wget && \
    yum install wget -y && \
    yum install unzip -y 

#Change directory 
RUN cd /var/www/html

#Download Webfiles
RUN wget https://github.com/simplynadaf/static-website/archive/refs/heads/main.zip

# unzip folder
RUN unzip main.zip

# copy files into html directory
RUN cp -r static-website-main/* /var/www/html/

# remove unwanted folder
RUN rm -rf static-website-main main.zip

#Exposes port 80 on the container 
EXPOSE 80

#Set the default application that will start when the container start 
ENTRYPOINT ["/usr/sbin/httpd","-D","FOREGROUND"]
