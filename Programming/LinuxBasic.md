# Content

# Multiple Directories Createion

    mkdir sa{1..50}
    mkdir -p sa{1..50}/sax{1..50}
    mkdir {a-z}12345 
    mkdir {1,2,3}
    mkdir test{01..10}
    mkdir -p `date '+%y%m%d'`/{1,2,3} 
    mkdir -p $USER/{1,2,3} 

# Copy a File to Multipule Folder

    echo dir1 dir2 dir3 | xargs -n 1 cp file1
    OR
    echo dir{1..10} | xargs -n 1 cp file1


# Scp Multipule Folder/File to Target Server

    scp -r `echo dir{1..10}` user@target.server:/target/server/path/
