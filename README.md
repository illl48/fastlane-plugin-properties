# properties plugin

[![fastlane Plugin Badge](https://rawcdn.githack.com/fastlane/fastlane/master/fastlane/assets/plugin-badge.svg)](https://rubygems.org/gems/fastlane-plugin-properties)

## Getting Started

This project is a [_fastlane_](https://github.com/fastlane/fastlane) plugin. To get started with `fastlane-plugin-properties`, add it to your project by running:

```bash
fastlane add_plugin properties
```

## About properties

Adds 2 actions to fastlane to read and update properties files.
Adds 2 actions to read/write the whole properties file.
Adds 2 more actions to increase versionCode and versionName fast.

Your file does not require to be `.properties`. This plugin can work with any file which content is in the `KEY=VALUE` format, ie `.env` files or etc.

## Example

```ruby
lane :test do

  # Read VERSION_NAME value from Configs/versions.properties
  version_name = get_properties_value(
    key: "VERSION_NAME",
    path: "./Configs/versions.properties"
  )

  # Set VERSION_NAME value to '0.2.0' in Configs/versions.properties
  # VERSION_NAME will be added if it doesn't exist
  set_properties_value(
    path: "./Configs/versions.properties",
    key: "VERSION_NAME",
    value: "0.2.0"
  )

  # Increase VERSION_CODE value in Configs/versions.properties by 1
  increment_version_code_in_properties_file(
    key: "VERSION_CODE",
    path: "./Configs/versions.properties"
  )
  
  # Increase VERSION_NAME's minor value in Configs/versions.properties by 1
  # update_type can be one of ['major', 'minor', 'patch']. Default to 'minor'
  increment_version_name_in_properties_file(
    key: "VERSION_NAME",
    path: "./Configs/versions.properties",
    update_type: "minor"
  )

  # Read the versions.properties file and sttore it as a hash-map in the content variable
  content = parse_properties_file(
    path: "./Configs/versions.properties"
  )

  # Rewrites your versions.properties with new data, generated from some_hash
  write_properties_file(
    path: "./Configs/versions.properties",
    hash: some_hash
  )

end
```

## Issues and Feedback

For any other issues and feedback about this plugin, please submit it to this repository.

## Troubleshooting

If you have trouble using plugins, check out the [Plugins Troubleshooting](https://docs.fastlane.tools/plugins/plugins-troubleshooting/) guide.

## Using _fastlane_ Plugins

For more information about how the `fastlane` plugin system works, check out the [Plugins documentation](https://docs.fastlane.tools/plugins/create-plugin/).

## About _fastlane_

_fastlane_ is the easiest way to automate beta deployments and releases for your iOS and Android apps. To learn more, check out [fastlane.tools](https://fastlane.tools).
