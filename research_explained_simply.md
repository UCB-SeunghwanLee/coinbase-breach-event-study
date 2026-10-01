# Did a Data Breach Hurt Coinbase's Stock?
### A research project explained so a 10-year-old can understand it

---

## 1. The story: what happened?

**Coinbase** is a company where people buy and sell digital money called *crypto* (like Bitcoin). Millions of people keep accounts there, a bit like a bank.

In **May 2025**, some bad guys **paid a few Coinbase helpers** (people who answer customer questions) to secretly copy customers' private information: names, addresses, phone numbers, and pictures of their IDs.

The bad guys could **not** take anyone's money directly. But they used the information to **trick people** by pretending to be Coinbase on the phone. Then they asked Coinbase for **$20 million** to keep quiet. Coinbase said **no**, and on **May 15, 2025** it told the whole world what had happened.

This kind of event is called a **data breach**: private information gets out when it shouldn't.

---

## 2. Our question

> **When people found out about the breach, did Coinbase's stock price drop more than it normally would?**

A **stock** is a tiny piece of a company that people can buy. If people trust a company less, they often sell its stock and the price goes down. So the stock price is a bit like a **"trust score"** that changes every day.

---

## 3. Why does this matter?

- If breaches make a company's stock fall, companies have a **big reason to protect our information**.
- Investors (people who buy stocks) want to know how much a breach can hurt.
- It teaches us how to tell if one event *caused* something, instead of just guessing.

---

## 4. The data we collected

We downloaded **daily stock prices** from Yahoo Finance, from May 2023 to March 2026, for:

| Group | Who | Why we included them |
|---|---|---|
| **Our main company** | Coinbase (COIN) | The company that had the breach |
| **Crypto money** | Bitcoin, Ethereum | Coinbase's price moves a lot with crypto prices |
| **The whole market** | S&P 500 (SPY), Nasdaq (QQQ), VIX | To see how *all* stocks were doing |
| **Crypto friends** | Robinhood, MicroStrategy, MARA, RIOT | Similar companies that were **not** breached |
| **Money-app friends** | PayPal, Block, Interactive Brokers, Schwab | Other finance companies that were **not** breached |

Then we turned prices into **daily returns**: *how much did the price go up or down today, in percent?*
For example, if a stock was $100 yesterday and is $93 today, its return is **−7%**.

We also cleaned the data. Bitcoin trades every day, but stocks only trade Monday to Friday, so we kept **only weekdays** to compare fairly.

---

## 5. How we tested it: a fair comparison

Imagine your whole class takes a test on a really hard day, and everyone's score drops. If **your** score drops, you can't blame just yourself. It was a hard day for everyone!

So we didn't just ask *"Did Coinbase go down?"* We asked:

> **"Did Coinbase go down *more than its friends* on the day of the news?"**

The friends are the 8 similar companies that **didn't** have a breach. If something bad happened to all of them that day (like a bad day for crypto), it shows up in the friends too, and we subtract it out.

Our **model** is very simple:

> **Breach effect = Coinbase's return on May 15 − the friends' average return on May 15**

---

## 6. What we found

On **May 15, 2025**, the day the breach was announced:

| | Return that day |
|---|---|
| **Coinbase** | **−7.20%** 📉 |
| Friends' average | −1.34% |
| **Difference (the breach effect)** | **about −5.9 percentage points** |

So everyone had a slightly bad day, but **Coinbase fell about 6 points more than its friends.**

---

## 7. Was it just bad luck? (The "fake day" test)

Coinbase's stock is **jumpy**. It moves a lot even on normal days. So maybe a 6-point gap happens all the time?

To check, we did a **placebo test** (a "fake day" test). We pretended the breach happened on **60 ordinary days** when nothing special happened, and measured the gap between Coinbase and its friends each day.

- On normal days, the average gap was **about 0**. Coinbase and its friends usually move together. ✅
- Only **2 out of 60** normal days (about **3%**) had a gap as big as May 15.

That means a drop this big is **pretty rare** on a normal day. It's like flipping a coin and getting heads 5 times in a row: possible, but unusual enough to make you think something real is going on.

---

## 8. Why we have to be careful

Good researchers always say what could make their answer wrong:

1. **Other news happened the same week.**
   - Around **May 12–13**, news came out that Coinbase would join the **S&P 500** (a list of the biggest US companies). That's *good* news, and the stock **jumped about 24%** on May 13.
   - On **May 16**, the day after the breach news, Coinbase **bounced up 9%**, probably because big funds were buying the stock to get ready for the S&P 500.
   - Around May 15, there was also reportedly news about a **government investigation** into how Coinbase counted its users. That could have pushed the price down too.

   So the May 15 drop might be **partly** the breach and **partly** other news. We can't fully separate them.

2. **It's only one company and one day.** With so little data, our answer is a good clue, not a final proof.

3. **The stock bounced back quickly.** The breach seemed to hurt for **one day**, not for a long time.

---

## 9. Conclusion

> **On the day Coinbase announced its data breach, its stock fell about 6 percentage points more than similar companies. A drop that big happens on only about 3% of normal days, so it looks like a real reaction to bad news, but other news that same week makes it hard to say the breach was the *only* cause. The stock also bounced back the very next day.**

In kid language: **people got worried and sold Coinbase stock when they heard about the breach, but they calmed down quickly.**

---

## 10. Words to know

| Word | What it means |
|---|---|
| **Data breach** | When private information gets out to people who shouldn't have it |
| **Stock** | A tiny piece of a company that people can buy and sell |
| **Return** | How much a stock's price went up or down, in percent |
| **Peers / friends** | Similar companies we compare against |
| **Treated** | The company the event happened to (Coinbase) |
| **Placebo test** | Pretending the event happened on a normal day, to check our method isn't fooling us |
| **Percentage point** | The difference between two percents (−7.2% vs −1.3% is a 5.9-point gap) |
| **Causal** | Showing one thing actually *caused* another, not just happened at the same time |

---

*Analysis: `coinbase_breach_analysis.ipynb` in this folder. Data: Yahoo Finance via `yfinance`.*
