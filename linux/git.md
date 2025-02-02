
ubuntu:

```console
sudo apt install git-all
```


commit messages:

- `feat` – a new feature is introduced with the changes
- `fix` – a bug fix has occurred
- `chore` – changes that do not relate to a fix or feature and don't modify src or test files (for example updating dependencies)
- `refactor` – refactored code that neither fixes a bug nor adds a feature
- `docs` – updates to documentation such as a the README or other markdown files
- `style` – changes that do not affect the meaning of the code, likely related to code formatting such as white-space, missing semi-colons, and so on.
- `test` – including new or correcting previous tests
- `perf` – performance improvements
- `ci` – continuous integration related
- `build` – changes that affect the build system or external dependencies
- `revert` – reverts a previous commit

```
git commit -m "type:(component): message"
```

Merge Test to Main

```
git checkout test
git pull 
git checkout master
git pull
git merge --no-ff --no-commit test
```

Solve Conflicts

```
git commit -m 'merge test branch'
git push
```


## generate ssh

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

```shell
ssh-keygen -t ed25519 -C "joshua.homen@gmail.com"
```