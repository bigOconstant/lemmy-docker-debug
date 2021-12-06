
# Lemmy docker debug instructions

git clone https://github.com/LemmyNet/lemmy.git lemmy
cd lemmy
git clone git@github.com:bigOconstant/lemmy-docker-debug.git docker/debug
docker-compose -f docker/debug/docker-compose.yml build
mkdir -p docker/debug/volumes/pictrs
sudo chown -R 991:991 docker/debug/volumes/pictrs
docker-compose -f docker/debug/docker-compose.yml up -d
docker-compose -f docker/debug/docker-compose.yml exec lemmy /bin/bash

Might need to update rust;

rustup update

If the project still doesn't build you can try a nightly rust.

rustup default nightly && rustup update

Now you can start up the rust backend just like any other rust project. All the environement variables are set by docker-compose

cargo run

You can bring down your containers with 

docker-compose -f docker/debug/docker-compose.yml down

## Run in VSCode

If you would like a whole development environment with all plugins auto installed continue to the next section.


