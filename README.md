# build-tools

Common build configs and tools used in WlcmTech.

## [.editorconfig](.editorconfig)

An [EditorConfig](https://editorconfig.org/) config file for our tech-stack. This config helps to maintain the consistency of the code-style across our codebase while having out-of-box support for most popular IDEs like IntelliJ, VSCode, VIM, etc., and requires almost no setup on the client-side.

Apart from default editorconfig properties this file also contains IDE-specific configs, which simplify usage of the configuration with a given IDE, like IntelliJ.

### Usage

Simply copy the file to the root of the project. The [supported IDE](https://editorconfig.org/#pre-installed) should pick it up and start using the configuration automatically.

> [!NOTE]
> Might need to check that you have the editorconfig plugin enabled in your IDE.

## [wlcmtech_checks.xml](wlcmtech_checks.xml)

A custom [checkstyle] configuration file based on default [google_checks.xml](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/google_checks.xml) config with a few modifications of our own that make our eyes hurt less when we look at the code.

All the custom modifications are specified at the top of our config file.

### Usage

#### IntelliJ

In IntelliJ this can be used to set the code style for Java which will be adjusted according to the rules defined in the xml config.

First install [CheckStyle-IDEA](https://plugins.jetbrains.com/plugin/1065-checkstyle-idea) plugin.

Then download the xml file locally to a temporary location and go to Settings -> Editor -> Code Style -> Java -> Import Scheme -> Checkstyle configuration

Additionally, to enable real-time feedback in the IDE, go to Settings -> Tools -> Checkstyle. Then add a new configuration via URL of the raw xml config file.
See [checkstyle-idea configuration files](https://github.com/jshiell/checkstyle-idea?tab=readme-ov-file#configuration-files) documentation for more details.

#### Maven

With maven, one can simply provide the url to the raw file in the [checkstyle maven plugin config](https://maven.apache.org/plugins/maven-checkstyle-plugin/examples/custom-checker-config.html).

> [!NOTE]
> The plugin documentation incorrectly sets custom `configLocation` property in a plugin configuration under `project.reporting.plugins` tag. We've found that this currently does not work and the plugin will use a default sun_java config instead.
> Instead, set the configuration for the plugin under `project.build.plugins` for the checkstyle plugin, and then the custom config will be used.


