Title: ssh key
tags: #atomic_note #google_cloud #git


# Notes
1. Generate SSH key locally on Mac or Linux - ssh-keygen -t rsa -b 4096 -f ~/.ssh/mac -C "log"
2.  cd /Users/name_user/.ssh
3. copy the content of key.pub
4. add to SSH key in GitHub or instance metadata
5. to enter an instance use `ssh -i private_key username@ip_adres`



# Links
[[Git and GitHub for Beginners]]
https://youtu.be/elXJCyBSHUk?si=dV9_SdtdbJKefWWh