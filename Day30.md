# Git hard reset

## Question

```bash
The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/media present on Storage server in Stratos DC. This was just a test repository and one of the developers just pushed a couple of changes for testing, but now they want to clean this repository along with the commit history/work tree, so they want to point back the HEAD and the branch itself to a commit with message add data.txt file. Find below more details:



In /usr/src/kodekloudrepos/media git repository, reset the git commit history so that there are only two commits in the commit history i.e initial commit and add data.txt file.


Also make sure to push your changes.
```

## Solution

- SSH to storage server
- cd `/usr/src/kodekloudrepos/media`
- Check commit history:

```bash
git log --oneline
```
- Reset to the commit with `add data.txt file`

```bash
git reset --hard commit-hash
```
- Push to Origin

```bash
git push origin HEAD --force
```
- Verify after push

```bash
git log --oneline
```
