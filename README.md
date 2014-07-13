# Mac OS X Terminal cd alies folders

```
step1. compile getTrueName.c
gcc -o getTrueName -framework Carbon getTrueName.c

step2. in .bash_profile file
add follow script
-------------
export PATH=$PATH:~/Documents/iSoft/gettruename

function cd {
  if [ ${#1} == 0 ]; then
    builtin cd
  elif [ -d "${1}" ]; then
    builtin cd "${1}"
  elif [[ -f "${1}" || -L "${1}" ]]; then
    path=$(getTrueName "$1")
    builtin cd "$path"
  else
    builtin cd "${1}"
  fi
}
-------------
```
