**This is intended for maintainers only**

## Setting up the repo
To create a prod/stable release, first go to https://github.com/eried/portapack-mayhem/tree/next/.github/workflows and edit the `past_version.txt` and the `version.txt` files.

* `past_version.txt` needs to be the current release (I.E if you are creating a new release and the old/current stable release is `v1.0.0` and you want the new version to be `v1.1.0`, then past version needs to be `v1.0.0`).
* `version.txt` needs to be the version you want for your new release. So from the example above, that would be `v1.1.0`.

## Running the pipeline
Once that is done then you need to create the draft stable release. You can do this by running the stable release pipeline on `next` branch https://github.com/eried/portapack-mayhem/actions/workflows/create_stable_release.yml

This should take around 7-15 minutes.

## Editing the draft release
This then create a draft release that you should be able to see in releases at the top https://github.com/eried/portapack-mayhem/releases

Next, make sure you test it on your own device before going any further. This is to ensure it created it correctly and that there are no last minute bugs.

Once tested, you then need to manually update the files in the `mayhem_nightly_X_COPY_TO_SDCARD.zip` folder. This is because there are some files (like the world map) that are too big to host on the GitHub repo, so they need to be manually added into the zip folder. So to do this, download `mayhem_nightly_X_COPY_TO_SDCARD.zip` from the draft release and then download `mayhem_nightly_PREVIOUS_RELEASE_X_COPY_TO_SDCARD.zip` from the previous stable release. Copy the files from the previous to the new release making sure to not overwrite any files (As we are just wanting to add the ones missing).

Once that is done, make sure to upload that to the new draft release replacing the old zip folder (Which you need to delete first).

Take a quick look over the draft release and make sure everything looks good, If it does go ahead an publish it!

## Finishing off
Once all is done, create a PR to merge the `next` branch into the `master` branch.

Then make sure to create an announcement on Discord that vx.x.x has just been released and post a link to it.