# Fullstack Fable example

This project shows how Fable can be used fullstack with a node.js server written in F#. This is a variation from Maxime Mangel's [Fableconf workshop](https://github.com/fable-compiler/fableconf-workshops/tree/master/elmish) and [Fulma demo](https://github.com/MangelMaxime/fulma-demo).

## Requirements

- [Dotnet SDK 2.1.302](https://www.microsoft.com/net/download)
- [node.js with npm](https://nodejs.org)
- [Mono Framework](https://www.mono-project.com/download/stable/) for some tooling if working in non-Windows environment
- An F# IDE, like Visual Studio Code with [Ionide extension](http://ionide.io/)

## Installing dependencies

Type `npm install` to install dependencies (for both JS and F#) after cloning the repository or whenever dependencies change.

> [Paket](https://fsprojects.github.io/Paket/) is the tool used to manage F# dependencies.

## Development

Fable and Webpack are used to compile and bundle both the client and the server projects. To start them in watch mode (so the server is reloaded whenever there's a change in the code) type: `npm run start`. After the first build is complete you can open `http://localhost:8082` in your browser to try the app. Whenever you make any change in either the client or the server, the code will be reloaded automatically.

> Please note there will be two servers running at the same time in development: the webpack-dev-server which enables hot-reloading for client code, and the API server. In production only the API server will run (it will serve the static files too). Server ports and other build settings can be configured in `webpack.common.js`.

## Project Structure

The main files/directories in the repo are:

- `package.json`: Contains JS dependencies and also scripts executed with `npm run`.
- `paket.dependencies`: Contains F# dependencies.
- `webpack.*.js`: These are the Webpack configuration files (one for the common config, and two more specific for client and server projects).
- `public`: Contains public assets for the web (images, etc).
- `src/index.html`: This is the HTML template, webpack will add script tags to load the generated code automatically.
- `src/style`: Contains style files in SCSS format.
- `src/Shared`: Contains shared files between the server and the client projects.
- `src/Server`: Contains the server code. This is just a simple [Express](https://expressjs.com/) server written in F# and using a JSON file as test database. Files in `Import` folder are just bindings to JS libraries.
- `src/Client`: Contains the client code, again written in F# (Fullstack Fable FTW!). Still missing some features (sign in, answer voting). Uses [Elmish architecture](https://elmish.github.io/) and [Fulma](https://mangelmaxime.github.io/Fulma/) for styling.
