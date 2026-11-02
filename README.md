# stc tv (Jawwy) Streaming Analytics

Analysis of viewing behaviour on the stc tv (Jawwy) streaming platform, plus a content recommender. Two questions drive it:

1. **Does picture quality (HD vs SD) change how people watch?**
2. **What should we recommend to a viewer, based on what similar viewers watched?**

## Notebooks

| Notebook | What it does |
|---|---|
| [`01_hd_vs_sd_viewing_analysis.ipynb`](01_hd_vs_sd_viewing_analysis.ipynb) | Compares HD and SD viewing: share of views, watch time, content availability by year, top programs and genres, and user segmentation (HD-only / SD-only / both) by engagement |
| [`02_recommender_system.ipynb`](02_recommender_system.ipynb) | Item-based collaborative filtering: a user × program rating matrix and cosine similarity between programs |

## Key findings

**Content availability drives volume.** About **86% of titles are available only in SD**; only 14% exist in HD. SD therefore accounts for most total viewing. The number of HD titles was also noticeably lower in 2018 than in 2017.

**HD titles are watched more deeply.** Although HD is only 14% of the catalogue, **average watch hours per HD title are more than double** those of SD titles, which suggests picture quality increases depth of consumption.

**The most engaged users switch between qualities.** Segmenting users into HD-only, SD-only and both:
- Users who watch in **both** qualities have the most views, the most total hours, and the widest range of programs.
- High engagement is linked to *flexibility* (choosing quality by connection or content type), not to being an HD-only viewer.

**Viewing is concentrated but not dominated.** In the top 10 programs by watch time, the leader takes about 19% and the top three together about 40%. Animation and family titles are strongly represented.

### Recommendations
- Make switching between HD and SD seamless, since the users who switch are the most loyal.
- Prioritise HD versions of the most-watched titles, where HD is linked to longer viewing.

## Recommender example

Top 5 programs recommended to viewers who watched **Moana** (cosine similarity):

| # | Program | Similarity |
|---|---|---|
| 1 | Trolls | 0.572 |
| 2 | Surf's Up: WaveMania | 0.529 |
| 3 | The Mermaid Princess | 0.493 |
| 4 | The Boss Baby | 0.449 |
| 5 | The Jetsons & WWE: Robo-WrestleMania! | 0.439 |

All five are animated family titles, so the similarity is picking up a coherent audience.

## Data

The stc tv datasets are **not included** in this repository. To run the notebooks, place the files in a `data/` folder:
- `data/stc_tv_clean.xlsx` (sheet `Final_Dataset`): one row per viewing session with program, genre, class, duration, HD flag, date and anonymised user ID
- `data/stc TV Data Set_T3.xlsx`: user-program ratings

## Tech

Python · pandas · NumPy · matplotlib · Plotly · scikit-learn (cosine similarity)
