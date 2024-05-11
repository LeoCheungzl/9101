# 9101
# Random Forest
Introduction
In recent months, our project aimed to utilize various demographic and health-related variables to model and predict area visitor numbers in the New York region. This report details the methodologies applied in the regression analysis, focusing on the use of a Random Forest model, and discusses the results and implications of our findings.

Data Collection and Preprocessing
The primary dataset for our analysis included several key variables: median household income in the New York area, total population, COVID-19 infection numbers, and historical visitor counts. This data was sourced from public health records and local government databases.

To prepare the data for modeling, we undertook several preprocessing steps:

Data Reconstruction: We transformed the multi-dimensional time series data into a structured format suitable for regression analysis.
Normalization: We applied normalization to scale the features, aiding in the effective training of the Random Forest model and ensuring that no single feature would dominate the importance due to its scale.
Dimensionality Reduction: The high-dimensional data was converted into a two-dimensional format to streamline the modeling process and improve computational efficiency.
Model Selection and Configuration
The Random Forest model was selected due to its robustness and ability to handle non-linear relationships and interactions between features. Key steps in the model configuration included:

Dataset Splitting: The data was divided into training, validation, and test sets with different ratios to ensure robust evaluation while preventing data leakage.
Hyperparameter Tuning: We employed RandomSearch for hyperparameter optimization, which significantly enhanced the model's performance by finding the optimal settings for parameters like the number of trees and the depth of each tree.
Cross-Validation: To assess the model's performance and check for overfitting, we used k-fold cross-validation. This method provided a reliable estimate of the model's accuracy across different subsets of the dataset.
Model Evaluation
The Random Forest model was evaluated using several metrics:

Gini Importance: This metric helped identify the most influential features on the prediction, indicating how each feature contributes to the homogeneity of the nodes and leaves in the model.
Mean Squared Error (MSE): This measure helped quantify the model's prediction error, providing insight into the average squared difference between the estimated values and actual values.
R-Squared (R2): This statistic provided a measure of how well the observed outcomes are replicated by the model, based on the proportion of total variation of outcomes explained by the model.

# Random Forest Result
In the context of the Random Forest regression model that demonstrated the highest performance with a trains_size=80%, test_size=10%, raw_visit_minus_1, we will analyze the practical significance of the parameter importance as follows:


raw_visits_t_minus_1(importance:0.778152): The high importance indicates that past visits is a strong indicator of future visits, reflecting continuity in people's behaviors. In the commercial and service sectors, customers' repeat visits reflect loyalty to specific locations, which could be due to the convenience of the location, high satisfaction with the service quality, or unique consumption experiences. This behavioral inertia is crucial for retailers, service providers, and urban planners for market analysis and resource allocation. What’s more, the significant impact of prior visits also suggests that a region's attractiveness is not transient or coincidental but is built on a stable foundation of visits over time. A consistently high volume of visits indicates sustained attractiveness of a region to residents and visitors, possibly due to its unique products, services, or experiences.

Case Rate (Importance: 0.160513): This study found that the impact of COVID-19 is much more significant compared to other two feature(total population and median household income) A possible explanation is that compared to other more serious diseases, the effect of COVID-19 on human physiological functions is less significant, insufficient to notably restrict basic daily activities such as driving and shopping. This indicates that even those infected with COVID-19 can still maintain necessary activities like purchasing essential living supplies to some extent. The second explanation is that the transmission characteristics of COVID-19 usually do not lead to all members of a household being infected and incapacitated at the same time. This means that even with an increase in infection rates, there could still be family members who are able to go out, such as visiting specific places like supermarkets or restaurants. This finding further explains why the reduction in the number of visits to regions during the pandemic did not reach the expected level.

Total Population (Importance: 0.045020): Regions with larger populations, especially densely populated areas, tend to have higher levels of commercial activity because more people mean higher demands for basic living needs and consumer goods and services. This phenomenon is particularly evident in the visitation rates of business districts, shopping centers, and community service facilities. Furthermore, regions with larger total populations are often centers of socio-economic activity. These areas offer numerous job opportunities, as well as comprehensive services and entertainment facilities, thereby attracting more residents and tourists. Thus, the size of the total population directly reflects a region's attractiveness for various activities, subsequently affecting its visitation rates. At the same time, areas with larger populations require more transportation networks, educational institutions, medical facilities, and public spaces. The construction and improvement of these facilities and services also increase visitation rates, whether by residents or visitors from outside the area.

