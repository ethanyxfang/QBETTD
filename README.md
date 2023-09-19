# QBETTD
QQ Browser Event Topic Tracking Dataset

## Short Information
There are events $e$ and topics $\mathcal{G}$. A topic contains at most five events covering the same topic $\mathcal{G} = \{e_{g}^1,\cdots,e_{g}^k\}, k\leq5$. The event inside a topic is called topic event $e_{g}$ and a novel event that hasn't been linked to a topic is called a new event $e_n$. 

QBETTD dataset consists of samples of event-topic pairs  $(e^i_n, \mathcal{G}^i) \in \mathcal{D}$. Specifically, $e^i_n$ is the new event needed to match $\mathcal{G}^i$ in the $i$-th sample. For both the new event or topic events $e=\{T_e,s_e\}$, it contains a short title sequence $T_e$ and a timestamp $s_e$ in DATETIME (example of timestamp: 1970-01-01 00:00:00) format.

QBETTD encompasses a total of 13,967 samples, meticulously assembled from 10,884 events and 421 timelines (topics), spanning a time period from April 2021 to mid-September 2021. Each sample has a new event and up to 5 events extracted from a news topic timeline. The final dataset for the experiment consists of 12,967 training samples and 1,000 testing samples.

For more information, please refer to [paper link to be added]

## Sample Details
The QBETTD dataset contains 13,967 samples with fields shown as below:

| idx | Field  | Description                                                    |
|:---:|:------:|:---------------------------------------------------------------|
|  1  |   id   | unique identifier for each sample                              |
|  2  |  tid   | topic id, indicate which topic the topic events were extracted |
|  3  |  ts0   | timestamp on when the new event happens                        |
|  4  | title0 | title for new event                                            |
|  5  |  ts1   | timestamp on when the topic event 1 happens                    |
|  6  | title1 | title for topic event 1                                        |
|  7  |   ⋯    | ⋯                                                              |
|  8  |  ts5   | timestamp on when the topic event 5 happens                    |
|  9  | title5 | title for topic event 5                                        |
| 10  | score1 | score by annotator 1                                           |
| 11  | score2 | score by annotator 2                                           |
| 12  | score3 | score by annotator 3                                           |
| 13  |  avg   | score average taken from all 3 annotators                      |
| 14  |   sd   | score standard deviation taken from all 3 annotators           |

## Annotation Details

The annotation of the QBETTD dataset is done by three separate groups of people. Each group scores all samples.

While conducting annotation, the new event and topic events for one sample are shown to annotators. And the annotator needs to consider the main entity, action (behavior), time, and background mentioned in the events and give a 0-4 score. 

| Score | Meaning          |
| :---: | :--------------- |
|   0   | Irrelevance      |
|   1   | Low relevance    |
|   2   | Some relevance   |
|   3   | Good relevance   |
|   4   | Strong relevance |

And the detailed standard for these aspects is listed below:

- Main entity: The events should cover the same main entity, the main entity can be a person (e.g. US president), an object (e.g. new mobile phone), or a noun (e.g. COVID-19 pandemic).
- Action: This aspect is about the action by the main entity or the behavior the main entity shows. (e.g. US president participated in COP-26; The launch of the new mobile phone; COVID-19 pandemic cases increase). And the action/behavior should be the same or in order across the events.
- Background: The background adds scope to the events. The events should mention the same region, or share the same background knowledge.
- Time: The event should happen in the same tight time range, or if the events last for a long time, the timestamp should be in pattern.

If all aspects are fulfilled for the new event and the topic events, the sample should be labeled as strong relevance (4).  Conversely, if all aspects are not the same, the label is Irrelevance (0). If the sample partially meets some of the criteria, a deduction in score should be applied accordingly. Finally taking the average score from three groups of annotators can increase the confidence of the scoring.

Besides, we supplied a collection of annotated instances accompanied by rationales for the assigned scores, aimed at facilitating the annotators' alignment with the annotation criteria. We provide five examples shown below:

