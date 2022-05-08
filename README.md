[![DOI](https://zenodo.org/badge/482983391.svg)](https://zenodo.org/badge/latestdoi/482983391)

# Research: Examining Opinions Change Towards Cryptocurrency When Cost of Living Rises
**Course:** MACS 30200 Perspectives in Computational Research   
**Author:** Mintao Wei (mintao@uchicago.edu)
## Research Question
Do people become more favorable  cryptocurrency when the cost of living rises?
## Abstract
Examining 13 million bitcoin-related tweets on Twitter, the research presents an empirical Granger Causality test and vector autoregressions (VAR) analysis of whether people have become more favourable of bitcoins when the cost of living rises. The study shows that the granger causality effect of living cost on the opinion dynamics to adopt bitcoins is statistically strong and unidirectional, which is quantitatively approximated by an interweaving of short-term suppressions and long-term promotions. People are first cautious, but gradually change to support cryptocurrencies. Meanwhile, it is worth noting that the bitcoin endorsement atmosphere is more likely the result of a growing community rather than increasing fanaticism, and the social media public is far from reaching a consensus. ## Key Concepts and Proxietowards
### Cost of Living
  The cost of living is measured by [monthly Consumer Price Index (CPI-U) from U.S.Bureau of Labor Statistics](https://www.bls.gov/cpi/)
### Opinions towards Cryptocurrency    
  Guided by Mooijman et al. (2018), I use the sentiment classification extracted from bitcoin related tweets (unfavorable/favorable) to measure the attitudes toward bitcoin. Specifically, I used a lexicon-based approach by employing the VADER (Valence Aware Dictionary and sEntiment Reasoner) toolkit to extract the sentiments toward bitcoin from 13.1 million bitcoin related tweets. Followed the approach in Lerman and Ghosh (2010), I will use the percentage of bitcoin-favored tweets from all the bitcoin-related tweets and the corresponding sentiment intensity scores as proxies for the opinion trend toward bitcoin on the Twitter network. 

## Hypotheses
Faced with rising living costs, driven by the aspiration to escape poverty, people tend to become more risk-taking and thus more favorable toward cryptocurrencies on social media platforms.


## Model and Methods   
**1. Granger Causality**
    I will examine the granger causality effect of past CPI monthly difference on future percentage of crypto-endorsed tweets using the method described in Mooijman et al. (2018). 
    
**2. Vector Autoregressive Models (VAR)**
    Since depending solely on Granger causality has the potential to result in temporal gaps between rising costs of living and resulting opinion shifts. Furthermore, Granger causality analysis does not attempt to quantify the magnitude of effects, which is important in our context. I would first-order Vector Autoregressive (VAR) model, which has the lowest AIC, and another VAR model with lag order of 12 to observe the longer-term correlation. The VAR model is widely used to analyze the dependencies across time in such data and are already used extensively in applied research (Bringmann et al., 2013; Fisher et al., 2017; Groen et al., 2019; Pe et al., 2015; Snippe et al., 2017).

# Findings
## 1. Cost of Living
  Despite temporary sliding down in the second half of certain years (e.g. 2014, 2015, 2018), the cost of living generally rises up steadily from a long-term perspective.![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_cost_lineplot.png)
  
## 2. Cryptocurrency Market Trend & Sentiment
  ![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_crypto_lineplot_1.png) The activeness of people participating in bitcoin related discussion on Twitter drastically climbed up after 2017, when the market prices rocket up since 2017.![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_crypto_lineplot_2.png)
 This might imply a strong correlation of social discussion and market prices, which needs to be controlled when studying the time serial effect of living cost.
 
## 3. Relationship between Crypto Sentiments and Cost of Living
  To explore the correlation between bitcoin sentiments and the cost of living, I visualized the dynamics of the two corresponding proxies: the percentage of Bitcoin favoring tweets and CPI in Figure 3(a). the month-over-month differences were also mapped to exclude the effect of intrinsic time serial trends. As demonstrated in Figure 3(a), in spite of the volatility in the percentage of positive sentiments, we can observe a persistent upward growing trend after 2017 if evaluating from the long-term perspective. This resembles the steadily rising momentum in CPI and suggests a latent positive correlation between the two variables over a longer period. This is reiterated by the evidence in the shaded band of Figure 3(b), where the movement in the positive sentiments correspond to the CPI fluctuations in the past 3 months. Therefore, we hypothesize that there exists a positive correlation at a time lag of around 3 months. Meanwhile, due to the high volatility, we might also expect a negative correlation implied by the direct impact of CPI variations in a short time window.  ![image](https://github.com/macs30200-s22/replication-materials-mintaow/blob/main/graph/eda_btc_cpi_lineplot_2.png)
*Figure 3: Relationship between Cryptocurrency Sentiments and Cost of Living. (a) the relationship between percentage of BTC-favoring tweets and CPI in raw values. (b) the relationship between the two variables in month-over-month difference form. *
  Furthermore, the p-value for the granger causality test of the CPI Month-over-Month Diff (X) on the Percentage of BTC Favoring Tweets Month-over-Month Diff(Y) is 0.0001, while the reverse direction is not statistically significant. We are confident to reject the null hypothesis and conclude that historical values of the CPI month-over-month differences exert a statistically significant effect on the current Bitcoin-favoring sentiments.

  The below two findings from VAR(1) and VAR(12) provide quantitative evidence that the influence of the cost of living on the public crypto-favoring sentiments is a mix of short-term suppression and long-term promotion, with the market price fluctuation controlled. The rising cost of living tends to first result in negative emotions such as “fear of loss”. People become even more concerned about falling into poverty that they choose to stay against risky projects. However, the ever-increasing living cost induces risk-taking impulses. Individuals have “nothing left to lose” and therefore aspire to escape from the poverty trap through risky moves such as adopting cryptocurrencies (Chivers, 2017).

**Table 1: Results for VAR(1): Y = perc_btc_favor_diff**
=========================================================================
                        coefficient     std.error      t-stat      prob
-------------------------------------------------------------------------
const        	            0.018687       0.013995       1.335       0.182
L1.cpi_month_diff  	     -0.037909       0.018219       -2.081     0.037**
L1.perc_btc_favor_diff   -0.307041       0.100277       -3.062    0.002***
L1.avg_price_month_diff   				              CONTROL
=========================================================================
Note: L1 is the abbreviation for the lag order of 1.

**Table 2: Results for VAR(12): Y = perc_btc_favor_diff**
=========================================================================
                        coefficient      std.error      t-stat      prob
-------------------------------------------------------------------------
const              	     -0.014005       0.030447      -0.460      0.646
L1.cpi_month_diff        -0.023166       0.030373      -0.763      0.446
L2.cpi_month_diff        -0.012412       0.034534      -0.359      0.719
L3.cpi_month_diff         0.105482       0.035465       2.974   0.003***
L4.cpi_month_diff        -0.039477       0.038854      -1.016      0.310
L5.cpi_month_diff         0.033086       0.036615      -0.904      0.366
L6.cpi_month_diff        -0.034169       0.035268      -0.969      0.333
L7.cpi_month_diff         0.044045       0.033459       1.316      0.18
L8.cpi_month_diff         0.010820       0.034138       0.317      0.751
L9.cpi_month_diff         0.050473       0.034082       1.481      0.139
L10.cpi_month_diff        0.037386       0.034309       1.090      0.276
L11.cpi_month_diff       -0.000724       0.033486      -0.022      0.983
L12.cpi_month_diff       -0.021027       0.029415      -0.715      0.475
L1~L12.perc_btc_favor_diff   			            CONTROL
L1~L12.avg_price_month_diff   			          CONTROL
=========================================================================
Note: L1~L12 is the abbreviation for the lag order of 1~12.


## Note
### How to Replicate the Findings
To replicate the analysis and produce all of the figures as well as analyses, run the notebook in the code folder of this repository via the instructions in the file. The code was written in Python 3.7.13 on Google Colab. and all of its dependencies can be fulfilled by running the `!pip install` code lines embedded. You can also refer to the requirements.txt file in this repository for details.

It is worth noting that due to [Github's hard limit on the file size](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github), only **a sample snapshot** of the Bitcoin-related Twitter was uploaded. To abide by the Twitter developer policy, I removed the user name attributes and tweet IDs. The complete dataset can be found [here](https://www.kaggle.com/datasets/alaix14/bitcoin-tweets-20160101-to-20190329?sort=votes).  

If you use this repository for a scientific publication, it would be appreciated if you cited the Zenodo DOI ([to be updated](https://github.com/zenodo/zenodo/issues/1814)) or the following reference format: 
> Wei, Mintao, Changing Opinions Towards Cryptocurrency Under Rising Cost of Living, (2022), GitHub repository, https://github.com/macs30200-s22/replication-materials-mintaow/
