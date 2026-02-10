# devops-testing

Порядок запуска плейбуков:

```bash
ansible-playbook playbooks/users.yml
ansible-playbook playbooks/ssh-hardening.yml
ansible-playbook playbooks/packages.yml
ansible-playbook playbooks/docker.yml