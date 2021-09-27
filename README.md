## Usage:

### 1. Retrieve CA PKI database directory
### 2. Copy request to CA PKI directory
```cp serverName.req pki/```
### 3. Mount CA PKI dir under container's ```/usr/local/pki``` path
```docker run -it -v $(pwd)/pki:/usr/local/pki```

### 4. Import request
```docker run -it -v $(pwd)/pki:/usr/local/pki pmszmaglinski/easyrsa:latest easyrsa import-req ./serverName.req serverName```

### 5. Sign request
```docker run -it -v $(pwd)/pki:/usr/local/pki pmszmaglinski/easyrsa:latest easyrsa sign-req server serverName```

### 6. Copy certificate to requesting server

### 7. Backup and remove CA PKI database directory