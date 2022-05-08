[![DOI](https://zenodo.org/badge/482983391.svg)](https://zenodo.org/badge/latestdoi/482983391)

# Research: Examining Opinions Change Towards Cryptocurrency When Cost of Living Rises
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
## Hypotheses
1. **H1:** Faced with rising living costs, people tend to become more risk-taking and thus less antagonistic to cryptocurrencies on social media platforms.
2. **H2:** When the cost of living rises, the crypto-favoring thoughts and opinions are liked and retweeted more and thus spread faster across the social network, resulting in a more distinct polarization.

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

# Preliminary Findings
## 1. Cost of Living
  Despite temporary sliding down in the second half of certain years (e.g. 2014, 2015, 2018), the cost of living generally rises up steadily from a long-term perspective.![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_cost_lineplot.png)
  
## 2. Cryptocurrency Market Trend & Sentiment
  ![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_crypto_lineplot_1.png) The activeness of people participating in bitcoin related discussion on Twitter drastically climbed up after 2017, when the market prices rocket up since 2017.![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_crypto_lineplot_2.png)
 This might imply a strong correlation of social discussion and market prices, which needs to be controlled when studying the time serial effect of living cost.
 
## 3. Relationship between Crypto Sentiments and Cost of Living
  The time serial plots identify multiple time ranges when the month-over-month fluctuations of percentage of BTC favoring tweets and CPI are very similar to each other (e.g. 2015/04~2018/03). This initial finding suggests that the cost of living might be time serial correlated with the dynamics of positive opinions towards cryptocurrencies at a very short lag.![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_btc_cpi_lineplot_1.png)

  In addition, generally, people tend to engage more with bitcoin-favoring tweets from 2012 to 2019. When the cost of living climbs up at a higher speed, the average number of likes and retweets per bitcoin favoring tweet also spikes. However, further work needs to be done to exclude the confounding effect of external bitcoin market movement and people's overall activeness in talking about bitcoins (not just those tweets endorsing cryptocurrencies).   ![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_btc_cpi_lineplot_2.png)

  When the market price fluctuation is controlled, we observed a positive time serial correlation between cost of living in the t-2 time frame and the positive sentiments towards cryptocurrency in time t.  
![image](https://user-images.githubusercontent.com/71967604/165677436-84c75060-39e2-4ef5-9a83-52141921e42f.png)
