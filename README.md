# Home Assistant configuration

This git repository contains my home assistant configuration, maybe it's useful for other people.
Copy what ever you can use for your own projects and feel free to send bugreports if you find
errors.

## Dashboards

* Folder: [dashboards](./dashboards)

My dashboard exported as yaml file (at the moment it's only one, may change in the future).

## Packages

* Folder: [packages](./packages)

I've defined alle sensors, helpers and automations in yaml package files, which are included by
the configuration.yaml, therefor I've added the following lines:

```yaml
homeassistant:
  packages: !include_dir_named packages
```

The yaml files inside this [packages](./packages) directory are imported in alphabetic order,
I've prefixed the files with a number (as in unix System-V-Init boot files). Files which do not
depend on others are prefixed by "000_", the ones depend on them by "010_" and so on. The gaps
can be used to add depending files without renaming existing.

The package files containing comments which describe the functionality.

## VControld

* Folder: [vcontrold](./vcontrold)

My Viessmann Vitocal 350 heatpump with Vitotronic 200 is connected to Home Assistant by optolink
cable and included by vcontrol plugin. Two configuration files are used to make sensors and input
widgets available by mqtt, both you can find in this folder.

The vcontrold.xml has a tty definition based on serial device, this has to be changed to match
the specific situation. My heatpump additional has a bug, the wattmeter reports wrong results,
I've compared with electricity meter and added a correction factor of 1.7 to fix this for the
units "JAZ korrigiert" and "Kilowattstunden korrigiert". If you want to use my configuration,
please change the calc line for this units as in unit "Kilowattstunden".

## WWW

* Folder: [www/PV_forecast/](./www/PV_forecast/)

In this folder I've added a json file containing some definitions of my solar system, it's read
by one of the configuration packages using rest.
