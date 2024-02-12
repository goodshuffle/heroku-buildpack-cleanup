# heroku-buildpack-cleanup

Remove files that are specified in a .slugcleanup file.

## Rationale

> While this may seem to duplicate functionality provided by Heroku's
> `.slugignore`, there is a key difference: `.slugignore`'d files are
> removed after the repo is cloned, but before any buildpack is run. They
> can therefore not be involved in the build process itself.
> 
> However, it is not uncommon for there to exist files in the repo that
> are necessary for the build, but are not required at runtime. There may
> also be installable build dependencies that are not runtime
> dependencies.
> 
> In our case, a complex front-end build involves a large installation of 
> node modules, which are used only for building the production assets 
> and not required to run the app, but then remain part of the slug.
> 
> https://github.com/Lostmyname/heroku-buildpack-post-build-clean?tab=readme-ov-file#rationale

## Usage

    $ heroku buildpacks:add https://github.com/goodshuffle/heroku-buildpack-cleanup

    $ cat .slugcleanup
    src/main/client/node_modules

## License

MIT
