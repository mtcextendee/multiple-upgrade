# upgrade.php for  Mautic Multiple Bundle 

Upgrade script for multi tenant Mautic https://mtcextendee.com/multiple/

### Installation

1, Download multiple-upgrade.php to root of your mautic
2, Run multiple-upgrade.php script
3. Removemultiple-upgrade.php

- `rm multiple-upgrade.php;wget https://raw.githubusercontent.com/mtcextendee/multiple-upgrade/master/multiple-upgrade.php;`
- `php multiple-upgrade.php;`
- `rm multiple-upgrade.php;`

### Processing

The process is the same like with Mautic upgrade.php file.
This script just upgrade all multi tenant version

### Errors

#### Permission error

This error happend mostly If you have issue with permission.

![image](https://user-images.githubusercontent.com/462477/62820506-64dff280-bb65-11e9-870a-a7a0885145aa.png)

Just log as root to your server and set permission to all directories and files something like

`sudo chown -R web-data:web-data /path/to/mautic/`

#### Error 500

Try clear cache from root directory for all instances:

`rm -r app/cache*/prod/`

### Validation

After upgrade you can validate your update with basis steps

- Login to your Mautic 
- Try send e-mail from Configuration
- Try check database schema for all instances: `php app/console mautic:multiple:run --command="doctrine:schema:update --dump-sql"`
  - If you see some DB schema queries apply it for all instances `php app/console mautic:multiple:run --command="doctrine:schema:update --dump-sql"`
  
### More
  
- https://mtcextendee.com/knowledge-base/multiple-command/
- https://johnlinhart.com/blog/uh-oh-mautic-upgrade-was-not-successful
