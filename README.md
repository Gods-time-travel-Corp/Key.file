# Key.file
location:%20/home/linuxbrew%0ANote:%20Homebrew%20is%20pre-installed%20on%20image%20but%20not%20added%20to%20PATH.%0Arun%20the%20eval%20%22$(/home/linuxbrew/.linuxbrew/bin/brew%20shellenv)%22%20command%0Ato%20accomplish%20this.
<<<<gpg --full-generate-key>>
If you are not on version 2.1.17 or greater, the gpg --full-generate-key command doesn't work. Paste the text below and skip to step 6.

Shell
<<gpg --default-new-key-algo rsa4096 --gen-key>>

<<gpg --list-secret-keys --keyid-format=long>>
<<$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot <hubot@example.com>
ssb   4096R/4BB6D45482678BE3 2016-03-10
>>

<< gpg --armor --export 3AA5C34371567BD2
# Prints the GPG key ID, in ASCII armor format>>

<<<--gpg-sign, unset this configuration so the default format of openpgp will be used.

git config --global --unset gpg.format
Use the gpg --list-secret-keys --keyid-format=long command to list the long form of the GPG keys for which you have both a public and private key. A private key is required for signing commits or tags.

Shell
gpg --list-secret-keys --keyid-format=long
Note

Some GPG installations on Linux may require you to use gpg2 --list-keys --keyid-format LONG to view a list of your existing keys instead. In this case you will also need to configure Git to use gpg2 by running git config --global gpg.program gpg2.
From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:

Shell
$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot <hubot@example.com>
ssb   4096R/4BB6D45482678BE3 2016-03-10
To set your primary GPG signing key in Git, paste the text below, substituting in the GPG primary key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:

git config --global user.signingkey 3AA5C34371567BD2
Alternatively, you may want to use a subkey. In this example, the GPG subkey ID is 4BB6D45482678BE3:

git config --global user.signingkey 4BB6D45482678BE3
If you use multiple keys and subkeys, then you should append an exclamation mark ! to the key to tell git that this is your preferred key. Sometimes you may need to escape the exclamation mark with a back slash: \!.

Optionally, to configure Git to sign all commits and tags by default, enter the following command:

git config --global commit.gpgsign true
git config --global tag.gpgSign true
For more information, see [Signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits).

To add your GPG key to your .bashrc startup file, run the following command:

