# Code Style Guide
Ideally you should write PHP code that adheres to a known standard. This could be any combination pf PSR's, or one of the coding standards made by PEAR or Zend.
This means other developers can easily read and work with your code, and applications that implement the components can have consistency even when working with lots of third-party code.

PRS-0, PRS-1, PSR-2, PSR-4 are related to code-style.

You can use [PHP_CodeSniffer](http://pear.php.net/package/PHP_CodeSniffer/) to check code against any one of these recommendations.

You can fix the code layout automatically by using one of the two following tools.
* [PHP Coding Standards Fixer](http://cs.sensiolabs.org/), which has a very well tested codebase.
    * Requirements  
    PHP needs to be a minimum version of PHP 5.3.6

    * Installation  
    Globally (manual)  
    ```
    curl http://get.sensiolabs.org/php-cs-fixer.phar -o php-cs-fixer
    ```  
    then  
    ```
    sudo chmod a+x php-cs-fixer
    sudo mv php-cs-fixer /usr/local/bin/php-cs-fixer
    ```  
    Globally (homebrew on mac os x)
    ```
    brew install homebrew/php/php-cs-fixer
    ```
    * Update  
    Globally (manual)
    ```
    php php-cs-fixer self-update
    ```
    Globally (homebrew)
    ```
    brew upgrade php-cs-fixer
    ```
    * Usage  
    The **fix** command tries to fix as much coding standards problems as possible on a given file or directory:
    ```
    php php-cs-fixer fix /path/to/dir
    php php-cs-fixer fix /path/to/file
    ```
    The **--verbose** option show applied fixers. When using **txt** format (default one) it will also displays progress notification.  
    The **--level** option limits the fixers to apply on the project:
    ```
    php php-cs-fixer fix /path/to/project --level=psr0
    php php-cs-fixer fix /path/to/project --level=psr1
    php php-cs-fixer fix /path/to/project --level=psr2
    php php-cs-fixer fix /path/to/project --level=symfony
    ```
    By default, all PSR-2 fixers and some additional ones are run. The "contrib level" fixers cannot be enabled via this option; you should instead set them manually by their name via the **--fixer** option.  
    The **--fixer** option lets you choose the exact fixers to apply(the fixer names must be separated by a comma):
    ```
    php php-cs-fixer fix /path/to/dir --fixers=linefeed,short_tag.indentation
    ```
    You can also blacklist the fixers you don't want by placing a dash in front of the fixer name, if this is more convenient,using **-name_of_fixer**:
    ```
    php php-cs-fixer fix /path/to/dir --fixers=-short_tag,-indentation
    ```

* [php.tools](https://github.com/phpfmt/php.tools), which is made popular by the sublime-phpfmt editor plugin.
