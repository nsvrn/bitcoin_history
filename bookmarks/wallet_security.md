- [BIP39 not in Bitcoin Core](https://bitcoin.stackexchange.com/questions/88237/is-there-a-reason-to-why-bitcoin-core-does-not-implement-bip39)
- [Overview of anti-covert-channel signing, Wuille](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2020-March/017667.html)
- [Anti-exfil, Andrew Poelstra](https://blog.blockstream.com/anti-exfil-stopping-key-exfiltration/)
- [Anti-exfil/klepto, Bitbox](https://bitbox.swiss/blog/anti-klepto-explained-protection-against-leaking-private-keys/)



---
#### Notes:
- Seedsigner and Krux(and Jade) are DIY projects, both use [embit](https://embit.rocks/#/) library
- Seedsigner uses raspberry pi, it's firmware can't be flashed, only OS can be flashed
- Krux uses risc-v Kendryte K210 hardware, firmware can be flashed but not a popular all purpose hw
- Only Bitbox and Jade implement anti-exfil
- Jade air-gapped, [setup](https://help.blockstream.com/hc/en-us/articles/20272658303385-Air-gapped-Jade-Setup), [transact](https://help.blockstream.com/hc/en-us/articles/20347921365785-Send-air-gapped-bitcoin-transactions-with-Jade)
- As of Aug 2024, PSBT protocol doesn't have anti-exfil implemented/standardized
- HW devices like Coldcard and Trezor use RFC6979/deterministic nonces instead but not easily verifiable by users
- More exfiltration risks: https://x.com/n1ckler/status/1821114168910512173