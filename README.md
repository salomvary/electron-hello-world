## Electron Hello World

[Electron](https://electron.atom.io/) example application.

## Usage

Run the application in development mode:

    npm start

## Packaging

Package a macOS application:

    npm run build -- --mac
    open dist/mac/electron-hello-world.app

Sign a macOS application with a specific identity:

    CSC_NAME="My Identity Name" npm run build -- --mac

Package with a specific version:

    npm run build -- --mac --em.version=1.2.3

Package a Windows application with Docker:

	docker run --rm -v "$PWD:/project" \
		-v ~/.electron:/root/.electron \
		electronuserland/electron-builder:wine \
    npm run build -- --win

Package a signed Windows application with Docker:

	docker run --rm -e CSC_LINK=certificate.p12 -e CSC_KEY_PASSWORD=s3cr3t \
    -v "$PWD:/project" \
		-v ~/.electron:/root/.electron \
		electronuserland/electron-builder:wine \
    npm run build -- --win

## Setting up GitHub tokens on Travis CI and AppVeyor

This is required for automatically publishing releases to GitHub.

- Create a [new personal access token on GitHub](https://github.com/settings/tokens)
    - Only enable `public_repo` permission
- [Encrypt the token for AppVeyor here](https://ci.appveyor.com/tools/encrypt)
- Update `environment.GH_TOKEN.secure` with the token in `appveyor.yml`
- Update the token in `.travis.yml` with `travis encrypt --add env GH_TOKEN=<the token>` (install the Travis Gem first with `gem install travis`)
- Commit and push both `.travis.yml` and `appveyor.yml`
