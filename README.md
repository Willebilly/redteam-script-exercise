# redteam-script-exercise
A .sh script that will change the time to 1 year in the future, (wanted it to be something extreme like 100 years but I couldn't figure that one out), logg system and user info and then create a new file that, when run, will revert the changes made and remove itself and the original .sh file


Before running this. It is recommended to run in it in a controlled environment and to, (if possible), save a snapshot of your virtual linux machine BEFORE running redteam.sh

# Download redteam.sh
curl -L https://raw.githubusercontent.com/WilleBilly/redteam-script-exercise/main/redteam.sh -o redteam.sh

# Make it executable
chmod +x redteam.sh

# Quick time check first for reference
timedatectl status

# Run the script
sudo bash redteam.sh

# Check to see that everything worked like it should: 
date
timedatectl show -p NTP --value
ls -l /etc/not_a_virus.sh
sudo ls -l /var/lib/redteam-lab/
sudo bash -n /etc/not_a_virus.sh
stat -c '%A %a %U:%G %n' /etc/not_a_virus.sh

# To undo everything and remove the files run:
sudo bash /etc/not_a_virus.sh

# Check to see that everything returned to as it should be
date
timedatectl show -p NTP --value
