 - [Requesting a channel](#requesting-a-channel)
   * [What is this about?](#what-is-this-about)
   * [Why would anyone need that?](#why-would-anyone-need-that)
   * [How do I request a channel?](#how-do-i-request-a-channel)
   * [Are there any limitations?](#are-there-any-limitations)
   * [What are the fees?](#what-are-the-fees)
   * [What is the catch?](#what-is-the-catch)
   * [How long will the channel stay open?](#how-long-will-the-channel-stay-open)
   * [Can I request a channel with more capacity?](#can-i-request-a-channel-with-more-capacity)
   * [Are there any alternatives?](#are-there-any-alternatives)
 - [Troubleshooting](#troubleshooting)
   * [Wrong public key (unable to find node)](#wrong-public-key-unable-to-find-node)
   * [No public address associated with the key](#no-public-address-associated-with-the-key)
   * [Number of pending channels exceed maximum](#number-of-pending-channels-exceed-maximum)
   * [Local/remote feerates are too different](#localremote-feerates-are-too-different)
   * [You should have at least 10 open channels / 0.01 BTC capacity](#you-should-have-at-least-10-open-channels--001-btc-capacity)
   * [Various connection and timeout errors](#various-connection-and-timeout-errors)
 - [I have a question not answered here!](#i-have-a-question-not-answered-here)

## Requesting a channel

#### What is this about?

[LightningTo.Me](https://lightningto.me) allows merchants and enthusiasts to request a channel from our relatively [well-connected and well-balanced node](https://1ml.com/node/03bb88ccc444534da7b5b64b4f7b15e1eccb18e102db0e400d4b9cfe93763aa26d). This page answers some frequently asked questions.

#### Why would anyone need that?

In order to receive payments through lightning network, nodes need to have so-called *inbound capacity*. The easiest way to get inbound capacity is to ask another node to open a channel to you. This is exactly what we offer. [More on the topic.](http://medium.com/lightningto-me/60224aa13393)

#### How do I request a channel?

Go to https://lightningto.me, fill the form and press the button. That's it.

#### Are there any limitations?

Just please be nice. Only request a channel if you actually intend to keep it open and to use it.

#### What are the fees?

We set zero fees for the usage of our channels. When the network matures, we may increase the fees slightly, but we will always keep them unfairly low.

#### What is the catch?

There is no catch. We would like lightning network to succeed, and we see inbound capacity problem as one of the biggest obstacles to adoption. So we want to help.

#### How long will the channel stay open?

We will try to keep it as long as we can. We can close some channels if we need some on-chain funds, but only the channels that are not used / inactive.

#### Can I request a channel with more capacity?

Write to contact@lightningto.me about your use case and we will see what we can do. Usually we can allocate more funds for new merchants.

#### Are there any alternatives?

As a direct alternative you can use [Bitrefill's Thor](https://medium.com/@bitrefill/2d6ffbad3906). It is great, check it out! Keep in mind though that it will cost you ~3 dollars a month for a 0.02 BTC channel. For more ways to get inbound capacity, check out [this article](http://medium.com/lightningto-me/60224aa13393).

## Troubleshooting

#### Wrong public key (unable to find node)

Make sure you configured your node as public, not private. If your node is very new, just wait a couple of hours (the information about your node needs some time to propagate through the network). If you see your node on explorers like 1ml.com and still get this message, please contact us.

#### No public address associated with the key

Make sure that your node is advertising its external IP address (for lnd you should have `externalip` set), otherwise peers will not be able to establish connections to your node.

#### Number of pending channels exceed maximum

Just wait and try again later.

#### Local/remote feerates are too different

This is especially a [common issue](https://github.com/ACINQ/eclair-mobile/issues/118) with Eclair implementation. One option in this case is just to wait until the feerates stabilize and request a channel again. Another one is to increase your config to tolerate larger differences (`eclair.max-feerate-mismatch` for Eclair).

#### You should have at least 10 open channels / 0.01 BTC capacity

This check exists to prevent uncommitted users who are just starting to play around with a lightning node from requesting a channel. It is totally fine to request a channel if your node is new, but please show some dedication to the cause by opening some channels first.

#### Various connection and timeout errors

 * __Is your node behind NAT/firewall/router?__ Make sure your ports are properly forwarded. You should be able to `telnet your_ip your_ln_port` from another machine, otherwise something is wrong.
 * __Is your node online?__ Make sure the lightning software running and that is has finished all the startup tasks (can take a couple of hours).
 * __Does your node have a dynamic IP address?__ Make sure your node is advertising the right IP address publicly and consider switching to a static IP.
 * __Is your node behind Tor?__ Please establish connection to our node yourself and try again (for lnd the command is `lncli connect 03bb88ccc444534da7b5b64b4f7b15e1eccb18e102db0e400d4b9cfe93763aa26d@138.68.14.104:9735`).

## I have a question not answered here!

Please drop us an e-mail to contact@lightningto.me.
