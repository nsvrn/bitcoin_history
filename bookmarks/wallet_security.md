#### Points to remember:
- Always have a **complete** backup (derivation paths not applicable to BIP32):
    - single-sig: seed-words, derivation path
    - multi-sig: seed-words, derviation paths and ALL of the xpubs
    - corresponding passphrases (if used)

- Test your backup atleast once by recovering it from scratch

- Always verify checksum and signatures of hw/sw wallet firmware/software and any additional sw authenticity verification available specific to the software

- Air-gap/PSBT or use clean devices with operating system free of any malicious software

- Verify the outputs for amounts and addresses before broadcasting every tx (on hw wallet screens and broadcasting software in case of a PSBT)


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

