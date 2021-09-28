## Usage:

### 1. Generate private key and signing request on requesting server
```openssl genrsa -out serverName.key```

```openssl req -new -key serverName.key -out serverName.req```

### 2. Retrieve CA PKI database directory on signing node

### 3. Copy request to CA PKI directory
```cp serverName.req pki/```

### 4. Mount CA PKI dir under container's ```/usr/local/ca/pki``` path
```docker run -it -v /usr/local/ca/pki:/usr/local/ca/pki```

### 5. Import request
```docker run -it -v /usr/local/ca/pki:/usr/local/ca/pki pmszmaglinski/easyrsa:latest easyrsa import-req ./serverName.req serverName```

### 6.1 Sign request
```docker run -it -v /usr/local/ca/pki:/usr/local/ca/pki pmszmaglinski/easyrsa:latest easyrsa sign-req server serverName```

### 6.2 Sign request for wildcard certificate
```docker run -it -v /usr/local/ca/pki:/usr/local/ca/pki pmszmaglinski/easyrsa:latest easyrsa --subject-alt-name='DNS:home.lan,DNS:*.home.lan' sign-req server serverName```

### 7. Copy certificate to requesting server

### 8. Backup and remove CA PKI database directory