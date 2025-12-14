# nlp-lab2
_By Ostap Trush_

I submit one ipynb with my best experiments (there were a lot) and scores for them. I only ran the last experiment for output in this ipynb as I was doing this lab over multiple days.

In the submissions folder are all the submission csvs for respective experiments.

## Data Analisys
From what I analyzed in ipynb - classes have agreat imbalance. Fear barely is anywhere as an emotion and categories influence emotions. Moreover all my models predicted categories better than emotions. And just avoiding the rare emotions is bad because for final grade all emotions are graded equally.

## The Winner
The winner was xlm-roberta-large with LORA + Oversampling + "cascading" + a small rule that forces gratitude to be happiness to clear some hallucinations + no validation.
- LORA because I wanted to train a larger model fast and fit it on kaggle.
- Oversampling, because some emotion samples like Fear were rare.
- "cascading" is me feeding the category as an input for emotion training as well as they are dependent. Then do the same at predictions.
- Since almost all gratitude feedbacks were happiness (liek 99%) I just force it to avoid hallucinations.
- All that allowed me to break 0.7 with a really imbalanced dataset which is good.
- Finally, turning off 10% validation and having more train data allowed me to break from 0.69 to 0.7. (from one of the other experiments that got me 0.69.

## Others
ukr-roberta-base with weighted inclusion of class imbalance.
Result: 0.62

mdeberta-base with oversampling and weighted cross-entropy.
Result: 0.65

xlm-roberta-large + oversampling + lora + 10% validation
Result: 0.69

All the code for them is in the ipynb and csvs are in the repo.

## What I also tried
- ensembling: did not work and was training too long with hallucinations of fear everywhere.
- more rules: bad for average f1 score because I had more fear and sadness.
- teacher geenrating more labels from test set: The model performance was just not that good to proceed on that.

## Conclusion
LORA is cool and saved the day. Also feeding some data points like category to predict other like emotion also helped. I had fun:) And as of writing this readme, I am top 3! I hope it stays this way.
