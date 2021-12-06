
# Alternate Lemmy docker and vscode instructions

I like to be able to run a rust app with cargo run and not rebuild images. Even if it's quick.

This alternate docker method mounts the lemmy code into a container that installs all your dependencies.

To get started you need a couple things installed on your machine;

1. [Docker](https://www.docker.com)

For the ui features; 

2. [VSCode](https://code.visualstudio.com/)

3. [Remote Container Plugin](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Instructions

Clone lemmy down,

`git clone https://github.com/LemmyNet/lemmy.git lemmy`

`cd lemmy; # go into lemmy the directory`

`clone down this repo into the docker directory`

`git clone git@github.com:bigOconstant/lemmy-docker-debug.git docker/debug`

Build the image; builds a arch linux container with a suder user name developer

`docker-compose -f docker/debug/docker-compose.yml build`

Do house keeping stuff the same as other methods.

`mkdir -p docker/debug/volumes/pictrs`

`sudo chown -R 991:991 docker/debug/volumes/pictrs`

You can go ahead and test this with the terminal if you don't want to use vscode. do do that,

`docker-compose -f docker/debug/docker-compose.yml up -d`

`docker-compose -f docker/debug/docker-compose.yml exec lemmy /bin/bash`

Might need to update rust;

`rustup update`

Ok now you can just run 

`cargo run`

And you can visit the ui at,

`0.0.0.0:1236`


You can stop the container with;

`docker-compose -f docker/debug/docker-compose.yml down`

## Run in VSCode

If you would like a whole development environment based on vscode with all plugins auto installed continue to the next section.


Bring down the containers

`docker-compose -f docker/debug/docker-compose.yml down`


From the root directory of the lemmy code base, copy the devcontainer and vscode directories from the debug section to the root.

`cp -a docker/debug/devcontainer/ ./.devcontainer`

`cp -a docker/debug/vscode/ ./.vscode`

Now you can open up the project from vscode. VSCode will actually be running inside a arch container.

Type `F1` and select `Reopen in container`

![](.assets/picture1.jpg)

