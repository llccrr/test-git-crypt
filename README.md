# MacOS
```
brew install git-crypt
brew install gpg
```

# Linux
```
apt-get install -y git-crypt
sudo apt-get install gnupg
```

# Initialize a repo
```
git init
git-crypt init
```

# Defining files to encrypt
In the directory with the sensitive data, add a `.gitattributes` file and define which files should be encrypted. In our case, this will be `secrets.txt`:
`secrets.txt filter=git-crypt diff=git-crypt`

A good practice is to add a line to prevent encrypting the .gitattributes file itself:
```.gitattributes !filter !diff```

# Testing encryption
```git-crypt status -e```

# Exporting the gpg key
```git-crypt export-key path/where/key/should/be/saved```

The exported key should be passed to your team members in a secure way. They can now decrypt the repository by running:
```git-crypt unlock path/to/key```
