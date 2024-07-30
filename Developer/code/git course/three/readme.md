this is the installation instructions for ssh key

Open Terminal.

copy and paste 

ssh-keygen -t ed25519 -C "your_email@example.com"



> Generating public/private ALGORITHM key pair.

> Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM): [Press enter]

> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]

Start the ssh-agent in the background.

$ eval "$(ssh-agent -s)"
> Agent pid 59566

First, check to see if your ~/.ssh/config file exists in the default location.

$ open ~/.ssh/config
> The file /Users/YOU/.ssh/config does not exist.
If the file doesn't exist, create the file.

touch ~/.ssh/config


Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
  
Add your SSH private key to the ssh-agent and store your passphrase in the keychain
ssh-add --apple-use-keychain ~/.ssh/id_ed25519