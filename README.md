# Sui Sequencer
This repo aims to create a sequencer for FastPay that allows the aggregation of transactions into a block of 'batched' transactions.

The sequencer will aggregate transactions that are sent to it, rerun each transaction on their fullnode, merkelize the transactions into a tree, and send the root of the tree of users to hash.

More precisely, the users will be hashing: H(Merkle Root || txbranch) to ensure that they are only signing their own transaction.

The sequencer is not trusted for safety, and only liveness. However, this is not a huge problem, as FastPay's latency is extremely low. If your transaction doesn't go through with the sequencer, just resend the transaction to another sequencer.
