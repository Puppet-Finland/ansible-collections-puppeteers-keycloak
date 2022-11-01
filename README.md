# Ansible Collection - puppeteers.keycloak

Ansible code for managing Keycloak. This collection depends on the
community.general collection.

# Modules

## keycloak_realm_key

The *keycloak_realm_key* module can be used to manage custom Keycloak realm
keys. Currently only RSA256 keys are supported, but support can be extended
with trivial changes to the module. This module depends on the
community.general collection.

Example usage:

```
- name: Manage Keycloak realm key
    keycloak_realm_key:
      name: custom
      state: present
      parent_id: master
      provider_id: "rsa"
      auth_keycloak_url: "http://localhost:8080/auth"
      auth_username: keycloak
      auth_password: keycloak
      auth_realm: master
      config:
        private_key: "{{ private_key }}"
        enabled: true
        active: true
        priority: 120
        algorithm: "RS256"
```

Note that modifying the private_key after creating the realm key is not
possible, unless you change some other parameter as well. See the module source
code for details.

Also note that the private key should be string with literal linefeed
characters ('\n') instead of actual linefeeds.

# License

This module is licensed under BSD-2-Clause license. Some parts of it such as
*keycloak_realm_key* are under SPDX or GPL-3.0-or-later license due to
dependencies on the community.general license.
