by Michelle Tong (m1tong.edu)

---

## Introduction

Drawing insights from a comprehensive power outage dataset, the project embarks on an intriguing journey – one that melds data science with real-world impact. At its core lies a sophisticated **classification model** meticulously crafted to unveil the reasons behind power disruptions.

Picture a realm where our model, armed with the finesse of multiclass classification, navigates the intricate labyrinth of outage causes. With remarkable accuracy, it attributes a definitive label from among the seven distinct categories ingrained in our dataset.

Guided by the beacon of **CAUSE.CATEGORY,** I deliberately opt for simplicity and representation. This selection isn't arbitrary; it's a strategic decision that marries clarity with effectiveness. By distilling the complexity of outage origins into seven succinct categories, I equip the model to comprehend these intricacies without unnecessary convolution.

Consider the significance of comprehension – a revelation encapsulated in the identification of a larger cause like "severe weather." This newfound understanding becomes a compass, delineating whether an outage is a predictable outcome or an unforeseen quirk of fate. My aspiration morphs into prevention, and with the model as the harbinger of knowledge, I stand better equipped to thwart future disruptions.

As architects of this algorithmic marvel, my chosen yardstick for evaluation is **accuracy**. In a landscape where true positives and true negatives take precedence, accuracy emerges as a palpable gauge of success in unraveling this puzzle. Each precise classification propels us closer to nullifying the enigma, resonating with impact and progress in the language of accuracy.

With every prediction, the model illuminates the shadows concealing the intricacies of power outages. This endeavor isn't confined to classification alone; it's a transformative journey towards resilience. A symphony of technology and consequence orchestrated to ensure that when illumination falters, it does so with the promise of rapid restoration.

---

## Cleaning and EDA

Guided by the need to enhance the dataset's relevance and applicability to my project, I undertook the task of data cleaning within Excel. This encompassed the removal of columns and rows that lacked a meaningful connection to the project's objectives. Now, let's take a look at the power outage dataset after this cleaning process. This will provide us with a clearer starting point for our exploration.

|   YEAR |   MONTH | U.S._STATE   | POSTAL.CODE   | NERC.REGION   | CLIMATE.REGION     |   ANOMALY.LEVEL | CLIMATE.CATEGORY   | OUTAGE.START.DATE   | OUTAGE.START.TIME   | OUTAGE.RESTORATION.DATE   | OUTAGE.RESTORATION.TIME   | CAUSE.CATEGORY     | CAUSE.CATEGORY.DETAIL   |   HURRICANE.NAMES |   OUTAGE.DURATION |   DEMAND.LOSS.MW |   CUSTOMERS.AFFECTED |   RES.PRICE |   COM.PRICE |   IND.PRICE |   TOTAL.PRICE |   RES.SALES |   COM.SALES |   IND.SALES |   TOTAL.SALES |   RES.PERCEN |   COM.PERCEN |   IND.PERCEN |   RES.CUSTOMERS |   COM.CUSTOMERS |   IND.CUSTOMERS |   TOTAL.CUSTOMERS |   RES.CUST.PCT |   COM.CUST.PCT |   IND.CUST.PCT |   PC.REALGSP.STATE |   PC.REALGSP.USA |   PC.REALGSP.REL |   PC.REALGSP.CHANGE |   UTIL.REALGSP |   TOTAL.REALGSP |   UTIL.CONTRI |   PI.UTIL.OFUSA |   POPULATION |   POPPCT_URBAN |   POPPCT_UC |   POPDEN_URBAN |   POPDEN_UC |   POPDEN_RURAL |   AREAPCT_URBAN |   AREAPCT_UC |   PCT_LAND |   PCT_WATER_TOT |   PCT_WATER_INLAND |
|-------:|--------:|:-------------|:--------------|:--------------|:-------------------|----------------:|:-------------------|:--------------------|:--------------------|:--------------------------|:--------------------------|:-------------------|:------------------------|------------------:|------------------:|-----------------:|---------------------:|------------:|------------:|------------:|--------------:|------------:|------------:|------------:|--------------:|-------------:|-------------:|-------------:|----------------:|----------------:|----------------:|------------------:|---------------:|---------------:|---------------:|-------------------:|-----------------:|-----------------:|--------------------:|---------------:|----------------:|--------------:|----------------:|-------------:|---------------:|------------:|---------------:|------------:|---------------:|----------------:|-------------:|-----------:|----------------:|-------------------:|
|   2011 |       7 | Minnesota    | MN            | MRO           | East North Central |            -0.3 | normal             | 2011-07-01 00:00:00 | 17:00:00            | 2011-07-03 00:00:00       | 20:00:00                  | severe weather     | nan                     |               nan |              3060 |              nan |                70000 |       11.6  |        9.18 |        6.81 |          9.28 | 2.33292e+06 | 2.11477e+06 | 2.11329e+06 |   6.56252e+06 |      35.5491 |      32.225  |      32.2024 |         2308736 |          276286 |           10673 |           2595696 |        88.9448 |        10.644  |       0.411181 |              51268 |            47586 |          1.07738 |                 1.6 |           4802 |          274182 |       1.75139 |             2.2 |      5348119 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 |
|   2014 |       5 | Minnesota    | MN            | MRO           | East North Central |            -0.1 | normal             | 2014-05-11 00:00:00 | 18:38:00            | 2014-05-11 00:00:00       | 18:39:00                  | intentional attack | vandalism               |               nan |                 1 |              nan |                  nan |       12.12 |        9.71 |        6.49 |          9.28 | 1.58699e+06 | 1.80776e+06 | 1.88793e+06 |   5.28423e+06 |      30.0325 |      34.2104 |      35.7276 |         2345860 |          284978 |            9898 |           2640737 |        88.8335 |        10.7916 |       0.37482  |              53499 |            49091 |          1.08979 |                 1.9 |           5226 |          291955 |       1.79    |             2.2 |      5457125 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 |
|   2010 |      10 | Minnesota    | MN            | MRO           | East North Central |            -1.5 | cold               | 2010-10-26 00:00:00 | 20:00:00            | 2010-10-28 00:00:00       | 22:00:00                  | severe weather     | heavy wind              |               nan |              3000 |              nan |                70000 |       10.87 |        8.19 |        6.07 |          8.15 | 1.46729e+06 | 1.80168e+06 | 1.9513e+06  |   5.22212e+06 |      28.0977 |      34.501  |      37.366  |         2300291 |          276463 |           10150 |           2586905 |        88.9206 |        10.687  |       0.392361 |              50447 |            47287 |          1.06683 |                 2.7 |           4571 |          267895 |       1.70627 |             2.1 |      5310903 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 |
|   2012 |       6 | Minnesota    | MN            | MRO           | East North Central |            -0.1 | normal             | 2012-06-19 00:00:00 | 04:30:00            | 2012-06-20 00:00:00       | 23:00:00                  | severe weather     | thunderstorm            |               nan |              2550 |              nan |                68200 |       11.79 |        9.25 |        6.71 |          9.19 | 1.85152e+06 | 1.94117e+06 | 1.99303e+06 |   5.78706e+06 |      31.9941 |      33.5433 |      34.4393 |         2317336 |          278466 |           11010 |           2606813 |        88.8954 |        10.6822 |       0.422355 |              51598 |            48156 |          1.07148 |                 0.6 |           5364 |          277627 |       1.93209 |             2.2 |      5380443 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 |
|   2015 |       7 | Minnesota    | MN            | MRO           | East North Central |             1.2 | warm               | 2015-07-18 00:00:00 | 02:00:00            | 2015-07-19 00:00:00       | 07:00:00                  | severe weather     | nan                     |               nan |              1740 |              250 |               250000 |       13.07 |       10.16 |        7.74 |         10.43 | 2.02888e+06 | 2.16161e+06 | 1.77794e+06 |   5.97034e+06 |      33.9826 |      36.2059 |      29.7795 |         2374674 |          289044 |            9812 |           2673531 |        88.8216 |        10.8113 |       0.367005 |              54431 |            49844 |          1.09203 |                 1.7 |           4873 |          292023 |       1.6687  |             2.2 |      5489594 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 |


