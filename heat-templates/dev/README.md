# Heat templates for development use

In this directory you will find Heat templates that provide useful
functionality for Autostrap development.

## blank_nginx-master-agent.yaml

This template builds two Nova instances for test-driving Autostrap's
master-agent based puppet setup using autostrap.standalone. The instances will
not have a config drive, so you will have to specify metadata parameters as
`-m` arguments to `autostrap.standalone`. For convenience it clones the
[bootstrap-scripts](https://github.com/autostrap/bootstrap-scripts) repository
and accepts `deploy_key` and `override_yaml` parameters. The contents of these
parameters will be written to `/root/deploy_key` and `/root/override.yaml`,
respectively.

You will find example `autostrap.standalone` invocations in the template's
description section.

## blank_nginx-masterless.yaml

This template builds one Nova instance for test-driving Autostrap's masterless
puppet setup using autostrap.standalone. The instances will not have a config
drive, so you will have to specify metadata parameters as `-m` arguments to
`autostrap.standalone`. For convenience it clones the
[bootstrap-scripts](https://github.com/autostrap/bootstrap-scripts) repository
and accepts `deploy_key` and `override_yaml` parameters. The contents of these
parametrs will be written to `/root/deploy_key` and `/root/override.yaml`,
respectively.

You will find an example `autostrap.standalone` invocation in the template's
description section.

## nginx-master-agent.yaml

This template is largely identical to the identically named template in the
parent directory and builds the Autostrap documentation web server, configured
by a puppet master. There is just one difference: where the original template
passes the minimum number of parameters to the `AS::autostrap` resource, this
template exposes _all_ parameters of the `AS::autostrap` resource as template
parameters.

## nginx-masterless.yaml

This template is largely identical to the identically named template in the
parent directory and builds the Autostrap documentation web server, configured
by masterless puppet. There is just one difference: where the original template
passes the minimum number of parameters to the `AS::autostrap` resource, this
template exposes _all_ parameters of the `AS::autostrap` resource as template
parameters.

