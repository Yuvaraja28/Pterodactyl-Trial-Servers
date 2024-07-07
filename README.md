# Pterodactyl Trial Servers

Pterodactyl Trial Servers is a web dashboard developed for Pterodactyl cloud hosting companies. It allows users to create trial servers without requiring an account in the Pterodactyl panel. Built with Vite, React.js, Express.js, WebSocket, Pterodactyl, and reCaptcha, this project aims to streamline server trial setups.

## Features

- Create trial servers without a Pterodactyl account
- Utilizes Vite, React.js, Express.js, WebSocket, Pterodactyl, and reCaptcha
- Customizable dashboard for server management

## Getting Started

To get started with Pterodactyl Trial Servers, clone the repository and follow the setup instructions in the `README` file.

## Installation

1. Clone the repository.
2. Install dependencies using `npm install`.
3. Configure environment variables.
4. Build Vite with `npm run build`.
5. Start the Production server with `npm run start`.

> or

1. Clone the repository.
2. Configure environment variables.
3. Run `node start.js` which will install all dependencies, Builds the files, then starts the Production server.

## ENV Configuration

Refer `.env.txt` file for ENV Structure

## MongoDB Configuration 

Database Structure

```
{Database} -> {Collection}
```

```
Servers -> Categories
```

```json
{ 
  # id with * is a Wild Card which selects all the Trial Servers
  "id": "*", # Category ID which should be passed in Trial Server Object.
  "name": "All" # Category Name.
}
{
  "id":"plugin",
  "name":"Vanilla"
}
```


```
Servers -> List
```

Trial Server Object that should be inserted inside the `List` Collection in MongoDB

```json
{
  "name": "Trial Server Name",
  "description": "Description about this Trial Server",
  "price": "$99.99",
  "category": ["*", "mod"], # List of categories you want to put into.
  "popular": false,
  "server_data": {
    "user": 5, # Pterodactyl User ID under which this trial server should be created.
    "egg": 18, # Pterodactyl Egg ID for this trial server.
    "docker_image": "ghcr/... docker_image of the egg file",
    "startup": "java... startup command of the egg file",
    "environment": {
      "SERVER_JARFILE": "server.jar",
      "MC_VERSION": "latest",
      ... # Pass all `required` field ENV variables of the Egg file
    },
    "limits": { # Passing 0 value in limits denotes infinity resource
      "cpu": 200,
      "memory": 4096,
      "disk": 4096,
      "swap": 512,
      "io": 500
    },
    "feature_limits": { # Passing 0 value in feature_limits denotes 0
      "databases": 0,
      "backups": 0
    },
    "node": 2 # Pterodactyl Node ID under which this trial server should be created.
  },
  "expiry": 5, # Expiry time in hrs so that the trial server should be automatically purged by the server. Eg. here its 5hrs
  "links": {
    "Yuvaraja": "https://yuvaraja.tech",
    "Devley": "https://devley.yuvaraja.tech"
    ... # Pass the links in the same format so that can be showed in your server create section.
  }
}
```

## Contributing

Contributions are welcome! Please fork the repository and submit pull requests.

## Live Working

[trial.mysticlouds.com](https://trial.mysticlouds.com)

## Working

| HomePage                                                                                                                                        | Server Create                                                                                                                                     | Server Control                                                                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| ![pterodactyl-trial-servers-home](https://github.com/Yuvaraja28/Pterodactyl-Trial-Servers/assets/64340067/4c14e295-cabd-4501-a0d6-deab254ab555) | ![pterodactyl-trial-servers-create](https://github.com/Yuvaraja28/Pterodactyl-Trial-Servers/assets/64340067/9a3eac41-a8a7-4528-9160-1eef8d818035) | ![pterodactyl-trial-servers](https://github.com/Yuvaraja28/Pterodactyl-Trial-Servers/assets/64340067/de432522-35e9-4271-927d-f832888d63da) |

## License

This project is licensed under Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0).
