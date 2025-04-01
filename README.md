# update-ansible-git
Update local Ansible project git repositories

Since these scripts are intended to be used on Ansible projects, they are under the same license as Ansible itself: GNU General Public License v3.0 or later.

The `bash` script `update-me` attempts to bring your local branches up-to-date with their corresponding remotes.
If there are any `roles/requirements.yml` or `collections/requirements.yml`
files in the current branch, then use the `ansible-galaxy` command
to pull those requirements in as well. It should be generic enough to run safely on any git repo.
However, its behavior in the presence of `roles/requirements.yml` and `collections/requirements.yml`
are intended to make it useful for Ansible projects in particular.

The bash script `update-all` is intended to be run one directory level up from a set of
Ansible projects' git repositories. It looks for any git repos directly below the
current directory, then runs `update-me` in each of them in parallel. It is not nearly
so portable as `update-me`, assuming things about repository credentials that are
likely not true for many people. In particular, that a username and password are both required and sufficient
to access remote repositories.
