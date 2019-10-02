I got a YubiKey and I wanted to, you know, use the one key for everything. Save me the trouble of making all my keys be everywhere, making new keys all the time, etc. The problem being: how do you get a GPG key to fill in for an SSH key, since the two keys are... you know, totally different.

Here's how I made it work for my Mac laptop.

## The Big Picture

The way to make this work is:

1. Get your key on the Mac
2. replace {{ssh-agent}} with {{gpg-agent}}
3. Get the key to all the other machines you use 

h2. Get Your Key on the Mac

1. `brew install gpg-tools pinentry-mac` and then use GPG tools to do the needful.
1. Once your key is on the Mac, you'll need the ID. Get it by running {{gpg --list-keys}} to get the top-level ID of your key, which is probably a number starting with {{0x}} and which says "Key fingerprint" below it. You don't need the encryption method before the {{0x}} number.

h2. Replace SSH-Agent with GPG-agent

# Make the contents of `~/.gnupg/gpg.conf` like this:
```
# https://github.com/drduh/config/blob/master/gpg.conf
# https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration-Options.html
# https://www.gnupg.org/documentation/manuals/gnupg/GPG-Esoteric-Options.html
# Use AES256, 192, or 128 as cipher
personal-cipher-preferences AES256 AES192 AES
# Use SHA512, 384, or 256 as digest
personal-digest-preferences SHA512 SHA384 SHA256
# Use ZLIB, BZIP2, ZIP, or no compression
personal-compress-preferences ZLIB BZIP2 ZIP Uncompressed
# Default preferences for new keys
default-preference-list SHA512 SHA384 SHA256 AES256 AES192 AES ZLIB BZIP2 ZIP Uncompressed
# SHA512 as digest to sign keys
cert-digest-algo SHA512
# SHA512 as digest for symmetric ops
s2k-digest-algo SHA512
# AES256 as cipher for symmetric ops
s2k-cipher-algo AES256
# UTF-8 support for compatibility
charset utf-8
# Show Unix timestamps
fixed-list-mode
# No comments in signature
no-comments
# No version in signature
no-emit-version
# Long hexidecimal key format
keyid-format 0xlong
# Display UID validity
list-options show-uid-validity
verify-options show-uid-validity
# Display all keys and their fingerprints
with-fingerprint
# Display key origins and updates
#with-key-origin
# Cross-certify subkeys are present and valid
require-cross-certification
# Disable caching of passphrase for symmetrical ops
no-symkey-cache
# Disable putting recipient key IDs into messages
throw-keyids
# Enable smartcard
use-agent
default-key <key ID here>
{code}
# Make the contents of {{~/.gnupg/gpg-agent.conf}} like this:
{code:lang=shell}
enable-ssh-support
default-cache-ttl 60
max-cache-ttl 120
write-env-file $HOME/.gnupg/gpg-agent-info
pinentry-program /usr/local/bin/pinentry-mac
log-file $HOME/.gnupg/gpg-agent.log
{code}
# Point to the key you want to use for ssh by running {{ssh-add -L > ~/.gnupg/sshcontrol}}
# Add this to your bashrc:
{code:lang=shell}
unset SSH_AGENT_PID
export GPG_TTY="$(tty)"
if [ "${gnupg_SSH_AUTH_SOCK_by:-0}" -ne $$ ]; then
  export SSH_AUTH_SOCK="$(gpgconf --list-dirs agent-ssh-socket)"
fi
gpgconf --launch gpg-agent
```

## Get the Key to All the Other Machines You Use

1. `brew install ssh-copy-id`
1. Now get yourself a key you can copy up by doing `ssh-add -L | grep "cardno" > ~/.ssh/id_rsa_yubikey.pub`
1. `ssh-copy-id -i ~/.ssh/id_rsa_yubikey.pub opal` (and repeat for every other place you want the key

## Use the key

Just ssh to the desired server, with the following caveats:

* You need to have your Yubikey in to unlock the PGP key
* If you see the password prompt, your Yubikey is not being seen by gpg-tools; try reinserting
* Still no luck: try `gpgconf --launch gpg-agent` and then ssh again
