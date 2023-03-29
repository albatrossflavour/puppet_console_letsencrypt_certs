# puppet_console_letsencrypt_certs


## Table of Contents

1. [Description](#description)
1. [Setup - The basics of getting started with puppet_console_letsencrypt_certs](#setup)
    * [What puppet_console_letsencrypt_certs affects](#what-puppet_console_letsencrypt_certs-affects)
    * [Setup requirements](#setup-requirements)
    * [Beginning with puppet_console_letsencrypt_certs](#beginning-with-puppet_console_letsencrypt_certs)
1. [Usage - Configuration options and additional functionality](#usage)
1. [Limitations - OS compatibility, etc.](#limitations)
1. [Development - Guide for contributing to the module](#development)

## Description

Managing the Puppet console's SSL certificates can be automated, but it's not straightforward if you want them to be managed by Lets Encrypt.

This module will allow you request, install, and manage valid SSL certs for your console, via Lets Encrypt.

It does require that port 80 on your puppet server is accessible from the internet, and that your puppet servers has a publicly resolvable DNS name.

## Setup

### What puppet_console_letsencrypt_certs affects

The module will replace the autogenerated, self-signed, SSL certificates used by default.  These certs are usually found in `/etc/puppetlabs/puppet/ssl`.

It uses the [letsencrypt](https://forge.puppet.com/modules/puppet/letsencrypt/readme) module from Vox Pupuli to do the hard lifting.

### Setup Requirements

You **MUST** disable the default `http_redirect` which is created.  This can be done by setting the following value in the puppet server's hiera:
`puppet_enterprise::profile::console::proxy::http_redirect::enable_http_redirect: false`

The module will check that it is disabled and will cause a catalog compilation failure if it isn't.

### Beginning with puppet_console_letsencrypt_certs

The very basic steps needed for a user to get the module up and running. This
can include setup steps, if necessary, or it can be an example of the most basic
use of the module.

## Usage

At the very basic level, you can simply:
* Add the module and dependencies to your `Puppetfile`
* Add the following hiera to `common.yaml` : `puppet_enterprise::profile::console::proxy::http_redirect::enable_http_redirect: false`
* Classify your puppet server with : `include puppet_console_letsencrypt_certs`

## Limitations

Only works with Puppet Enterprise

## Development

Fork, develop, submit a pull request

Please make sure all pull requests include testing and that the tests pass

[1]: https://puppet.com/docs/pdk/latest/pdk_generating_modules.html
[2]: https://puppet.com/docs/puppet/latest/puppet_strings.html
[3]: https://puppet.com/docs/puppet/latest/puppet_strings_style.html
