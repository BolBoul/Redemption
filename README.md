# Spartacus DAO Redemption Mechanism: Proposal and FAQs

1. Proposal
2. Purpose and Discussion
3. Frequently Asked Questions 
4. Open Questions 



### I. Proposal: 

This section is written in the style and level of complexity of those previously voted upon, archived on snapshot.eth.

#### Title: Spartacus DAO should add a redemption mechanism 


**Background:** The value of SPA token has fallen significantly beneath multiple measures of backing assets. (Figures current as of December 18 at 8:31pm UTC. Grey fields need refreshing).

<img src="https://i.imgur.com/RdevSCz.png"/>

In particular, SPA has even fallen below its standalone backing assets per token, a conservative measure of the liquid assets the treasury possesses.

Specifically, with values as of Dec. 18, 2021: (Value of standalone DAI in Treasury (~44m) + Value of standalone FTM (~6.886m) in Treasury)/ #SPA tokens in circulation (~1.06m) > Price of 1 SPA token 

**Measure:** Implement a permanent token redemption system, akin to those used by ETFs, that floors the value of total outstanding SPA with standalone backing assets' value through arbitrage. 

Specifically, create a smart contract that users may interact with on the Spartacus Finance app dashboard.

Then, interacting with this contract, any SPA-holder can, at any time t>=s,

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Redeem X tokens 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; to receive X * standalone backing assets per token

calculated per above formula, paid out of the Treasury wallet.

The redeemed X tokens get burned. Any SPA-holder is thus guaranteed the maximum of standalone backing assets per token and the market SPA price.

#### Expected outcomes/risks: 

We expect, almost immediately after facility implementation, that the price per token appreciates such that it (weakly) exceeds redemption value per token.  We expect this will not require much redemption at all – i.e. the Treasury will shrink very little.  We expect that the price per token will almost never trade at a discount to redemption value per token in the future. Finally, we expect even the credible announcement of this policy will lead to a jump in token price such that it is closer to the redemption value per token, although the entire gap may not be closed.

This is a consequence of arbitrage: if there is a discount, arbitrageurs will buy SPA and redeem it until it trades at its standalone backing assets per token. If there is not, no redemptions will occur.  The redemption system (correctly) increases the value of individual SPA tokens, by providing existing and future tokenholders a free option.

Barriers to arbitrage buying, poor communication, or a complicated implementation could lead existing holders to simply redeem before price has a chance to react (very unlikely if there’s a pre-announcement). In this case, the treasury could shrink sizably, reflecting a massive lack of confidence by the existing investor base. Remaining holders would benefit from the repricing of tokens because Total Backing per Token will have increased. 


#### Timeline: 

In the event of a positive vote on this proposal, the DAO may make a public announcement detailing its intentions to adopt this proposal before implementation of the permanent redemption facility. 

This announcement will likely lead to speculative net buying of the token given that price is less than standalone value (and even RFV) at present.

Announcement language and accompanying disclosure should be decided by a subcommittee including project developers and moderators.  The timing of this announcement should be randomized and private for reasons of fairness. 


### II. Purpose and Discussion: 

Note, in what follows, when I speak of “per token,” I implicitly assume adjustment for supply expansion.


1. **This is a long term proposal that bolsters governance and tokenholder rights.** Why? In the event that management or developers are destroying or appropriating value (as the present discount to even RFV might suggest is market perception) or property rights over treasury holdings are unclear, giving tokenholders the option to redeem restricts the extent of this value destruction. This disciplines management, developers, and the DAO at large and promotes stability of backing. It also encourages transparent communication: if developers are taking high ROI actions that appear destructive in the short term, they are incentivized to communicate these transparently to tokenholders to discourage redemptions. Developers and management that adopt such a system of accountability are signaling confidence and above-boardness.

2. **This proposal benefits all tokenholders.** Holders see the value of their holdings increase through re-pricing. They also see total backing per token expand because redemptions happen at standalone value per token, which is less than that.  Do some arbitrageurs make money? Yes. Is that at the expense of tokenholders? No. It is at the expense of whomever was benefiting from previously ill-defined property rights and lack of accountability. Put this another way: a claim on 1/100th of the proceeds from a box containing $100 overseen by your friend Greg should be worth at least $1 to you unless either Greg is doing something value-destructive or it is unclear whether you can actually extract your claim.

 
3. **This proposal promotes efficiency and allows the DAO to get back to the core business of bonding** (infeasible at a hefty discount to assets) and grow its treasury. 


