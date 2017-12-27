---
layout: post
title: "Blockchain Bonanza"
blog: dev
date: 2017-24-26
categories: blockchain fun
show: true
permalink: /devBlog/:title.html
---

# Blockchain is huge! #

Bitcoin has grown ridiculously fast, as has my regret at not buying bitcoin when it was less than a penny. That explosive growth has also carried with it a plethora of questions. The second question people ask when they find out I'm a Software Engineer is always: _"Explain bitcoin to me!"_. The first thing people do is request me to fix something.

Back to bitcoin though, I was out with a lovely friend of mine, and she asked me to explain bitcoin to her. I had absolutely no idea how to do that. I spent that next ten minutes talking out of my ass about linked lists, and eventually just owned it. She motivated me though. I spent my night after work the next day reading the white paper, and looking into what exactly Bitcoin is. Ultimately I ended up writing my own version of the blockchain.

Before I get to that though, I want to share the analogy that helped me understand how bitcoin works. So picture an old timey town. All of the town's financial transactions are recorded on a ledger in a vault. The people's personal transactions are then added to the town's ledger and verified by a witness and signatures. This is essentially how bitcoin works. The ledger, or Blockchain, is the recording of the transactions. And in simple terms the miners are the witnesses verifying the transactions with signatures. And if you want to be thorough, bitcoin itself is just a representation of currency. Just how paper money only has value because we give it value.

Now to the code! I'm not going to go through everything, the full code is here [To the blockchain](https://github.com/Astjust1/bitcoinPOC)! The most interesting piece of the blockchain system, at least to me, is the algorithm used to verify the transactions. It's called the [Hascash algorithm](https://en.wikipedia.org/wiki/Hashcash). It was originally devised to slow down email spammers, by adding a cost to sending email. In the blockchain, it is used to provide a proof-of-work, or in other words, it forces the miners to expend enough computational energy to "verify the transaction". Back to my analogy, the "signature" that comes from the hashcash verification. Is in the form of a nonce, that is attached to the transaction being verified. Here is my simplistic variation of it:
```let proofOfWork = function(block,difficulty){
    let nonce = block.nonce;
    let oGHash = block.hash;
    let hash = oGHash;

    while(!prefixCheck(hash,difficulty)){
        nonce++;
        block.nonce = nonce;
        hash = block.hashBlock();
    }
    block.nonce = nonce;
    block.hash = hash;
    return block
}
```

To provide some more context, every transaction records the transaction preceeding it in the form of a hash. So when the nonce is recorded in the transaction data, it essentially signs that transaction. This makes it nigh impossible to forge the blockchain.

So back to the code! The basic gist, is that while the prefix fails to contain a specific number of 0's corresponding to the `difficulty` agrument being passed to `prefixCheck()`. The function loops and recomputes the hash of the block data using sha256 until the prefixCheck is satisfied. Then we know what the nonce/ signature is, so we apply that to the block, assign the hash, and return the newly signed block to be added to the blockchain!

So simple! Yet so effective!