<div class="table*">
<table>
<thead>
<tr class="header">
<th style="text-align: left;">title (translated into English)</th>
<th style="text-align: center;">timestamp</th>
<th style="text-align: center;">score</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td colspan="3" style="text-align: center;">Topic events</td>
</tr>
<tr class="even">
<td style="text-align: left;">Construction of Chinese Space Station (CSS) kicked off</td>
<td style="text-align: center;">2020-05-06 09:55:36</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="odd">
<td style="text-align: left;">The CSS will be officially deployed</td>
<td style="text-align: center;">2020-09-27 14:13:37</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="even">
<td style="text-align: left;">China will carry out 11 launch missions to build the CSS in the next two years</td>
<td style="text-align: center;">2020-10-07 07:04:34</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="odd">
<td style="text-align: left;">18 countries are approved to enter the CSS</td>
<td style="text-align: center;">2020-10-28 21:07:22</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="even">
<td style="text-align: left;">China has fully shifted to the CSS orbital construction phase</td>
<td style="text-align: center;">2021-03-04 09:01:15</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="odd">
<td style="text-align: left;">The Tianhe core module of the CSS will launch</td>
<td style="text-align: center;">2021-03-14 09:44:33</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="odd">
<td style="text-align: left;">The rocket carrying the Tianhe core module has moved to the launch area</td>
<td style="text-align: center;">2021-04-23 10:44:32</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="even">
<td style="text-align: left;">CSS core module launches</td>
<td style="text-align: center;">2021-04-29 08:36:03</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="odd">
<td style="text-align: left;">The core module of the CSS successfully launched</td>
<td style="text-align: center;">2021-04-29 12:07:44</td>
<td style="text-align: center;">-</td>
</tr>
<tr class="even">
<td colspan="3" style="text-align: center;">New events</td>
</tr>
<tr class="odd">
<td style="text-align: left;">4 International Space Station (ISS) astronauts return to Earth</td>
<td style="text-align: center;">2021-05-02 16:37:05</td>
<td style="text-align: center;">0</td>
</tr>
<tr class="even">
<td style="text-align: left;">The CSS Telescope is scheduled to launch in 2024</td>
<td style="text-align: center;">2021-06-20 21:44:02</td>
<td style="text-align: center;">1</td>
</tr>
<tr class="odd">
<td style="text-align: left;">CSS will be built with three rooms, two halls and hall room</td>
<td style="text-align: center;">2021-06-18 19:29:00</td>
<td style="text-align: center;">2</td>
</tr>
<tr class="even">
<td style="text-align: left;">The CSS is planned to be completed in two years</td>
<td style="text-align: center;">2021-05-18 21:02:19</td>
<td style="text-align: center;">3</td>
</tr>
<tr class="odd">
<td style="text-align: left;">CSS’s on orbital construction phase is in full swing</td>
<td style="text-align: center;">2021-04-29 13:04:03</td>
<td style="text-align: center;">4</td>
</tr>
</tbody>
</table>
</div>
*One of the examples provided to the annotator, showcases the requirement for annotating the scores. The sample is originally in Chinese titles but translated into English. For the 0 score event, the subject and action differ from those of the topic events (i.e., 4 ISS astronauts returning versus Chinese Space Station construction); hence, they represent distinct occurrences. Regarding the 1 score event, although the subject (CSS and CSS Telescope) and the timestamp are somewhat far from the topic events, they share the same background (CSS construction). For the 2-score event, the subject and background are the same as the CSS construction, but it does not provide a follow-up coverage of the previous topic. As for the 3-score event, the subject, action, and background are identical (CSS construction), although the timestamp appears to be unrelated to the topic events. Finally, the 4-score event covers the same subject, action, and background as the CSS construction and provides a follow-up coverage of it.

## Ethical Considerations

When constructing the dataset, we hired crowd-source workers from platforms to do the annotation work, and the annotation is conducted by web interface with complete anonymous measures. We set up compensation for each sample according to the average pay for scoring tasks in the platform, taking the median of the average payment with 50% extra.

## Request

Due to company policy restrictions, we will not provide dataset directly online. Please contact us if needed. We are happy to get in touch with you and provide the necessary support.

While reporting results using the QBETTD, please cite the following article:
[BibTex to be added]

Ethanfang 
Tencent
ethanfang@tencent.com
