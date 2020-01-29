# SSH Public Key Authentication Commands

## Summary
Here are various useful commands for working with SSH public keys.

## Steps
- Add or change encryption passphrase of a private key:
  - ssh-keygen -t rsa -b 4096
- Generate key: 
  - ssh-keygen -t ed25519 #generates a ~/.ssh/id_ed25519.pub
- Copy public key to server: 
  - ssh-copy-id -i ~/.ssh/id_ed25519.pub remoteuser@server.top.tld
-  On Windows, use Pageant or ssh-agent under WSL as your ssh-agent.
- On Linux/Mac, run these two commands:
  - ssh-agent   
  - ssh-add -t 8h   #keeps keys in memory for 8 hours
  - ssh-add -D  #clears all keys out of memory
- See fingerprint (for authorized_keys) for private key:
  - ssh-keygen -y -f ~/.ssh/id_ed25519  
  or
  - cat ~/.ssh/id_ed25519.pub
    




*** 
_Mandatory_page_footer: This article and the rest of the FreeKB is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._

