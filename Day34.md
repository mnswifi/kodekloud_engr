# Git Hook

## Question

```bash
The Nautilus application development team was working on a git repository /opt/blog.git which is cloned under /usr/src/kodekloudrepos directory present on Storage server in Stratos DC. The team want to setup a hook on this repository, please find below more details:



Merge the feature branch into the master branch`, but before pushing your changes complete below point.

Create a post-update hook in this git repository so that whenever any changes are pushed to the master branch, it creates a release tag with name release-2023-06-15, where 2023-06-15 is supposed to be the current date. For example if today is 20th June, 2023 then the release tag must be release-2023-06-20. Make sure you test the hook at least once and create a release tag for today's release.

Finally remember to push your changes.
Note: Perform this task using the natasha user, and ensure the repository or existing directory permissions are not altered.
```

## Solution

- ssh into storage server with natasha credential

- cd into `/usr/src/kodekloudrepos/blog/`

### Merge

- git checkout master
- git pull 
- git merge feature

### Create in a `post-update` in the bare repo `/opt/blog.git/hooks`

- sudo mv /opt/blog.git/hooks/post-update.sample /opt/blog.git/hooks/post-update

- sudo vi /opt/blog.git/hooks/post-update

- - clear and add the below script:

```bash
#!/usr/bin/sh

# First argument to post-update is the ref that was updated
REF="$1"

# Only run when master branch is updated
if [ "$REF" = "refs/heads/master" ]; then
    TODAY=$(date +%F)
    TAG="release-$TODAY"

    # get the latest commit on master
    SHA=$(git rev-parse refs/heads/master)

    # create tag and push
    git tag "$TAG" "$SHA"
    git push origin "$TAG"
fi

# Optionally update server info (AFTER hook logic)
git update-server-info
```

- save and make executable `sudo chmod +x /opt/blog.git/hook/post-update`

### Testing git tag

- echo "testing git tag" >> testingtag.txt

- git add testingtag.txt

- git commit -m "addest testing tag file"

- git push origin master


### Confirm tag is working

- git ls-remote --tags origin

You should see:

- `refs/tags/release-2025-03-19`