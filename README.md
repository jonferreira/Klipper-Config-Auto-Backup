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


######### update 2023 ###############

ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

Copy the contents of the to your SSH keys to your GitHub account settings (https://github.com/settings/keys).

Test the SSH key:

ssh -T git@github.com

Now try editing a file (try the README) and then do:

git add -A
git commit -am "Update README.md"
git push
Add the key to the ssh-agent

ssh-add ~/.ssh/id_rsa

# source https://gist.github.com/xirixiz/b6b0c6f4917ce17a90e00f9b60566278

#init

git clone git@github.com:jonferreira/BLV-Klipper config
