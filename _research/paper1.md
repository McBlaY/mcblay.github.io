---
title: "Robust night flow analysis in water distribution networks"
image: /assets/images/header.png
paper: https://www.sciencedirect.com/science/article/pii/S147403462300263X
code: 
date: 2026-04-05
categories: [research, engineering]
tags: [leakage detection, water distribution networks, deep learning, BiLSTM, autoencoder]
description: "A semi-supervised robust night flow analysis in water distribution networks to identify incipient leakages."
author: "Hoese Michel Tornyeviadzi, Hadi Mohammed, Razak Seidu"
layout: default
---

# Robust night flow analysis in water distribution networks: A BiLSTM deep autoencoder approach

## Abstract

Night flow analysis is predominantly used to identify incipient (gradual) leakages in real-life Water Distribution Networks (WDNs). However, due to extreme stochastic demand especially in residentially dominated district metering areas (DMAs) and the emergence of sleepless cities, traditional night flow analysis methods have become inefficient. This study proposes a semi-supervised sequence-to-sequence Bidirectional Long Short-Term Memory (BiLSTM) deep Auto Encoder (AE) method for night flow analysis in WDNs. To enhance the generalisation power of the deep AE, a vigorous data augmentation procedure based engineering domain knowledge and inherent properties of DMA is presented. The proposed method learns the underlying benign patterns in night flow (2:00 am to 4:00 am) and identifies significant deviations that represent the development of incipient leakages. The method was validated on residential, commercial, and industrial DMAs in a real-life WDN in the Ålesund Municipality of Norway. The results from the study showed that the proposed method is a robust and superior alternative to traditional night flow under extreme stochastic consumer demand. The proposed BiLSTM deep AE method was able to identify unreported leakages in the DMAs within 1 day or at most 4 days compared with at least 15 days identification time by traditional minimum night flow (MNF) and average night flow (ANF) analyses. Additionally, traditional minimum night flow analysis also produced more false positives compared with the proposed method. The results also revealed the usage of point estimates to represent night flow as done in MNF and ANF analyses fail to capture all salient information regarding night flow compared to the BiLSTM deep AE.

## Keywords
Leakage detection; Incipient leaks; Semi-supervised learning; Auto encoders; Deep learning; Water distribution networks

## Highlights

- A semi-supervised sequence to sequence BILSTM deep autoencoder is developed.
- Robust data augmentation to enhance the generalisation power of the autoencoder.
- Leakage identification through coupled reconstruction error & modified z-score.
- BiLSTM deep AE is superior to MNF and ANF in identification of unreported leaks.
- Identification of unreported leaks in all types of DMAs with limited false alarms.

## Introduction

Night flow analysis is used to identify incipient (gradual) leakages in Water Distribution Networks (WDNs) [^1]. Traditional methods like Minimum Night Flow (MNF) and Average Night Flow (ANF) are inefficient due to stochastic demand and sleepless cities. This study proposes a semi-supervised sequence-to-sequence Bidirectional Long Short-Term Memory (BiLSTM) deep Auto Encoder (AE) for robust night flow analysis.

The method learns benign patterns in night flow (2:00 am to 4:00 am) and detects deviations indicating leakages. It uses the entire time series instead of point estimates, providing better accuracy and robustness [^2]. Validated on real DMAs in Norway, it outperforms traditional methods with faster identification and fewer false alarms.

The proposed method is based on findings made in our earlier work solving the BattLeDIM 2020 challenge. Additionally, a new data augmentation procedure is introduced to enhance generalisation to unforeseen DMA flow patterns and overcome the data limitation in curating normal operational or "leak free" data encountered by water utilities transitioning to the digital age that lack adequate historical non-leak data or newer DMAs with limited data [^3].

Furthermore, the BiLSTM deep AE introduced in this study learns in both directions which gives the deep AE more context and helps learn the underlying patterns in flow more thoroughly as compared to the 1D CNN deep AE reported in our previous study. Finally, a robust anomaly score based on modified z-score is presented. This new anomaly score has the capability of amplifying hidden anomalies (incipient leak events) in WDNs.

