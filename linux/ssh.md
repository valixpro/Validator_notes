# SSH Setup and Useful Commands

## 1. Generate a new SSH key pair
```bash
ssh-keygen -t rsa
```

## 2. Create the .ssh directory for the user
```bash
mkdir /home/admin/.ssh
```

## 3. Add your public key to authorized_keys
```bash
nano /home/admin/.ssh/authorized_keys
```

## 4. Fix permissions for .ssh directory
```bash
sudo chown admin:admin /home/admin/.ssh
```

## 5. Fix permissions for authorized_keys
```bash
sudo chown admin:admin /home/admin/.ssh/authorized_keys
```

## 6. Allow admin to use sudo without password (optional)
```bash
echo "admin ALL=(ALL) NOPASSWD:ALL" | sudo tee -a /etc/sudoers
```

## 7. Harden SSH security
```bash
sudo sed -i 's|^PermitRootLogin .*|PermitRootLogin no|' /etc/ssh/sshd_config
sudo sed -i 's|^#PasswordAuthentication .*|PasswordAuthentication no|' /etc/ssh/sshd_config
sudo sed -i 's|^PubkeyAuthentication .*|PubkeyAuthentication yes|' /etc/ssh/sshd_config
```

## 8. Restart SSH service
```bash
sudo systemctl restart sshd
```

## 9. Show your public key
```bash
cat ~/.ssh/id_rsa.pub
```

## 10. NEVER share your private key
```bash
cat ~/.ssh/id_rsa
```
