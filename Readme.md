## Topics Discussed
- Introduction
setup traefik on top of localhost
- 3 steps -
setup traefik in docker-compose,
expose traefik on localhost,
deploy a backend server behind traefik reverse proxy

- Show boilerplate docker compose
- Setup etc/hosts

- Setup traefik image
- generate certs
- create configuration file

- Setup backend image
- setup traefik labels
- browser demostration

## Steps for localhost certificate

1. Update /etc/hosts
2. openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout localhost.key \
  -out localhost.crt \
  -subj "/CN=dev.localhost" \
  -addext "subjectAltName=DNS:dev.localhost,DNS:*.dev.localhost"
3. Add trust certificate -
   1. sudo security add-trusted-cert -d -r trustRoot -k Library/Keychains/System.keychain traefik.localhost.crt
   2. sudo cp traefik.localhost.crt /usr/local/share/ca-certificates/ && sudo update-ca-certificates
