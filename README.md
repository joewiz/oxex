# oxex

An oXygen project file to simplify common tasks in eXist app development. 

The core file is `oxex.xpr`, an oXygen project file that defines a set of entries for oXygen's [External Tools](https://www.oxygenxml.com/doc/versions/20.0/ug-editor/topics/integrating-external-tools.html) menu. Once you open the `oxex.xpr` file in oXygen, you will see a new menu in your toolbar containing commands that perform the following tasks:

- Upload the currently open file to eXist. The file is uploaded from its location on the filesystem to the corresponding location inside of `/db/apps` (the conventional location where applications installed in the eXist database). Also, you can delete the current file from eXist—all without drilling into oXygen's [Data Source Explorer](https://www.oxygenxml.com/xml_editor/eXist_support.html) for eXist.
- Fetch updates from a remote git repository containing the app's files (without switching to or activating a git client)
- Build and deploy the app to eXist (assuming your app can be built by calling its Apache Ant build.xml file that is commonly used to package applications into for [EXPath Packages](http://expath.org/spec/pkg) in the eXist community)
- Wipe the eXist database (sometimes you just want a clean start)
- Open the current repository in commonly used apps like GitHub Desktop or Atom (pre-populating an .existdb.json file in the latter)

These commands simply pass information from oXygen to the ant scripts. 

## Setup

- Clone this repository to the folder where you clone your other eXist app repositories. For example, if you typically clone your repositories to your a directory in your home directory called "workspace", you would clone oxex there too. 
- Make a copy of `build.properties`, called `local.build.properties`.
- Supply the full path to your "workspace" directory in the property, "apps.home"; and supply your eXist credentials in "local.instance.user" and "local.instance.password".
- Open the `oxex.xpr` file in oXygen, which will cause oXygen to open the Project pane with the parent directory, and which will configure an External Tools menu with oxex's commands.
- Select the "Setup" command to download required libraries for interacting with eXist. This is only needed once.
- Using oXygen's project pane, open a file in one of your eXist applications (e.g., `workspace/my-app/my-file`).
- Select the "Upload current file to localhost" to upload the file to the database (e.g., `/db/apps/my-app/my-file`) (keyboard shortcut: command-u).
- Select the "Deploy current repository to localhost" to call the app's own `build.xml` file and upload and deploy the resulting .xar file (conventionally stored in the build directory)..

These functions can be called directly from the command line, but they are geared toward use from oXygen. Additional functions are contained in `build.xml`, which could be exposed if there is interest.
