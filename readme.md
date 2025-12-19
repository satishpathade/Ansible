# Ansible Task Collection — focused playbooks (local & EC2)

# Ansible Task Collection

A collection of small, focused Ansible playbooks for learning and practicing core automation tasks on localhost and EC2 instances.

Each playbook performs a single task, making it easy to understand and modify. All playbooks run locally by default and can be adapted to work with remote EC2 hosts.

## What This Repository Includes

- Connectivity testing using Ansible ping
- Creating files and directories
- Copying files to remote hosts
- Installing packages with `dnf`
- LAMP and LEMP stack installation using variables

## Project structure

- [ping.yml](ping.yml) — simple connectivity check (hosts: localhost)
- [create_folder.yml](create_folder.yml) — creates `/root/ansible.txt` and `/home/ec2-user/aws`
- [copy_files.yml](copy_files.yml) — copies `/root/ansible.txt` from controller to group `ec2` targets
- [install_package.yml](install_package.yml) — installs `tree` and an `nginx` example (uses `dnf`)
- [lamp_with_var.yml](lamp_with_var.yml) — installs LAMP components using variables defined in the playbook
- [lemp_with_var.yml](lemp_with_var.yml) — installs LEMP components using variables defined in the p

## How to run (local, no inventory)
-------------------------------
Run playbooks directly on the control machine (no inventory file) as `root`:

```bash
ansible-playbook -i 'localhost,' ping.yml -c local -u root
ansible-playbook -i 'localhost,' create_folder.yml -c local -u root
ansible-playbook -i 'localhost,' install_package.yml -c local -u root
ansible-playbook -i 'localhost,' lamp_with_var.yml -c local -u root
ansible-playbook -i 'localhost,' lemp_with_var.yml -c local -u root
```

## Notes for Local Runs
- `-i 'localhost,'` uses an inline inventory to target the local system.
- `-c local` executes tasks locally without establishing an SSH connection.
- `-u root` runs the playbook with root privileges. Adjust the user if you are running as a non-root user.


