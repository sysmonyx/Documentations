# Procedure to generate new SSH Keys using the SSH Agent.

New SSH Keys can be generated using the SSH Agent.

## 1. Procedure for Windows

1. Open a PowerShell Windows.
2. Enter the following command. Replace with your own email or you can use USERNAME@DEVICE-HOSTNAME as well.

    `ssh-keygen -t ed25519 -C "your_email@example.com"`

3. The above command generates a `ed25519` key. You can also use `rsa` as well if you are on a legacy system that does not support `ed25519`. To generate a key-pair using `rsa` enter the following command.

    `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

4. This creates a new SSH key, using the provided email as a label.
5. You should get an ouput saying

    `> Generating public/private ALGORITHM key pair.`

6. When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ALGORITHM with your custom key name.

    `> Enter file in which to save the key (/c/Users/YOU/.ssh/id_ALGORITHM):[Press enter]`

7. At the prompt, type a secure passphrase or leave it blank if you don't want to use a passphrase with your key.

    ```
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```

8. The new key should be automatically added to the SSH Agent. But in case it doesn't, you can manually add the key with the following command. Replace `id_ed25519` with the name of your key.

    `ssh-add c:/Users/YOU/.ssh/id_ed25519`

**Your new keys can be found in the `.ssh` directory at ```C:\Users\USER_NAME\.ssh``` or the location you specified.**

## 2. Procedure for Linux

1. Open Terminal.
2. Enter the following command. Replace with your own email or you can use USERNAME@DEVICE-HOSTNAME as well.

    `ssh-keygen -t ed25519 -C "your_email@example.com"`

3. The above command generates a `ed25519` key. You can also use `rsa` as well if you are on a legacy system that does not support `ed25519`. To generate a key-pair using `rsa` enter the following command.

    `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

4. This creates a new SSH key, using the provided email as a label.
5. You should get an ouput saying

    `> Generating public/private ALGORITHM key pair.`

6. When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ALGORITHM with your custom key name.

    `> Enter file in which to save the key (/c/Users/YOU/.ssh/id_ALGORITHM):[Press enter]`

7. At the prompt, type a secure passphrase or leave it blank if you don't want to use a passphrase with your key.

    ```
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```

8. The new key should be automatically added to the SSH Agent. But in case it doesn't, you can manually add the key with the following command. Replace `id_ed25519` with the name of your key.

    `ssh-add c:/Users/YOU/.ssh/id_ed25519`

**Your new keys can be found in the `.ssh` directory at ```~/.ssh/``` or the location you specified.**
