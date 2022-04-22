# Ansible luarocks module

This module lets you manage lua rocks with ansible.

# Installing

Copy the module to your ansible library (any path in the `ANSIBLE_LIBRARY` environment variable), or
to a playbook-specific library (`./library` relative to your YAML file).

# Examples

```yaml
- name: Install the "luasocket" rock.
  luarocks:
    name: luasocket

- name: Install the "luasocket" rock in a more explicit way.
  luarocks:
    name: luasocket
    state: present

- name: Install the "luasocket" rock from a specific server.
  luarocks:
    name: luasocket
    server: http://http://rocks.moonscript.org

- name: Install the "luasocket" rock into your local tree.
  luarocks:
    name: luasocket
    local: yes

- name: Install the "luasocket" rock into a specific tree.
  luarocks:
    name: luasocket
    tree: /srv/foo/rocks

- name: Install version 2.0.2 of the "luasocket" rock.
 luarocks:
    name: luasocket
    version: '2.0.2'

- name: Remove the "luasocket" rock.
  luarocks:
    name: luasocket
    state: absent
```

# Supported Options

## Required

* `name`: the name of the rock

## Optional

* `state`: `absent` or `present`
* `version`: a specific version to install or remove
* `deps_mode`: how to handle dependencies
  * `all`: use all trees from the rocks_trees list for finding dependencies
  * `one`: use only the current tree (possibly set with `tree`)
  * `order`: use trees based on order (use the current tree and all trees below it on the rocks_trees list)
  * `none`: ignore dependencies altogether.
* `executable`: your luarocks executable, useful if you'd like to use a specific version of lua
* `local`: [boolean] whether to use your local rocks tree
* `tree`: a specific rocks tree to use
* `server`: a specific luarocks server to fetch rocks and rockspecs from
* `override_server`: [boolean] use only the specified server
  * `false`: specified server takes priority over servers in config file
  * `true`: specified server overrides all servers in config file
* `keep_other_versions`: [boolean] whether to keep other versions of the rock (the --keep flag to luarocks install)

