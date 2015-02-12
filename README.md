# encrypted diary 
This collection of simple bash scripts provide an easy way to write  confidential notes with strong encryption. It uses asymetric GnuPG for encryption,  therefore you can write entries without entering the gpg password. You only have to decrypt (and enter your key-password) when you actually want to read something. 


# setup (on osx)
 * brew install fswatch 
 * brew install gpg 
 * create a new GPG key only for this purpose (choose a strong passphrase!)

# configuration 
You have to edit a few file before getting started: 

 * diary-add and diary-edit: set your keyid (GPG_KEYID)
 * diary-add: change default directory (ENTRIES_DIR)
 * diary-edit: set your favorite text editor (instead of Mou) 

# usage 
## write an entry (add)
use ``diary-add`` which reads stdin: 

    echo my first entry | diary-add

    diary-add < notes.html
    
    diary-add
     my first entry
     <CTRL-D>

## edit encrypted entry
use ``diary-edit`` to open gpg-file in a fancy text/markdown editor. When saving, the content is automatically encrypted again. 

    diary-edit path/to/file.txt.asc

or use the vim gpg plugin: https://github.com/jamessan/vim-gnupg

    vi path/to/file.txt.asc

## decrypt to console
``diary-print`` simply prints an entry to stdout. 

    diary-print path/to/file.md.asc
