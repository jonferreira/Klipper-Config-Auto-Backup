#install git if not already installed

sudo apt-get install git -y

#init git

cd ~/klipper_config/

git init

git config --global user.email "email"
git config --global user.name "name"

git remote add origin Your-GitHub-Repo-URL

git add .

git commit -m "my first backup"

git push -u origin master

#store credentials

git config --global credential.helper store

#create backup script

nano klipper_config_bk.cron

########## paste this ###############

git -C /home/pi/klipper_config/ add .

git -C /home/pi/klipper_config/ commit -m "auto backup"

git -C /home/pi/klipper_config/ push --force origin master

########## save and exit ############

crontab -e

########## paste this ###############

* * * * * /home/pi/klipper_config_bk.cron

########## save and exit ############
