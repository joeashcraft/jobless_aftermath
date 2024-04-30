# jobless_aftermath
test ansible-lint mock_modules

## use case
ansible-lint supports "mock_modules" by creating empty module files so that `syntax-check[unknown-module]` passes linting for modules not actually installed in the environment.

## problem statement
~ansible-lint fails to resolve modules in the same collection as mocked modules~

ansible-playbook fails to resolve modules from a collection split across two parts of ANSIBLE_COLLECTIONS_PATHS

## root cause
ansible-playbook apparently resolves modules by searching only the first directory in ANSIBLE_COLLECTIONS_PATHS which matches a collection name.

### affected versions
ansible-lint 6.14.3 using ansible 2.15.6
ansible-lint 6.15.0 using ansible 2.14.4
ansible-lint 6.15.0 using ansible 2.16.6
ansible-lint 24.2.3 using ansible-core:2.16.6 ansible-compat:4.1.11 ruamel-yaml:0.18.6 ruamel-yaml-clib:0.2.8