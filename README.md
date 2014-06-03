Team-Explorer-Everywhere-Cheatsheet
===================================

A cheatsheet for common tasks within Team Explorer Everywhere

Create a workspace and get all files
====================================

    mkdir $TEMP_DIR$
    tf workspace -new $TEMP_WORKSPACE$ -collection:$SERVER_URL$/$COLLECTION_NAME$
    tf workfold -map $SERVER_PATH$ -workspace:$TEMP_WORKSPACE$ $TEMP_DIR$
    cd $TEMP_DIR$
    tf get
Where:

    $TEMP_WORKSPACE$  - any string will do (Should be configurable)
    $SERVER_URL$      - The URL of your TFS server (usually ends with "/tfs" and by default is on port 8080)
    $COLLECTION_NAME$ - The name of the collection (i.e. DefaultCollection)
    $TEMP_DIR$        - Any valid directory (Relative paths are not allowed)
    $SERVER_PATH$     - The path to the team project

Add a file to repo and checkin
==============================
NOTE: Must be in a directory which is mapped using the above workfold command

    tf add $FILENAME$
Where: 

    $FILENAME$ - Name of file to add (Must exist!)

Check-in changes
================
NOTE: Must be in a directory which is mapped using the above workfold command

    tf checkin -comment:$COMMENT$
Where:

    $COMMENT$  - A comment to associate with the changeset

Get the status of workspace
===========================
NOTE: Must be in a directory which is mapped using the above workfold command

    tf status

Unmap local directory
=====================
    tf workfold -unmap -collection:$SERVER_URL$/$COLLECTION_NAME$ -workspace:$TEMP_WORKSPACE$ $TEMP_DIR$
Where:

    $TEMP_WORKSPACE$  - any string will do (Should be configurable)
    $SERVER_URL$      - The URL of your TFS server (usually ends with "/tfs" and by default is on port 8080)
    $COLLECTION_NAME$ - The name of the collection (i.e. DefaultCollection)
    $TEMP_DIR$        - Any valid directory (Relative paths are not allowed)

Delete workspace
================
    tf workspace -delete -collection:$SERVER_URL$/$COLLECTION_NAME$ $TEMP_WORKSPACE$
Where:

    $TEMP_WORKSPACE$  - any string will do (Should be configurable)
    $SERVER_URL$      - The URL of your TFS server (usually ends with "/tfs" and by default is on port 8080)
    $COLLECTION_NAME$ - The name of the collection (i.e. DefaultCollection)

