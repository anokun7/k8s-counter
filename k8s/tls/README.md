Create a root certificate and private key to sign the certificates for the services:
```
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -subj '/O=noop Inc./CN=noop.ga' -keyout noop.ga.key -out noop.ga.crt
```
Create a certificate and a private key for demo.noop.ga:
```
openssl req -out demo.noop.ga.csr -newkey rsa:2048 -nodes -keyout demo.noop.ga.key -subj "/CN=demo.noop.ga/O=demo organization"

openssl x509 -req -days 365 -CA noop.ga.crt -CAkey noop.ga.key -set_serial 0 -in demo.noop.ga.csr -out demo.noop.ga.crt
```
