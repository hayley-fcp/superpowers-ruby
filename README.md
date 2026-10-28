# superpowers-ruby (trimmed)

A trimmed fork of [lucianghinda/rubypowers](https://github.com/lucianghinda/rubypowers) (formerly superpowers-ruby), itself a fork of [obra/superpowers](https://github.com/obra/superpowers). It keeps Brakeman and the process skills, and drops the hooks, agents and commands. It's meant to be installed at user scope so it works in every repo.

## Target stack

Examples and default commands target:

- Ruby 3.3
- Rails 8.1
- RSpec (rspec-rails 8), run with `bundle exec rspec`

In a project on a different stack, the skills use that project's own test framework and commands.

## How it fits alongside each repo

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

## Changes from upstream

What's different from lucianghinda/rubypowers:

**Removed**

- Hooks, agents and commands
- Skills outside this list, including the Ruby and Rails style skills, Hotwire skills, handoff skills, `using-rubypowers` and `using-sqlite-worktrees`
- The upstream team's testing guide (`testing-strategy.md`), which required Minitest and fixtures
- The `systematic-debugging` creation log and pressure-test fixtures

**Stack**

- Test examples converted from Minitest to RSpec in TDD, testing anti-patterns, worktrees, finishing a branch, debugging and Brakeman
- Writing-plans examples converted from Python to Ruby and RSpec
- Code review checks no longer require Minitest, fixtures or no system tests. They check the project's own conventions instead
- `find-polluter.sh` runs `bundle exec rspec` by default, overridable with `TEST_CMD`
- Worktree setup uses the project's documented setup first, and drops the SQLite helper

**Git safety**

- Every skill that commits carries the git rules above
- `finishing-a-development-branch` rewritten: no merge or discard options. It offers keep the branch, or push and open a PR, and only pushes when that option is picked
- `using-git-worktrees` no longer edits or commits `.gitignore`. It uses a global worktree folder or asks
- Implementer subagents commit only to the current branch

**Fitting into other repos**

- Every skill defers to the project's CLAUDE.md and skills
- TDD, worktrees, requesting code review and writing skills step aside when the project has its own
- Code review uses a general-purpose subagent with the bundled template, since the upstream reviewer agent was dropped
- `brainstorming` and `writing-plans` are opt-in instead of triggering on every feature
- Specs and plans use one folder, `docs/superpowers/`, instead of upstream's two-folder fallback
- Skill references renamed from `rubypowers:` to `superpowers-ruby:`
- Commit message examples use plain imperative subjects instead of `feat:` prefixes

## License

MIT. See [LICENSE](LICENSE). All skill content is from the upstream projects, with the changes above.
