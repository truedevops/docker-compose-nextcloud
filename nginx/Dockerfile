FROM nginx:latest
#MAINTAINER nickname <my-email@domain>

RUN rm /etc/nginx/conf.d/default.conf \
	&& rm /etc/nginx/nginx.conf
COPY ./conf/site.conf /etc/nginx/conf.d/
COPY ./conf/nginx.conf /etc/nginx/nginx.conf

EXPOSE 80 443
#EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
