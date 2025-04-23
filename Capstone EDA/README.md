### Project Title: Predicting Electrification Project Success

Author: Cassandra Tang

#### Executive summary
As electricity is sourced from increasingly clean and renewable sources, electrification of traditionally gas-fired appliances, like water heaters and furnaces, is an increasingly viable path to decarbonization. At some point, most homeowners will need to replace one or both of these pieces of equipment in their homes, and they now have the option of choosing efficient heat pump technology, in addition to the traditionally available options of electric resistance and gas-fired equipment. Many people would like to decarbonize their home or are, at least, not resistant to the idea of replacing their gas-fired equipment with a heat pump. Because heat pumps are relatively new technologies, there is a lot of skepticism around their cost-effectiveness, their reliability, and the experience they provide compared to what people are used to. The cost-effectiveness of electrifying gas-fired equipment is the most hotly debated of this list. If heat pumps can be definitively demonstrated to be more cost-effective than their gas-fired counterparts, average consumers will be more likely to adopt them. Based on initial findings, the more energy (both gas and electric) that a homeowner consumes, the more likely they are to save by electrification alone (there are additional options to increase savings post-electrification). These findings also suggest that the larger and the older the home, the more likely the homeowner is to save money by electrifying.

#### Rationale
Given the nascent state of heat pump technology, many problems are likely to be identified as more people adopt them. With this in mind, unilaterally mandating the adoption of heat pump technology should be expected to be counter-productive to decarbonization. The alternative is to identify homeowners who are most likely to reap savings from switching from gas-fired appliances to heat pump appliances and preemptively introducing heat pumps as an option. Accurately identifying and converting these homeowners will, not only electrify an additional measure, but also: 1) help a homeowner save money on their utility bill in a high-energy rate era (at least in California) and 2) provide a homeowner with a positive electrification experience which accelerates the electrification effort as more average consumers share their positive experiences.

#### Research Question
What are the characteristics of homeowners who are likely to save money by switching from gas-fired equipment to heat pumps?

#### Data Sources
Almost all data I am using is internal data not intended to be publicly shared, combined with publicly available data. Because the data is not public, it has been removed from the Jupyter Notebook, so that only the high level dataframe information, methods, and model results are visible.

My data includes: anonymized gas and electric usage data, calculated bill costs, publicly available tax assessor data (for home age, square footage, bed/bath count, whether it's owner-occupied, the designation for the property), whether or not an EV is believed to be registered at the site, and internal project information. This dataset was built as part of other, related internal projects, and outlier detection is not straightforward in this situation.

#### Methodology
I applied some feature engineering to derive additional information from the raw features. I also used one-hot encoding and ordinal encoding to process the categorical features. Because I have a small dataset, I wanted to take advantage of bootstrapping, so I used a Random Forest model with hyperparameter tuning after cleaning and feature engineering. I wanted to explore whether a model like AdaBoost might be helpful, but it seems that it overfit too easily.

I split the feature space into 2 main groupings. The first grouping is what I call "a priori", or information we have available around the time or before a project occurs. The second grouping is data that is collected after a project occurs. Because I am initially approaching this from a predictive mindset, I wanted to build a model based only on features that would be feasibly available to someone prior to going through with a project. I consider installation date to be an 'a priori' feature because someone can choose the month or season to go through with a project. I am keeping the second grouping on standby because I think it can be used with the a priori group of features in a regression model or some kind of hybrid model to tease out causal relationship or correlations that subject matter experts can use to monitor the performance of a project over time.

#### Results
The most influential a priori factors are: the average monthly gas usage pre-electrification, the average monthly electric usage pre-electrification, the building square footage, and the decade the home was built. 

With the a priori features, my Random Forest model can predict with ~70% accuracy whether a project will be successful. 

#### Next steps
I want to dive deeper into understanding my Random Forest model. I chose it because of its interpretability, but based on my external knowledge of the situation, I can't rule out whether there are "goldilocks zones" for one or more of the features. If there are, then I want to be able to determine the bounds on those zones. This might be as simple as creating a diagram of the decision tree, or it might require more complex digging.

I am also considering adding a dataset that includes more details on energy usage, such as seasonal mins, maxes, averages, and standard deviations. Since the two strongest predictors of success are the electric and gas average monthly usages, it might be worth diving deeper into the nuances of energy usage.

I could also explore whether some combination of a regression model and a classification model can be used. Right now, my model has a binary success criteria: either the bills decreased or they didn't. There is a middle ground that equates to "breaking even", and there are different ranges of success. A household's bill could increase by a small amount, say 5%, and the homeowner could still consider that a success, for example, if they value decarbonization at 10% of their average utility bill.

#### Outline of project
Link to Notebook: Capstone EDA/20250422 Submission Electrification Success Model.ipynb


##### Contact and Further Information
Contact Cassandra Tang via Canvas
