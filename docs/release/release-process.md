# Release Process

## tl;dr Process Overview


## Detailed Process

all features should be merged into master
all docs and examples are updated for new features/paradigms (but not updated to include latest release tags/versions)
API docs are generated/updated
all issues in the milestone and zenhub boards should be closed

testing should be done on the master build
if all looks good, proceed to creating release branch

(feature freeze day)

Create release branch manually in github
no tagging is done yet
this automatically starts a build from the release branch with version like `v0.3.0-96.g9c48bb1`
more testing can be done on this build, but it should likely be the same as what was in master

master can move on with new features
bug fixes go into the release branch (cherry-picked from master)
Update example yamls, docs, etc. with final versions of stacks etc. in the release branch only

Draft release notes, collect feedback

(build essentially goes out to the community here)
Run tag pipeline with version and commit hash
    - first time you run on a new branch, you won't get prompted to input values
    - run (not replay) the pipeline on the release branch again, enter the version and commit hash
    - link to this issue? how is this not fixed yet?

if a normal build pipeline build isn't automatically kicked off from this tagging, go ahead and run the build pipeline for the release branch manually
this will be the official release build with official version number and it should be published to docker hub, etc.
verify all published artifacts (docker hub, helm charts, s3 releases bucket, docs website)

publish release notes, this will send email to all watchers of the repo

run promote to alpha channel
verify alpha channels are updated (dockerhub, helm)

release announcements
 - twitter account
 - post tweet to slack #announcements channel, copy slack post to #general channel
 - other social media (reddit)


patch releases
fix bugs in master and cherry-pick to release branch
if master has moved on then fix directly in release branch
after all testing on release branch builds look good, tag release branch HEAD commit with patch version (e.g. v0.4.1)
run build pipeline on release branch
run promote to alpha channel
