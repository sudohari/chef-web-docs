+++
title = "Supermarket Logs"
description = "DESCRIPTION"
draft = false

aliases = "/supermarket_logs.html"

[menu]
  [menu.docs]
    title = "Log Files"
    identifier = "chef_infra/setup/supermarket/supermarket_logs.html Log Files"
    parent = "chef_infra/setup/supermarket"
    weight = 60
+++    

[\[edit on
GitHub\]](https://github.com/chef/chef-web-docs/blob/master/chef_master/source/supermarket_logs.rst)

The Chef Supermarket omnibus package does not log Ruby on Rails messages
by default. To enable debug logging, edit the
`/opt/supermarket/embedded/service/supermarket/config/environments/production.rb`
file and set the `config.log_level` setting to `:debug`:

``` ruby
config.logger = Logger.new('/var/log/supermarket/rails/rails.log')
config.logger.level = 'DEBUG'
config.log_level = :debug
```

Save the file, and then restart the Ruby on Rails service:

``` bash
$ supermarket-ctl restart rails
```