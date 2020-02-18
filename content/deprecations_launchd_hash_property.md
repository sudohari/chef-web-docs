+++
title = "Deprecation: Launchd hash Property (CHEF-12)"
draft = false

aliases = "/deprecations_launchd_hash_property.html"


  
    
    
    
    
+++    

[\[edit on GitHub\]](https://github.com/chef/chef-web-docs/blob/master/content/deprecations_launchd_hash_property.md)

<meta name="robots" content="noindex">

The launchd resource has a property called `hash` which conflicts with
the already-existing Ruby `hash` method that exists on every object.

The [CHEF-11](/deprecations_property_name_collision.html) deprecation
warns whenever a resource property is named the same as an existing Ruby
method. Chef's core `launchd` resource is guilty of this behavior. The
`hash` property accepts a Ruby Hash containing the data to be output to
the launchd property list. However, `hash` is an already-existing Ruby
method.

A deprecation warning is logged when the `hash` property is used. In
Chef Client 13, this will raise an exception and your Chef run will
fail.

Remediation
===========

When using the `launchd` resource and passing a hash for the launchd
property list, use the `plist_hash` property instead of the `hash`
property.