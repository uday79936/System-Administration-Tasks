## USER MANAGEMENT CONFIGURATION:

## EC2 Instance Setup, SSH Access, User Management, and Configuration:

## Step 1: Launch EC2 Instance:


Go to AWS Management Console.

Navigate to EC2 Dashboard → Launch Instance.

Select the desired Amazon Machine Image (AMI), e.g., Ubuntu Server.

Choose instance type (e.g., t2.micro).

Configure instance details, add storage, and configure security group (allow SSH port 22).

Launch the instance and download the .pem key pair.

## Step 2: Connect to EC2 Instance via SSH:
```
ssh -i /path/to/key.pem ubuntu@<EC2_Public_IP>
```

## Step 3: Update the System:

sudo apt update -y

## Step 4: Create a New User:
```
sudo useradd uday
```

## Step 5: Set Password for New User:
```
sudo passwd uday
```
# Enter the desired password when prompted:


## Step 6: Change Ownership and Permissions:
```
sudo chown uday:uday /home/uday/
```

## Step 7: Edit Sudoers File for User Permissions:
```
sudo visudo
```
# Add the following line at the end:
```
uday ALL=(ALL) NOPASSWD:ALL
```
# Save and exit (:wq)

## Step 8: Configure SSH Password Authentication:


# Open the main SSH configuration file:
```
sudo vi /etc/ssh/sshd_config
```


## Set the following parameter:
```
PasswordAuthentication yes
```

Save and exit (:wq).

## Edit cloud-init configuration file (specific to Ubuntu cloud images):
```
sudo vi /etc/cloud/cloud.cfg.d/60-cloud-init-settings.cfg
```

## Ensure the following line exists or is set:

ssh_pwauth: true


Save and exit (:wq).

## Step 9: Restart SSH Service:
```
sudo systemctl restart ssh
sudo systemctl restart ssh.service
```

## Step 10: Test SSH Login with New User:
```
sudo -u uday ssh localhost
```
# Enter password when prompted

## Step 11: Deleting the User:
```
sudo userdel -r uday
```

## Images:


## Author:

**Uday Sairam Kommineni**

**Linux System administrater**

**Mail Id:** saikommineni5@gmail.com

**Linkedin-URL:**  https://www.linkedin.com/in/uday-sai-ram-kommineni-uday-sai-ram/