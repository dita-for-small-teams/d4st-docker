# d4st-docker
Materials for providing Docker containers for the D4ST components

D4ST release packages are available from the main dita-for-small-teams release area: https://github.com/dita-for-small-teams/dita-for-small-teams/releases

See the D4ST Docker manual at http://www.dita-for-small-teams.org/d4st-docker/

## Bash completion

The file `bash_completion.d/d4st.bash-completion` is a bash completion script that lets you 
use tab to do autocomplete for the `d4st` command options.

To install the completion file do the following:

### macOS

You must have bash completion installed. See http://davidalger.com/development/bash-completion-on-os-x-with-brew/ for instructions on using homebrew to install bash completion if you haven't already.

To install the completion file link the `d4st.bash-completion` file to  /etc/bash_completion.d/d4st:

```
$ cd d4st/bash_completion.d
$ ln -s $PWD/d4st.bash-completion `brew --prefix`/etc/bash_completion.d/d4st
```

You should now be able to type "d4st", space, and tab to get a list of available options:
```
Mako:bash_completion.d ekimber$ d4st 
addhooks             cleanimages          gitlab               log-gitlab           pause                stop                 up                   
cleanall             down                 kill                 make-gitlab-project  pull                 test-gitlab          
cleancontainers      getdemo              linkmgr              make-gitlab-user     start                unpause              
Mako:bash_completion.d ekimber$ d4st 
```

### Windows git bash shell

TBD

### Windows bash (Windows Linux Subsystem)

TBD

### Linux

To install the completion file link the `d4st.bash-completion` file to  /etc/bash_completion.d/d4st:

```
$ cd d4st/bash_completion.d
$ ln -s $PWD/d4st.bash-completion /etc/bash_completion.d/d4st
```


