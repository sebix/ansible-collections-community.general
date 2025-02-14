# Contributing

We follow [Ansible Code of Conduct](https://docs.ansible.com/ansible/latest/community/code_of_conduct.html) in all our contributions and interactions within this repository.

If you are a committer, also refer to the [collection's committer guidelines](https://github.com/ansible-collections/community.general/blob/main/commit-rights.md).

## Issue tracker

Whether you are looking for an opportunity to contribute or you found a bug and already know how to solve it, please go to the [issue tracker](https://github.com/ansible-collections/community.general/issues).
There you can find feature ideas to implement, reports about bugs to solve, or submit an issue to discuss your idea before implementing it which can help choose a right direction at the beginning of your work and potentially save a lot of time and effort.
Also somebody may already have started discussing or working on implementing the same or a similar idea,
so you can cooperate to create a better solution together.

* If you are interested in starting with an easy issue, look for [issues with an `easyfix` label](https://github.com/ansible-collections/community.general/labels/easyfix).
* Often issues that are waiting for contributors to pick up have [the `waiting_on_contributor` label](https://github.com/ansible-collections/community.general/labels/waiting_on_contributor).

## Open pull requests

Look through currently [open pull requests](https://github.com/ansible-collections/community.general/pulls).
You can help by reviewing them. Reviews help move pull requests to merge state. Some good pull requests cannot be merged only due to a lack of reviews. And it is always worth saying that good reviews are often more valuable than pull requests themselves.
Note that reviewing does not only mean code review, but also offering comments on new interfaces added to existing plugins/modules, interfaces of new plugins/modules, improving language (not everyone is a native english speaker), or testing bugfixes and new features!

Also, consider taking up a valuable, reviewed, but abandoned pull request which you could politely ask the original authors to complete yourself.

* Try committing your changes with an informative but short commit message.
* All commits of a pull request branch will be squashed into one commit at last. That does not mean you must have only one commit on your pull request, though!
* Please try not to force-push if it is not needed, so reviewers and other users looking at your pull request later can see the pull request commit history.
* Do not add merge commits to your PR. The bot will complain and you will have to rebase ([instructions for rebasing](https://docs.ansible.com/ansible/latest/dev_guide/developing_rebasing.html)) to remove them before your PR can be merged. To avoid that git automatically does merges during pulls, you can configure it to do rebases instead by running `git config pull.rebase true` inside the respository checkout.

You can also read [our Quick-start development guide](https://github.com/ansible/community-docs/blob/main/create_pr_quick_start_guide.rst).

## Test pull requests

If you want to test a PR locally, refer to [our testing guide](https://github.com/ansible/community-docs/blob/main/test_pr_locally_guide.rst) for instructions on how do it quickly.

If you find any inconsistencies or places in this document which can be improved, feel free to raise an issue or pull request to fix it.

## Creating new modules or plugins

Creating new modules and plugins requires a bit more work than other Pull Requests.

1. Please make sure that your new module or plugin is of interest to a larger audience. Very specialized modules or plugins that
   can only be used by very few people should better be added to more specialized collections.

2. When creating a new module or plugin, please make sure that you follow various guidelines:

   - Follow [development conventions](https://docs.ansible.com/ansible/devel/dev_guide/developing_modules_best_practices.html);
   - Follow [documentation standards](https://docs.ansible.com/ansible/devel/dev_guide/developing_modules_documenting.html) and
     the [Ansible style guide](https://docs.ansible.com/ansible/devel/dev_guide/style_guide/index.html#style-guide);
   - Make sure your modules and plugins are [GPL-3.0-or-later](https://www.gnu.org/licenses/gpl-3.0-standalone.html) licensed
     (new module_utils can also be [BSD-2-clause](https://opensource.org/licenses/BSD-2-Clause) licensed);
   - Make sure that new plugins and modules have tests (unit tests, integration tests, or both); it is preferable to have some tests
     which run in CI.

3. For modules and action plugins, make sure to create your module/plugin in the correct subdirectory, and create a symbolic link
   from `plugins/modules/` respectively `plugins/action/` to the actual module/plugin code. (Other plugin types should not use
   subdirectories.)

   - Action plugins need to be accompanied by a module, even if the module file only contains documentation
     (`DOCUMENTATION`, `EXAMPLES` and `RETURN`). The module must have the same name and directory path in `plugins/modules/`
     than the action plugin has in `plugins/action/`.

4. Make sure to add a BOTMETA entry for your new module/plugin in `.github/BOTMETA.yml`. Search for other plugins/modules in the
   same directory to see how entries could look. You should list all authors either as `maintainers` or under `ignore`. People
   listed as `maintainers` will be pinged for new issues and PRs that modify the module/plugin or its tests.

   When you add a new plugin/module, we expect that you perform maintainer duty for at least some time after contributing it.
