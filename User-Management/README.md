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
## Change the shell:
```
sudo chsh -s /bin/bash uday
```
# Enter password when prompted

## Step 11: Deleting the User:
```
sudo userdel -r uday
```

## Images:

## Step-1: EC2 Instance:

<img width="1915" height="962" alt="Image" src="https://github.com/user-attachments/assets/561de4fe-1b1a-40a5-a15e-38a5d82f67b0" />

## Step-2: User and Password:

<img width="837" height="225" alt="Image" src="https://github.com/user-attachments/assets/555b1bcd-de38-4f21-a9e8-de9d84d6565c" />

## Step-3: Folder Creation:

<img width="855" height="220" alt="Image" src="https://github.com/user-attachments/assets/324cdf42-7a19-4166-82a9-5ab89fd0208c" />

## Step-4: Permissions:

<img width="742" height="292" alt="Image" src="https://github.com/user-attachments/assets/1c7500cc-c073-4e91-b979-3ef643c1f408" />

## Step-5: Change Own Permissions:

<img width="788" height="378" alt="Image" src="https://github.com/user-attachments/assets/6416500b-e85f-4983-905d-96f791404f53" />

## Step-6: Sudo visudo file permissions:

<img width="1912" height="1015" alt="Image" src="https://github.com/user-attachments/assets/6d956133-955c-4c18-ba60-d9561a7e9bbd" />

## Step-7: ssh config:

<img width="1112" height="1006" alt="Image" src="https://github.com/user-attachments/assets/74a58a6b-10fb-44ba-92cf-39ace8cb6736" />

## Step-8: ssh config.d:

<img width="897" height="295" alt="Image" src="https://github.com/user-attachments/assets/7289d206-c092-4117-8068-b31ae3263314" />

## Step-9: 60 cloudimage settings conf:

<img width="552" height="347" alt="Image" src="https://github.com/user-attachments/assets/b996424e-cfe0-46b3-890a-492b270a0970" />

## Step-10: User Management Output:

<img width="1257" height="1007" alt="Image" src="https://github.com/user-attachments/assets/7367c8ed-dd48-4acb-ad18-078dfa776482" />



## Author:

**Uday Sairam Kommineni**

**Linux System administrator**

**Mail Id:** saikommineni5@gmail.com

**Linkedin-URL:**  https://www.linkedin.com/in/uday-sai-ram-kommineni-uday-sai-ram/
