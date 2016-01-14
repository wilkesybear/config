# config
========
various config files

### .zsh
- Requires oh-my-zsh
- Changed the robbyrussell theme to print out the full directory path (instead of first character only)
- `.zshrc` has a few aliases, but more importantly has `unsetopt nomatch` to prevent zsh from messing up wildcards in various functions (e.g. `rsync`)

### tmux
tmux config hotness

### watchman + rsync (in `bin/`)
watchman setup that will rsync files to a remote machine whenever files in certain directories are changed. This is extremely useful for developing/testing on multiple machines and need things to be sync'ed before runs
- `watch` is just a simple bash script where the `watchman -- trigger` lines are declared. These could be made more fancy but work perfectly well for what I need.
  - It's really important to define file filters with `**/*ext` becuase the first `**/` allows that file to live on any level in the directory. Without this, it will only look in the root!
  - `rsync-belwas` is a stupid-simple ruby script that takes in a target directory and a list of changed files. For each file, it'll `rsync` the file to `belwas` (one of my current remote aliases) under the target directory
