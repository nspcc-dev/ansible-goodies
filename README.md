# nspcc ansible_goodies collection

This is a collection of simple helpers that used frequently:

- system_user: create a system user
```Yaml
- ansible.builtin.include_role:
    name: nspcc.ansible_goodies.system_user
  vars:
    system_user__user: '<user_name>'
    system_user__group: '<group_name>'
    system_user__home: '<home_directory_absolute_path>'
```

- github: get release from github
```Yaml
- ansible.builtin.include_role:
    name: nspcc.ansible_goodies.github
  vars:
    github__org: '<ORGANIZA_NAME>'
    github__repo: '<REPOSITORY_NAME>'
    github__version: '<RELEASE_VERSION>'
    github__asset_name: '<ASSET_NAME>'
    github__args:
      dest: '<ABSOLUTE_PATH_TO_PUT_ASSET>'
      owner: '<target_file_user>'
      group: '<target_file_group>'
      mode: '<target_file_permission>'
    github__notify: [ 'Restart NeoFS REST service' ]
```

- mkprivdir: make user-chown'ed directory with root-chown'ed parents
```Yaml
- ansible.builtin.include_role:
    name: nspcc.ansible_goodies.mkprivdir
  vars:
    mkprivdir__dir: '<target_directory_absolute_path>'
    mkprivdir__user: '<target_directory_user>'
    mkprivdir__group: '<target_directory_group>'
```

It will probably be rewritten in Python in the future.
