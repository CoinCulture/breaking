# Got

Got is a tool for doing things with go and git that the go tool doesn't do for you by default. It's particularly useful for working with 
forks of open source projects, where import paths become an issue.

# Usage

### Replace strings in an entire directory tree

```
got replace [-d <depth> -p <dirpath>] <oldString> <newString>
```

### Switch import paths to upstream repo, pull, switch back

```
got pull <remote> <branch>
```

This does the same thing as running replace, followed by a commit, followed by a git pull, followed by a replace which undoes the first replace.

### Check out the same branch across many repositories

```
got checkout develop
```

This will `cd` into every directory in the current one and run `git checkout develop`. If you want to specify exceptions, add arguments of the form `<repo>:<branch>`, ie


```
got checkout develop myrepo:newfeature repo2:master
```

will `cd` into every repo and run `git checkout develop` except in `myrepo` it will do `git checkout newfeature` and in `repo2` will do `git checkout master`. To only `cd` into some directories, just list them, ie. 

```
got checkout develop myrepo anotherepo repo2:master
```

will checkout `myrepo` and `anotherepo` onto develop and `repo2` onto master while leaving all others alone.
