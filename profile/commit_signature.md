# Commit Signature Verification

In order to verify the author of the code and ensure that we have a reliable user list (without any duplicated users), we are enforcing [commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification). If you are working through the web, this feature is enabled by default since it is a good practice.

There are multiple ways to enable this feature by default on our machines. Since [we already need an SSH key to push to repositories](https://docs.github.com/en/authentication/connecting-to-github-with-ssh), the easiest way is to use this key. If you don't have an SSH key, please generate one by following [this guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent). You also need to have your email properly configured.

The process of enabling commit signature verification using an SSH key is detailed in [the documentation](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key#telling-git-about-your-ssh-key). Here is a TL;DR version of the process:

1. Have your SSH key, or generate it (e.g., `ssh-keygen -q -N "" -f ~/.ssh/github-key-ssh -C "Keys generated for GitHub" -t ed25519`).
2. Set up your Git configuration by running the following commands in your terminal:

```sh
git config --global user.email "youremail@iberia.com"
git config --global user.name "Your Name"

git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/github-key-ssh.pub

git config --global commit.gpgsign true
```

3. Add the generated key as a sign key in [your GitHub settings](https://github.com/settings/keys) by following [these instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account#adding-a-new-ssh-key-to-your-account).
4. Check that my commits now show a 'Verified' mark.
