---
title: 既存の SSH キーの確認
intro: SSH キーを生成する前に、SSH キーがすでに存在するかどうかを確認できます。
redirect_from:
  - /articles/checking-for-existing-ssh-keys
  - /github/authenticating-to-github/checking-for-existing-ssh-keys
  - /github/authenticating-to-github/connecting-to-github-with-ssh/checking-for-existing-ssh-keys
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - SSH
shortTitle: Check for existing SSH key
---

## About SSH keys

You can use SSH to perform Git operations in repositories on {% ifversion fpt or ghec or ghes %}{% data variables.product.product_location %}{% elsif ghae %}{% data variables.product.product_name %}{% endif %}. 詳しい情報については「[SSHについて](/authentication/connecting-to-github-with-ssh/about-ssh)」を参照してください。

If you have an existing SSH key, you can use the key to authenticate Git operations over SSH.

## 既存の SSH キーの確認

Before you generate a new SSH key, you should check your local machine for existing keys.

{% data reusables.ssh.key-type-support %}

{% data reusables.command_line.open_the_multi_os_terminal %}
2. 既存の SSH キーが存在するかを確認するため、以下のように `ls -al ~/.ssh` と入力します.

  ```shell
  $ ls -al ~/.ssh
  # .ssh ディレクトリ内のファイルを一覧表示する（存在する場合）
  ```

3. ディレクトリの一覧から、公開 SSH キーをすでに持っているか確認します。 By default, the {% ifversion ghae %}filename of a supported public key for {% data variables.product.product_name %} is *id_rsa.pub*.{% else %}filenames of supported public keys for {% data variables.product.product_name %} are one of the following.
    - *id_rsa.pub*
    - *id_ecdsa.pub*
    - *id_ed25519.pub*{% endif %}

  {% tip %}

  **Tip**: If you receive an error that *~/.ssh* doesn't exist, you do not have an existing SSH key pair in the default location. You can create a new SSH key pair in the next step.

  {% endtip %}

4. Either generate a new SSH key or upload an existing key.
    - If you don't have a supported public and private key pair, or don't wish to use any that are available, generate a new SSH key.
    - If you see an existing public and private key pair listed (for example, *id_rsa.pub* and *id_rsa*) that you would like to use to connect to {% data variables.product.product_name %}, you can add the key to the ssh-agent.

      For more information about generation of a new SSH key or addition of an existing key to the ssh-agent, see "[Generating a new SSH key and adding it to the ssh-agent](/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)."
