# WordPress localisation configurations

## TL;DR

This is a repository of configuration files that describe how WordPress "bundles" (themes and plugins) have been **localised**.

It's been set up specifically to help the [Loco Translate](https://localise.biz/help/wordpress/translate-plugin) plugin make sense of non-standard translation setups, but any software could potentially use it for the same purpose.

Current status: **experimental**.


## Background

Developers have a great deal of freedom in how they arrange, compile and load translation files into WordPress. This makes it very hard for other software to **automatically** present translators with the correct workflow for adding new files. WordPress is focussed on the end result of loading translations and lacks a formal enough structure for bundles to be self-describing about their localisaton setup. When bundles are set up in particularly unconventional ways, the software's burden is shifted to the translator and very often that person is not technical enough to make sense of all the files and what they're supposed to do with them. We have [over 700 support requests](https://wordpress.org/support/plugin/loco-translate) as testament to this.

The new version of Loco Translate ([currently in beta](https://localise.biz/help/wordpress/translate-plugin/developers)) introduces a [configuration model](https://localise.biz/help/wordpress/translate-plugin/manual/bundle-config) that allows the localisation of bundles to be described in great detail. Although we created this for our own needs, the model could be useful to other translation software too.



## Contributing

We welcome contributions to the repository. We'll be adding bundles as needed (generally when people report problems), but there are thousands upon thousands of bundles out there. We can't do all that on our own.

If you're a theme or plugin developer, please consider shipping a `loco.xml` file in the root of your bundles. This will make your work automatically [compatible with Loco Translate](https://localise.biz/help/wordpress/translate-plugin/authors). Thousands of non-technical translators will benefit without even knowing it.



## The repository

The repository is just a dumb collection of files. We've chosen XML, because it best [visualises the model](https://localise.biz/help/wordpress/translate-plugin/manual/bundle-config/schema). To look up data in the repository you'll have to build your own tools to compile and query the data. Tooling is beyond the scope of this project for the time being.

### The model

The configuration model is [documented here](https://localise.biz/help/wordpress/translate-plugin/manual/bundle-config/). We welcome suggestions and feedback, but please stick to the [documented XML schema](https://localise.biz/help/wordpress/translate-plugin/manual/bundle-config/schema) if you plan to contribute.

### File layout

Each configuration file is held in a simple folder structure under `data/<vendor>/(theme|plugin)/`. For example, you'll find Loco's own configuration under `data/wordpress/plugin/loco-translate/`.

You can call the XML file anything you like, but `loco.xml` is preferred for the latest, stable version of a bundle.

### Vendor names

The directories immediately under the `data` directory are short names for the websites that officially list the bundles. For example "wordpress" refers to a bundle listed on wordpress.org and wordpress.com. We'd like to keep the vendor list under control, so please don't add personal websites, or sites dedicated to a single bundle. End users may have to select the correct vendor from a list, so we'd like to keep that list as short as possible.

### Bundle names

The directories inside each `"themes"` or `"plugins"` directory are named after the unique slug of each bundle. WordPress has no real concept of a universally unique bundle identifier, but this slug must identify the bundle uniquely for its type within each vendor. Ideally the slug is also the default folder name that the bundle installs into.


### Simple bundles

Bundles that follow WordPress localisation standards may be self-describing enough in many cases. Good examples are the core WordPress themes such as "Twenty Fifteen". 
They declare a single text domain and place conventionally named files in a "languages" subdirectory. We won't be adding such bundles ourselves but you're welcome to do so.

### Premium bundles

We're keen to list premium themes and plugins as well as open source ones, but for cost and licensing reasons we're unlikely to be adding these ourselves. If you've bought a theme and had to configure our plugin to translate it, please consider sharing your configuration here.

