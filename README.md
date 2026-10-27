# superpowers-ruby (trimmed)

A trimmed fork of [lucianghinda/superpowers-ruby](https://github.com/lucianghinda/superpowers-ruby), itself a fork of [obra/superpowers](https://github.com/obra/superpowers). It keeps only three skills and drops the hooks, agents, commands and workflow skills.

## Skills

- `rails-upgrade`: systematic Rails version upgrade workflow with breaking change detection and gem compatibility checks
- `ruby-upgrade`: Ruby interpreter upgrade workflow (3.x to 4.0.x)
- `brakeman`: Rails security static analysis

## Install (Claude Code)

```
/plugin marketplace add hayley-fcp/superpowers-ruby
/plugin install superpowers-ruby@superpowers-ruby
```

## License

MIT. See [LICENSE](LICENSE). All skill content is from the upstream projects.
