# npmrc-buildpack
Heroku buildpack for modifying the .npmrc file based on .env variables

## Usage

### Add the buildpack

1. On the settings page for your app, e.g. https://dashboard.heroku.com/apps/MY-APP/settings, find the `Buildpacks` section.
1. Click on the 'Add buildpack' button.
1. Provide the URL for this repository: `https://github.com/anova-technology/heroku-buildpack-npmrc.git`
1. Click 'Save Changes'
1. Verify that this build pack is used **before** the `heroku/nodejs` build pack.
    - If you have already added `heroku/nodejs`, use the UI to re-order the build packs so that `heroku-buildpack-npmrc` comes first.
    - If you haven't added `heroku/nodejs`, add it now. It should be placed after `heroku-buildpack-npmrc`.
    
### Set the environment variable

While still on the settings page, add an environment variable `TOKEN=00000000-0000-0000-0000-000000000000`. When this variable is present, the npmrc will become:

//npm.pkg.github.com/:_authToken=00000000-0000-0000-0000-000000000000
//npm.pkg.github.com/anova-technology/:_authToken=00000000-0000-0000-0000-000000000000
@anova-technology:registry=https://npm.pkg.github.com
always-auth: true
