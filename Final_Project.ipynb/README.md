# Final_Project.ipynb

README for Final Project

Dawson Data
- .csv file
- contains data examining the relationships between environmental factors (ie: region, temperature, precipitation), human socioeconomic factors (ie: regional GDP), and the global richness of eight taxa of alien species
- comprehensive, but contains many missing/"NA" values

Introduction 

When a response variable is impacted by multiple factors, determining the relative importance of each factor on the response variable can be difficult. In their article, “Variable Importance Measures Suggest Paramount Influence of Human Economics on Alien-Species Introductions,” Arranz et. al (2025) aimed to ascertain the relative importance of environmental, economic, and human population factors on the success of alien species richness in eight taxonomic groups at a global scale. To analyze the variable importance of the aforementioned factors on alien species richness, Arranz et. al ran a dataset provided by Dawson et. al (2017) through linear mixed models, random forests, and hierarchical partitioning. 

For the purpose of this Final Project, I will focus on the random forest analysis utilized by the authors. The random forest algorithm is a machine learning technique that creates decision trees trained on subsets of the data. For classification tasks like the one in the Arranz et, al (2025) article, random forests use majority voting among the trees to determine the final class. The authors elected to use a random forest in their study because random forests allow for non-linear relationships and the highlighting of variable importance when predictors are intercorrelated.  

For their random forest algorithm, Arranz et. al used the predictors included in the training data, which consisted of 70% of the dataset per each taxonomic group, to create classification rules. Each decision tree in their random forest was built on a subset of the data created by bootstrapping. Bootstrapping is a resampling technique involving the creation of multiple datasets by randomly sampling the original dataset with replacement. The classification rules are built by splitting the training data into two nodes from two regions increasing in homogeneity with respect to the classification variable. Data samples are then generated using bootstrapping, with individuals present in the bootstrap sample referred to as “in-bag” data and the remaining individuals referred to as “out-of-bag" data. Non-pruned classification trees are built from each bootstrap sample. An algorithm (iRF) is used to search for the optimal number of variables to randomly sample as candidates for each split. RF was then applied to each taxonomic group with 10,000 trees. RF analysis was performed with the packages tuneRF and randomForest. 

Random forest models have a plethora of uses in quantitative ecology. Random forests have high classification accuracy, and they can be used to classify rare and invasive species. Additionally, random forests can be utilized to determine variable importance and complex interactions in ecological systems. Lastly, random forests are useful for high-dimensional data handling, as seen in Arranz. et al’s application of the random forest model to analyze relationships present in the comprehensive Dawson dataset. 

Final_ProjectDataCleaning.ipynb
- week of 11/10/2025
- cleaned up data by removing missing/NA values
- created a bar chart for visualization of global alien species richness in eight different taxa
- answered questions regarding input, output, and SciKit learn packages

Data Collection and Preprocessing

The Dawson et. al dataset was displayed in a .csv file that included the raw data and a metadata page that defined the column headings. The column headings include TDWG_name (country/region name), TDWG_code (combined TDWG code levels 1-4), along with headings describing species taxa, the mean temperature and precipitation of the region, and the national GDP of the region. This dataset was provided to explore relationships and variable importance between environmental and economic factors and global alien species richness. 

While the Dawson dataset was comprehensive, it included multiple rows of missing or “NA” values. During data cleaning, I used the “data = data.dropna()” to remove these undefined values. After cleaning, the counts of the eight main taxa extracted from the dataset were plotted on a bar chart to create a visualization of global alien species richness. The initial input for the model was the cleaned Dawson dataset, and the output was the bar chart.  

While pursuing the quasi-replication of Arranz et. al's random forest model, I decided to narrow down on the relationship between one or two factors on one taxon. The Dawson data provides a fascinating glimpse at the impacts of environmental and human factors on alien species richness; however, the intercorrelated relationships present in the dataset are a bit complex for the purpose of this project. I selected latitude and longitude as factors whose impact on global richness of alien mammal species I would explore in my random forest model. The data will be used to classify the variable importance of the relationships between latitude, longitude, and alien mammal species richness on a global scale. A 20/80 train/test split was utilized to balance the amount of training and testing data. While performing the train/test split, I altered the number of layers and nodes in the neural network to provide a better glimpse of accuracy. The result was a heat-map displaying fairly accurate data, with the highest accuracy found at 12 nodes and 8 layers. 

Train_Test_Data.ipynb
- weeks of 11/10/2025-11/17/2025
- used IC_SkiKitLearnExample as guidance
- reflected on the original paper
- decided on input and output
- split dataset into a 20/80 train/test split
- adjusted the numbers of layers and nodes
- generated a seaborn heatmap of results

Random_Forest_Model.ipynb
- week of 11/24/2025
- creating the random forest model 
- assessed model performance
- altered parameters to look at the variable importance of latitude and longitude on amphibian alien species richness
- answered questions
- created a reflection of the project

Reflection/Discussion (also found in submitted document and at the end of Random_Forest_Model.ipynb)

My random forest model examines the variable importance of latitude and longitude on mammal alien species richness. The model is displayed on a bar chart, with the “Factors” on the x-axis and the variable importances quantified on the y-axis. This model provides a snapshot of what Arranz. at al studied in their 2025 article on the effect of intercorrelated environmental and human factors on alien species richness in eight different taxonomic groups on a global scale. The bar chart highlights how latitude was found to have a higher variable importance than longitude on mammal alien species richness.  

This project required patience, thoroughness, and time-management skills. Learning about creating models- from cleaning data to creating train/test splits to assessing the model’s performance- increased my respect for individuals who work to develop accurate models displaying their research findings. While working on this project, one of the biggest challenges I faced was organization and proper documentation. During the early stages of the project, I still had many questions about the process, which made it difficult for me to create comments describing my code and record my progress on README. Additionally, I faced a significant hold-up during the train/testing portion of the project. I have created models in previous classes, but I was never required to slow down, clean the data, and run it through a train/test split. However, I used online resources and asked questions in class, and I was able to create a seaborn heatmap displaying the accuracy of the train/test split. 

If I were offered the chance to redo this project, I would want to look at the variable importances of more factors on the richness of different taxa. I think that I could come close to replicating Arranz et. Al's random forests, garnering a more thorough idea of the variable importances of different factors on alien species richness. I enjoyed tweaking the parameters and examining different results. 

Overall, I found this process to be rewarding. I chose to examine random forest models because they sounded like a challenge, and I am glad that I stuck with my initial selection, even during setbacks.  

