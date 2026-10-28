# superpowers-ruby (trimmed)

A trimmed fork of [lucianghinda/superpowers-ruby](https://github.com/lucianghinda/superpowers-ruby), itself a fork of [obra/superpowers](https://github.com/obra/superpowers). It keeps Brakeman and the process skills, and drops the hooks, agents and commands. It's meant to be installed at user scope so it works in every repo.

How it fits alongside each repo:

- A project's CLAUDE.md and its own skills take priority over these wherever they differ.
- TDD, worktrees, code review and skill writing defer to the project's own skill for that, if there is one.
- Git: commit only to the current branch. Never push unless asked. Never merge into another branch, and never deploy.
- Brainstorming and writing-plans only run when asked. Specs and plans go in `docs/superpowers/` and are committed to the current branch.

## Skills

- `brakeman`: Rails security static analysis
- `systematic-debugging`: find the root cause before fixing
- `verification-before-completion`: run the check before claiming it works
- `receiving-code-review`: weigh review feedback instead of agreeing by default
- `requesting-code-review`: dispatch a reviewer subagent on finished work
- `test-driven-development`: red, green, refactor
- `dispatching-parallel-agents`: split independent problems across subagents
- `using-git-worktrees`: set up an isolated worktree
- `brainstorming`: turn an idea into an approved spec (opt-in)
- `writing-plans`: turn a spec into a step-by-step plan (opt-in)
- `executing-plans`: work through a plan with checkpoints
- `subagent-driven-development`: work through a plan with a subagent per task and two reviews
- `finishing-a-development-branch`: verify, then keep the branch or push and open a PR
- `writing-skills`: write and test new skills

## License

MIT. See [LICENSE](LICENSE). All skill content is from the upstream projects.
