# Metadata Navigator for SAS®

The Metadata Navigator for SAS® is an open source project for revealing information on SAS® Metadata.
It is easy to use, easy to deploy, secured by SAS® Authentication, and beautifully illustrates the power of SAS® for Enterprise application development.

This application is useful for Developers and Administrators who need to understand the nuances of, or specifics about, metadata.  Being a web app, it is possible to share a link to any object!  As can be seen in the SAS code, this tool only READS metadata, it cannot be used to WRITE.

![gifrecord_2019-02-28_174948](https://user-images.githubusercontent.com/11962123/53587186-a6657e00-3b81-11e9-9ddc-f95302dbdba1.gif)


## Usage
The Metadata Navigator for SAS® is split into three parts:

### List of Types

The left hand bar always displays the full list of metadata types.  There is a filter box to quickly select the type you need.

### List of Objects

After selecting a type, you are presented with the list of objects for that type.  These can be filtered on object Name.

### Object View

After selecting an individual object, we are in Object View - and can see the object Attributes, Associations, and Properties.  This can be viewed in table form, or using a D3 graph (the top tabs let you choose a view of either table, graph, table + graph horizontal split, table + graph vertical split).  By clicking on an association, it is possible to 'drill into' then next object (a history is kept of the navigation).

## Deployment Instructions

There are five steps to getting the Meta Navigator up and running in your environment:

### 1 - Download the Source

The latest stable version of Meta Navigator is always available as a github [release](https://github.com/Boemska/metanav/releases).  If you prefer to build from source, follow the [Build Instructions](https://github.com/Boemska/meta-navigator/blob/master/CONTRIBUTING.md).

### 2 - Implement the backend

Unzip `metanavigator.zip` and import the `import.spk` file using SAS Management Console (or batch tools) to a preferred location in metadata.  Secure this application by setting an ACT on the parent folder with only ReadMetadata selected and apply it to the parent folder for the appropriate Users/Groups.  Take note of the folder root in which these STPs were deployed (it's used in the following configuration step).

### 3 - Update the h54s config file

Inside the `metanavigator` folder there is a configuration file called `h54sConfig.json`.  Open this with your favourite text editor and set the `metadataRoot` value to the SAS metadata location you've created in the previous step.

### 4 - Deploy the frontend

Copy the entire `metanavigator` folder (with the modifed `h54sConfig.json`) to your web server.  The relative path for this location would be `../Config/Lev1/Web/WebServer/htdocs` within the root SAS installation directory.


### 5 - Profit

Your app is now live!  Simply navigate to YOURHOST.DOMAIN:8080/metanavigator (where `YOURHOST` is the hostname of your SAS Web Server, `8080` is your port, and `/metanavigator` is the location in which the files were loaded in step 3).

## Build Instructions

See [CONTRIBUTING.md](https://github.com/Boemska/meta-navigator/blob/master/CONTRIBUTING.md)


