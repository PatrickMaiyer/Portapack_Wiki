In order to get your PR merged into the code base, there are a few checks that need to happen first.

* At least one code approver needs to approve your code. 
* If any code reviewer left PR comments, then all those PR comments left by reviewers need to be marked as resolved.
* All 3 code format gate checks need to complete successfully. (don't know how to format your code? Check out how to do it here https://github.com/eried/portapack-mayhem/wiki/Code-formatting) 

Once these steps are all complete, if you are an approved contributor you will notice you have a green merge button available, then means you are good to go and merge your code into the code base. Everyone else will see that tests have passed and will need to ask an approved contributor to merge it in for them (You can as the dev that approved the changes).

If any of these steps are not complete or failed, then you will be blocked from merging your code until they have all been completed.

### Usernames on the nightly change log
A new build of 'next' is released every night. Your contribution will be added to the list of changes that were accepted that day.
In order for your user account to display correctly you must either.
1) Enable 'Keep my email addresses private' which will add a unique email address like '417283+YourGitHubUser@noreply...'. Your username will be extracted from the private no-reply email address.
2) Set your GitHub profile name to be your GitHub username. Basically if your username is "foobar", then also set your public profile's name to "foobar".