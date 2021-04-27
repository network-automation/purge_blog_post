# Purge Feature

This Github repo corresponds to a blog post on Ansible.com (to be released) around the purge feature.  There is four example included in this Github repo:

# Table of Contents

* [Using state: gathered](#using-state-gathered)
* [state: merged](#state-merged)
* [state: deleted](#state-deleted)
* [state: purged](#state-purged)


## Using state: gathered

It is trivial using the `state: gathered` parameter to turn running-configuration from a Cisco IOS/XE network device into structured data (e.g. YAML) and create a SoT (Source of Truth)

Use the `playbooks/gather_ios_bgp.yaml` playbook:
[Link to playbook](playbooks/gather_ios_bgp.yaml)

To execute playbook:
```
ansible-playbook gather_ios_bgp.yaml
```

## state: merged

To configure a network device from your SoT (source of truth) use the `state: merged` parameter.  This is the default parameter so if no state parameter is set, it will default to merged.

Use the `playbooks/merge_ios_bgp.yaml` playbook:
[Link to playbook](playbooks/merge_ios_bgp.yaml)

To execute playbook:
```
ansible-playbook merge_ios_bgp.yaml
```

## state: deleted

To remove all BGP configuration use the `state: purged` parameter.  This will remove all BGP configuration, regardless of which BGP module was use to place it there.

Use the `playbooks/gather_ios_bgp.yaml` playbook:
[Link to playbook](playbooks/purge_ios_bgp.yaml)

e.g.
```
- name: Use the bgp_global resource module
  cisco.ios.ios_bgp_global:
    config: "{{ bgp_global }}"
    state: deleted

- name: Use the bgp_address_family
  cisco.ios.ios_bgp_address_family:
    config: "{{ bgp_address_family }}"
    state: deleted
```
To execute playbook:
```
ansible-playbook purge_ios_bgp.yaml
```

## state: purged

To remove specific BGP configuration use the `state: deleted` parameter.  This will remove the specified BGP configuration.

Use the `playbooks/delete_ios_bgp.yaml` playbook:
[Link to playbook](playbooks/delete_ios_bgp.yaml)

e.g.
```
- name: Use the bgp_global resource module
  cisco.ios.ios_bgp_global:
    state: purged
```

To execute playbook:
```
ansible-playbook purge_ios_bgp.yaml
```

---
More info on Ansible Network Automation

  - [Part 1: Modernize Your Network with Red Hat](https://www.ansible.com/resources/ebooks/network-automation-for-everyone?hsLang=en-us)
  - [Part 2: Automate Your Network with Red Hat](https://www.ansible.com/resources/ebooks/automate-your-network?hsLang=en-us)
  - [More E-Books on Ansible.com](https://www.ansible.com/resources/ebooks)

![Red Hat Ansible Automation](https://github.com/ansible/workshops/raw/devel/images/rh-ansible-automation-platform.png)
