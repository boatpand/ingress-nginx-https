# ingress-nginx-https

# create self signed with openssl
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365

# openssl command to unencrpted key
openssl rsa -in key.pem -out unencryed.key

# create secret tls on K8s 
kubectl create secret tls tls-example-ingress --key=unencryed.key --cert=cert.pem
