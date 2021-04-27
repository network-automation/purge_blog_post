# Purge Feature

This Github repo corresponds to a blog post on Ansible.com (to be released)


## Using state: gathered

It is trivial using the `state: gathered` parameter to turn running-configuration from a Cisco IOS/XE network device into structured data (e.g. YAML)

Use the `playbooks/gather_ios_bgp.yaml` playbook:
[Link to playbook](playbooks/gather_ios_bgp.yaml)

```
ansible-playbook gather_ios_bgp.yaml
```
