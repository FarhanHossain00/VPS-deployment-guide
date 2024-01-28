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

Step 3: Add SSH Keys to SSH Agent
---------------------------------

    # Start the SSH agent
    eval "$(ssh-agent -s)"
    
    # Add SSH keys to the agent
    ssh-add ~/.ssh/directory_github
    ssh-add ~/.ssh/b2bdirectory_github
    

Step 4: Automate SSH Agent Setup
--------------------------------

### For Bash Users:

Open or create `~/.bashrc`:

    nano ~/.bashrc
    

Add the following lines at the end of the file:

    # Start the SSH agent (if not running)
    if [ ! -S "$SSH_AUTH_SOCK" ]; then
        eval "$(ssh-agent -s)"
    fi
    
    # Add SSH keys to the agent
    ssh-add -l | grep -q "directory_github" || ssh-add ~/.ssh/directory_github
    ssh-add -l | grep -q "b2bdirectory_github" || ssh-add ~/.ssh/b2bdirectory_github
    

Save and exit the editor. Restart your terminal or run:

    source ~/.bashrc
    

### For Zsh Users:

Open or create `~/.zshrc`:

    nano ~/.zshrc
    

Add the following lines at the end of the file:

    # Start the SSH agent (if not running)
    if [ ! -S "$SSH_AUTH_SOCK" ]; then
        eval "$(ssh-agent -s)"
    fi
    
    # Add SSH keys to the agent
    ssh-add -l | grep -q "directory_github" || ssh-add ~/.ssh/directory_github
    ssh-add -l | grep -q "b2bdirectory_github" || ssh-add ~/.ssh/b2bdirectory_github
    

Save and exit the editor. Restart your terminal or run:

    source ~/.zshrc
    

Now, your SSH keys are configured, and the SSH agent is set up to automatically handle them whenever you start a new terminal session.
