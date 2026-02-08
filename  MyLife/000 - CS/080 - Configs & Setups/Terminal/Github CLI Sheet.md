---
id: Github CLI
aliases:
Topic: Explanation on Github CLI commands and installation.
Related:
  - "[[%Config]]"
  - "[[%Command]]"
Tags:
  - w
Date:
Updated:
Source:
---
# Github CLI


### Installation

```bash
brew install gh

---

brew install github-copilot-cli

// OR

gh extension install github/gh-copilot
```


### Setup

```bash
gh auth login 

...
```



### Usage 



```bash
<-- Interactive Mode 

gh copilot




<-- slash commands

/model | choose model

/help | list all commands

/exit | leave TUI 

/delegate | AI RP creation

/repo | setting repo context

/clear | clearing history

/settings | show settings

/explain | explain

/tests | generate test

/fix | fix an error

/optimize | optimize code

/doc | create docs

/commit | create commit message

/pr | create pull request
```


```bash
<-- direct prompt mode

copilot -i 

copilot -p



<-- commands

Inline‑Prompt:

copilot -i "explain what is 2+2"

Prompt‑Flag:

copilot -p "write a bash script that cleans logs"

file as input:

copilot -f script.sh -i "explain this file"

write output into a file:

copilot -i "generate a README" > README.md

```






  


  