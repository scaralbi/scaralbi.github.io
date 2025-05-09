---
title: A Mathematical Theory of Communication, Claude Shannon
layout: post
date: 2019-04-20

---

My friend and flatmate Ale, who studies Electronic and Information Engineering suggested me to read [ A mathematical theory of communication](http://math.harvard.edu/~ctm/home/text/others/shannon/entropy/entropy.pdf) by Claude Shannon. Here is what I got from it.
How can we describe mathematically information?
This is important to engineer communication. The logarithmic function is a good function to represent information. One reason is that it is practically more convenient (many engineering parameters like time, bandwidth etc... tend to vary linearly with the number of possibilities). Essentially, he chooses the logarithmic scale as the unit to encode information. If you choose the base 2 of the loc, you end up with binary digits (bits).
Then, he argues that a communication system shall consist of 5 parts: information source, transmitter, channel, receiver, destination. The information source produces the messages (where the information is stored), for example in the radio the message is a single function in time f(t), in color TV messages are functions f (x; y; t ), g(x; y; t ), h(x; y; t ) defined in a three-dimensional continuum. The transmitter makes the message suitable for propagation, for example in telephones this operation is just changing the sound pressure into a proportional electrical current. The channel is just the medium of transmission. The receiver performs the inverse operation of the transmitter.
How can we quantify amount of information in bits per seconds? We need to properly encode it first.  For example, in telegraphy sequences of letters are not random. In English E occurs more frequently than Q. Thus, E is a dot and Q is 3 lines plus one dot. This allows to save time. And increase bits per seconds at the source. This discrete source has to choose between different symbols, the transitions between these different states are governed by probabilities of having certain symbols. A mathematical model of this kind, that must produce certain sequences of symbols by random walks in sets of probabilities is a stochastic process. Examples of this discrete sources are natural written languages (like English), quantized television signal etc...
He develops with transition probabilities of English language and successive orders of approximations an artificial language. This kind of stochastic process at the end is just a Markov process.
