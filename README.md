# PhpStorm URL Handler

This package contains a launcher to open files in PhpStorm at the defined line
number and an associated desktop file that conforms to the Desktop Entry
Specification for use in Gnome and KDE desktop environments.

## Installation

The executable `phpstorm` or `pstorm` must be in your `$PATH`.
If it is not, either add the install location to your path

    export PATH="/path/to/phpstorm/bin/phpstorm.sh:$PATH"

or symlink it to one of `/usr/bin` or `/usr/local/bin` - which already should be in your `$PATH`.
Use `sudo` if needed

    ln -s /path/to/phpstorm/bin/phpstorm.sh /usr/bin/phpstorm

Then copy the actual handler to your `$PATH` and make it executable.
Use `sudo` if needed

    cp phpstorm-url-handler /usr/bin/phpstorm-url-handler
    chmod +x /usr/bin/phpstorm-url-handler

Install the `.desktop` file to register the mime-types.
Use `sudo` if needed

    desktop-file-install phpstorm-url-handler.desktop
    update-desktop-database

## Usage

It can be used to open files at the specified line from within the browser by 
placing a link of the following kind in the markup:

    <?php
    $file = "/path/to/filename.php";
    $line = 35;
    print "<a href='phpstorm://open?url=file://$file&line=$line'>Open with PhpStorm</a>";
    // Alternate Syntax to match PhpStorm 8 for the Macintosh
    print "<a href='phpstorm://open?file=$file&line=$line'>Open with PhpStorm</a>";
    ?>

Added in ability to path map to local files from docker/devilbox.

Edit phpstorm-url-handler file, find the following lines:

    find="/shared/httpd/"
    
    replace="/home/michael/public_html/";

change the content of the find variable with the path the files are located on docker/devilbox, and change the content of the replace variable with the path to the local files.

## Command-line usage

    FILE="/path/to/filename.php"
    LINE=35
    ./phpstorm-url-handler "phpstorm://open?url=file://${FILE}&line=${LINE}"


This alternative syntax matches the format used by
PhpStorm 8 for the Macintosh for cross-platform compatibility.

    FILE="/path/to/filename.php"
    LINE=35
    ./phpstorm-url-handler "phpstorm://open?file=${FILE}&line=${LINE}"

This script is used in the ARCH linux package to be found at  
phpstorm-url-handler https://aur.archlinux.org/packages/phpstorm-url-handler/

## License

GNU GENERAL PUBLIC LICENSE
