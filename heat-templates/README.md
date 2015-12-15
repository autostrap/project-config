# Heat Templates with Cloudstrap Usage Examples

This directory contains the following example heat templates:

* 'nginx-masterless.yaml`: Deploys a Sensu server configured through masterless puppet.
* 'nginx-master-agent.yaml`: Deploys a Puppet master and web server (the latter receives its configuration from the Puppet master).

These templates will only work on Openstack Kilo and later.

You can instantiate these stacks by issuing a

  `heat stack-create -f nginx-masterless.yaml -P key_name=<my_nova_keypair_name> -P deploy_key="$(cat <my_deploy_key>)" -P config_repo=<my_project-config_git_fork> nginx-masterless`

for the masterless puppet setup, and
  
  `heat stack-create -f nginx-master-agent.yaml -P key_name=<my_nova_keypair_name> -P deploy_key="$(cat <my_deploy_key>)" -P config_repo=<my_project-config_git_fork> nginx-master-agent`

for the Puppet master/agent setup. 

`<my_deploy_key>` is your SSH private deployment key, for example ~/.ssh/deploy.key
`<my_nova_keypair_name>` is the name of the SSH Keypair in nova, for example "mykey"
`<my_project-config_git_fork>` is the fork of project-config specific to your client, for example "git@gitlab.syseleven.de:mycustomer/project-config.git"


If you would like to use Syseleven's
[scloud](https://github.com/syseleven/python-cloudutils) utility, you can
instatiate these stacks using the scloud configuration provided along with the
heat templates:

  `scloud --config-file ~/.scloud.conf --config-file nginx-masterless.conf`
  `scloud --config-file ~/.scloud.conf --config-file nginx-master-agent.conf`

This assumes you configured sensible defaults for the `key_name` and
`deploy_key` parameters in ~/.scloud.conf.
