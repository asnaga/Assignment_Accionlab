# Assignment_Accionlab
for Test

#Base Image
FROM nginx:1.19-alpine

#for Security Best Practice will use non-root user
USER:nginx

#Use RUN instructon
RUN addgroup -S nginx_group && adduser -S nginx_user -G nginx_group

#Set woring Directory
WORDIR /user/share/nginx/html

#Copy custom configuration files
COPY nginx.conf /etc/nginx/nginx.conf
COPY index.html /user/share/nginx/html

#Change Ownership to non-root user
RUN chown -R nginx_user:nginx_group /user/share/nginx/html

#Ensure minimal privalage execution
USER nginx_user

#Expose default Nginx port
EXPOSE 80

#Run Nginx
CMD ["nginx", "-g" "daemon off;"]

---------------------------------------
#Scan the Image:
docker build -t my-nginx .
docker scan my-nginx
------------------------------
#Bulild & Run the Image
docer build -t my-nginx
docer run -d -p 8080:80 my-nginx
------------------------------------
#check
http://localhost:8080

E
