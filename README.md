## Electron Hello World

[Electron](https://electron.atom.io/) example application.

## Setting up GitHub tokens on Travis CI and AppVeyor

This is required for automatically publishing releases to GitHub.

- Create a [new personal access token on GitHub](https://github.com/settings/tokens)
    - Only enable `public_repo` permission
- [Encrypt the token for AppVeyor here](https://ci.appveyor.com/tools/encrypt)
- Update `environment.GH_TOKEN.secure` with the token in `appveyor.yml`
- Update the token in `.travis.yml` with `travis encrypt --add env GH_TOKEN=<the token>` (install the Travis Gem first with `gem install travis`)
- Commit and push both `.travis.yml` and `appveyor.yml`
