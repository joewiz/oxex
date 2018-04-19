# oxex

An oXygen project file to aid in common tasks in eXist app development. 

The core file is `oxex.xpr`, an oXygen project file that contains entries for oXygen's External Tools menu. Once you open this file in oXygen, you will see a new menu in your toolbar containing commands that perform the following tasks:

- Upload the currently open file (from the filesystem) to the corresponding location inside of /db/apps (the conventional location in the eXist database where applications installed). Also, you can delete the current file from the database.
- Fetch updates from a remote git repository containing the app's files
- Build and deploy the app to eXist
- Wipe the eXist database
- Open the curent repository in commonly used apps like GitHub Desktop or Atom (pre-populating an .existdb.json file in the latter)

These commands simply pass information from oXygen to the ant scripts. 

## Setup

- Clone the repository to the folder where you clone your other eXist app repositories. For example, if you typically clone your repositories to your a directory in your home directory called "workspace", you would clone oxex there too. 
- Make a copy of `build.properties`, called `local.build.properties`.
- Supply the full path to your "workspace" directory in the property, "apps.home"; and supply your eXist credentials in "local.instance.user" and "local.instance.password".
- Open `oxex.xpr` and notice the new External Tools menu.
- Select the "Setup" command to download required libraries for interacting with eXist (only needed once).
- Using oXygen's project pane, open a file in one of your eXist applications (e.g., `workspace/my-app/my-file`).
- Select the "Upload current file to localhost" to upload the file to the database (e.g., `/db/apps/my-app/my-file`) (keyboard shortcut: command-u).
- Select the "Deploy current repository to localhost" to call the app's own `build.xml` file and upload and deploy the resulting .xar file (conventionally stored in the build directory)..

These functions can be called directly from the command line, but they are geared toward use from oXygen. Additional functions are contained in `build.xml`, which could be exposed if there is interest.
