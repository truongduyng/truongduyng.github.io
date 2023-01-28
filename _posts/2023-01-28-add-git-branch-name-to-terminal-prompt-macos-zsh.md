---
title: Add Git Branch Name to Terminal Prompt (MacOS zsh)
tag: terminal, technical
layout: post
---

Open ~/.zshrc in your favorite editor and add the following content to the bottom.

```
function parse_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}

COLOR_DEF=$'%f'
COLOR_USR=$'%F{243}'
COLOR_DIR=$'%F{197}'
COLOR_GIT=$'%F{39}'
setopt PROMPT_SUBST
export PROMPT='${COLOR_USR}%n ${COLOR_DIR}%~ ${COLOR_GIT}$(parse_git_branch)${COLOR_DEF} $ '
```

To reload and apply adjustments to the formatting use source ~/.zshrc in the zsh shell.