4. **This mechanism is tried and tested in the ETF market.** ETFs manage to retain and even dramatically grow assets under management (AUM). So although such a mechanism is new among Olympus forks, it is hardly new in the financial world.

### III. Questions and Explanations:


***Conceptual Clarifications:***

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **1\. How much redemption will happen? Is this not equivalent to a full redistribution of the Treasury, effectively ending (or crippling) Spartacus DAO?**

For an individual agent, redemption is only economically sensible if redemption value exceeds price: otherwise, it is more profitable for her to sell on the open market. Per a recent test on Spookyswap, a net demand of roughly 2mm DAI would raise price to RFV/token and 4mm DAI would move price to standalone value/token. 

As such, these numbers are reasonable upper bounds for the total amounts of buy-to-redemption that would actually occur from the treasury until there were no incentives for further redemptions.  

We expect the total amount of redemption to be far less. We expect strongly positive net demand from non-arbitrageurs at any price less than redemption value: the fact that tokenholders have been given superior property rights and governance for the long term, the fact that tokenholders have a floor, and the fact that devs delivered such a value-accretive solution should encourage net purchases. (Note, we are not including speculators whose net demand we expect to be roughly zero – they will buy at current prices but sell at or slightly below RFV). 

Note: because redemption occurs precisely at standalone value per token, redemption does not change – increase or decrease – the pro-rata share of Treasury (i.e. the standalone value per token) that future arbitrageurs may redeem. This means there is neither a run nor (which would occur if there were a decrease) nor is there a complicated fixed point analysis to do (if there were an increase). 


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  **2\. Isn’t this a bank run?**

No. A bank run occurs when there aren’t enough liquid assets to cover redemptions. Here, holders are being compensated less than treasury value per token for redemptions (standalone value < treasury value), which means total treasury value is more than sufficient to cover redemptions.  Moreover, by the preceding answer, the requisite amount of redemptions is an order of magnitude smaller than the treasury size. 


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **3\. Doesn’t rebasing (i.e. token supply expansion) lead to a rush for redemptions?**

No.

For the short term (immediately after implementation): there certainly is no “run” (see above) and the 8 hour inter-rebase period is plenty of time for arbitrage to occur given characteristic trade volumes. 

Now think mechanically.

When a rebase occurs, token supply expands. The cumulative token supply expansion (as a ratio to initial supply) is captured by the “Current Index” on the Spartacus dashboard. For a fixed value of standalone assets, this reduces standalone assets per token, which we’ve defined as the redemption price. Does this create an incentive to redeem quicker?

Consider two possible assumptions (it would seem this is a topic of debate/empirical investigation):

Assumption 1: price stays fixed at rebase, i.e. it doesn’t systematically or predictably dip (I don’t find this assumption convincing because rebase then produces arbitrage opportunities).

Imagine you are at the instant right before a rebase and you have X staked SPA tokens. Suppose token supply is set to expand by a factor of k>1.

Value from redeeming before rebase: VX; Value from selling at market: Xp

Value from redeeming after rebase: V/k\*Xk = VX; Value from selling at market after rebase: Xkp

Thus the value of redemption is unchanged. If anything (again, this doesn’t exactly square with a no-arbitrage world), redemption might be in-the-money before the rebase, but an agent might wait to just sell on market after the rebase.


Assumption 2: price systematically drops (e.g. by the factor of 1/k) at rebase.

Value from redeeming before rebase: VX; Value from selling at market: Xp

Value from redeeming after rebase: Vk\*X/k=VX; Value from selling at market after rebase: Xk\*p/k=Xp

So the calculus is identical before and after. The value of redemption is unchanged.


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **4\. What’s the difference between buybacks and redemption?**

In a buyback, the Treasury uses its funds (standalone DAI or standalone FTM), in one-off episodes, to purchase SPA out of the market, and then possibly burns it.  This can raise prices but prospectively only temporarily if participants choose to dump the buybacks. Moreover, this approach is vulnerable to front-running. Repeated use of such a procedure would deplete the Treasury without limit; moreover, there is no guarantee (because there is no arbitrage/no incentive) price will not drop beneath RFV or standalone backing per token at any point in time, which itself might be decreasing. 

