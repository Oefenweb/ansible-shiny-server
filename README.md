## shiny-server

[![CI](https://github.com/Oefenweb/ansible-shiny-server/workflows/CI/badge.svg)](https://github.com/Oefenweb/ansible-shiny-server/actions?query=workflow%3ACI)
![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-shiny--server-blue.svg)](https://galaxy.ansible.com/Oefenweb/shiny_server/)

Set up (the latest version of) [Shiny Server](https://www.rstudio.com/products/shiny/shiny-server/) in Debian-like systems.

#### Requirements

* `curl` (will be installed)
* `r-base` (will not be installed)
* `shiny` ([R package](https://cran.r-project.org/web/packages/shiny/index.html), will not be installed)

#### Variables

* `shiny_server_version`: [default: `1.5.16.958`]: Version to install
* `shiny_server_install`: [default: `[]`]: Additional packages to install (e.g. `r-base`)

* `shiny_server_conf_directives`: [default: see `defaults/main.yml`]: Configuration directives ([see](http://docs.rstudio.com/shiny-server/#default-configuration))

## Dependencies

None

## Recommended

* `ansible-r` ([see](https://github.com/Oefenweb/ansible-r))
* `ansible-rstudio` ([see](https://github.com/Oefenweb/ansible-rstudio))
* `ansible-rstudio-server` ([see](https://github.com/Oefenweb/ansible-rstudio-server))

#### Example

```yaml
---
- hosts: all
  roles:
    - shiny-server
  vars:
    shiny_server_conf_directives:
      - |
        run_as shiny;
        server {
          listen 3838;
          location / {
            site_dir /srv/shiny-server;
            log_dir /var/log/shiny-server;
            directory_index on;
          }
        }

```

#### License

MIT

#### Author Information

Mischa ter Smitten

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-shiny-server/issues)!
