# lol-win-analysis
Predicting League of Legends match outcomes from the first 10 minutes of Diamond-ranked games (Python, pandas, scikit-learn)

# League of Legends: What Decides the Game in the First 10 Minutes?

## Overview
Using about 10,000 Diamond-ranked solo queue games, I analyzed which early-game factors (first 10 minutes) are related to winning, and built a simple model to predict the match outcome.

## Data
[League of Legends Diamond Ranked Games (10 min)](https://www.kaggle.com/datasets/bobbyscience/league-of-legends-diamond-ranked-games-10-min) on Kaggle
- 9,879 games, 40 columns
- Target: `blueWins` (1 = blue team won, 0 = lost)
- Blue team win rate is 49.9%, so the data is balanced

## Key Findings
1. **Gold difference is the strongest signal.**
   In games the blue team won, it was ahead by about +1,270 gold at 10 minutes on average. In games it lost, it was behind by about -1,240.

2. **Objectives matter, especially dragons.**
   - First Blood: win rate 59.9% (taken) vs 39.7% (not taken)
   - Dragon: 64.1% vs 41.9% (+22 points)
   - Rift Herald: 59.5% vs 47.7% (+12 points)

3. **Destroying a tower early is a strong sign of winning.**
   Teams that destroyed 1 tower by 10 minutes won about 75% of the time (429 games). Games with 2+ towers had very high win rates, but there were only 35 such games, so I did not draw conclusions from them.

4. **The number of wards placed has almost no relation to winning.**
   Both winning and losing games averaged about 22.3 wards. However, this data cannot measure *where* or *when* wards were placed, which may still matter.

5. **The model predicts about 72% of games correctly.**
   A logistic regression model reached 71.8% accuracy on the test data, compared to about 50% for random guessing. Adding more features (CS, level, kill difference) did not improve accuracy, likely because that information is already included in gold difference.

## Limitations
- These results show correlation, not causation. For example, stronger teams may get First Blood *and* win, rather than First Blood causing the win.
- Only the first 10 minutes are included, so about 28% of games are comeback cases the model cannot predict.

## What I Learned
- Always compare results to a baseline (50% for random guessing)
- Be careful with small groups: a 100% win rate from 1 game means nothing
- Adding features only helps if they contain new information

## Tools
Python, pandas, matplotlib, scikit-learn, Google Colab, and generative AI (Claude, Gemini) for coding support
