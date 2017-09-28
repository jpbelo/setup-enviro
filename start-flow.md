1. new folder localhost on the Desktop

1. setup Fork for Gitlab
   1. on Fork, Gitlab section - log in...
   2. on gitlab.com, settings -> access tokens - create a personal access token
   3. paste the access token on fork
   4. on terminal, ssh-keygen -t rsa -C "your.email@example.com" -b 4096 to generate a SSH key
   5. pbcopy < ~/.ssh/id_rsa.pub to put the key in the clipboard (if using Fork, there's no need to copy, next step will make it unnecessary)
   6. on Fork, gitlab section, SSH keys tab, Add SSH keys (it should have already selected the public key)
2. on Fork, clone gitlab repos into the localhost folder
3. open codekit, and setup the settings for the new projects ( File > Edit Defaults For New Projects - cmd + D )
   1. Project settings
      1. browser refreshing - external server options, turn switch on and http://localhost in the address field
      2. build process, enable on
   2. languages
      1. javascript
         1. ESLint
         2. minify output with UglifyJS off
      2. CSS
         1. style compact




