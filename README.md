# Squirrel-Navigator
**A private and secure text based browser. With Pictures**

or a fully fledged Web Browser 😲

Squirrel-Navigator is based on [Browsh](https://www.brow.sh/).

## Install

Download a [https://github.com/squirrelcom/Squirrel-Navigator/releases](release) (~2MB).
You will need to have Firefox >=57 aleady installed.

Or download and run the Docker image (~800MB) with:
    `docker run -it squirrelcom/Squirrel-Navigator`

## Usage
Most keys and mouse gestures should work as you'd expect on a desktop
browser.

`CTRL+l` Focus URL bar
`ALT+P` Take screenshot

## Contributing
To setup a dev env you will need NodeJS and Golang installed. If you get stuck
setting up your env, take a look in `.travis.yml`, it has to setup everything
from scratch for every push to Github.

I'd recommend `[nvm](https://github.com/creationix/nvm)` for NodeJS - note that
`nvm install` will automatically parse the `.nvmrc` version in this repo to get
the correct NodeJS version. For Golang it's probably best to just use your OS's
package manager. The current Golang version being used is stored in `.travis.yml`.

You'll then need to install the project dependencies. For the webextension, just
run: `npm install` inside the `webext/` folder. For the CLI client you will first
need to install `dep`, there is a script for this in `interfacer/contrib/setup_go.sh`.
I don't fully understand Golang's best practices, but it seems you are forced to
keep your Go project's code under `$GOPATH/src`, you might be able to get away
with symlinks. Anyway, to install the dependencies use: `dep ensure` inside the
`interfacer/` folder.

Then the ideal setup for development is:
  * have Webpack watch the JS code so that it rebuilds automatically:
    `webpack --watch`
  * run the CLI client without giving it the responsibility to launch Firefox:
    `go run ./interfacer/*.go -use-existing-ff`
  * have Mozilla's handy `web-ext` tool run Firefox and reinstall the
    webextension everytime webpack rebuilds it: (in `webext/dist`)
    `web-ext run --verbose --url https://google.com`

## License
## Apache License
### Version 2.0, January 2004
###### http://www.apache.org/licenses/

