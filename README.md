# perun-ansible-roles
repo with git submodules for roles source code

Add this repo as a submodule for repo with playbook and add it to roles_path:

```bash
git submodule add https://github.com/CESNET/perun-ansible-roles.git cesnet_roles 
git submodule update --init --recursive

echo "roles_path=cesnet_roles" >>ansible.cfg
```

When any of the roles get updated, first update the perun-ansible-roles repo to latest versions of submodules:
```bash
git submodule update --init --recursive --remote
git commit -a -S -m "updated submodules"
```
then update the repos linking perun-ansible-roles by issuing:
```bash
git submodule update --init --recursive 
```

The --remote option of "git submodule update" tells to pull the master branch of the submodules,
without it the commits referenced in super-repo are checked out.
