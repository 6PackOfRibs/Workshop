## Predicting the Spread of Disease with Human Mobility Data

**Introduction**

As people become more and more interconnected, the spread of disease likewise becomes more difficult to predict and contain. The introduction of new diseases or strains of old diseases can cost many lives, lives that might not have to be paid. The unrestrained spread of a disease can overload hospitals, keeping many people from getting the medical attention they need. By minimizing the spread of the disease and properly distributing aid to affected areas, the number of casualties could be reduced significantly.

Amartya Sen's definition of human development is "the process of expanding fundamental human freedoms", one of which being the capability to live a long and healthy life. In the case of highly infectious novel diseases such as Covid-19, the ability to predict human mobility and its effect on disease spread can directly translate into allowing countries to better prepare and make policies. If acted upon early enough, it could be possible to completely contain and prevent the spread of a novel disease. If not, then the information would still be useful in flattening the curve and ensuring as few people as possible die from the disease. This topic contributes to sustainable development goal 3, to "ensure healthy lives and promote well-being for all ages."

**Inquiry**

The broad central research question focused on in this paper is "how can the spread of disease be predicted in regards to human mobility." The majority of research has been purely descriptive given the sheer complexity of the subject. Predicting human mobility and the spread of disease is extremely difficult to do with a high degree of accuracy, especially given the varying degrees of information available to make use of in different places.

There are many important sub-research questions to answer, one of which being "how does treatment-seeking behavior affect the spread of disease?" Treatment-seeking behavior depends on a variety of individual factors, travel time to the nearest facility and income being a couple of them. It also depends on severity and type of symptoms, which by extension means it varies according to the type of disease. It is already quite difficult to quantify human mobility by itself, but treatment-seeking behavior is an important aspect to account for as well.

Since the majority of research done on this topic has been descriptive, one important question to answer is "how can the spread of disease be predicted in a way that would be most useful in making decisions on containment and resource allocation." While we could use mathematical models to simulate disease spread with varying degrees of accuracy, perhaps a spatial diffusion model would be more useful in deciding how large of an area to contain and which places most need resources.

Another sub-question is "how can we simulate the effect of certain decisions on the spread of disease?" If an action were to be taken at a certain point in time, how accurately can we predict its effect? Answering this question would bring this subject partially out of the descriptive category and allow the current research to affect policy, and by extension human development.

**Methods**

Mathematical models are a given when researching the effect of human mobility on the spread of disease. While they have been in use for a long time, are unfortunately less useful when real mobility data - by means such as call and text records - are available. The usefulness of these models really shine in areas where data is lacking, such as during epidemics of low-income countries, when it is important to forecast the best possible allocation of resources given the scarce information. Mathematical models can predict mobility patterns based solely on population size, population density, and travel distance. 

One method I found significant was the impedance model (Sallah, 2017). The impedance model is a parameter-free model adapted from Ohm's law of electricity. Using the formula P = I * R, Mobility potential is calculated by multiplying distance (resistance) by the number of trips per day (current). With alpha being the probability of human mobility and d being distance, the number of trips flow from i to j can be formulated as

![](images/Screen%20Shot%202020-04-19%20at%209.15.35%20PM.png)

The probability for a person in location i to travel to location j is given by

![](images/Screen%20Shot%202020-04-19%20at%209.24.59%20PM.png)

When compared to the gravity and radiation models, the impedance model outperforms both when tested on simulated data. The gravity model estimates the number of trips between two places by using the population sizes and the distance between them. The issue with the gravity model is that it requires parameter tuning and is difficult to implement without reference data. The radiation model estimates the probability of commuting from one place to another and likely patterns of commuting. While parameter-free, this model assumes mobility to depend on population density, making it inherently biased. The impedance model contributes to the central research question because it further describes the spread of disease in regards to human mobility.

A study done by Kraemer (2019) used both the gravity model and radiation model, as well as an adjacency network to create an invasion model and transmission model. The formulas for the gravity model and radiation model respectively are

![](images/Screen%20Shot%202020-04-19%20at%209.27.23%20PM.png)

![](images/Screen%20Shot%202020-04-19%20at%209.32.52%20PM.png)

In each model, T<sub>i,j</sub> represents the total number of individuals moving from district i to district j; N<sub>j</sub><sup>alpha</sup> is the population size at the origin; N<sub>j</sub><sup>beta</sup> is the population size at the destination; d<sub>i,j</sub><sup>Y</sup> is the distance between them; and s<sub>i,j</sub> is the total population in the radius between i and j.

The adjacency network is one where movements are assumed to proceed along edges connecting each of the districts in the countries. It encodes the number of district borders one would need to cross to move from one district to another, which reflects the impacts of borders on movements in a region. All three metrics were used independently as well as together to capture effects that might not be described separately.

The invasion model estimates the probability p<sub>i</sub>(t) that one or more cases will be identified in previously disease-free district i at time t (with presence or absence of new cases indicated by Y<sub>i</sub>(t)), as a function of the number of cases C<sub>-i</sub>(t − 1) in all other districts in the previous time point (two weeks in their analysis), the product of corresponding values of the mobility covariates x<sub>j,−i</sub> for each covariate j, regression coefficient b<sub>j</sub> and a fixed intercept term c. This is given by the logistic regression model:

![image-20200419220627223](/Users/jamesyao/Library/Application Support/typora-user-images/image-20200419220627223.png)

For the transmission model, I<sub>t,i</sub> is the number of infectious individuals and S<sub>t-1,i</sub> is the number of susceptible individuals at time t in district i. N<sub>i</sub> is the population of district i and Beta<sub>t,i</sub> is the covariate-driven mobility rate characterized by a linear combination of mobility metrics. alpha<sub>i</sub> is an approximation of the contact rate of the population in district i and a parameter to account for the continuous process.

The model did relatively well in predicting up to two weeks ahead. When tested in real time, the model fit and results were very similar. The invasion model was not particularly accurate in predicting invasions within a two week period, but when extended to a month, the model made accurate predictions of the invasion process. The transmission and invasion model contributes to answering the central research question because it applies multiple methods to better describe the spread of disease.

Overall, I was very impressed with the impedance model and transmission and invasion models. Since the transmission and invasion models were implemented with the gravity and radiation models, I think a gap in the literature that needs to be further explored is the implementation of these models with the impedance model. According to Sallah et al. (2017), the impedance model was more effective than the gravity and radiation models on simulated data. It would be interesting to see how the accuracy of the transmission and invasion models, which was accurate predicting two weeks to a month, changes when utilizing the impedance model.
