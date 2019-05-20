# Container Behavior

## The Environment
`docker container run -it -e "PS1=\h:\w# " subratabauri/myalpine:latest`

`\h` => Hostname

`\w` => Path


## The ENV Instruction

```
ENV PS1 "\h:\w#"
ENV PS1="\h:\w#" PS2=">>"
```

