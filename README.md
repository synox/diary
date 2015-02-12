# encrypted diary 
This is a quick and dirty collection of bash scripts that help creating encrypted diary entries. It uses GnuPG for encryption. It uses asymetric encryption, therefore you can write entries without entering the gpg password. Only for reading you need the keyfile and the password. 

# setup on osx
 * brew install fswatch
 * create a new GPG key only for this purpose

# configuration 

 * diary-add and diary-edit: set GPG_KEYID to your keyid 
 * diary-add: change default save location
 * diary-edit: set your favorite text editor (instead of Mou) 

# usage 
## add entry
diary-add works with stdin: 

    echo my first entry | diary-add

    diary-add < notes.html

## edit entry

    diary-edit path/to/file.txt.asc

or use the vim gpg plugin: https://github.com/jamessan/vim-gnupg

    vi path/to/file.txt.asc

## print entry to console

    diary-print path/to/file.md.asc
    
# motivation
There should be a easy way to write confidential notes with strong encryption. But you should only decrypt if you actually want to read something. 

The scripts are as simple as possible to make it possible to understand and validate. 

Of course this tool is not limited to diary entries. 