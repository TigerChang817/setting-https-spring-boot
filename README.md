# setting-https-spring-boot godaddy #windows server #aws

after buying ssl certificate from GoDaddy:


***step1.  `openssl genrsa -des3 -out mydomain.key 2048`***

input some value & 
create private.key



***step2.  `openssl req -new -key mydomain.key -out server.csr`***

create server.csr



***step3.  open server.csr to get code and copy all to Godaddy website to get crt files back***



***step4.  get 1 file (not gd_bundle-g2-g1.crt) `openssl pkcs12 -export -clcerts -in xxxxxxx.crt -inkey mydomain.key -out server.p12`***

 to get server.p12

***step5.  copy server.p12 to src/main/resources  (the folder which contains application.properties)***



***step6.  setting application.properties***

` server.port=443`
 
 `erver.ssl.key-store:classpath:server.p12`
 
 `server.ssl.key-store-password:password`
 
 `server.ssl.keyStoreType:PKCS12`
 
 `server.ssl.keyAlias:1`
 

***step7.  start up your web application & success!!!!!!!!!!!!!!!!!***