With a redemption facility, the protocol is putting in place permanent incentives for arbitrageurs to purchase SPA out of the market and redeem it for standalone backing per token whenever price is less than standalone backing.  This entails value creation for tokens, as it enhances tokenholder property rights in an incentive compatible way. This is much less expensive for the Treasury: it does not get dumped on or front-run, etc., and per earlier estimates (Question 1), we’re talking at most $2-4mm.  It is also not ad-hoc, which makes it more credible and durable. 


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **5\. Does this proposal sacrifice protocol owned liquidity?**

No. Note that LP tokens are NOT part of standalone backing: it is not part of redeemable value.   POL is an important concept to this DAO, and this proposal does not reduce it. In fact, the proposal benefits the LP position in two ways: (i) SPA tokens increase in value, meaning that the overall value of the LP position rises. (ii) Because LP position value is not paid out for redemptions, LP value/token increases when redemptions occur. 


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **6\. Can whales “dump” price beneath liquidation and exploit the redemption mechanism?**

No. This strategy doesn’t make coherent sense. 

Without shorting this strategy doesn't work. Participant (if not already long) has to buy SPA in order to dump (e.g. beneath redeem price), which is px neutral if quantity is matched. Even if shorting existed, participants would lose money on slippage/impact by dumping SPA, so it's not clear that the strategy proposed could actually be profitable. They'd have to lose less money by dumping than they would from redemption: this implicitly requires many other sellers to follow them (not themselves). With a strong community of arbitrageurs who will buy back these sales, it's not even clear such participants would be able to monetize the dumps they expended cash to make, so it's not clear this can be operationalized. 

If whales were already long and tried to exit around known liquidation levels of Spartacadabra loans (so the criterion of other sellers following them would occur mechanically)? It would appear that they could then in principle buy back cheaper if they get their timing right (a tough ask - they need to be slow enough to allow all liquidations, but fast enough to catch bottoms and generate profit exceeding their slippage). This could be happening even at present! This situation is better under the redemption proposal. Why? Arbitrageurs will buy into market indiscriminately if price is beneath redemption value, so it doesn't matter that the liquidations are happening - as soon as redemption facility becomes available they're made whole.

But this raises the idea (see Open Questions) of interactions with Spartacadabra. 


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **7\. Does this mechanism create a ceiling on the price of SPA?**

No. It creates a floor at the redemption price.

