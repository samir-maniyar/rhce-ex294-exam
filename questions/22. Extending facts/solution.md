# 22. Extending facts - Solution

The playbook might look as follows:
```yml
---
- hosts: all
  tasks:
  - name: Gather package facts
    when: inventory_hostname in groups["database"]
    package_facts:
  - name: Print out facts
    debug:
      var: ansible_facts
...
```
---
- hosts: all
  tasks:
          - name: gather package facts
            when: inventory_hostname in groups['database']
            ansible.builtin.package_facts:
                    manager: auto

          - name: Print the package facts
            ansible.builtin.debug:
                    var: ansible_facts.packages
...
