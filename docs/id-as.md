# Nickname a plugin or snippet

Zplugin supports loading a plugin or snippet with a nickname. Set the nickname
through the `id-as` ice-mod. For example, one could try to load
[**docker/compose**](https://github.com/docker/compose) from Github binary
releases:

```zsh
zplugin ice as"program" from"gh-r" mv"docker-c* -> docker-compose"
zplugin light "docker/compose"
```

This registers plugin under the ID `docker/compose`. Now suppose the user would
want to also load a completion from the project's GitHub repository (not the
binary release catalog) which is also available under the GitHub url-path
**…/docker/compose**. The two IDs, both being "docker/compose", will collide.
The solution – the `id-as` ice to which this document is devoted: by using the
`id-as` ice the user can resolve the conflict by loading the completion under a
nickname, for example "dc-complete":

```zsh
zplugin ice as"completion" id-as"dc-complete"
zplugin load docker/compose
```

The completion is now seen under ID `dc-complete`. Issuing `zplugin report
dc-complete` works, so as other Zplugin commands:

```zsh
~ zplugin report dc-complete
Plugin report for dc-complete
-------------------------------

Completions:
_docker-compose [enabled]
```

This can be also used to nickname snippets. For example, you can use this to
create handy IDs in place of long urls:


```zsh
zplugin ice as"program" id-as"git-unique"
zplugin snippet https://github.com/Osse/git-scripts/blob/master/git-unique
```

`zplugin update git-unique`, `zplugin delete git-unique` and other commands will
work normally and e.g. `zplugin times` will show `git-unique` instead of the
long URL.

[]( vim:set ft=markdown tw=80: )
