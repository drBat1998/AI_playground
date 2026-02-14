Title: Connect to a VM using SSH from an OpenSSH client, do the following
Author: [[]]
Tags: #


# Notes
Connect to a VM using SSH from an OpenSSH client, do the following:
1. Add an SSH key to the VM if you haven't already.
2. In the Google Cloud console, go to the VM Instances page and find the external IP address of the VM that you want to connect to.
3. Open a terminal on your workstation.
4. Connect to the VM by running the following command:
```bash
ssh -i PATH_TO_PRIVATE_KEY USERNAME@EXTERNAL_IP
```
Replace the following:
	PATH_TO_PRIVATE_KEY: the path to the private SSH key file that corresponds to the public key you added to the VM.
	USERNAME: your username. If you manage your SSH keys in metadata, the username is what you specified when you created the SSH key. For OS Login accounts, the username is defined in your Google profile. For example, cloudysanfrancisco_example_com or cloudysanfrancisco.
	EXTERNAL_IP: the external IP address of the VM.

# Links