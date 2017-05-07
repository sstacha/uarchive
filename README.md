# uarchive
Basic script and directories to track and restore config file changes on a server.

- cd to a place in your home directory to install uarchive
- git clone https://sstacha/uarchive
- in your ~/.profile
    - add the <clone dir>/bin to your path variable
        ex: PATH=$PATH:~/uarchive/bin
    - add the ARCHIVE_DATED=<clone dir>/archive/dated
        ex: export ARCHIVE_DATED=~/uarchive/archive/dated
    - add the ARCHIVE_CURRENT=<clone dir>/current
        ex: export ARCHIVE_DATED=~/uarchive/archive/dated
        
- test it
    - create a simple text file in your home directory test.txt with the body testing
    - type: archive -c testing.txt
    - goto: <clone dir>/archive/dated/
        - there should be a testing file with a dated timestamp
        for example: /Users/sstacha/test/test.txt.20170429...
    - goto: ../current
        - there should be a similar file wihtout the timestamp
    - delete the text.txt file
    - restore the file from the current directory
        archive -r 
        or archive -r text.txt
        answer yes to prompt since there shouldn't be any other files in the archive
        
You can now easily restore files and archive them.  Check your archive directory into a git private repo for backup and tracking.

If you ever need to rebuild your server:

    - reprovision your machine
    - re-install uarchive
    - clone your private repo into the archive directory
    - archive -r
        - this is provided you keep an archive -c of all changed files on the server.
