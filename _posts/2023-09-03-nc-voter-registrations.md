---
layout: post
title: Anticipating 2024: NC Voter Registrations since 2020
tags: commentary life
---

In 2020, the news coverage of my Southern home state --- North Carolina --- was
too horserace-y, given that it was the most important election of our
lifetimes. I spent much of that late Summer and Fall looking at voter
demographic and registration data to make sense of what was going on.

I just looked at voter registrations since the end of 2020 to see if trends from
that period are holding for 2024 (tldr: they've changed!). I'll continue to
update those here every few months.

# Background

To win an election, you must first register a lot of voters. Elections also
matter: they have [real practical outcomes][ncdems_flip] for voters and so
voters should care about voter registration and the momentum around it. Southern
states have structural advantages in the Electoral College. Some states (like
NC) may be diversifying demographically and politically faster than others, but
are impacted by the [crazy gerrymandering][nc_map] of the state legislative
districts.

To [recap 2020][nc_wiki], Biden lost NC to Trump by about 74k votes, or about
1.3% of votes cast. State Democrats also lost the state court, lost State House
seats, and lost the opportunity to push fairer electoral maps following the 2020
Census. I donated to the Long Leaf Pine Slate, which lost 2 of 17 races they
backed! Nationally: the Democratic Party's ground organizing campaign focused on
mail-in voting and prohibited in-person organizing until September 2020 due to
obvious COVID-19 concerns. The NC GOP, as far as I could tell, simply adopted
social distancing and masking policies for in-person registrations well before
the Democratic Party.

You can kind of see this in the accumulated voter registration totals leading up
to the election:

![registration count and changes](https://mookerji.github.io/nc-2020-dat/assets/images/statewide-registrations-changes-by-party.png){:class="img-responsive"}

[nc_map]: https://projects.fivethirtyeight.com/redistricting-2022-maps/north-carolina/

# 2024 ... As of September 2023

A few graphs here that I think are interesting:

![statewide-by-county](https://github.com/mookerji/mookerji.github.io/assets/353255/df5d6444-7ea5-44d3-94b5-9949f17d4ede){:class="img-responsive"}
![statewide-per-month](https://github.com/mookerji/mookerji.github.io/assets/353255/5af0c855-af8c-463e-a7b9-4a8e6b9c0015){:class="img-responsive"}
![statewide-cumulative-all-counties](https://github.com/mookerji/mookerji.github.io/assets/353255/cc4075d2-d9b5-44e3-8e49-7096a0a2c354){:class="img-responsive"}
![statewide-cumulative-without-wake-mecklenburg](https://github.com/mookerji/mookerji.github.io/assets/353255/c12a1791-96bb-4bd4-87df-abcfdc62e6a8){:class="img-responsive"}


Totals:

| Party      | All    | w/o Meck/Wake |
|:-----------|-------:| -------------:|
| DEM        | 307628 | 223729 |
| REP        | 309917 | 267982 |
| THIRD      |  13252 | 10428  |
| UNA        | 561085 | 432133 |

Some takeaways:

- Unaffiliated voters still dominate the voter registrations (as they have for
  some time), but new Democratic and GOP voter registrations since December 2020
  are surprisingly even! The gap between newly registered Republicans and
  Democrats is less than 3k.
- As of August 2024, the 'No Labels' Party is [official in NC][old_north_nlb],
  with about 400 people registered, of which 52 are in Wake County.
- If you exclude Wake and Mecklenburg Counties --- the biggest urban Democratic
  counties from the data --- the gap isn't *that huge* (around 43k). I would
  have expected something huge, given that organizing efforts have focused on
  these larger counties.

[nc_wiki]: https://en.wikipedia.org/wiki/2020_United_States_presidential_election_in_North_Carolina
[ncdems_flip]: https://www.nytimes.com/2023/07/30/us/inside-the-party-switch-that-blew-up-north-carolina-politics.html
[elect_project]: https://www.electproject.org/home
[old_north_state]: http://www.oldnorthstatepolitics.com/
[registrations_online]: https://www.nbcnews.com/politics/2020-election/campaigning-during-coronavirus-dnc-takes-organizing-line-n1171811
[old_north_nlb]: http://www.oldnorthstatepolitics.com/2023/08/a-too-early-look-at-no-labels.html

# Methodology

I love that it's possible for anyone to do this kind of analysis at home using
open source tools. To generate these graphs above I used [Pandas][pandas] and a
[Jupyter notebook][jupyter] and you can follow a similar process for your
state. In the following, I'll talk through the process using the NC voter file,
using similar analysis to the one I posted [here][nc-2020-dat] in 2020.

[nc-2020-dat]: https://mookerji.github.io/nc-2020-dat/
[pandas]: https://pandas.pydata.org/
[jupyter]: https://jupyter.org/

## Getting the Data

The NC Board of Elections maintains a [page][nc_voter_file] where you can
download the the public state voter file. Some quick links:

- [Voter file][nc_voter_dl]:
- [Voter file schema][nc_voter_layout]

If you're setup with AWS and use the terminal, you can download these files
directly from where they're hosted:

```bash
$ aws s3 cp s3://dl.ncsbe.gov/data/ncvoter_Statewide.zip .
$ aws s3 cp s3://dl.ncsbe.gov/data/layout_ncvoter.txt .
```

## Normalize the Data

The statewide voter file is **really big**: about 3.6G and almost 8.4M rows (as
of 09-03-2023). I didn't want to exhaust my RAM while plotting data, so I parsed
and simplified this dataset to something smaller: new, active registrations
since the last general election, voter demographics, and city/county data.

```python
import pandas as pd

# Parse the data
df = pd.read_csv('ncvoter_Statewide.txt',
                   delim_whitespace=True,
                   on_bad_lines='skip',
                   encoding_errors='ignore',
                   parse_dates=['registr_dt'],
                   infer_datetime_format=True)

# Normalize and save subset of interest
to_keep = ['registr_dt', 'voter_status_desc',
           'birth_year','race_code', 'ethnic_code', 'gender_code',
           'party_cd', 'county_desc', 'res_city_desc']
start_date = '2020-12-01'
newly_registered = df[to_keep][df['registr_dt'] > start_date]
newly_registered = newly_registered[newly_registered['voter_status_desc'] == 'ACTIVE']

# Group all third parties, including 'No Labels' (!)
newly_registered['party_cd'] = newly_registered['party_cd'].replace(['LIB', 'NLB', 'LIB', 'GRE'], 'THIRD')

# Save the subset
newly_registered.to_csv('ncvoter_Statewide_post-2020-12-01.csv', index=False)
```

The `layout_ncvoter.txt` includes a schema for the file. Like many voter files
everywhere, it contains a huge amount of identifying information that would
normally be considered private in any other context. This is the subset for the
columns I selected above:

```
------------------------------------------------------------------------------------
name                    data type          description
------------------------------------------------------------------------------------
county_desc             varchar(15)        County name
voter_status_desc       varchar(25)        Registration status description
registr_dt              char(10)           Registration date
res_city_desc           varchar(60)        Residential city name
race_code               char(3)            Race code
ethnic_code             char(3)            Ethnicity code
party_cd                char(3)            Registered party code
gender_code             char(1)            Gender/sex code
birth_year              char(4)            Year of birth
```

The resulting table `newly_registered` is much smaller and less creepy: about
1.2M records for a 62MB CSV file.  The contents (from `newly_registered.head()`)
looks like this:

|    | registr_dt          | voter_status_desc   |   birth_year | race_code   | ethnic_code   | gender_code   | party_cd   | county_desc   | res_city_desc   |
|---:|:--------------------|:--------------------|-------------:|:------------|:--------------|:--------------|:-----------|:--------------|:----------------|
|  0 | 2023-05-09 00:00:00 | ACTIVE              |         1945 | W           | NL            | M             | REP        | ALAMANCE      | GRAHAM          |
|  1 | 2023-05-17 00:00:00 | ACTIVE              |         1967 | W           | NL            | F             | REP        | ALAMANCE      | HAW RIVER       |
|  2 | 2021-04-15 00:00:00 | ACTIVE              |         2003 | W           | NL            | M             | REP        | ALAMANCE      | GIBSONVILLE     |
|  3 | 2021-05-21 00:00:00 | ACTIVE              |         1981 | B           | NL            | M             | UNA        | ALAMANCE      | BURLINGTON      |
|  4 | 2022-10-07 00:00:00 | ACTIVE              |         1992 | W           | NL            | F             | REP        | ALAMANCE      | MEBANE          |

## Analyzing the Data

### County Aggregates

To get the county aggregates you:

- group by county name and party registration
- count those groups
- pivot counts by party registration and total for each county

```python
# Color coding
COLORS = {'DEM': 'blue', 'REP': 'red', 'THIRD': 'green', 'UNA':'purple'}
parties = ['DEM', 'REP', 'THIRD', 'UNA']

# Group, count, and pivot
# Note: following .count(), all columns have the same value, so choose any one and rename to count
groupby = ['county_desc', 'party_cd']
total_by_county = newly_registered.groupby(groupby).count()['birth_year'].reset_index().rename(columns={'birth_year': 'count'}).pivot_table(values='count', index='county_desc', columns='party_cd')
total_by_county['ALL'] = total_by_county.sum(axis=1)
total_by_county = total_by_county.sort_values(by='ALL')
total_by_county

ax = total_by_county[parties.plot.bar(stacked=True, color=COLORS_
ax.set_title('Statewide New Voter Registrations Since 12-01-2020',)
ax.set_xlabel('County')
ax.set_ylabel('Registrations (count)')
plt.tight_layout()
plt.savefig('statewide-by-county.png')
```

Some sample data:

| county_desc   |   DEM |   REP |   THIRD |   UNA |   ALL |
|:--------------|------:|------:|--------:|------:|------:|
| TYRRELL       |    65 |    65 |     nan |   104 |   234 |
| HYDE          |    93 |   131 |       2 |   160 |   386 |
| GRAHAM        |    73 |   402 |       9 |   287 |   771 |
| GATES         |   204 |   330 |      18 |   428 |   980 |
| WASHINGTON    |   283 |   255 |       9 |   438 |   985 |


### Weekly Registration

This will produce demographic statistics similar to what you'd find on the NC
Registration Statistics [page][nc_stats]. To get these demographics you group by
registration week and demographic feature (race/ethnicity, gender/sex, and party
registration) and then count.

```python
groupby = [pd.Grouper(key='registr_dt', freq="M"),'race_code', 'ethnic_code', 'gender_code', 'party_cd']
monthly_voter_stats = newly_registered.sort_values('registr_dt').groupby(groupby).count()['birth_year'].reset_index().rename(columns={'birth_year': 'count'})
monthly_voter_stats
```

Some sample data:

|    | registr_dt          | race_code   | ethnic_code   | gender_code   | party_cd   |   count |
|---:|:--------------------|:------------|:--------------|:--------------|:-----------|--------:|
|  0 | 2020-12-31 00:00:00 | A           | HL            | M             | UNA        |       2 |
|  1 | 2020-12-31 00:00:00 | A           | NL            | F             | DEM        |      53 |
|  2 | 2020-12-31 00:00:00 | A           | NL            | F             | REP        |      25 |
|  3 | 2020-12-31 00:00:00 | A           | NL            | F             | THIRD      |       2 |
|  4 | 2020-12-31 00:00:00 | A           | NL            | F             | UNA        |      72 |


[results-2020]: https://mookerji.github.io/nc-2020-dat/
[nc_voter_file]: https://www.ncsbe.gov/results-data/voter-registration-data
[nc_stats]: https://vt.ncsbe.gov/RegStat/
[nc_voter_dl]: https://dl.ncsbe.gov.s3.amazonaws.com/data/ncvoter_Statewide.zip
[nc_voter_layout]: https://dl.ncsbe.gov.s3.amazonaws.com/data/layout_ncvoter.txt
[nc_2020_dat_git_repo]: https://github.com/mookerji/nc-2020-dat
