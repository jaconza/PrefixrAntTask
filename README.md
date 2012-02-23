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

See the https://github.com/jaconel/PrefixrAntTask/blob/master/src/prefixr.build.xml file for example usage