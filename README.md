# css-sprite v0.1.1

Create css sprites via bash using http://css.spritegen.com/

## Installation

I tested these scripts on a Mac and some on Git-bash.

Place the desired scripts on a folder (Ex.: `~/bin/`) and concatenate it to the PATH variable on yout ~/.bash_profile file:

    export PATH="${PATH}:~/bin"

Give executable permission on the folder:

    chmod -R +x ~/bin

## Usage

    css-sprite FOLDER_PATH [-s, -o=OUTPUT_PATH]
    css-sprite ?

`?`   help page;    
`-s`  silent mode. Only outputs the generated CSS on the stdout;    
`-o`  output png file (optional). If nothing is passed, will use the folder name and output at the same directory;

After the first run, a `sprite.config` file will be created with the file list. It is possible to create a simple replace rule so the generated CSS classes doesn't need to follow the filenames. The rule for this file is something like:

    file-name.png=.new-css-rule:hover, .in-one-line
    file-name2.png
    file-name3.png=a.css-rule:hover

When `sprite.config` exists, the script will ONLY use the listed files instead of listing through the folder.

### Examples

    css-sprite ~/sprites/structure
    css-sprite ~/sprites/structure -s
    css-sprite ~/sprites/structure -o=teste.png
    css-sprite ~/sprites/structure -s | pbcopy (to copy to clipboard)

## Roadmap

  1. Create an installer;
  2. Create an option to add new files automatically to `sprite.config` files instead of doing this manually;
  3. Improve the CSS output;
  4. Optimize the output png;
  5. Create a grunt.js plugin;

## Log History

### 0.1.1
  * Fixed the upload verifier when a file was not found (feedbacking it to user also);
  * Fixed the sprite.config replacer bug;
  * Created better comments on the code;
  * Added more relevant feedback to the user, as "finished with warnings" message;