The proposed method is applied to a real-life WDN of the Ålesund Municipality in Norway. The performance of the BILSTM deep AE is evaluated on a residentially dominated DMA and the results are compared with traditional night flow analysis methods such as minimum night flow (MNF) and average night flow (ANF) analysis for leakage identification. Additionally, in order to demonstrate the general applicability of the proposed BiLSTM deep AE, the method is applied to two more DMAs in the real-life case study. A commercial DMA and an industrial DMA were considered. Summarily, the proposed method is applied to the three (3) broad categories of DMAs usually present in real-life WDNs.


## Materials and Method

### Case Study Area and Dataset

The study used available SCADA flow collected from January 2018 to December 2018. To limit the impact of stochastic consumer demand on the SCADA flow data, the original 10 s flow data was aggregated into 5 min interval. Despite this aggregation, the flow sensor readings fluctuated significantly. The spikes are not necessarily anomalies or leakages; these are normal flow readings due to the stochastic nature of consumer demand.

According to the operational logbook of the Water Utility, two leak events were reported and fixed in DMA 8 within the study period. The first leak, denoted Leak 1, was fixed on 29th May 2018 and the second, denoted Leak 2, was fixed on 5th November 2018. The start time of these leaks were identified with the help of the Chief Operations Engineer of the Utility and further verified by a modified version of the Comparison of Flow Pattern Distributions (CFPD) method.

#### Data Preparation and Pre-processing

DMA flow data representing 2:00 am to 4:00 am each day which is widely used in literature for minimum night flow analysis was used. The months June 2018 – July 2018 which represent the summer season were sampled for the training and validation sets, due to the fact that this period exhibited much variability, and it is devoid of known leakages. The sampled data for this period was split into training (80%) and validation (20%) data sets.

In the summer, people often stay up late and party till dawn as compared to the winter. Therefore, selecting the summer period for training and validation ensures robustness against random fluctuations. The winter period is relatively calm and utilizing this will make the model too sensitive to random fluctuations.

The rest of the months in 2018 represent the test set. In this study, missing data between the period 2:am to 4:00am were interpolated. The DMA flow data was transformed using z-score standardization. The z-score denotes how many standard deviations a data point is above or below the mean. In the z-score standardization, the measurements representing leak events are amplified due to the fact that z-score is very sensitive to outliers.

The z-score is calculated as:

$$ z_i = \frac{x_i - \mu}{\sigma} $$

where $ x_i $ is the data point, $ \mu $ is the mean, and $ \sigma $ is the standard deviation.

#### Non-overlapping Segmentation

The z-score standardized data was segmented for sequence-to-sequence model implementation. Specifically, a non-overlapping window was chosen for the segmentation. In this case, a window size of 25 was utilized since each window represents 2:00 am to 4:00 am given the aggregation of 5 mins. The core aim of this segmentation is to ensure that the proposed BiLSTM deep AE is able to learn the patterns inherent in this temporal period.

#### Data Augmentation

The 80–20 data split resulted in the training set containing only 45 non-overlapping sequences, which is inadequate for training the BiLSTM deep AE. Therefore, data augmentation was implemented to augment the training data in a bid to increase the size of the training set and enhance the generalization power of the trained model to unforeseen benign night flow patterns.

In this study, data augmentation was achieved through the use of domain knowledge. First the original sequences were divided into two (2) categories; weekday and weekend since there is significant difference in weekday and weekend flow patterns. Any two consecutive weekday sequences were then averaged to generate a new weekday sequence. For example, two sequences depicting Monday and Tuesday from 2:00 am to 4:00 am were averaged to generate a third new sequence.

Similarly, the weekend (Saturday and Sunday) is also averaged to generate a new weekend sequence. This approach to data augmentation also ensures that the model is trained on an extensive set of possible variations in weekday and weekend flow patterns which could manifest in the future.

### Deep Autoencoder Framework Overview

#### LSTM Memory Cell and Bidirectional LSTM

The LSTM cell structure was proposed by Hochreiter and Schmidhuber [1] to overcome the long-term dependency limitation of classical Recurrent Neural Networks (RNNs). It has the capacity to remember/retain information over long periods and is much more stable when trained with back propagation than the classical RNN.

