# css-sprite v0.1

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

### Known bugs

  1. As the replace happens line-by-line on `sprite.config`, be carefull with
     the file names. On the example above, the order should
     be changed to avoid wrong replacement:

         file-name=.test
         file-name2=.second-test
         file-name3=a:hover

     the output css will be wrongly replaced:

         .test { background-position ...
         .test2 { background-position ...
         .test3 { background-position ...
     
     Changing the order will fix the behaviour:

         file-name3=a:hover
         file-name2=.second-test
         file-name=.test

## Roadmap

  1. Create an installer;
  2. Fix the sprite.config replacer bug;
  3. Create an option to add new files automatically to `sprite.config` files instead of doing this manually;
  4. Improve the CSS output (create a way to define the url or css extra rules for the classes);
  5. Optimize the output png;
  6. Create a grunt.js plugin;