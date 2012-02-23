# PrefixrAntTask

## Introduction

This project is the creation of an Apache Ant task for use of the Prefixr api (http://prefixr.com/). It will 
allow developers to make use of css3 styles and replace these with the correct prefix at build/deploy time.

It will allow for a user to set multiple filesets to be scanned for css content and call the Prefixr Api to prefix 
the CSS3 styles with the cross browser spesific styles.

For example a css file containing the following styles

```css
.class {
  border-radius: 5px;
```

will be converted to 

```css
.class{
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  border-radius: 5px;
}
```

## Usage

The task allows for an the user to either override the current css file or to use a suffix at the end of the file. 

I have included a example build file to use the ANT task at https://github.com/jaconel/PrefixrAntTask/blob/master/src/prefixr.build.xml.


In order to use the task you can either clone this directory and build the JAR yourself or use the pre-built jar included in the source directory.

Ensure that the JAR is available some where on your class path and add the following to the top of your build file 

```xml
<taskdef name="prefixr" classname="org.apache.tools.ant.taskdefs.Prefixr" classpath="Prefixr.jar" />
```

once this has been done, you can use the task def in any of your targets in the following way

```xml
<prefixr override="false" suffix="out">
  <fileset dir="/path/to/css/folder" includes="**/*.css" />
</prefixr>
```

When the override option is set to true, the suffix option will be ignored and your current css files will be overriden with the results received from prefixr.

If the override option is set to false a suffix is required. The suffix will be used when creating a new file to save your css to. For example, the above code
will save the results for a file named styles.css to styles.out.css. This option is usefull if you do not wish to override your current css.

For more information on using Filesets, please refer to the Apache documentation found at http://ant.apache.org/manual/Types/fileset.html
    