Description
===========

This directory contains node specific configuration. Its contents are added to
the hierarchy based on the following fact interpolation:

  "project-config/nodes.d/%{::fqdn}"

This means that all files in this directory must have the desired node's
fully-qualified domain name as their filename (and the extension .yaml, of
course).

At minimum node configuration files must contain a classes array containing the
classes to be deployed on the node in question. config.d and repos.d
configuration for these classes must either be pulled in from global-config by
adding the relevant topics to puppet/topics (see above) or by adding it to
puppet/hieradata/repos.d and puppet/hieradata/config.d in full (the latter is
not recommended). Apart from a classes array, node configuration may contain
any configuration parameters meant exclusively for a given node.  Configuration
in nodes.d will take precedence over anything apart from override.yaml (the
latter is passed as a heat parameter at stack creation time).

Each node to be managed by puppet must have at least one entry that matches its
::fqdn or ::nodetype fact, respectively in either puppet/hieradata/nodes.d or
puppet/hieradata/nodetypes.d (or both).
