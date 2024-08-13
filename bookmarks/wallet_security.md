#### Points to remember:
- Always verify checksum and signatures of hw/sw wallet firmware/software and any additional sw authenticity verification available specific to the software 
    - a checksum verifies that the binary hasn't been modified, whereas GPG signature verifies the attestation done by others that the binary indeed has been compiled from the claimed source-code
    - ref: [Verifying open source sw](https://freedom.press/training/verifying-open-source-software/)
    - example: follow the ["verify download"](https://bitcoincore.org/en/download/) section of Bitcoin-Core
    - example commands assuming you've the sha256sums(fingerprints), sha256sums.asc(signatures) and public gpg keys for importing to your keyring (`gpg --import keys/*`):
        ```
            sha256sum --check SHA256SUMS --ignore-missing
            gpg --verify SHA256SUMS.asc
        ```

- Always have a **complete** backup ([BIP39](https://en.bitcoin.it/wiki/BIP_0039) scheme):
    - single-sig: seed-words, derivation path
    - multi-sig: seed-words, derviation paths and **ALL** of the xpubs
    - corresponding passphrases (if used)

- Test your backup atleast once by recovering it from scratch before committing all of the intended funds

- Air-gap/PSBT or atleast use clean devices with operating system free of any malicious software or SSH/remote access

- Verify the outputs for amounts and addresses before broadcasting every tx (on hw wallet screens and broadcasting software in case of a PSBT)

- RNG(random number generation) is critical for seed/private-key generation as elliptic-curve-cryptography is dependent on RNGs, adding a high entropy passphrase and/or generating one **accurately** with physical dices has some advatanges in that regard.


---
#### Notes:
- Seedsigner and Krux(and Jade) are DIY projects, both use [embit](https://embit.rocks/#/) library
- Seedsigner uses raspberry pi, it's firmware can't be flashed, only OS can be flashed
- Krux uses risc-v Kendryte K210 hardware, firmware can be flashed but not a popular all purpose hw
- Only Bitbox and Jade implement anti-exfil
- Jade air-gapped, [setup](https://help.blockstream.com/hc/en-us/articles/20272658303385-Air-gapped-Jade-Setup), [transact](https://help.blockstream.com/hc/en-us/articles/20347921365785-Send-air-gapped-bitcoin-transactions-with-Jade)
- As of Aug 2024, PSBT protocol doesn't have anti-exfil implemented/standardized
- HW devices like Coldcard and Trezor use RFC6979/deterministic nonces instead but not easily verifiable by users
- Verifying deterministic nonces is not practical:
    - Requires to use a seed on an external setup to compare nonces, 
    - Malicious software could program theft to happen on n-th transaction instead of first 10/20
    - Hence verifying after not just every firmware upgrade but also every tx makes it impractical mitigation
- More exfiltration risks: https://x.com/n1ckler/status/1821114168910512173


---

#### Additional references:

- [BIP39 not in Bitcoin Core](https://bitcoin.stackexchange.com/questions/88237/is-there-a-reason-to-why-bitcoin-core-does-not-implement-bip39)
- [Overview of anti-covert-channel signing, Wuille](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2020-March/017667.html)
- [Anti-exfil, Andrew Poelstra](https://blog.blockstream.com/anti-exfil-stopping-key-exfiltration/)
- [Anti-exfil/klepto, Bitbox](https://bitbox.swiss/blog/anti-klepto-explained-protection-against-leaking-private-keys/)

