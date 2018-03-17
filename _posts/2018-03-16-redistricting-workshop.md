---
layout: post
title: Notes from the GEOMETRY OF REDISTRICTING WORKSHOP
tags: commentary life
---

# {{ page.title }}

<p class="meta"> 16 March 2018 - San Francisco </p>

https://gerrymandrsanfrancisco.weebly.com/

## Thursday, March 15
<br>
### 09:30 - 10:20AM - *Moon Duchin (Tufts) - [slides][moon_slides]*
**Math, Politics, and Law in the Study of Gerrymandering**

* Techniques to identify, adjudicate, and remediate
* MGGG has been putting on these workshop
* Redistricting is a mathematical partitioning problem (smash or scalpel)
* Cycling of redistricting: enumeration, apportionment, partition (litigation)
  - Two federal bodies:
    * Senate: 2 per state
    * House: % share of US population, adding up to 435.
  - States are required to redistrict after each Census
  - Officials set their own process
* Six redistricting principles
  - Mathematical
    * Equal population (number) - All districts must be equal to each other +/-
       one.
    * Compactness (shape) - "Reasonable" shape. Geometry here is all 1900
    * Contiguous (shape) - All districts must be connected
       - From these [Cohen-Addad-Klein-Young](https://arxiv.org/abs/1710.03358)
         (picture from Texas).
  - Political
    * Respect for county/city boundaries (political geography) - Don't split up
      a city.
    * Respect for "communities of interest" (sociology) - More on this in the
      future. Hard to make algorithmic.
    * Compliance with Voting Rights Act (race) - Need to give minority
      communities the ability to elect a candidate of their choice.
  - Other stuff
    * Other things not on test, but seem intuitive: Proportionality?
      Competitiveness? Responsiveness?  Stability? Voice for the marginalized?
      Different states can adopt different combinations of rules.
* Concepts
  - Draw diagrams. Plurality election in each vote.
  - Efficient majorities for you = Packing and Cracking for your
    opponents. Cracking is dispersed among losing districts. Opponent is packed
    into smaller number of districts. Theoretically it's possible to double your
    representation from your votes.
  - Examples from WI, PA, and NC with outstanding congressional lawsuits. Half
    the votes, 63/99, 10/13, and 10/13 seats.
  - No legal framework around political gerrymandering
  - Parties gerrymander when they have control to do so.
* A redistricting plan meets a distribution of voters
  - You have a distrusting plan and compare them to a distribution of voters `(D, delta)`.
    * Delta determines `V`, the vote share for the party
    * `D` determines compactness
  - `(D, delta)` pair gives `(V1, ... , Vn)` the vote share by district
  - `(V1, .... , Vn)`   gives `S`, the seat share for a party (how many `Vi > 1/2`).
  - Fix `Delta`, very `D`: How do they perform under various scenarios?
* Menagerie of districts. tl;dr: Important to look at shape and the underlying
  demographics.
  - Florida-5
    * Created after 1990 from 2013 - 2017
    * Packing
    * Change opposed by packed incumbent
  - Maryland-3
    * Drawn by Democrats (opposed by civil rights groups)
  - Pennsylvania-7
    * Barely contiguous. Strung together by only two buildings.
  - North Carolina-12
    * After 1990 census: billed as a voting rights district. Race is used as a
      proxy for map design.
  - Illinois-4
    * Two Hispanic communities linked by a highway
    * Accidental packing
* Race and the Voting Rights Act of 1965
  - Aimed at eliminating barriers to the black vote
  - Only supposed to last for four or five years.
  - Any states with problematic regions needed preclearance with all new plans.
  - Still best tool for addressing redistricting fairness.
* Race and party = 'conjoined polarization'
* Eyeball compactness test is dead
* Dual graph representations describe both population density and connectedness.
* See likelihood [analysis](https://arxiv.org/abs/1708.09852)
* Q/A: 'Democrats pack themselves and therefore underperform': counterexample is
  actually Massachusetts (Republicans uniformly spread out, but no seats).

[moon_slides]: https://sites.tufts.edu/gerrymandr/files/2018/03/Duchin.pdf

<br>
### 10:30 - 11:20AM - *Kris Tapp (St Joseph's) - [slides][tapp_slides]*
**Measurements of Political Gerrymandering**

* Mathematics of elections outcomes and gerrymandering
* Gerrymandering is detected by:
  1. Geometry ('odd shapes')
  2. Statistics ('more votes than average map')
  3. Symmetry ('if voter opinions shift to 50-50, A would have one more seats')
  4. Wasted votes ('party B wasted more votes than party A')
* Presentation focuses on: 3 and 4 are computed using only district outcome data.
* Idea of Symmetry Methods (Gelman, King, and Grofman)
  - Simulate a uniform shift in voter opinion
  - Can produce a simulated seats-votes graph
  - A fair outcome should be symmetric about the origin. Unfair outcome has a
    non-zero bias.
  - If tables turned so blue got 60% of the vote, they wouldn't have received
    the same award.
* Weakness of symmetry methods
  - Rooted in speculative, counterfactual simulations
  - Methods never impressed Supreme Court, but Kennedy suggested alternatives
  - Led to work in other areas.
* Wasted vote methods (Eric McGhee, 2014)
  - Efficiency gap (Excess vote, losing vote)
  - Always between -0.5 and 0.5 (up to half of the votes are wasted)
  - Assumes equal turnout (depends only on seat margin and vote margin)
  - Not covering unequal turnout (see Veomett, 2018)
  - Efficiency gap has slope 2 on the symmetry method parallelogram
  - With 60% of vote, you deserve 70% of seats.
  - With 75% of vote, you deserve 100% of seats. With more lopsided elections,
    EG is useless.
  - Is "winner's double bonus" normative? Fit line for 1972 state house election
    data closely matches EG.
* Shortcomings in efficiency gap
  - Depends on election outcome and volatile in competitive races.
  - Flags demographic packing that isn't related to gerrymandering
  - See Gill v. Whitford
  - Penalizes packing and cracking? Yes, but depends on cutoff of the percentage
    of the vote.
* Variations on the EG formula - Weight (Nagle)
  - Excess votes counted by weight lambda
  - `lambda=1` counts votes in excess of what's needed for majority
  - `lambda=2` counts votes in excess of what losing party received (generalizes
    to multi-party elections).
  - A district won with 66-75% of the vote is considered packed.
* Variations on the EG formula - Relative (Nagle)
  - Measures the difference between proportions of votes that parties wasted.
  - Parties wasted same proportions, but not the same number.
  - Grounded in *voter* fairness as opposed to *party* fairness. A randomly
    selected voter from party A is equally likely to have wasted their vote as
    someone for party B.
  - Court has already ruled that lack of proportionality is not a political
    right.
* Variations on the EG formula - Weighted-Relative
  ([Cover](https://law.yale.edu/system/files/area/center/liman/document/ssrn-id3019540.pdf))
  - Fails any efficiency principle

[tapp_slides]: https://sites.tufts.edu/gerrymandr/files/2018/03/Tapp.pptx

<br>
### 11:30 - 12:20PM - *Santiago Olivella (UNC) - [slides][olivella_slides]*
**Other Frontiers: Voting Precincts and Associated Voting Costs**

* Not about redistricting
* Lines matter: How we discretize the geographic distribution of preferences
  matters for electoral outcomes (social science "path dependence"). More
  perspectives are coming into play, with many academic disciplines bearing on
  the problem.
* Districts matter: smallest units of votes. Constraints are common across
  districts.
* Redistricting has gotten increasingly political.
* Costs of participating can be asymmetric on different groups, as a consequence
  of seemingly technical decisions around electoral administration: where to
  place polling places, how many voting machines, how much staff, etc. (bread
  and butter of applied mathematics).
* Questions to ask to measure electoral quality of service
  - How long did it take to vote? (varies by race)
  - Registration times/locations
  - ID/requirements
  - Learning about candidates
  - Understanding ballot use
* If costs are different across population groups, then we say there is
  discrimination. These may affect registration and turnout rates. Number of
  eligible voters is not known.
p* Issues also affect other countries, not just the US (e.g., population centers
  and polling places in Hungary).
* Distribution of outcomes are not a function of asymmetry or simply
  disinterest. Interests are difficult to observe.
* Bayesian latent variable model of participating and turnout (joint work with
  [Kelsey Shoub](http://shoub.web.unc.edu/))
  - Use it to determine hypothetical interaction between registration, turnout,
    and turnout given registration.
  - Excellent use of [STAN](http://mc-stan.org/)
  - Simulated
  - Apparent discrimination for Hispanic voters in NC is quite high, especially
    during midterm elections.

[olivella_slides]: https://sites.tufts.edu/gerrymandr/files/2018/03/Olivella.pdf

<br>
### 02:00 - 02:50PM - *Eric McGhee (Public Policy Institute of California) - [slides][mcghee_slides]*
​**Partisan Gerrymandering and the Supreme Court**

* Step back and talk about the legal issues
* Legal status quo
  - [Davis v Bandemer (1986)](https://en.wikipedia.org/wiki/Davis_v._Bandemer).
    Court decided that partisan gerrymandering is justiceable.
  - Justice White: we believe partisan gerrymandering exists, but we have no
    means of actually measuring it. The court also doesn't want to interfere,
    because there's no clear definition or criteria on gerrymandering.
  - [Vieth v Jubelirer (2004)](https://en.wikipedia.org/wiki/Vieth_v._Jubelirer).
    Polarized court. Court is split, but Kennedy says that one has not yet been
    provided: if a standard emerges, it should be used.
  - [LULAC v Perry (2006)](https://en.wikipedia.org/wiki/League_of_United_Latin_American_Citizens_v._Perry).
    Still split, but 'Gelman-King bias' (i.e., symmetry) is provided to
    the court. Kennedy suggests that technologists may come up with a clear
    means of shedding light on this measurement question.
* The measurement problem is difficult
  - System was designed for geographic/district representation, but *parties*
    dominate American politics (i.e., an aggregate across geography). Parties do
    the work, but are defined by geography. The votes-seats relationship is not
    codified in law, and parties are not fundamentally covered through law.
  - Geographic system but with parties laid on top: impedance mismatch is the
    source of the Court's difficulties.
* Consequence: we now have an opening for mathematics and social science
  - It's a real challenge for the court, but requires a transparent solution
* Metrics before the court
  - Gelman-king bias ([Gelman & King, 1994](https://gking.harvard.edu/files/abs/writeit-abs.shtml))
    * Principle: equal parties should be treated equally ('symmetrically'). Same
      votes, same seats.
    * Advantages: grounded in core idea of majority rule.
    * Disadvantages: inconsistent and weird for competitive states. May
      suggest gerrymandering where it may not exist. Advocates have not offered
      thresholds for when a map is gerrymandered
  - Mean-median difference ([McDonald and Best, 2015](https://www.utdallas.edu/sppc/pdf/Best_etal.pdf))
    * MMD = average district outcome (mean) - outcome dividing in half (median)
  - Efficiency gap ([McGhee and Stephanopoulos, 2015](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2457468))
    * Wasted votes don't apply to a win.
    * Advantages: works for competitive and uncompetitive states (up to a
      point), targets efficiency. 2-1 seats-to-votes fits historical pattern,
      and this basis is used on historical data. Can also support turnout
      variations and multiple parties. Good for simulation: allows to measure
      intent.
    * Disadvantages: untested! Is it the only or best way? Requires commitment
      to equal wasted votes and can vary from one election to the next. Bad for
      simulations: does it really cover all of them?
  - Simulation generally: does it matter if a plan is improbable?
* [Gill v. Whitford](https://en.wikipedia.org/wiki/Gill_v._Whitford)
  - 2011 Wisconsin Assembly Plan: aggressive seat maximization plan (48.6% of
    vote yields 60/99).
  - Metrics agree for a competitive state.
* Culture clash
  - Complex concepts, such as the EG, will fail Justice Robert's 'man on the
    street' test.
  - Can the court solve this problem, a complex measure, without compromising
    its legitimacy?
  - Each measure has a weakness against the court.
* New measures
  - Determines intent
  - Declination ([Warrington, 2017](https://arxiv.org/abs/1705.09393))
  - Sampling as sensitivity testing
    ([Chikini, Frieze, and Pegden, 2017](http://www.pnas.org/content/114/11/2860)).
  - Aggregate into simple proportionality
    ([Chambers, Millers, and Sobel, 2017](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3046797)).

[mcghee_slides]: https://sites.tufts.edu/gerrymandr/files/2018/03/McGhee.pptx

<br>
### 03:00 - 03:50PM - *Michal Migurski (PlanScore)*

**Making Gerrymandering Boring**

* Works on [Planscore](https://planscore.org/) making gerrymandering modeling
  more useful and hopefully back into a niche problem we don't have to worry
  about (i.e., something predictable, uncontroversial, and low-reward).
* Example: [WalkScore](https://www.walkscore.com/) made walkability mainstream
* Current visualizers use past election results (Trump v Clinton) as a proxy for
  assessing redistricting plans.
* 1000-district model
* New data sources:
  - [Open Elections](http://openelections.net/)
  - [District shapefiles](https://github.com/nvkelso/election-geodata)
* Kennedy on metrics: limit weak, but non-frivolous, metrics. Metric should
  ensure that elected representation reflect real voter intent.

<br>
### 05:00 - 05:50PM - *Bruce Cain (Stanford)*

**By Form or By Outcome? The Fifty Year Quest for Redistricting Fairness**

* Currently revisiting some ideas from early discussions
* Discussion around putting partisan and racial gerrymandering on comparative
  terms. How aggressive can you be in remedying racial injustice through
  redistricting?
* Nothing in the Constitution asserts proportionality, but does protect against
  racial protections (because of prior history of discrimination).
* "A measurement is not the same thing as a standard". It is necessary, but it
  is not sufficient. The thresholds here need to be defined, and should it be
  done at the state level or the national level?
* A solution for one state may not work for another
* Homopoly
* Lots of interesting stories about being on redistricting boards.

<br>
### 06:00 - 07:30PM - *Justin Levitt (Loyola Law), Moon Duchin (Tufts), Michal Migurski (PlanScore)*
**Panel Discussion - "Technology and Law in Redistricting"**

* Justin Levitt: Coming up with the best redistricting plan through technology
  is like coming up with the ideal tax system through programming. There are,
  however, many ways we can use technology to alleviate the problems.
* Moon Duchin:
  - Discretized
    [Polsby-Popper](https://en.wikipedia.org/wiki/Polsby-Popper_Test) (used
    because it's referenced and available to use in
    [Maptitude](https://www.caliper.com/maptovu.htm)).
  - Technological intervention: How extreme is your intervention?
  - A good plan doesn't have to sit at the highest bar
  - These methods are for analysis, not generating plans
  - Both sides of the bell curve are not created equally.
* Justin Levitt: must start simulations with the governing law of the state
  (e.g., laws don't require compactness, for example). Not having these
  constraints mean that your simulations don't match the political will of the
  state.
* Michal: It's only a matter of time for the block chain people to show up.
* Moon Duchin: Lots of clever ways of doing things like encoding the Voting
  Rights Act, communities of interest, etc. into redistricting sampling.
* Justin Levitt: Lots of opportunities to computationally verify the Voting
  Rights Act.
* Moon Duchin: See Justin Levitt's website about state-level redistricting
  rules. Frequently, laws don't actually make that much sense which makes
  operationalizing them very difficult. Also, random assignment doesn't work
  (via the Central Limit Theorem).

<br>
## Friday, March 16

<br>
### 09:30 - 10:20AM - *Lisa García Bedolla (UC Berkeley) - [slides][bedolla_slides]*
**Why the Lines Matter: Race and Representation**

* NOTE(mookerji): Missed the beginning of the presentation
* Commentary on disparities across race on political representation.
* The problem: the lack of outreach across races. Candidates don't reach out to
  constituents they don't need to (e.g., safe majority-minority districts, ones
  that may not contribute to a win).
* In studies (on white voters), children get political preferences from
  parents. Immigrants pick up preferences from children, who learn civic
  engagement from (public) school.
* Why does this matter? Low engagement in US is structural and ultimately
  affects the quality of public policy.
* Please don't say 'identity politics': race matters because it affects their
  material experience of reality. People with similar racial experiences likely
  experience the same structures.
* Examples from American Values Survey
* Turnout affects who candidates speak to, and some candidates may only target
  specific groups and ignore others (or self-identify on certain positions that
  may not be universally felt across groups; e.g., AVS: is one group
  systematically targeted by the police?)
* tl;dr: structure inequality has political consequences. You can have different
  interpretations of current events because of your race-consequent social
  position.
* Q/A: Compulsory voting improves voting rights.
* Q: What line drawing principles could increase participation? A: Hard
  question. Anything that isn't drawn to protect incumbents.
* Q/A: A lot of political money is spent through ineffective reach out (mailers,
  TV ads) in national campaigns because of compensation structure around
  political consultants.

[bedolla_slides]: https://sites.tufts.edu/gerrymandr/files/2018/03/Garcia-Bedolla.pptx

<br>
### 10:30 - 11:20AM - *Greg Herschlag (Duke) - [slides][herschlag_slides]*
**Quantifying Gerrymandering: Revealing Political Structure with Sampling**

* Duke team's work:
  - Gill v. Whitford (WI State Assembly)
  - [Common Cause v. Rucho](http://www.scotusblog.com/case-files/cases/rucho-v-common-cause/) (NC Congressional)
  - [NC vs Covington](https://supreme.justia.com/cases/federal/us/581/16-1023/)
    (NC State Assembly)
  - See [group page](https://sites.duke.edu/quantifyinggerrymandering/)
* Q: When is a map fair? When is it typical?
  - What if we drew the districts randomly? (No regard to party or demographics)
  - Can use algorithmicly-generated maps to benchmark plans?
  - All use MCMC
  - Recipe: generate *compliant* random redistricting plans, generate a winner
  - NC redistricting simulation (distribution of outcomes is between 4 to 9 for
    13 seats). Judge panel is a typical result, per the MCMC ensemble. Note that
    via this method the WI State Assembly plan would seem typical.
  - Gerrymandering can occur in nicely-shaped districts, and skewed results
    don't necessarily indicate that it has occurred.
  - Gerrymandering index. See Eric Lander amicus brief in
    [Gill v. Whitford](http://www.campaignlegalcenter.org/sites/default/files/16-1161bsacLander.pdf).
  - Plot series of ensembles: Parametric on Fraction of Opposing Party Vote //
    Likelihood vs Number of Seats for Opposing Party
  - Sampling can be used to recover these structural geopolitical biases
* Q: Can you surface gerrymandered districts?
  - Fix precinct. Determine outlier precincts compared to the generated outcomes
    of the its containing district. You can then shade (red or blue) the
    district by their tendency relative to district (i.e., deviation from the
    median).

[herschlag_slides]: https://sites.tufts.edu/gerrymandr/files/2018/03/Herschlag.pdf

<br>
### 11:30 - 12:00PM - *Taren Stinebrickner-Kauffman and Kelsey Kauffman*
**Modern Malapportionment: Prison Gerrymandering and Local Redistricting**

* Nobody is tracking whether local governments are redistricting when they are
  required to do so.
* All government bodies with single-member electoral districts in the US are
  required to redistrict every 10 years, including local governments with single
  member districts.
  - 90k local governments in the US
  - No central database of how/when/where how this is happening.
  - Failure to redistrict systematically advantages entrenched parties, affects
    the pipeline to higher office.
  - Lots of egregious cases of maldistricting and refusal to redistrict.
  - See [the webpage](http://indianalocalredistricting.com/)
  - Teachers: identify local governments that are not redistricting. Present
    data, sue governments that aren't in compliance with the law.
* Shifts to prison incarceration
  - Prison population increases dramatically in 1970, not long after the
    population of the voting rights act.
  - How is representational equality affected by incarceration?
  - Q for survey with state representative: which inmate would you feel was more
    truly a part of your constituency? Seems that the current state of counting
    prisoners in population base, may be unconstitutional.
  - Census directors ultimately decide on population base, even though it's not
    in their job description.
  - Possible solutions (maybe Constitutional):
    * Courts: Maybe remove prison inmates from population base?
    * Reallocate prison inmates to their hometowns (or next of kin, most recent
      address) for the purposes of redistricting.
  - See the [webpage](https://www.prisonersofthecensus.org/).
  - Stuff here at state-level: inmates can vote in some places, get reallocated.
  - See article: Counting Matters: Prison Inmates
    * [Link](http://heinonline.org/HOL/LandingPage?handle=hein.journals/vajsplw11&div=14)
* See the page from [Common Cause](http://www.localredistricting.org/)

<br>
### 02:00 - 02:40PM - *Tanya Cecena Pellegrin (MALDEF) and Jonathan Stein (Asian Americans Advancing Justice) - [slides][pellegrin_slides]*
**The California Voting Rights Act**

* Voter suppression techniques
* At-Large Elections: found to be discriminatory by the courts. Always dilutes
  the (numerical) minority vote.
* 100 US Senators elected at-large. Has effect of suppressing minority
  representation.
* [Voting Rights Act of 1965](https://en.wikipedia.org/wiki/Voting_Rights_Act_of_1965)
  (VRA)
  - How do you prove a district is legally mandated under Section 2.
  - Bottom line: does the minority group have less opportunity have less
    opportunities to elect representatives of its choice? A demographer looks at
    this.
  - Senate factors: history of voting-related discrimination. Other factors that
    dilute the minority vote.
* [California Voting Rights Act](https://en.wikipedia.org/wiki/California_Voting_Rights_Act) (CVRA)
  - Less costly, need not demonstrate the ability to draw
  - Only applicable in challenging at-large voting systems.
  - Requires pre-litigation demand letter. A jurisdiction then has a period of
    time to respond.
  - Caps pre-litigation fees at $30k.
* Voting History
  - *1790* - Immigrant (White) men
  - *1848* - Mexicans in acquired territories
  - *1870* - Black men - 15th amendment
  - *1920* - Women - 20th amendment
  - *1943* - Asian-Chinese immigrants - repeal of exclusion act
  - *1945* - Asian-Indian immigrants
  - *1952* - All Asian immigrants - capped immigration
  - *1965* - Protected right to vote - Voting Rights Act

[pellegrin_slides]: https://sites.tufts.edu/gerrymandr/files/2018/03/Pellegrini.pptx

<br>
### 02:50 - 30:40PM - *Ellen Veomett (St. Mary's) - [slides][veomett_slides]*
​**The Efficiency Gap, Voter Turnout, and the Efficiency Principle**

* In search of a metric to define gerrymandering?
  - Geometric tools and their issues
    * Boundary length to contained area (isoperimetric inequality). Issues with
      coastlines or other boundaries. Map zooming (Duchin and Tenner)
    * Compare district to some desired shape. Bad shapes are very similar to
      nice ones.
* Efficiency gap. A measure of partisan gerrymandering must satisfy two
  principles. `S(D, delta)` = seat share for party A, `V(delta)` = vote share for
  party A. `G(D, delta)` number such that the higher value means that the
  redistricting plan is more favorable to party A (this is the tool that does
  measurement).
  - EP1. No wasted votes
  - EP2. No not-wasted votes
* Facts/concerns about EG
  - If we consider only a single-district, it's volatile
  - Seems like it wouldn't work well for states with few districts
* EG doesn't support EP2, or EP1 for competitive elections (i.e., doesn't work
  for unequal turnout).
* For any rational numbers, `1/4 < V < 3/4` and `0 < S < 1`, there exists an
  election outcome data with vote share `V`, seat share `S` and `EG=0`.
* Don't compare EG across states or across different elections (historical time
  periods) for the same state.

[veomett_slides]: https://sites.tufts.edu/gerrymandr/files/2018/03/Veomett.pdf

<br>
### 03:50 - 04:40PM - *Karin Mac Donald (SWDB and UC Berkeley) and Denise Hulett (MALDEF)*
**Implementation Challenges and Race Discrimination in the Era of Algorithms**

* How is redistricting actually implemented?

<br>
### 06:00PM - 07:30PM - *Colleen Mathis (AZ Commission Chair), Wendy Underhill (National Conference of State Legislatures Redistricting Coordinator), California Commissioners: Angelo Ancheta (D), Vince Barabba (R), Cynthia Dai (D), and Michelle DiGuilio (I)*
**Panel Discussion - Independent Commissions and Redistricting Reform**

* Wendy
  - [NCSL](http://www.ncsl.org/)
  - Overview of states that use independent commissions or legislatures to
    handle redistricting.
  - Overview of redistricting commission adoption after each Census
  - Overview of states with citizens' initiatives
  - Overview of states with legislature introduction of commissions.
  - Reform - Beyond Commissions
    * Mixed record on independent commissions
    * Each state: Criteria, principles, guard-rails (all available on website)
    * Transparency, accountability, citizen input
* Colleen
  - Overview of
    [Arizona Independent Commission](https://www.azredistricting.org/) (created
    in 2000)
  - Citizen initiative to take away power from legislature and have an
    independent redistricting commission (Proposition 106).
  - 25% area of the land is Native American. Gerrymandered here to preserve the
    Hopi as a community of interest.
  - AZ is the only state with competitiveness as a criteria.
  - Five commissioners, ~6 million people, 2 Democrats, 2 Republicans, 1
    Independent. Independent is chosen and is the chair.
  - Public hearing process to hear about criteria and the draft map. Very public
    website.
  - What does Independent mean? It means that it's independent of the
    legislature. Provision in the Constitution for the legislature to remove a
    commissioner. Party line vote removed her from the position, but she was
    then reinstated by the State Supreme Court.
  - Map needs to pass preclearance by the Department of Justice.
  - AZ is now looking to expand the number of seats on the commission (possibly
    to include more independents).
  - "If you want a friend in redistricting, get a dog"
* [Angelo](http://wedrawthelines.ca.gov/bios.html)
  - [California Citizens Redistricting Commission](http://wedrawthelines.ca.gov/)
  - California: 5 Democrats, 5 Republicans, 4 Neither
  - Filled a lottery seat
  - Ranked constitutional criteria. Not included: competitiveness. Prohibitions:
    incumbency, candidacy, and party criteria.
* Michelle
  - Qualifications: impartial, appreciation for California's diversity,
    analytical skills, no conflicts of interest.
  - Long extensive interview process with veto option over names by the state
    legislature. Lottery process and then selection.
  - Description of listening tour in CA. Decisions are final and cannot be
    appealed by the legislature.
* Vince
  - Census director under Nixon and Carter
  - Fairness in redistricting; as well as an overview of the process the
    committee undertook.
  - Listening tour in Marysville: definitely included a large community of
    interest (Sikh's and Hmong), that otherwise would not have been uncovered
    and included without the tour (for at least one reason: religion is not
    included in the Census).
* Cynthia
  - Review: Assessing California's Redistricting Commission (from McGhee)
  - 2-1 voter approval of commission's work (via direct ballot)
  - CA independent redistricting has dramatically improved approval of the state
    legislature.
