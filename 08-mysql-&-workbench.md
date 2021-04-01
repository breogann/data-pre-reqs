#8. MySQL & workbench

MySQL and workbench often are difficult to install. If you didn't manage to connect MySQL to workbench, follow these steps:

##8.1. How to know if MySQL and Workbench don't work:

- Open MySQLWorkbench
- Click on the `+` button
- Create a connection

If you see something like:
[workbench_does_not_work]()

It's not working. So follow these steps ⬇️

### 1. Uninstall

1.0. Uninstall Workbench: locate MySQL Workbench in the Applications folder, right-click, and select Move to Trash.



1.1. Uninstall
```bash
brew remove mysql
brew cleanup
```

1.2. Unload previous MySQL Auto-Login
```bash
launchctl unload -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
```

1.3. Remove files: it'll ask for your admin password
```bash
sudo rm /usr/local/mysql
sudo rm -rf /usr/local/var/mysql
sudo rm -rf /usr/local/mysql*
sudo rm ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
sudo rm -rf /Library/StartupItems/MySQLCOM
sudo rm -rf /Library/PreferencePanes/My*
```

1.4. Remove previous configuration: it'll ask again for your admin password
```bash
rm -rf ~/Library/PreferencePanes/My*
sudo rm -rf /Library/Receipts/mysql*
sudo rm -rf /Library/Receipts/MySQL*
sudo rm -rf /private/var/db/receipts/*mysql*
```

1.5. **Restart** your computer just to ensure any MySQL processes are killed

1.6. Try to run mysql, it shouldn't work.


### 2. Re-installing MySQL
```bash
brew install mysql #Install
mysql.server start #Start
sudo mysql -u root
USE mysql;
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'admin'; #Substitute 'admin' by your password
FLUSH PRIVILEGES;
QUIT;
```

### 3. Download & install workbench
It is important you download the version **8.0.20**, otherwise there might be conflicts.

https://downloads.mysql.com/archives/workbench/

It should all be set now! How do you know everything's okay? You should see:

[workbench_works]("imgs/workbench-works.png")

############################

_Refs: https://gist.github.com/vitorbritto/0555879fe4414d18569d_