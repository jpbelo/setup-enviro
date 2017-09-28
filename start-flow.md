1. new folder ``localhost`` on the Desktop
2. setup fork for gitlab
  1. on Fork, gitlab section - log in...
  2. (on gitlab.com) settings -> access tokens - create a personal access token
  3. paste the access token on fork
  4. terminal - ``ssh-keygen -t rsa -C "your.email@example.com" -b 4096`` to generate a SSH key
  5. terminal - ``pbcopy < ~/.ssh/id_rsa.pub`` to put the key in the clipboard (if using fork, don't need to copy, next step will make it unnecessary)
  6. on Fork, gitlab section, SSH keys tab, Add SSH keys (it should have already selected the public key)
3. fork -> clone gitlab repos into the ``localhost`` folder



