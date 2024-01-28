  SSH Key and Agent Setup Tutorial

SSH Key and Agent Setup Tutorial
================================

This tutorial guides you through the process of setting up and configuring SSH keys for multiple GitHub repositories, along with automating the SSH agent for a smoother workflow.

Step 1: Generate SSH Keys
-------------------------

    # Navigate to the SSH directory
    cd ~/.ssh
    
    # Generate SSH key for the 'directory' repository
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f directory_github
    
    # Generate SSH key for the 'b2bdirectory' repository
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f b2bdirectory_github
    

Replace "your\_email@example.com" with your actual email address.

Step 2: Create SSH Config File
------------------------------

    # Open the SSH config file
    nano ~/.ssh/config
    

    # Default GitHub account
    Host directory
      HostName github.com
      User git
      IdentityFile ~/.ssh/directory_github
      IdentitiesOnly yes
    
    # Second GitHub account
    Host b2bdirectory
      HostName github.com
      User git
      IdentityFile ~/.ssh/b2bdirectory_github
      IdentitiesOnly yes
    

Save and exit the editor.

Step 3: Add SSH Keys to SSH Agent using keychain
------------------------------------------------

    # Install keychain (if not installed)
    # For Debian/Ubuntu
    sudo apt-get install keychain
    
    # For Red Hat/Fedora
    sudo dnf install keychain
    

    # Start keychain to manage SSH agent and keys
    eval "$(keychain --quiet --eval --agents ssh)"
    keychain --clear id_rsa directory_github b2bdirectory_github
    

Step 4: Automate SSH Agent Setup
--------------------------------

### For Bash Users:

Open or create `~/.bashrc`:

    nano ~/.bashrc
    

Add the following line at the end of the file:

    # Start keychain to manage SSH agent and keys
    eval "$(keychain --quiet --eval --agents ssh)"
    

Save and exit the editor. Restart your terminal or run:

    source ~/.bashrc
    

### For Zsh Users:

Open or create `~/.zshrc`:

    nano ~/.zshrc
    

Add the following line at the end of the file:

    # Start keychain to manage SSH agent and keys
    eval "$(keychain --quiet --eval --agents ssh)"
    

Save and exit the editor. Restart your terminal or run:

    source ~/.zshrc
    

Now, your SSH keys are configured, and the SSH agent is set up using keychain to automatically handle them whenever you start a new terminal session.
