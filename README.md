# What Happened To Our Electricity!?

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

<iframe src="assets/10-80-enrollment.html" width=800 height=600 frameBorder=0></iframe>

---

## Assessment of Missingness

Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

```py
print(counts[['Quarter', 'Count']].head().to_markdown(index=False))
```

| Quarter     |   Count |
|:------------|--------:|
| Fall 2020   |       3 |
| Winter 2021 |       2 |
| Spring 2021 |       6 |
| Summer 2021 |       4 |
| Fall 2021   |      55 |

---

## Hypothesis Testing


---