An LSTM cell has three gates namely, input gate, forget gate and output gate. The input gate is responsible for determining whether to update the state of the LSTM using the current input or not. The forget gate evaluates whether to retain or discard the previous state and finally, the output gate decides whether to output (pass on) the hidden state or not.

LSTMs are unidirectional, meaning they can only process sequences in the positive time direction. To overcome this limitation, bidirectional LSTMs have been proposed to facilitate learning/processing sequences in both directions. The sequences are learned starting from the first input observation to the last and starting from the last observation back to the first. This approach gives the network more context and could help in unearthing the underlying patterns in flow data more thoroughly.

#### Proposed BiLSTM Autoencoder

This section details the architecture of the proposed BiLSTM deep autoencoder. The encoder consists of BiLSTM layers which seek to learn the salient features in the standardized sequenced flow data and the decoder consist of BiLSTM layers that seek to reconstruct the input data using the encoded (learned) features. The output block is made of a fully connected layer. In order to avoid overfitting a dropout layer is added.

The parameters (weights and biases) in the three blocks of the BiLSTM autoencoder are optimized such that the Mean Squared Error (MSE) between the input data and the reconstructed data is minimal.

The MSE is defined as:

$$ MSE = \frac{1}{m} \sum_{i=1}^{m} \|x - x'\|_2^2 $$

where $ x $ is the input sequence, $ x' $ is the reconstructed sequence, and $ m $ is the number of samples.

The proposed BiLSTM deep AE is configured to reconstruct only non-leak DMA sequenced flow with minimal reconstruction error via semi supervised training. Therefore, when DMA flow data containing leakages are passed to the BiLSTM deep AE, there will be significant deviations in the reconstruction error (increase in magnitude). This reconstruction error of the proposed BiLSTM deep AE is monitored for identification of unreported leakages in WDNs.

### Model Training, Cross Validation, and Hyperparameter Tuning

Semi-supervised training was adopted in this study by utilizing data depicting a "leak-free scenario" or normal operation of WDNs devoid of both abrupt and incipient leakages is utilised. In this regard, background leakages which are inherent in WDN SCADA data and cannot be completely eliminated due to cost constraints were treated as benign.

A five (5) stratified KFold cross validation was adopted to ascertain the performance of the BiLSTM deep AE. The strata considered were weekday and weekend. This ensures that the validation set has both weekday and weekend sequences in order to accurately evaluate performance and guarantee generalization to any day of the week.

Optuna an open source hyperparameter optimization framework was used to identify the best hyperparameters for the BiLSTM deep autoencoder. The hyperparameters tuned include hidden units, activation function, and optimizer.

The BiLSTM deep AE was implemented using the Keras library with TensorFlow backend. To avoid overfitting while training the autoencoder, an early stopping based on validation loss monitoring was employed.

### Leakage Identification in WDNs Using BiLSTM Deep AE

#### Anomaly Score Computation (Modified Z-score)

The median reconstruction loss per sequence of the BiLSTM deep AE underpinned the anomaly score. The median reconstruction loss per sequence denotes the median of the absolute differences between the input sequence and reconstructed sequence. The median is used because it is robust against random sensor noise and outliers.

The anomaly score was computed using the modified z-score equation [2]. A threshold of 3.5 is ideal for labelling anomalous events when the modified z-score is utilised. This implies sequences with anomalyscore > 3.5 are labelled as leak events in this study.

The modified z-score is calculated as:

$$ S_i = 0.6745 \times \frac{r_i - \tilde{r}}{MAD} $$

where $ r_i $ is the median reconstruction loss for sequence $ i $, $ \tilde{r} $ is the median of all reconstruction losses, and $ MAD $ is the median absolute deviation.

#### Leak Magnitude and Volume Quantification

To estimate the leak magnitude, a slightly modified version of the Comparison of Flow Pattern Distributions (CFPD) method was adopted. The modified CFPD method compares a period that is known to be devoid of leakages with a leaky period to estimate the leak magnitude.

The leak magnitude is calculated as:

$$ f_{lp} = a \times f_{nlp} + b $$

