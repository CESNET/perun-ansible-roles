# perun-ansible-roles
repo with git submodules for roles source code

Add this repo as a submodule for repo with playbook and add it to roles_path:

```bash
git submodule add https://github.com/CESNET/perun-ansible-roles.git cesnet_roles 
git submodule update --init --recursive

echo "roles_path=cesnet_roles" >>ansible.cfg
```

When any of the roles get updated, either update the perun-ansible-roles repo to latest versions of all submodules:
(the --remote option of "git submodule update" tells to pull the master branches of the submodules,
without it the commits referenced in super-repo are checked out)
```bash
git submodule update --init --recursive --remote
```
or update just the roles that you want to update to specific versions:
```bash
git fetch --recurse-submodules --prune
cd cesnet.xxx
git checkout vV.W
cd ..
```

Then update the main perun-ansible-roles repo:
```bash
git commit -a -S -m "updated cesnet.xxx to version V.W"
git tag -a vX.Y -m "updated cesnet.xxx to version V.W"
git push --follow-tags
```

Then update the repos linking perun-ansible-roles by issuing:
```bash
cd repo-with-playbook
cd cesnet_roles
git checkout master
git pull
git submodule update --init --recursive
cd ..
git submodule status --recursive
git status
git add cesnet_roles
git commit -S -m "updated perun-ansible-roles to version X.Y"
git push
```
