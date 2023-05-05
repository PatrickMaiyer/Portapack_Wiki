**This is intended for maintainers only**

## Setting up the repo
To create a prod/stable release, first go to https://github.com/eried/portapack-mayhem/tree/next/.github/workflows and edit the `past_version.txt` and the `version.txt` files

* `past_version.txt` needs to be the current release (I.E if you are creating a new release and the old/current stable release is `v1.0.0` and you want the new version to be `v1.1.0`, then past version needs to be `v1.0.0`)
* `version.txt` needs to be the version you want for your new release. So from the example above, that would be `v1.1.0`

## Running the pipeline
Once that is done then you need to create the draft stable release. You can do this by running the stable release pipeline on `next` branch https://github.com/eried/portapack-mayhem/actions/workflows/create_stable_release.yml

This then create a draft release that you should be able to see in releases at the top https://github.com/eried/portapack-mayhem/releases

## Finishing off
Once all is done, create a PR to merge the `next` branch into the `master` branch