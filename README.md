[Ant]: https://ant.apache.org
[ant-contrib]: http://ant-contrib.sourceforge.net/
[ant-contrib-1.0b2]: https://sourceforge.net/projects/ant-contrib/files/ant-contrib/ant-contrib-1.0b2/ant-contrib-1.0b2-bin.zip/download
[maven]: https://maven.apache.org/


# ant-jag-contrib

This is an extension of [ant-contrib] with contributed tasks.

It was developed in 2013 to help with the building of Eclipse RCP plugins without
using the `build.xml` generated by Eclipse itself, being more generic than those.
One of the disadvantages of using the [Ant] scripts created by Eclipse is that they
change everytime a new dependency is added to the plugin, and then they need to
be checked in in the code repository. However with `ant-jag-contrib`, the
task for building takes automatically the dependency, without further modifications.

## Dependency
It requires the [ant-contrib-1.0b2] library installed in [Ant] classpath
(`ANT_HOME/lib`, `${user.home}/.ant/lib`, etc.).

## Compilation and installation
In order to create the package, you need to have installed [maven]
The generated package `ant-jag-contrib` must be put also into the [Ant]
classpath to be accessible by the script making use of any of the contributed
tasks.

## Tasks
Currently are implemented the following categories:

* log
* property
* build
* plugin

### log

* Description: These are contributed tasks for logging the [Ant] target or operations.
* **xmlns**: antlib:org.jag.common.log

The contribution of tasks is done introducing in the script `<project>` tag
the location of the tasks definition:

> <project xmlns:log="antlib:org.jag.common.log" name="...">

#### init

Description: Initializes the logger. It must come among the first lines in the [Ant] script

Parameter | Mandatory | Default value | Description
--- | --- | --- | ---
`dir` | Optional | Current directory, `.` |  Directory where to write the logs to.
`file` | Optional | `${ant.project.name}_${DSTAMP}${TSTAMP}.log` | Log file where to write the log entries to.
