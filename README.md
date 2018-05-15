## Overview

A fork of the library that generates an interactive radar, inspired by [thoughtworks.com/radar](http://thoughtworks.com/radar).

This is a special modification of the original thoughtworks code to load the data directly from code instead of a googlesheet.

## Contribute
Please feel free to contribute to this repo or have a look at the original ThoughtWorks repo and consider contributing to that repository.

## Details

### Prereqs

- node.js installed
- npm installed
- webpack installed

### Setting up your data

- We leveraged excel as the source of truth for data but any data repository will work.  We created a macro in excel to iterate through a worksheet and build a "blip" extract that we could copy directly into the radar code.  These instructions are specific to excel.
- Create an excel worksheet with the following format:

| name          | ring   | quadrant               | isNew | description                                             |
|---------------|--------|------------------------|-------|---------------------------------------------------------|
| Composer      | adopt  | tools                  | TRUE  | Although the idea of dependency management ...          |
| Canary builds | trial  | techniques             | FALSE | Many projects have external code dependencies ...       |
| Apache Kylin  | assess | platforms              | TRUE  | Apache Kylin is an open source analytics solution ...   |
| JSF           | hold   | languages & frameworks | FALSE | We continue to see teams run into trouble using JSF ... |

- Run the macro in the spreadsheet to generate the blips, it will generate to a techvitalityblips.txt file.  As mentioned you can use any generation mechanism basically we just need the javascript for creating a blip and we're going to paste that content directly into the code.  It's also certainly possible to query a database for the conent and then dynamically generate.
- copy the contents of techvitalityblips.txt to the factory.js file in src/util.  There is a comment in the factory.js file "insert output from excel macro here".


### Test/Dev/Debug

- `git clone git@github.com:VantivLabs/TechVitality.git` or download the .zip file and extract manually
- `npm install`
- `npm test` - to run your tests
- `npm run dev` - to run application in localhost:8080. This will watch the .js and .css files and rebuild on file changes.  Navigate to http://localhost:8080 when running to view your 'radar'.


### Production

- make sure webpack is installed.  If not use:  npm install webpack -g
- run webpack from the site's root directory to generate the production site:  webpack -p
- production files will be located in the 'dist' folder
- copy those files to a live site and test.....life is good
