## 🚨 🚧 This page has been moved 🚧 🚨

Go to https://wiki.hackeriet.no/infra:hackerpass

pass is the secret sharing infra we use at hackeriet. It's low effort, and every write becomes a commit. Since _hackerpass_ is on a [private repo](https://github.com/hackeriet/pass/), the README.md file from that repo is pasted below so others can benefit from the docs.

The name _hackerpass_ is something someone chose at one time to separate from _pass_. Feel free to name your own non-hackeriet shared pass repo _pinkfluffyunicornpass_ or something to avoid confusion. :unicorn: 

***


# Getting started

You'll need a GPG key for this. Send your public key to someone who already has access to follow "Adding a new user" below. You also need to be a member of hackeriet org in github for this next part to succeed. 

First install [pass](https://www.passwordstore.org), then clone this repository into ~/.hackeriet_pass:

```
git clone git@github.com:hackeriet/pass.git ~/.hackeriet_pass
```

Then add the following alias to your .bashrc:

```
alias hackerpass='PASSWORD_STORE_DIR="$HOME/.hackeriet_pass" pass'
```

Or the following alias to your .config/fish/config.fish:

```
alias hackerpass='env PASSWORD_STORE_DIR="$HOME/.hackeriet_pass" pass'
```

And import the gpg keys:
```
for i in $(<.hackeriet_pass/.gpg-id) ; do gpg --recv $i ; done
```

To update the password database from this repo type:

```
hackerpass git pull
```

# Adding a password

Beware this repository leaks file name information to everyone with access to the repo. Generally use the FQDN as a file name unless it reveals something it should not. 

```
hackerpass generate that-place-i-put-that-thing-one-time.com 28
```

Then remember to push the new password:

```
hackerpass git push
```

# Adding a new user

After you have the new users' PGP key in your keyring, reencrypt the whole repository adding the new key:

```
hackerpass init $(<~/.hackeriet_pass/.gpg-id) <PGP key signature>
```

And then push it:

```
hackerpass git push
```

If you get the error message 
```
gpg: <PGP key signature>: There is no assurance this key belongs to the named user
gpg: [stdin]: encryption failed: Unusable public key
```

then do:

```
gpg --lsign-key <PGP key signature>
```

or if you don't have your certification key available, you can set the tofu policy for the keys:

```
gpg --tofu-policy good $(cat .hackeriet_pass/.gpg_id) 
```

