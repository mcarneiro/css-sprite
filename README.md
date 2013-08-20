# css-sprite v0.1.2

Create css sprites via bash using http://css.spritegen.com/

## Installation

I tested these scripts on a Mac and some on Git-bash.

Place the desired scripts on a folder (Ex.: `~/bin/`) and concatenate it to the PATH variable on yout ~/.bash_profile file:

    export PATH="${PATH}:~/bin"

Give executable permission on the folder:

    chmod -R +x ~/bin

## Usage

    css-sprite FOLDER_PATH [-s, -o=OUTPUT_PATH, -padding=2, -output-type=png, -jpeg-quality=75]
    css-sprite ?

`?` help page;    
`-s` silent mode. Only outputs the generated CSS on the stdout;    
`-o` output png file (optional). If nothing is passed, will use the folder name and output at the same directory;
`-padding`${B2}` space between images on the sprite. By default it's 2 and max-value is 25;
`-output-type`${B2}` image format. By default it's png, can be jpg, gif and png;
`-jpeg-quality`${B2}` image quality from 0 to 100. By default it's 75;


After the first run, a `sprite.config` file will be created with the file list. It is possible to create a simple replace rule so the generated CSS classes doesn't need to follow the filenames. The rule for this file is something like:

    file-name.png=.new-css-rule:hover, .in-one-line
    file-name2.png
    file-name3.png=a.css-rule:hover

When `sprite.config` exists, the script will ONLY use the listed files instead of listing through the folder.

### Examples

    css-sprite ~/sprites/structure
    css-sprite ~/sprites/structure -s
    css-sprite ~/sprites/structure -s -padding=4
    css-sprite ~/sprites/structure -o=teste.png
    css-sprite ~/sprites/structure -s | pbcopy (to copy to clipboard)

## Roadmap

  1. Create an installer;
  2. Create an option to add new files automatically to `sprite.config` files instead of doing this manually;
  3. Improve the CSS output;
  4. Create a grunt.js plugin;

## Log History

### 0.1.2 - 20/08/2013
  * Minor fix when creating sprite.config
  * Passing arguments (-padding, -output-type, -jpeg-quality) to spritegen api
  * Possibility to create output other then png
  * CSS output now write the correct file name
  * Added png compression (TinyPNG.org) on the output file

### 0.1.1 - 27/07/2012
  * Fixed the upload verifier when a file was not found (feedbacking it to user also);
  * Fixed the sprite.config replacer bug;
  * Created better comments on the code;
  * Added more relevant feedback to the user, as "finished with warnings" message;
