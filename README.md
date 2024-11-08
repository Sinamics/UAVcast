# ⚠️ DEPRECATED

This repository has been archived and is no longer maintained. No further updates, bug fixes, or support will be provided.

## Status

- 🔒 **Archived**: This repository is now in read-only mode
- ⛔ **No Maintenance**: No further development or updates will be made
- 🚫 **No Support**: Issues and pull requests are no longer accepted

# uavcast-community edition - companion software for remote :helicopter: :boat: :red_car:

uavcast-community edition is an application that provides an easy method for streaming mavlink (telemetry) data and video over a LTE/4G or WiFi network.

:warning: This project is still in development and does not have a stabel version yet. Feel free to make improvements and provide a PR.

<br />

## :hammer: Codebase

:white_check_mark: Express nodejs (Typescript)\
:white_check_mark: Typeorm && sqlite3 database\
:white_check_mark: React (Typescript)\
:white_check_mark: Semantic-ui-react\
:white_check_mark: graphql / type-graphql && codegen

<br />

## :wrench: Developer Instructions

### Prerequisites

:warning: These packages needs to be installed

:heavy_plus_sign: Docker\
:heavy_plus_sign: Docker Compose\
:heavy_plus_sign: Visual Studio Code

### :computer: Open the repo with Visual Studio Code

Upon opening, you should be prompted to open the project in a **remote container**. This will build a container on top of the base uavcast-community container with all the development dependencies installed. This ensures everyone uses a consistent development environment without the need to install any dependencies on your host machine.

If vscode does not start the remote container automatically, use hotkeys: <kbd>Ctrl</kbd> + <kbd>shift</kbd> + <kbd>p</kbd> and select <kbd>Remote-Container: Rebuild and Reopen container</kbd>

After starting the container for the first time, it will install some additional package, give it few minutes to complete.
![install](https://i.ibb.co/6XWg1sV/Skjermbilde-2022-01-19-202346.png)

<br />

### Run uavcast-community from the command line

VSCode will start the docker compose file for you and open a terminal window connected to `/app/uavcast` folder.

:heavy_minus_sign: Run `cd backend && npm install`\
:heavy_minus_sign: Run `cd frontend && npm install`\
:heavy_minus_sign: Run `npm start` from the project root to start both frontend & backend.

### Supervisor

Uavcast-community uses a supervisor container to manage the application update ect. Supervisor is not needed for development.
To run the supervisor, type `cd supervisor && npm install && npm start` from the uavcast-community project root.

### Teardown

After closing VSCode, you may still have containers running. To close everything down, just run\
`docker-compose down -v` to cleanup all containers.

### Making changes

Do not make large sweeping changes. Open a discussion on GitHub for any large or architectural ideas.
Ensure lint passes. `npm run lint` This command will ensure basic conformance to styles, applying as many automatic fixes as possible, including Prettier formatting.

### Build docker locally

Use these commands in the project root (!not in the vscode developer container).\
Type `./compile_release.sh` + arguments to genereate local docker image, or you can publish to your own container registery.

Example local build:\
`./compile_release.sh --image_name sinamics/uavcast --version 5.x.x --docker_local`

run docker image locally:

```docker
docker run --restart unless-stopped --name uavcast -d \
    -v uavdata:/app/uavcast/data \
    -v /var/lib/zerotier-one:/var/lib/zerotier-one \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /dev:/dev \
    --privileged=true --net=host [image_name]:[version]
```

### Images

![Map](https://i.ibb.co/1zZTysD/Skjermbilde-2022-01-19-204037.png)
![Dashboard](https://i.ibb.co/7CpNwQS/Skjermbilde-2022-01-19-204107.png)

<br />

### Copyright and License

Uavcast-community is provided under the [the 3-Clause BSD License](https://opensource.org/licenses/BSD-3-Clause).  
