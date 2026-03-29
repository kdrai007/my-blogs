---
title: "config_nd_env"
draft: false
---

Tag : #linux #env #alias #commands

# Configuration & Environment

The shell stores key information during sessions, known as the *environment*, Programs  see data stored in the environment to determine facts about system' configurations. While most programs use configurations files for specific program settings.

## Command Used

1. printenv - print part of all environment
2. set - Set shell options
3. export - Export environment to subsequently executed program
4. alias - Create an alias for command

### Examining The Environment

To see what's stored in Environment, we can use `set` builtin in bash or `printenv` program. 

syntax,
`$ printenv |less`

- The `set` command while using without any argument will show, both shell variables and environment

syntax,
`$ set | less`


### Modifying the Environment

Since, we know where startup files are and what they contain, So we can modify env the way we want

#### Which Files should We Modify?

One general rule is that, You should define or update `PATH` variables or `env`  in `.bash_profile` or `.zprofile` both are shells configurations files, one is for `bash` and other is for `zsh`

- `zsh` is just updated version of `bash` just keep this in mind.









