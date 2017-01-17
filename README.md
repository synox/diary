# encrypted diary
This collection of simple bash scripts provide an easy way to write  confidential notes with strong encryption. It uses asymetric GnuPG for encryption,  therefore you can write entries without entering the gpg password. You only have to decrypt (and enter your key-password) when you actually want to read something.

Hint: Can be combined mit https://github.com/synox/secret-letterbox

# setup (on osx)
 * brew install fswatch
 * install GnuPG  (https://gpgtools.org/)
 * create a new GPG key only for this purpose (choose a strong passphrase!)
 * add the scripts to your `PATH`.

# configuration
You have to configure some variables with your ``.bash_profile`` (or edit the source files). bash example:

```bash
export DIARY_KEYID=1234567
export DIARY_EDITOR=/Applications/Mou.app/Contents/MacOS/Mou
export DIARY_DIRECTORY=/home/joe/diary
export DIARY_READER=subl
```

fishshell example:

```bash
set -x DIARY_KEYID 1234567
set -x DIARY_EDITOR /Applications/Mou.app/Contents/MacOS/Mou
set -x DIARY_DIRECTORY /home/joe/diary
set -x DIARY_READER subl
```

# usage
## write an entry (add)
use ``diary-add`` which reads stdin:

```bash
echo my first entry | diary-add

diary-add < notes.html

diary-add
 my first entry
 <CTRL-D>
 ```

`diary-add-hidden` is just like `diary-add`, but without echoing what you type.

or you can attach a file

```bash
diary-add /home/john/photo.jpg
```

## edit encrypted entry
use ``diary-edit`` to open gpg-file in a fancy text/markdown editor. When saving, the content is automatically encrypted again.

```bash
diary-edit path/to/file.txt.gpg
```
or use the vim gpg plugin: https://github.com/jamessan/vim-gnupg

```bash
vi path/to/file.txt.gpg
```

## decrypt one entry console
``diary-print`` simply prints an entry to stdout.

```bash
diary-print path/to/file.txt.gpg
```

## read all entries
``diary-read-all`` decrypts all entries and prints in $DIARY_READER. It used `gpg2` for to use the gpg-agent on OSX. The implementation can be changed with the environment variable `GPG_CMD`.

```bash
diary-read-all
```

----

### similar projects
There are a few similar projects. I didn't use them because I want the scripts to be short and validatable.

* https://github.com/matthiasbeyer/diary.sh/
* https://github.com/colinux/GPG-Editor/blob/master/GPG-Editor.sh
* https://github.com/almien1/NoPeeking

Articles:
 * http://abesto.net/journaling-for-geeks/
