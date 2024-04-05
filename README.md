# build-tools

Common build configs and tools used in WlcmTech.

## [wlcmtech_checks.xml](wlcmtech_checks.xml)

A custom [checkstyle] configuration file based on default [google_checks.xml](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/google_checks.xml) config with a few modifications of our own that make our eyes hurt less when we look at the code. Namely we've modified the following modules' properties:

- LineLength -> max -> 120 (default: 100)
- Indentation -> basicOffset -> 4 (default: 2)

### Usage

#### IntelliJ 

In IntelliJ this can be used to set the code style for Java which will be adjusted according to the rules defined in the xml config.

First install [CheckStyle-IDEA](https://plugins.jetbrains.com/plugin/1065-checkstyle-idea) plugin.

Then download the xml file locally to a temporary location and go to Settings -> Editor -> Code Style -> Java -> Import Scheme -> Checkstyle configuration

#### Maven

With maven, one can simply provide the url to the raw file in the [checkstyle maven plugin config](https://maven.apache.org/plugins/maven-checkstyle-plugin/examples/custom-checker-config.html).

> [!NOTE]
> The plugin documentation incorrectly sets custom `configLocation` property in a plugin configuration under `project.reporting.plugins` tag. We've found that this currently does not work and the plugin will use a default sun_java config instead.
> Instead, set the configuration for the plugin under `project.build.plugins` for the checkstyle plugin, and then the custom config will be used.