Median Household Income(Importance: 0.016315): Median household income is a critical indicator of the purchasing power within a community. Higher income levels typically correlate with a greater capacity for discretionary spending, influencing the types and frequencies of visits to various establishments. The context in which median household income operations can significantly affect its impact on visitation rates. For instance, in times of economic downturn, even areas with higher median incomes might experience reduced visitation rates due to increased saving behaviors. Conversely, in robust economic conditions, the effect of median household income on visitation rates might be more pronounced as consumer confidence and spending increase. It may be that the high inflation caused by the epidemic made most consumers unwilling to spend.

# STGCN

Introduction
In the realm of predictive analytics for area visitor volume, capturing complex interdependencies between various factors like time and space is crucial. Our initial approach using traditional machine learning models, such as Random Forest, revealed limitations in modeling the relationships among the data dimensions adequately. To address this challenge, we pivoted to implementing the Spatio-Temporal Graph Convolutional Network (STGCN), a deep learning framework tailored for handling the intricacies of spatial and temporal data dependencies.

Methodology
Data Encoding and Graph Construction
We transformed our tabular dataset into a graph format, where nodes represent different regional parameters (e.g., locations with visitor counts, infection rates). These were interconnected through a weighted adjacency matrix, reflecting the spatial dependencies and the strength of the relationship between different nodes.

Graph Convolutional Networks (GCN)
The spatial structure of the data was processed using Graph Convolutional Networks (GCN). This method allowed us to capture spatial dependencies effectively by applying convolution over the graph structure, encoded in our weighted adjacency matrix.

Handling Temporal Dynamics with Gated CNNs
For the temporal data, such as historical visitor counts and COVID-19 infection trends, we utilized Gated Convolutional Neural Networks (Gated CNNs). This approach helped in capturing the temporal patterns by applying convolutions across the time axis of the data, ensuring that both recent and older information could affect the forecasts adequately.

Model Training and Optimization
The STGCN model underwent rigorous training, where we fine-tuned various network parameters such as kernel size and the number of layers to optimize performance. We utilized techniques like Cross-Validation and Random Search for hyperparameter tuning to enhance the model's ability to generalize over different data splits.

Feature Importance and Model Evaluation
To understand the impact of different features on our predictions, we developed a custom algorithm based on the permutation feature importance method. This analysis helped identify which factors most significantly affected visitor volume predictions, providing insights into both static and dynamic feature influences across spatial and temporal dimensions.

We assessed the model's performance using metrics such as Gini importance, Mean Squared Error (MSE), and R-Squared (R2). The STGCN model demonstrated superior capability in capturing complex patterns and dependencies, achieving robust prediction accuracy and outperforming traditional models.

Conclusion
The implementation of STGCN represented a significant advancement in our analytical capabilities, allowing for a more nuanced understanding and forecasting of area visitor volumes. This approach not only improved prediction accuracy but also provided deeper insights into how different variables interact over time and space.

# Future Work

Integration of Advanced Models
For future iterations of our analysis, we aim to incorporate more sophisticated models such as Attention Based Spatio-Temporal Graph Convolutional Networks (ASTGCN). These models are known for their enhanced ability to capture complex interactions over both spatial and temporal dimensions, potentially providing even more accurate predictions.

Incorporation of Weather Data
Another critical area of development will be the inclusion of weather conditions as a feature in our models. Weather significantly affects visitor behavior; thus, its integration is expected to improve the predictive performance of our models. By analyzing how different weather patterns impact visitor volumes, we can refine our predictions and offer more tailored insights.

Addressing Endogeneity Issues
A crucial aspect of our future work will involve tackling the endogeneity issues within our data. For example, a rise in infection rates might lead to decreased area visitation in subsequent periods, while a reduction in visitor volume could conversely lead to lower infection rates in the following periods. Addressing these feedback loops will require sophisticated modeling techniques that can capture these two-way interactions. This will not only make our model more robust but also increase the accuracy and reliability of our forecasts.

These enhancements will ensure our model remains at the cutting edge of predictive analytics, providing valuable insights for urban planning and public health management.
