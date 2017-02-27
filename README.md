# PhpStorm URL Handler

This package contains a launcher to open files in PhpStorm at the defined line
number and an associated desktop file that conforms to the Desktop Entry
Specification for use in Gnome and KDE desktop environments.

## Installation

    cp phpstorm-url-handler /usr/bin/phpstorm-url-handler
    desktop-file-install phpstorm-url-handler.desktop

## Usage

It can be used to open files at the specified line from within the browser by 
placing a link of the following kind in the markup:

    <?php
    $file = "/path/to/filename.php";
    $line = 35;
    print "<a href=\"phpstorm://open?url=file://$file&line=$line\">Open with PhpStorm</a>";
    // Alternate Syntax to match PhpStorm 8 for the Macintosh
    print "<a href=\"phpstorm://open?file=$file&line=$line\">Open with PhpStorm</a>";
    ?>

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
