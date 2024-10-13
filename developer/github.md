# [Developer Guide](index.md)

## Github

### Configure commit email address

[Setting your commit email address on Github](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address#setting-your-commit-email-address-on-github)

[Setting your commit email address in Git](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address#setting-your-commit-email-address-in-git)

```
git config --global user.email "firstame.lastname@enine.school"
git config --global user.name "firstname lastname"
```

Confirm that you have set it correctly

```
git config --global user.email
```

Run the above commands in a git repo without the global to set a name and email address for the particular repo only.

### [Personal Access Tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

Classic
- [Creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic)
- [New personal access token (classic)](https://github.com/settings/tokens/new)

Fine-grained Token
- [Creating a fine-grained personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token)
- [New fine-grained personal access token](https://github.com/settings/personal-access-tokens/new)

Using
- [Using a personal access token on the command line](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#using-a-personal-access-token-on-the-command-line)