## Baseline Model

In crafting our foundational model, we chose the robust Random Forest algorithm as our guiding beacon. This sophisticated classifier amalgamates multiple decision trees, each rooted in distinct subsets of our dataset. By doing so, it illuminates the intricate landscape of power outages, predicting their underlying causes.

The brilliance of this algorithm shines through in its ability to tackle two significant challenges: overfitting and the enigma of unknown data. An ingenious built-in technique empowers our model to seamlessly accommodate the unknown as a potential prediction outcome. This visionary approach alleviates concerns about unfamiliar cause categories within our training dataset, fortifying the precision of our predictions.

Our selection of influential features was a deliberate endeavor. Nominal categories such as STATES, CLIMATE.REGION, CLIMATE.CATEGORY, CAUSE.CATEGORY, and CAUSE.CATEGORY.DETAIL were chosen to underpin our training model. To seamlessly integrate these features, we harnessed the power of the OneHotEncoding transformer, preparing them for a seamless fit within our model's framework.

Results from our model's training unveiled an accuracy of 0.6834782608695652 for our training data and 0.6171875 for our test dataset. Notably, our model demonstrated a balanced performance, with training and validation accuracies standing in close proximity. This harmony lends confidence that overfitting was diligently mitigated.

With an average accuracy of 61.7\% in predicting cause categories based on features, our model showcases commendable performance. Yet, it's crucial to acknowledge that our reliance on nominal categories might have introduced limitations, potentially constraining predictive precision. To further refine our model's accuracy, we recognize the potential for enhancement through the inclusion of more intricate data and features.

Indeed, our baseline model stands as a testament to its capability in confronting the unfamiliar. As a multiclass classifier, it breaks free from the confines of predefined categories. It stands ready to predict not only the seven known cause categories but also an expanding spectrum that could span 8, 10, or even 100 different possibilities – all contingent on the availability of a richer dataset. As emphasized before, our model's architectural cornerstone, the pipeline object, serves as a bulwark against the unknown. The OneHotEncoder within the ColumnTransformer gracefully embraces unknown data, enriching the model's adaptability and resilience during training.


<iframe src="assets/10-80-enrollment.html" width=800 height=600 frameBorder=0></iframe>

---

## Assessment of Missingness


---

## Hypothesis Testing


---
