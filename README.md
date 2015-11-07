# Docker-Modulus
Tiny node+npm image based on alpine linux with modulus installed


## Usage

_from your project root_

~~~sh
# create an ephemeral container for deploying to modulus
docker run --rm -it -v "$PWD":/app -w /app theremix/docker-modulus

# (inside the container) login to modulus
/app # modulus login

# (inside the container) deploy to modulus
/app # modulus deploy

# (inside the container) view the most recent logs from modulus
/app # modulus project logs
~~~
