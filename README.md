# Research: Changing Opinions Towards Cryptocurrency Under Rising Cost of Living
**Course:** MACS 30200 Perspectives in Computational Research   
**Author:** Mintao Wei (mintao@uchicago.edu)
## Research Question
1. Do people become more favorable of cryptocurrency when the cost of living rises?
2. How does the polarization of the public opinions towards cryptocurrency evolve when the cost of living rises?
## Summary
The research aims to explore the time serial correlation between the rising cost of living and changes in public risk perception on Twitter, especially of cryptocurrency. Additionally, this study will depict the opinion dynamics in terms of how the polarization evolves using computational social network methods.
## Key Concepts and Proxies
### Cost of Living
  The cost of living is measured by [monthly Consumer Price Index (CPI-U) from U.S.Bureau of Labor Statistics](https://www.bls.gov/cpi/)
### Opinions towards Cryptocurrency    
  I would retrieve the sentiments from the bitcoin-related tweets (see [source](https://www.kaggle.com/datasets/alaix14/bitcoin-tweets-20160101-to-20190329?sort=votes)) and use the Percentage of positive/negative tweets towards cryptocurrency as the proxy for the cost of living (Bovet et al., 2018).
### Opinion Dynamics and Polarization   
  Guided by Bovet et al. (2018), Bravo et al.,(2012), Lerman & Ghosh (2010), I construct three methods to describe the opinion dynamics:
  1. The distribution of the number of likes & retweets for those cryptocurrency-favored tweets
  2. Sentiment Polarity Score: Positiveness(Average number of positive words/scores per tweet in the period) - Negativeness(Average number of negative words/scores per tweet in the period)
  3. \**Community Detection + Polarization Visualization using Subgraphs (if data permits)*
## Model and Methods   
**1. Granger Causality**
    I will examine the causal predictability of past monthly CPI on future percentage of crypto-endorsed tweets above and beyond historical tweet sentiments, using the Granger Causality Test described in Mooijman et al. (2018). 
    
**2. Vector Autoregressive Models (VAR)**
    Since depending solely on Granger causality has the potential to result in temporal gaps between rising costs of living and resulting opinion shifts. Furthermore, Granger causality analysis does not attempt to quantify the magnitude of effects, which is important in our context. I would use First-order Vector Autoregressive (VAR) models, which predict each variable by all variables including itself at the previous time point, as the next step to study quantitatively how the cost of living fluctuation over the past several months predicts the future trend in public opinions towards cryptocurrency. This VAR model is widely used to analyze the dependencies across time in such data and are already used extensively in applied research (Bringmann et al., 2013; Fisher et al., 2017; Groen et al., 2019; Pe et al., 2015; Snippe et al., 2017).

## Note
### How to Replicate the Findings
To replicate the analysis and produce all of the figures as well as analyses, run the notebook in the code folder of this repository via the instructions in the file. The code was written in Python 3.7.13 on Google Colab. and all of its dependencies can be fulfilled by running the `!pip install` code lines embedded. You can also refer to the requirements.txt file in this repository for details.

It is worth noting that due to [Github's hard limit on the file size](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github), only **a sample snapshot** of the Bitcoin-related Twitter was uploaded. To abide by the Twitter developer policy, I removed the user name attributes and tweet IDs. The complete dataset can be found [here](https://www.kaggle.com/datasets/alaix14/bitcoin-tweets-20160101-to-20190329?sort=votes).  

If you use this repository for a scientific publication, it would be appreciated if you cited the Zenodo DOI ([to be updated](https://github.com/zenodo/zenodo/issues/1814)) or the following reference format: 
> Wei, Mintao, Changing Opinions Towards Cryptocurrency Under Rising Cost of Living, (2022), GitHub repository, https://github.com/macs30200-s22/replication-materials-mintaow/
