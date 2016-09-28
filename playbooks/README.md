# Playbooks

***
wait_for_bootup.yml -- I created this playbook because the playbooks I found just didn't work as expected. I needed this on AIX for my patchtool playbook
An example of one that didn't work for me was from
https://support.ansible.com/hc/en-us/articles/201958037-Reboot-a-server-and-wait-for-it-to-come-back

- name: restart machine
  shell: sleep 2 && shutdown -r now "Ansible updates triggered"
  async: 1
  poll: 0
  sudo: true
  ignore_errors: true

- name: waiting for server to come back
  local_action: wait_for host={{ inventory_hostname }} state=started delay=30 timeout=300
  sudo: false
***