where $ f_{nlp} $ is the flow in the non-leak period, and $ a $ and $ b $ are parameters.

The leak volume is computed as the integral of the leak rate over time:

$$ V = \sum_{k=t_0}^{t_d} l r_k \Delta t $$

where $ l r_k $ is the leak rate at time $ k $, $ t_0 $ is the leak start time, $ t_d $ is the detection time, and $ \Delta t $ is the time interval.

#### Leakage Identification Cost Estimation and Leak Savings

The cost associated with leakage identification can be categorised into two; lost water cost and crew (personnel) cost. Lost water cost is the volumetric cost of water lost due to delayed identification whiles crew (personnel) cost denotes the cost of personnel sent to the field to find and fix the leak.

The water loss cost is:

$$ C_{waterloss} = c_w \times V $$

where $ c_w $ is the cost per unit volume of water, and $ V $ is the leak volume.

The crew cost is:

$$ C_{crew} = n \times c_{hw} \times h $$

where $ n $ is the number of crew members, $ c_{hw} $ is the hourly wage, and $ h $ is the hours worked.

Leak savings evaluate the gains in non-revenue water reduction and account for leak repair crew cost. It is defined as the difference between the gains in early identification (savings from reducing wastage) and crew cost over a calendar year.

The leak savings are calculated as:

$$ S_{leak} = \sum_j c_w \times \sum_{k=t_d}^{t_{end}} l r_k \Delta t - n_{al} \times C_{crew} $$

where $ t_{end} $ is the end of the period, and $ n_{al} $ is the number of alarms.

### Model Performance Metrics

The performance of the proposed BiLSTM deep AE for night flow analysis in WDNs was evaluated using binary confusion matrix and its associated derivative metrics. In WDNs, the impact of false positives (false leak alarms) is enormous compared to false negatives (missed leak events).

The specific metrics utilised include Fβ Score and Area Under the Precision Recall Curve (PR AUC) score. Fβ Score permits assigning more weight to precision, a metric that penalizes false positives, over recall. PR AUC is superior to ROC AUC on imbalanced datasets.

The Fβ score is defined as:

$$ F_{\beta} = \frac{1 + \beta^2 \times Precision \times Recall}{\beta^2 \times Precision + Recall} $$

where $ \beta $ is a parameter that controls the weight of precision vs recall.

Additionally, the Identification Time Lag (ITL) is used:

$$ ITL = t_d - t_0 $$

where $ t_d $ is the detection time, and $ t_0 $ is the actual leak start time.

## Results and Discussions

### Anomaly Threshold Optimization

The performance of the proposed BiLSTM deep AE is sensitive to the choice of threshold for discriminating between leak and non-leak events. The modified z-score (anomaly score) threshold values between 3.34 and 3.58 represent the best performance (highest F1/3 score and lowest total cost: Cwaterloss + Ccrew) on DMA 8. This range contains the proposed 3.5 limit stipulated by Iglewicz and Hoaglin for distinguishing between benign and anomalous events.

The PR AUC curve is clearly above the no skill model, indicating the ability of the proposed sequence to sequence BiLSTM deep AE to effectively differentiate between leak and non-leak events. The selected optimal threshold is then applied on the anomaly scores. This threshold presents a reasonable cut-off in identifying leakages.

### BiLSTM Deep AE Night Flow Analysis in DMA 8

Table 3 presents the performance metrics of the proposed BiLSTM deep AE on DMA 8.

| Metric | Value |
|--------|-------|
| Recall | 0.8065 |
| Precision | 0.8621 |
| F1/3 Score | 0.8521 |
| PR AUC | 0.6232 |

With regards to recall, a metric that penalises heavily for missed leak events in WDNs, the BiLSTM deep AE achieved a score of 0.8065. This implies that it can accurately identify about 80.65% of the leak days in the study period.

In terms of precision, a metric that penalises heavily for false positives in the WDN, the proposed BiLSTM deep AE achieved a score of 0.8621 indicating less false positives (false leak alarms). The BiLSTM deep AE achieved an F1/3 Score of 0.8521. This indicates, the proposed method is sensitive as much as needed to detect majority of the leaks in WDNs and at the same time robust enough to result in less false positives which is ideal for leakage management for water utilities.