For any price s<redemption value, some arbitrageur will want to buy if a redemption facility is in place (this argument doesn't work before facility is in place UNLESS said promise is 100% credible - and there's always risk; so we'll still trade at a discount to redemption, where the size of the discount indicates market perception of credibility and time discounting. This is relevant to SB.). For a price s>redemption value, there is no arbitrage opportunity. There may be buyers who want to buy at that value because they are optimistic about value creation; there may be sellers who want to liquidate their positions, but it is hard to ascribe a directional bent or a certain"dump."


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **8\. Is this mutually exclusive with BUIDL and/or MultiSig?** 

No. At the end of the day, we’re trying to set up the DAO to be as innovative and productive as possible.

These are synergistic pursuits. MultiSig enhances credibility and accountability – which amongst other things would help the announcement effect. And a redemption mechanism disciplines and stabilizes future BUIDLing by limiting options for value destruction. 

In a narrow sense, there is a tradeoff between the Treasury funds likely redeemed under such a mechanism and other costly value-accretive measures we could pursue. First, the current market view (through the discount) implies that any measures being pursued or contemplated currently are ROI negative. Second, the redemption mechanism – by bolstering property rights – will help us use incentives to ensure that future measures pursued are strongly ROI positive. 



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **9\. If an announcement will raise prices, why not just do that and not follow through with building the mechanism?**

Just because announcement may drive risk arbitrage (i.e. speculative) activity itself, doesn't mean that we should plan on only making an announcement.

There are several long-term accountability and stability reasons that having redemption is good, not the least for the meaning/mission of a reserve currency. It is a sign of confidence and transparency of management/devs, an offering of optionality to token holders, and can be pursued in tandem with other value-creating measures. 

Finally, a lack of credibility undermines the whole announcement effect, making the proposal more expensive. This may be part of what's going on with SB's situation, which feels very much like a gambit. Risk neutral pricing suggests market thinks they have a 50-50% chance of going through (490-330)/2 is approximately current price. Having this as an ongoing facility/option is not a gambit: it's good governance. Redemption also won't be used unless price dips beneath the redemption value (e.g. because of a massive sale, etc.): it is out of the money option in that case. In steady state, it's just an extra (irrational to exercise) right for tokenholders.



***Implementation Questions:***

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **10\. Why not include a paper-hands or redemption fee?**

Doing so makes arbitrage more difficult and costly. But it’s the arbitrageurs who drive the value that accrues to tokenholders in this proposal . In other words, doing so simply reduces returns to tokenholders.  

Furthermore, this creates a wedge between standalone backing/token and the floor redemption value provides for price. That slows down the protocol’s return to bonding.

Consider the extreme example of imposing a 99% paper hands tax or redemption fee. This would achieve essentially nothing. 


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **11\. Shouldn’t we use a price that is at a fixed discount to RFV (resp. total treasury backing per token)? This way, on a per token basis, RFV (resp. total treasury backing) increases with redemptions.**

We *are* using a price that is lesser than total treasury backing per token: the standalone backing.  Therefore redemptions increase total treasury backing per token. All treasury assets (including the LP position, through transaction fees) are potentially yielding, so redemptions create fundamental value for remaining holders.

Why not use RFV? In the future the DAO (and this would certainly be consistent with a plan to be a reserve currency) will likely accumulate significant non-stablecoin assets, which themselves can be yielding. Even if it comes at a marginally higher cost in terms of redemptions-to-adjust-to-equilibirum today, it is important to ensure tokenholder property rights extend to those coins as well – and to extend governance implications (constraining management and DAO value destruction) to those assets as well.  In particular, we do not want the fact that redemption contains only risk free assets to distort management's incentives so that they hold too many risky positions as a percentage of portfolio composition (i.e. if tokenholders have a claim only on standalone DAI, management converts DAI into FTM or  BOO or whatever else unilaterally and without a positive ROI case, effectively diluting tokenholder claims). Finally, standalone backing per token exceeds RFV per token, and so the expected token appreciation is higher (and responsible, sustainable, etc.): this is better for all holders, and represents a highly positive return on investment at a time where the market is imputing a strongly negative ROI to various measures this DAO is undertaking.

The above arguments also apply to proposals considering arbitrary fractions of RFV as redemption price: those are even more inefficient.


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **12\. What about a mechanism where redemption value per token gradually increases from current levels to the target?**

If buyers have similar rates of time preference, this achieves nothing. If not, this is a way to screen relatively more impatient buyers (or arbitrageurs). If buyers are not capital constrained relative to the $2-4m in question, this will also achieve nothing: the most patient buyers will borrow and bid up the price to the final redemption value (minus some small risk premium) and wait. If buyers are very capital constrained relative to the $2-4m in question, we’ll see some “early” redemptions from relatively more impatient arbitrageurs who’d rather not keep holding. The existence of Spartacadabra and the size of some investors make me think this really doesn’t make a difference.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **13\. How about a mechanism where redemption value (RV) is interpolated between RFV (or standalone value) and prevailing market price, i.e. RV(t) = c\*min(p(t), SV(t)) + (1-c)\*SV(t), with 0<c<1?**


First and foremost, note that the mechanism is to be ongoing.  So we cannot fix a particular “snapshot in time” RFV or SV per token as a one-off.  This is why all quantities are indexed by the relevant time t.

As a matter of economic theory, the same outcome will obtain here as in the case where redemption value is at RFV itself (i.e. c=1): price will converge to RFV, so that halfway distance is irrelevant. And perhaps there’s a benefit in terms of communication.

How is this different from @kromer's calculation and conclusion that c=0.5 is optimal? 

Recall, @kromer's model considers one representative arbitrageur doing a trade and loop sequence (buy SPA, redeem, use proceeds to buy more, redeem, etc.). 

First, note that c<1, redemptions, when they do happen, boost future redemption value (RV)/token, making redemption more valuable in the future.

To gauge the impact of a particular choice of c, an economic model needs a criterion (equations or a formula) for the determination of equilibrium spot price that arises as the result of trading (not just the initial spot price at the "start of" the simulation.  This quantity determines the moneyness of the redemption option and hence when agents will redeem.
@kromer's model does not have such an equilibrium determination. Equilibrium requires all agents to be simultaneously optimizing, given each others' actions. This is different from simply the price resulting from each "round" of collective arbitrageur activity (using the AMM's constant function and the existing LP balances). Why is that not equilibrium? 

First, the arbitrageur (or abstraction of market as arbitrageur) would actually want to submit a demand (to the LP) larger than that which brings price to be equal to RV (redemption value) at this given instant, because he accounts for the increase in RV his redemption would induce (e.g. if he redeemed token by token). More  importantly, as his purchase and redemption occur at best in a simultaneous block, he would account for the fact that subsequent purchases/redemptions (if price is left beneath the new RV) by others would further drive up the price so that he would have done better to hold on to his assets and either redeem or sell into the market in the future. An arbitrageur would not then pursue the suboptimal action of immediate redemption and would instead wait to sell or redeem. That is a profitable deviation.  Thus, unless a single, fastest arbitrageur can execute the entire [buy --> redeem --> buy --> redeem -->...] loop some large number of times in one single block (which I don't believe he can), equilibrium will not look like @kromer's simulation.  To repeat, the key insight is that under those dynamics, it pays for the arbitrageur to wait. 

Of course, both policy proposals will (unambiguously, by defintion) function very similarly if the discount to the RFV or SV (whichever is chosen) closes substantially before implementation of the facility.  This will likely occur on account of announcing the policy ahead of time and corresponding speculative behavior ("risk arbitrage"). We even expect Spartacus DAO holders to start buying the token as they anticipate a concrete plan's successful vote.  Additionally, @Troughkin makes an interesting suggestion that the DAO can do a buyback to close any existing gap at the instant of facility rollout. This would, at least upon implementation, remove any difference between the two proposals.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **14\. Should we have a permanent mechanism or just a one time implementation here?**

A permanent implementation is cleaner (since the facility has to be programmed/developed anyway): if the option is unused when p<redemption, it still works exactly as you desire (I imagining few "non-economic" redeemers who redeem when price exceeds redemption, instead of selling). The problem with ad hoc emergency interventions is that it's hard to believe when or not one happens.

This constitutes a stronger commitment. If one day (say the 99th time value drops beneath RFV) "A" (in my metaphor above)/management wakes up and decides, oh fuck it we're going to engage in massively value destructive activities and these DAO members have no way of stopping us, and we can appropriate the Treasury at their expense (idk, to buy ourselves bored apes) then nothing stops p --> 0. I do not think that is the case, but having a standing facility in that case imposes constraints and commits management not to doing that.

### IV. Open questions:

1. How to implement this in the most secure way? 
     - This proposal is about economic merits of the proposal. We are not knowledgeable about security constraints and how they interact with the design of the redemption mechanism. 
     - Multiple folks have mentioned oracle attacks that tamper with the pricefeeds of underlying assets, and it will be important to be robust to that.  For example, using RFV and harcoding DAI:=1$ may create less risk than using standalone value. This needs to be traded off against the fact that a higher floor can be supported, and this is better for governance incentives.
     - Others have mentioned vulnerabilities in redemption contracts more generally -- not in connection with arbitrage strategies, but rather in terms of fundamental security flaws. These are also important to address, and the dev team's input is extremely important here.
     - One possibility is implementing a fixed cap in redeemable treasury, to avoid nefarious redemption of the treasury.

2. What is the best communication strategy? @Magic32 and @CryptoJedi had ideas about this. Credibility is of paramount importance. Redemption value at c=1 is the easiest to explain, as well.

3. Interaction with Spartacadabra is important. It removes arbitrageurs’ frictions, which is a good thing as it facilitates repricing.  But there are a handful of other questions:
     - What happens to liquidation thresholds under redemption value in Spartacadabra? 
     - Similarly, does Spartacadabra automatically liquidate loans if RFV is reached? 
     - Are there any ways, other than discussed in Question 6, how known liquidation thresholds might interact with the RF threshold?
     - What is the clearest cross-platform way of communicating a token unit? The wsUnit? 
     - Are wsTokens redeemable or just basic SPA?
