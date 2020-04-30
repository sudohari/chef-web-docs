---
resource_reference: true
common_resource_functionality_multiple_packages: false
common_resource_functionality_resources_common_windows_security: false
cookbook_file_specificity: false
debug_recipes_chef_shell: false
handler_custom: false
handler_types: false
nameless_apt_update: false
nameless_build_essential: false
properties_multiple_packages: false
properties_resources_common_windows_security: false
properties_shortcode: 
ps_credential_helper: false
registry_key: false
remote_directory_recursive_directories: false
remote_file_prevent_re_downloads: false
remote_file_unc_path: false
resource_directory_recursive_directories: false
resource_package_options: false
resources_common_atomic_update: false
resources_common_guard_interpreter: false
resources_common_guards: true
resources_common_notification: true
resources_common_properties: true
ruby_style_basics_chef_log: false
syntax_shortcode: 
template_requirements: false
unit_file_verification: false
title: kernel_module resource
resource: kernel_module
aliases:
- "/resource_kernel_module.html"
menu:
  infra:
    title: kernel_module
    identifier: chef_infra/cookbook_reference/resources/kernel_module kernel_module
    parent: chef_infra/cookbook_reference/resources
resource_description_list:
- markdown: 'Use the **kernel_module** resource to manage kernel modules on Linux

    systems. This resource can load, unload, blacklist, disable, install,

    and uninstall modules.'
resource_new_in: '14.3'
syntax_full_code_block: |-
  kernel_module 'name' do
    load_dir        String # default value: "/etc/modules-load.d"
    modname         String # default value: 'name' unless specified
    options         Array
    unload_dir      String # default value: "/etc/modprobe.d"
    action          Symbol # defaults to :install if not specified
  end
syntax_properties_list: 
syntax_full_properties_list:
- "`kernel_module` is the resource."
- "`name` is the name given to the resource block."
- "`action` identifies which steps Chef Infra Client will take to bring the node into
  the desired state."
- "`load_dir`, `modname`, `options`, and `unload_dir` are the properties available
  to this resource."
actions_list:
  :blacklist:
    markdown: Blacklist a kernel module.
  :disable:
    markdown: 'Disable a kernel module


      **New in Chef Client 15.2.**'
  :install:
    markdown: Default. Load kernel module, and ensure it loads on reboot.
  :load:
    markdown: Load a kernel module.
  :uninstall:
    markdown: Unload a kernel module and remove module config, so it doesn't load
      on reboot.
  :unload:
    markdown: Unload kernel module.
  :nothing:
    shortcode: resources_common_actions_nothing.md
properties_list:
- property: load_dir
  ruby_type: String
  required: false
  default_value: "/etc/modules-load.d"
  description_list:
  - markdown: The directory to load modules from.
- property: modname
  ruby_type: String
  required: false
  default_value: The resource block's name
  description_list:
  - markdown: An optional property to set the kernel module name if it differs from
      the resource block's name.
- property: options
  ruby_type: Array
  required: false
  new_in: '15.4'
  description_list:
  - markdown: An optional property to set options for the kernel module.
- property: unload_dir
  ruby_type: String
  required: false
  default_value: "/etc/modprobe.d"
  description_list:
  - markdown: The modprobe.d directory.
examples_list: 
- example_heading: Install and load a kernel module and ensure it loads on reboot.
  text_blocks:
  - code_block: kernel_module 'loop'
- example_heading: 'Install and load a kernel with a specific set of options and ensure
    it

    loads on reboot.'
  text_blocks:
  - markdown: 'Consult kernel module documentation for specific options that are

      supported.'
  - code_block: "kernel_module 'loop' do\n  options [ 'max_loop=4', 'max_part=8' ]\n\
      end"
- example_heading: Load a kernel module.
  text_blocks:
  - code_block: "kernel_module 'loop' do\n  action :load\nend"
  - markdown: "**Unload a kernel module and remove module config so it doesn\u2019\
      t load on\nreboot.**"
  - code_block: "kernel_module 'loop' do\n  action :uninstall\nend"
- example_heading: Unload kernel module.
  text_blocks:
  - code_block: "kernel_module 'loop' do\n  action :unload\nend"
- example_heading: Blacklist a module from loading.
  text_blocks:
  - code_block: "kernel_module 'loop' do\n  action :blacklist\nend"
- example_heading: Disable a kernel module.
  text_blocks:
  - code_block: "kernel_module 'loop' do\n  action :disable\nend"

---