[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc>>>

<< git config --global gpg.format ssh
To set your SSH signing key in Git, paste the text below, substituting /PATH/TO/.SSH/KEY.PUB with the path to the public key you'd like to use.

git config --global user.signingkey /PATH/TO/.SSH/KEY.PUB>>

<< $ cat ~/.ssh/id_ed25519.pub
# Then select and copy the contents of the id_ed25519.pub file
# displayed in the terminal to your clipboard>>

<<<>>> from cryptography.hazmat.primitives import hashes
>>> from cryptography.hazmat.primitives.asymmetric import dh
>>> from cryptography.hazmat.primitives.kdf.hkdf import HKDF
>>> # Generate some parameters. These can be reused.
>>> parameters = dh.generate_parameters(generator=2, key_size=2048)
>>> # Generate a private key for use in the exchange.
>>> server_private_key = parameters.generate_private_key()
>>> # In a real handshake the peer is a remote client. For this
>>> # example we'll generate another local private key though. Note that in
>>> # a DH handshake both peers must agree on a common set of parameters.
>>> peer_private_key = parameters.generate_private_key()
>>> shared_key = server_private_key.exchange(peer_private_key.public_key())
>>> # Perform key derivation.
>>> derived_key = HKDF(
...     algorithm=hashes.SHA256(),
...     length=32,
...     salt=None,
...     info=b'handshake data',
... ).derive(shared_key)
>>> # And now we can demonstrate that the handshake performed in the
>>> # opposite direction gives the same final value
>>> same_shared_key = peer_private_key.exchange(
...     server_private_key.public_key()
... )
>>> same_derived_key = HKDF(
...     algorithm=hashes.SHA256(),
...     length=32,
...     salt=None,
...     info=b'handshake data',
... ).derive(same_shared_key)
>>> derived_key == same_derived_key
DHE (or EDH), the ephemeral form of this exchange, is strongly preferred over simple DH and provides [forward secrecy](https://en.wikipedia.org/wiki/Forward_secrecy) when used. You must generate a new private key using [generate_private_key()](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHParameters.generate_private_key) for each [exchange()](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHPrivateKey.exchange) when performing an DHE key exchange. An example of the ephemeral form:

>>> from cryptography.hazmat.primitives import hashes
>>> from cryptography.hazmat.primitives.asymmetric import dh
>>> from cryptography.hazmat.primitives.kdf.hkdf import HKDF
>>> # Generate some parameters. These can be reused.
>>> parameters = dh.generate_parameters(generator=2, key_size=2048)
>>> # Generate a private key for use in the exchange.
>>> private_key = parameters.generate_private_key()
>>> # In a real handshake the peer_public_key will be received from the
>>> # other party. For this example we'll generate another private key and
>>> # get a public key from that. Note that in a DH handshake both peers
>>> # must agree on a common set of parameters.
>>> peer_public_key = parameters.generate_private_key().public_key()
>>> shared_key = private_key.exchange(peer_public_key)
>>> # Perform key derivation.
>>> derived_key = HKDF(
...     algorithm=hashes.SHA256(),
...     length=32,
...     salt=None,
...     info=b'handshake data',
... ).derive(shared_key)
>>> # For the next handshake we MUST generate another private key, but
>>> # we can reuse the parameters.
>>> private_key_2 = parameters.generate_private_key()
>>> peer_public_key_2 = parameters.generate_private_key().public_key()
>>> shared_key_2 = private_key_2.exchange(peer_public_key_2)
>>> derived_key_2 = HKDF(
...     algorithm=hashes.SHA256(),
...     length=32,
...     salt=None,
...     info=b'handshake data',
... ).derive(shared_key_2)
To assemble a [DHParameters](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHParameters) and a [DHPublicKey](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHPublicKey) from primitive integers, you must first create the [DHParameterNumbers](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHParameterNumbers) and [DHPublicNumbers](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHPublicNumbers) objects. For example, if p, g, and y are [int](https://docs.python.org/3/library/functions.html#int) objects received from a peer:

pn = dh.DHParameterNumbers(p, g)
parameters = pn.parameters()
peer_public_numbers = dh.DHPublicNumbers(y, pn)
peer_public_key = peer_public_numbers.public_key()>>>
<<<# Key.file
location:%20/home/linuxbrew%0ANote:%20Homebrew%20is%20pre-installed%20on%20image%20but%20not%20added%20to%20PATH.%0Arun%20the%20eval%20%22$(/home/linuxbrew/.linuxbrew/bin/brew%20shellenv)%22%20command%0Ato%20accomplish%20this.

<<<Location: /home/linuxbrew
Note: Homebrew is pre-installed on image but not added to PATH.
run the eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" command
to accomplish this.>>
<<Both Xdebug and PCOV extensions are installed, but only Xdebug is enabled.>>
<<User: postgres
PostgreSQL service is disabled by default.
Use the following command as a part of your job to start the service: 'sudo systemctl start postgresql.service'>>
<<User: root
Password: root
MySQL service is disabled by default.
Use the following command as a part of your job to start the service: 'sudo systemctl start mysql.service'>>
<<name: Run commands on different operating systems
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  Run-npm-on-Ubuntu:
    name: Run npm on Ubuntu
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '14'
      - run: npm help

  Run-PSScriptAnalyzer-on-Windows:
    name: Run PSScriptAnalyzer on Windows
    runs-on: windows-latest
    steps:
      - uses: actions/checkout@v4
      - name: Install PSScriptAnalyzer module
        shell: pwsh
        run: |
          Set-PSRepository PSGallery -InstallationPolicy Trusted
          Install-Module PSScriptAnalyzer -ErrorAction Stop
      - name: Get list of rules
        shell: pwsh
        run: |
          Get-ScriptAnalyzerRule
>
><<name: Build on Ubuntu
on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository code
        uses: actions/checkout@v4
      - name: Install jq tool
        run: |
          sudo apt-get update
          sudo apt-get install jq
Note

Always run sudo apt-get update before installing a package. In case the apt index is stale, this command fetches and re-indexes any available packages, which helps prevent package installation failures.
Installing software on macOS runners

The following example demonstrates how to install Brew packages and casks as part of a job.

name: Build on macOS
on: push

jobs:
  build:
    runs-on: macos-latest
    steps:
      - name: Check out repository code
        uses: actions/checkout@v4
      - name: Install GitHub CLI
        run: |
          brew update
          brew install gh
      - name: Install Microsoft Edge
        run: |
          brew update
          brew install --cask microsoft-edge>>>>>>