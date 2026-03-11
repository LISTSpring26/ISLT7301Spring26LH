# Remove Wordpress and Reinstall an older version
### Step 1: Remove Previous install/database/user

log into MySQL as root
    
    sudo mysql -u root
    
delete wordpress user
    
    DROP USER 'wordpress'@'localhost';
    
Delete wordpress database
    
    DROP DATABASE wordpress;

Confirm Database drop

    show databases;

Exit MYSQL

    \q

Change to /var/www/html directory

    cd /var/www/html

Rename library directory (Wordpress directory) to save as backup

    sudo mv library library_backup
  
### Step 2: Re-do applicable steps from Burns

re-install PHP modules
    
    sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl
    
In your browser, go to the [WordPress Release Archive](https://wordpress.org/download/releases/) and find which release you would like to use. Copy the link to the zip download.

Download the desired version of WordPress using the wget command and the URL you just copied from the release archive

    sudo wget (Link to zip file)

Unzip the package (the zip file's name will be the part of the copied URL after the last "/", i.e. "wordpress-6.5.4.zip")

    sudo unzip (file name)

check for wordpress directory

    ls -a
  
confirm presence of wordpress directory
 
Rename wordpress directory (If desired)
  
    sudo mv (current directory name) library
  
Follow Step 3 onward exactly from [Burns](https://cseanburns.github.io/systems-librarianship/6a-install-wordpress.html)

