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

### Other commands

~~~sh
modulus project restart

modulus project stop

modulus project start
~~~


## Environment Variables

### Configure Environment variables

#### Create an Environment variable

~~~sh
modulus env set CUSTOM_VAR_C custom_value_3
Setting CUSTOM_VAR_C for project ExampleProject
[✓] Successfully set environment variable.
~~~

Your project environment variable will be accessible via process.env.CUSTOM_VAR_C.

#### List Current Variables

~~~sh
modulus env list
Project ExampleProject Environment Variables
NODE_ENV = production
CUSTOM_VAR_A = custom_value
CUSTOM_VAR_B = custom_value_2
~~~

#### Delete an Environment variable

~~~sh
modulus env delete CUSTOM_VAR_C
~~~

## Mongo DB

You can add a MongoDB to your project with a simple command:

~~~sh
modulus addons add mongo:base
~~~

This will create an `ENV` variable called `MONGO_URL`. You can use this with any node.js MongoDB client.

~~~js
var MongoClient = require('mongodb').MongoClient;

MongoClient.connect( process.env.MONGO_URI, function(err, db) {
  // Query the DB.

} );
~~~

More info here [nodeknockout.com/deploying](http://www.nodeknockout.com/deploying)
