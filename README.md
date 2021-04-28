# Traefik Certificate Extractor

Tool to extract Let's Encrypt certificates from Traefik's ACME storage file.

## Installation
```
git clone https://github.com/bufanda/traefik-certificate-extractor
cd traefik-certificate-extractor
```

## Usage
```
python3 extractor.py [directory]
```
Default input directory is `./data`. The output directories are `./certs` and `./certs_flat`. The certificate extractor will extract certificates from any JSON file in the input directory (e.g. `acme.json`), so make sure this is the same as Traefik's ACME directory.

## Docker
There is a Docker image available for this tool: [bufanda/traefik-certificate-extractor](https://hub.docker.com/r/bufanda/traefik-certificate-extractor).
Example run:
```
docker run --name extractor -d -v /srv/traefik/acme:/app/data -v /srv/extractor/certs:/app/certs bufanda/traefik-certificate-extractor
```

## Output
```
certs/
    example.com/
        cert.pem
        chain.pem
        fullchain.pem
        privkey.pem
    sub.example.nl/
        cert.pem
        chain.pem
        fullchain.pem
        privkey.pem
certs_flat/
    example.com.crt
    example.com.key
    example.com.chain.pem
    sub.example.nl.crt
    sub.example.nl.key
    sub.example.nl.chain.pem
```
