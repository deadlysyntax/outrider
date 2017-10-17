# Outrider - Cryptocurrency Exchange Arbitrage Bot
Outrider is a bot that monitors cryptocurrency exchanges for arbitrage opportunities.

Every few seconds the bot will check the specified exchanges and calculates profit/loss - accounting for fees automatically and ignoring potential trades that don't meet a certain profit/loss threshold.

## How does arbitrage work?
Due to the volitility of cryptocurrencies, there are often differences in prices at different exchanges. So if you have one bitcoin and enough local currency to buy one coin at each of those exchanges, you can sell at the higher exchange and buy at the lower exchange. After a trade has taken place you rebalance your accounts and go again, keeping the difference.

A very basic example:
* At **BTC Markets** bitcoin is selling for **5000**
* At **Independent Reserve**, bitcoin is selling for **5080**
* Your accounts at each exchange are stocked with enough bitcoin and AUD to sell a coin at one exchange and buy a coin at the other, depending on which combination of those presents the opportunity.
* Lets say at each exchange you have **1 bitcoin** and **5100 AUD**.
* At the higher-priced exchange, in this example Independent Reserve, you would sell 1 coin, placing a Limit Sell Order at around the current selling price.
* At the other exchange - the lower priced one, in this example BTC Markets, you would place a Limit Buy Order to buy a coin at the lower rate.
* If that is successful (which isn't guaranteed) you will have **0 bitcoins** and **$10,180 AUD** on **Independent Reserve**
* On **BTC Markets** you would have **2 bitcoins** and **$100 AUD**, leaving you $80 in the green. That's about 1.5% profit on the trade - one of those per day is a lot per annum.
* Send 1 bitcoin from BTC Markets to Independent Reserve, deposit $5000 to BTC Markets and withdraw $5080 from Independent Reserve.

***

### Risks
There are risks involved in arbitrage, it's not a guaranteed slam dunk. You can read more about the basics of arbitrage and the risks involved on this [Stack Overflow thread](https://bitcoin.stackexchange.com/questions/49819/cryptocurrency-arbitrage-what-do-i-need-to-know).

Outrider seeks to minimise those risks, but this bot is an experimental system and is a work in progress.

**We do not accept any responsibility for what you do with these tools or any financial losses. You use Outrider at your own risk.**

In saying that, Outrider can be used in a way that doesn't actually trade until you have a thorough understanding of Crypto-Arbitrage. You can watch the numbers and monitor the markets for as long as you like until you are comfortable. We suggest you then start trading with very small amounts until your process has proven itself.

This software is still in development and is not yet complete. Contributions are welcome.

***

## Technical Overview
The software is made up of two parts.

### The engine
One part is the bot engine which monitors the exchanges, calculates opportunities and runs trades. It is built using NodeJS and Typescript. It is a command line tool that anyone can install and run with enough knowledge of the NodeJs environment.

The engine also connects to the database and provides API endpoints for our user interface.

### The user interface
The other part of Outrider is the user interface, which is built using Ionic 2 with Angular 2. It can be deployed in the web browser or on a mobile device.

The interface provides charts of all the monitored data and records of trade opportunities and completed trades. It provides insight into the actual numbers coming through from the exchanges, including calculated figures of profit/loss, profit percentage and fees.

![Dashboard Example]({{ site.url }}/assets/dashboard.png)
