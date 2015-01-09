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
