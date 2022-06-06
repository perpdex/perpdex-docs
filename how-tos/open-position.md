---
description: Make a trade
---

# Open Position

Once you have funds deposited into the PerpDEX App, you can use those funds to trade various perpetual futures contracts on PerpDEX. Following are the steps to open a position:

* Click trade from the navigation menu
* Select a **perpetual futures pair** you want to trade.
* Select the type of trade you want to go: **Long/Short**
* Enter the **amount** of collateral you want to trade with.
* Select **leverage** if you want to do leverage trading. (Max 10x)
* Click **confirm** button to initiate trade.
* **Confirm** transaction from Metamask
* Within a few seconds, the transaction should be confirmed.
* Once the transaction is confirmed, your position should appear in the positions tab at the bottom.

{% hint style="info" %}
If the position you just opened is a long position and you already have another long position open for the same asset, the balance of position will simply sum up in the positions tab.
{% endhint %}

{% hint style="info" %}
If the position you just opened is a short position and you already have another long position open for the same asset, instead of treating them as two different, the system will subtract short position value from long and put the remaining as new position.
{% endhint %}

