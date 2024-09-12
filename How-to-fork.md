# With GitHub

Making your own fork of Synergy is easy: [Fork a repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)

# Workflows

If you want to run the CI workflow on your Synergy fork, you'll need to enable actions for your fork (off by default).

Packaging is off by default, but you can enable it by [adding a variable](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/store-information-in-variables): `CI_ENABLE_PACKAGING` with the value `true`

The CI workflow is setup to run:
- when you update a PR (`on: pull_request`)
- when run it manually ([`on: workflow_dispatch`](https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch/))
- nightly on a cron schedule (`on: schedule`)

# Branding

You don't need to use the Synergy logo or call your fork Synergy. You can call it whatever you like. Notable Synergy-derivatives are [Barrier](https://github.com/debauchee/barrier) and [Input Leap](https://github.com/input-leap/input-leap).

Please remember that the Synergy logo is a trademark.

# Credit

While you certainly don't have to, we think that derived work should credit the original authors. We would appreciate a mention, even if you don't directly fork from Synergy (e.g. if you fork from a fork).