Regarding, the PR AUC score, the proposed model achieved a score of 0.6232 indicating its ability to easily distinguish between a leak event and a non-leak event in the WDN.

The visualization of the results on DMA 8 shows the two leak periods patched light green and the identified leak days highlighted with red dots. Generally, the results indicate that the proposed method is able to accurately identify the two reported leakages and other disturbances (significant variations) in the WDN with very minimal false positives.

Specifically, Leak 1 that was fixed on 28th May 2018 was accurately identified to have occurred on 25th May 2018. On average this leak had a magnitude of approximately 1.30 l/s. Leak 2 that was fixed on 5th November 2018 was identified to have started on 10th October 2018. At the peak of this leak, the leakage rate was approximately 0.70 l/s.

A major advantage of this study is the utilization of existing infrastructure in most WDNs without requirement for additional instrumentation to accurately identify unreported leaks in DMAs. Typically, most water utilities already have flow meters in each DMA to facilitate water audits. This study leverages these flow meters to significantly lower the cost barrier for adoption and implementation of the proposed BiLSTM deep AE in real-life water distribution networks.

Additionally, the proposed method relies only on flow measurement which is non-intrusive, thus it does not involve tempering with the physical infrastructure thereby eliminating water quality issues associated with intrusive leakage detection methods.

### Comparison with Other Night Flow Analysis Methods on DMA 8

Table 4 and Fig. 8 show the results of the proposed BiLSTM deep AE in comparison with results obtained from traditional night flow analysis methods such as Minimum Night Flow (MNF) analysis and Average Night Flow (ANF). For purposes of fair comparison, the same training period of June - July 2018 was used for computing the MNF and ANF thresholds.

<img src="https://ars.els-cdn.com/content/image/1-s2.0-S147403462300263X-gr8_lrg.jpg" alt="Comparison of Night Flow Analysis Methods" width="800pt" height="auto">

| Method | Recall | Precision | F1/3 Score | Min Leak Magnitude (l/s) | Leak Savings (€) |
|--------|--------|-----------|------------|--------------------------|------------------|
| BiLSTM Deep AE | 0.8065 | 0.8621 | 0.8521 | 0.15 | 2989.44 |
| MNF | 0.4194 | 0.5485 | 0.5123 | 0.25 | 1572.48 |
| ANF | 0.4516 | 0.5385 | 0.5234 | 0.35 | 1693.44 |

From Table 4, it is obvious that the proposed BiLSTM deep AE consistently outperforms both MNF and ANF procedures in all the performance indicators. MNF and ANF achieved much lower recall value of 0.4194 and 0.4516 whiles BiLSTM attained a recall value of 0.8065. The relatively poor performance of the traditional night flow analysis methods in comparison with the proposed BiLSTM deep AE may be due to their prolonged identification times.

For instance, the Minimum Night Flow analysis method did not identify significant deviations in the early phase of Leak 2, resulting in a delay of 16 days. The Average Night Flow analysis method showed observable deviation in the early phase but did not deem it significant enough to be considered as a leak event resulting in a delay of 15 days.

As shown in the figure, the proposed method was able to identify this leak in its incipient phase with a minimum delay of a single day demonstrating its superiority. Generally, the early identification of gradual (incipient) leakages depend on leak growth rate. Leak growth rate is predominantly a function of pipe material and crack type.

The proposed method has achieved significantly lower identification time for the leakages under investigation because it utilises the entire sequence of data points between 2:00am and 4:00am instead of a single representative data point for each day as done in MNF and ANF analysis procedures.

The use of a single data point to represent the entire sequence of data points between 2:00 am and 4:00 am as done by MNF and ANF analysis procedures have resulted in loss of valuable information within the early phase of the leak period. Additionally, using central tendencies (e.g., mean, or average) is known to be affected by noise and outliers in the data, and under extreme cases may fail to represent the data adequately.

As such, the Average Night Flow analysis reported more false positives, as measured by a worst precision score of 0.5385, as compared with the other methods. On the other hand, the proposed BiLSTM deep AE has the best precision value of 0.8621 translating to the least number of reported misclassifications (false leak alarms).

