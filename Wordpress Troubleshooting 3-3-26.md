# Problem: Wordpress Link (<IP Address>/library) does not load on browsers 
## Strategy 1: reconfigure wp-config.php file at /var/www/html/library/wp-config.php by replacing it with wp-config-sample.php in the same directory
  Step 1: backup current wp-config.php file 
  
      sudo mv wp-config.php wp-config.php.bak
  
  Step 2: copy wp-config-sample.php to be the new wp-config.php 
  
      sudo cp wp-config-sample.php wp-config.php
  
  Step 3: Use Nano to edit the database and user information in the config file

      sudo nano wp-config.php
  
  Step 4: 
  
      sudo systemctl restart apache2 
  
  Step 5:
  
      sudo systemctl restart mysql
  
  *Result: New error at "<Ipaddress>/library" - "Error establishing a database connection"*


## Strategy 2: Complete Reinstall
### Step 1: Remove Previous install/database/user

log into MySQL as root
    
    Sudo mysql -u root
    
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
    
latest.zip (wordpress zip file) is still in html directory, so unzip it
  
    sudo unzip latest.zip

check for wordpress directory

    ls -a
  
confirm presence of wordpress directory
 
Rename wordpress directory
  
    sudo mv wordpress library
  
Follow Step 3 onward exactly from [Burns](https://cseanburns.github.io/systems-librarianship/6a-install-wordpress.html)
  
Result: Success, Wordpress Site loading on browsers again