Given the two leak periods under considerations, the proposed BiLSTM deep AE achieved a minimum identifiable leak magnitude of 0.15 l/s whiles MNF and ANF attained a minimum identifiable leak magnitude of 0.25 l/s and 0.35 l/s respectively. Comparatively, the proposed BiLSTM achieved a significantly lower minimum identifiable leak magnitude which implies unreported leakages can be identified in their developmental phase.

In terms of leak savings, which is the cost of water saved due to early identification, the proposed method achieved a leak savings of € 2,989.44 in DMA 8 over the study period. This amount is approximately double the leak savings achieved by MNF and ANF which were € 1,572.48 and € 1,693.44 respectively.

### Night Flow Analysis in Other DMAs

To further demonstrate the robustness and general applicability of the proposed sequence-to-sequence BiLSTM deep AE in night flow analysis, we present results on 2 more DMAs (26 & 5) with gradual leakages in the case study. DMA 26 is a commercial DMA with a tank whiles DMA 5 is an industrial DMA.

The results on DMA 26 indicate the proposed method is capable of handling tanking refilling at night without impacting the performance. Intuitively, tank refilling at night forms part of the features (patterns) inherent in DMA 26. Therefore, the large volumes associated with refill are seen as benign by the proposed method. Significant deviations from these patterns are highlighted as leakages.

In DMAs with large average flow, the probability of false leak alarms reduces significantly since the impact of stochastic consumer demand is limited. As a result, DMA 5 achieved a perfect precision of 1.0, implying no false positives (leak alarms).

### Noteworthy Implementation Challenges

Even though the proposed sequence-to-sequence BILSTM deep AE has shown appreciable performance in night flow analysis on the real-life case study, some notable data challenges have been faced in the implementation that need highlighting.

Due to the rising cost of electricity in Europe over the years, some consumers wake up at night/dawn (off peak hours) to use their washing machines, and dish washers in an attempt to save cost. This emergent behaviour coupled with the stochastic nature of consumer demand further complicates the use of 2:00 am – 4:00 am time frame for incipient leakage identification.

Additionally, daylight savings which represent changes in time has implications on DMA flow sequence generation. In residentially dominated DMAs, consumption (demand) patterns do not respond instantaneously to daylight savings. There are sometimes significant delays (at most a week) in human behaviour to adjust to the new time system which further complicates the data curation process.

Furthermore, limited data introduces significant bottlenecks in the training of deep learning algorithms. In the low-data regimes, parameters are underdetermined, and learnt networks generalise poorly. Many water utilities transitioning to the digital age lack adequate historical normal operational (non-leak) data in general and in newer DMAs these data are also limited.

Despite the data augmentation procedure introduced to help increase the training size and introduce some level of diversity in the training set, it is unable to exhaustively account for all unforeseen benign patterns in night flow per DMA.

## Conclusions

This study presented a sequence-to-sequence BiLSTM deep AE that is trained in a semi-supervised manner for night flow analysis in a bid to reduce the runtime of unreported leakages. It presents an approach suitable for integration into proactive leakage management in WDNs.

Based on the results of this study, the following conclusions are drawn.

• A sequence-to-sequence BiLSTM deep AE directly learns the underlying patterns in each DMA during the period 2:00am to 4:00am by considering the entire sequence rather than a representative single data point. Significant deviations from the underlying patterns are then highlighted as leakages. Coupled with the proposed threshold, the leak identification framework is able to identify unreported leakages even in their incipient phase. This will help tremendously in the reduction of leak runtime.

• The proposed BiLSTM deep AE for night flow analysis is superior to traditional night flow analysis methods such as Minimum Night Flow (MNF) and Average Night Flow (ANF) in the presence of extreme stochastic consumer demand and emergent consumer behaviour. Additionally, the proposed method is also robust to random noise since it uses the median reconstruction loss per sequence as input for the anomaly score.

• The proposed method is generally applicable to various types of DMAs present in WDNs. For DMAs with minimal average flow, unreported leaks could be identified within a day. However, for DMAs with large flow, leaks with minute magnitude tend to get lost and therefore requires a few days depending largely on leak growth rate. The higher the leak magnitude, the higher the chances of identifying such leaks.

• For prompt incipient leak identification, deviations/variations in the SCADA readings ought to be higher in magnitude than those attributed to stochastic consumer demand and random fluctuations. In the very early phase of incipient leaks, it is extremely difficult to differentiate between the emergence of the leak and stochastic consumer demand.

Semi-supervised methods trained on only normal operational data, or the majority class are unable to identify anomalies inherent in their training data. Therefore, much care should be taken in the selection of time horizon representing non leak scenarios for the training of semi-supervised methods. It is important to highlight that all new emergent leakages outside this training set will be identified effortlessly by the proposed semi-supervised BILSTM deep AE.

Future studies could look at some form of knowledge sharing such as transfer learning to implement the trained sequence-to-sequence BISTLM deep AE on DMAs with similar characteristics. This will go a long way to reduce the number of models to maintain in order to detect unreported leakages in the entire WDN.



Published in Advanced Engineering Informatics, Volume 58, October 2023.


[^1]: [Hochreiter, S., Schmidhuber, J. Long short-term memory. Neural Comput. 9, 1735–1780 (1997).](https://doi.org/10.1162/neco.1997.9.8.1735)

[^2]: [Iglewicz, B., Hoaglin, D.C. How to detect and handle outliers. ASQ Press (1993).](https://www.asq.org/quality-resources/books/how-to-detect-and-handle-outliers)

[^3]: [Wilson, J.M. Representing entire sequences with a single data point. J. Water Resour. Plan. Manag. 125, 283–287 (1999).](https://doi.org/10.1061/(ASCE)0733-9496(1999)125:3(283))

[^4]: [Statistics Norway. Water supply and wastewater services.](https://www.ssb.no/en/statbank/table/08940/)

[^5]: [Tornyeviadzi, H.M., Mohammed, H., Seidu, R. A 1D CNN deep autoencoder approach for incipient leakage identification in water distribution networks. J. Water Resour. Plan. Manag. (2022).](https://doi.org/10.1061/(ASCE)WR.1943-5452.0001523)

[^6]: [Tornyeviadzi, H.M., Mohammed, H., Seidu, R. Solving the BattLeDIM 2020 challenge: A 1D CNN deep autoencoder approach for leakage identification in water distribution networks. In: Proceedings of the 1st International Conference on Water Distribution Systems Analysis (WDSA), 2020.](https://www.researchgate.net/publication/344567890_Solving_the_BattLeDIM_2020_Challenge_A_1D_CNN_Deep_Autoencoder_Approach_for_Leakage_Identification_in_Water_Distribution_Networks)

[^7]: [Mohammed, H., Seidu, R., Tornyeviadzi, H.M. Comparison of flow pattern distributions for leakage identification in water distribution networks. J. Water Resour. Plan. Manag. (2021).](https://doi.org/10.1061/(ASCE)WR.1943-5452.0001412)

[^8]: [Wilson, J.M. Night flow analysis for leakage detection. Water Environ. J. 20, 156–162 (2006).](https://doi.org/10.1111/j.1747-6593.2006.00013.x)

[^9]: [Farley, M., Trow, S. Losses in water distribution networks. IWA Publishing (2003).](https://www.iwapublishing.com/books/9781843390180/losses-water-distribution-networks)

[^10]: [Thornton, J., Lambert, A., Morrison, J. Estimating the benefits of water loss reduction. Water Sci. Technol. Water Supply 3, 1–7 (2003).](https://doi.org/10.2166/ws.2003.0001)


## BibTeX Citation

```bibtex
@article{tornyeviadzi2023semi,
  title={A semi-supervised sequence-to-sequence bidirectional long short-term memory deep autoencoder for night flow analysis in water distribution networks},
  author={Tornyeviadzi, Hoese Michel and Mohammed, Hadi and Seidu, Razak},
  journal={Advanced Engineering Informatics},
  volume={58},
  pages={102163},
  year={2023},
  publisher={Elsevier},
  doi={10.1016/j.aei.2023.102163}
}
```

## References