
# An examination of social and economic data across nations worldwide using statistical analysis

![](https://github.com/gretapoc/duomenu-statistine-analize/blob/main/pics/Untitled-1.png)

## Turinys 
1. [Introduction](https://github.com/gretapoc/Data-analyst-portfolio)

2. [Socio-Economic Analysis of Countries Worldwide](https://github.com/gretapoc/duomenu-statistine-analize/edit/main/README.md#pasaulio-%C5%A1ali%C5%B3-statistin%C4%97-analiz%C4%97) 

    2.1. [Data editing and review](https://github.com/gretapoc/duomenu-statistine-analize/edit/main/README.md#duomen%C5%B3-redagavimas-ir-ap%C5%BEi%C5%ABra)

    2.2. [Factor extraction and interpretation](https://github.com/gretapoc/duomenu-statistine-analize/edit/main/README.md#faktori%C5%B3-i%C5%A1skyrimas-ir-interpretacija)

    2.3. [Country clustering](https://github.com/gretapoc/duomenu-statistine-analize/edit/main/README.md#%C5%A1ali%C5%B3-skirstymas-%C4%AF-klasterius)

    2.4. [Identification and interpretation of the main components](https://github.com/gretapoc/duomenu-statistine-analize/edit/main/README.md#pagrindini%C5%B3-komponen%C4%8Di%C5%B3-i%C5%A1skyrimas-ir-interpretacija)

    2.5. [Hypothesis testing for clusters](https://github.com/gretapoc/duomenu-statistine-analize/edit/main/README.md#hiptezi%C5%B3-tikrinimas-klasteriams)

3. [Conclusion](https://github.com/gretapoc/duomenu-statistine-analize/edit/main/README.md#i%C5%A1vados)

## Introduction

The world is divided into countries with many differences between them. Gross Domestic Product (GDP) per capita is considered as one of the primary indicators that reflect how countries are classified based on economic development. It reflects the market value of all final goods and services produced in a country over a given period of time, making it the primary indicator for a country's economic development. Nevertheless, there are various socio-economic indicators that aid in comprehending the level of poverty, lack of healthcare, lack of education, and inequality between men and women in parts of the world. Statistical surveys can be conducted to identify the countries that face severe issues regarding socio-economic problems. Graphical representations present the results in a comprehensible way and help draw clearer conclusions.

This paper seeks to showcase the rich diversity of countries around the world by analyzing their socio-economic data, clustering them based on similarities and differences, and applying appropriate statistical methods to characterize the resulting groups.

## Socio-Economic Analysis of Countries Worldwide

### Data editing and review

The dataset is compiled from the [World Bank's](https://databank.worldbank.org/source/world-development-indicators) Health, Nutrition, Population Statistics Database, the Gender Statistics Database and the World Development Indicators Database. The dataset contains indicators on the socio-economic life of countries around the world as of 2019.


The data needs to be edited before statistical methods can be used to analyze it. The [dataset](https://github.com/gretapoc/duomenu-statistine-analize/blob/main/Duomenys.xlsx) contains 207 observations (countries) and 24 variables (socio-economic indicators).


<div align="center">

| Social and economic indicators (variables) | Year |
|-----|:----:|
| Population, total  | 2019 |
| Population growth (annual %) | 2019 |
| Urban population (% of total population) | 2019 |
| Population density (people per sq. km of land area) | 2019 |
| Birth rate, crude (per 1,000 people) | 2019 |
| Death rate, crude (per 1,000 people) | 2019 |
| GDP per capita (current US$) | 2019 |
| GDP growth (annual %) | 2019 |
| Life expectancy at birth, male (years) | 2019 |
| Life expectancy at birth, female (years) | 2019 |
| Fertility rate, total (births per woman) | 2019 |
| Mortality rate, infant (per 1,000 live births) | 2019 |
| Current health expenditure (% of GDP) | 2019 |
| Suicide mortality rate, female (per 100,000 female population) | 2019 |
| Suicide mortality rate, male (per 100,000 female population) | 2019 |
| Immunization, DPT (% of children ages 12-23 months) | 2019 |
| Access to electricity (% of population)  | 2019 |
| Individuals using the Internet (% of population) | 2019 |
| People using at least basic drinking water services (% of population) | 2019 |
| Wage and salaried workers, female (% of female employment) | 2019 |
| Wage and salaried workers, male (% of male employment) | 2019 |
| Labor force, total | 2019 |
| School enrollment, secondary, female (% gross) | 2019 |
| School enrollment, secondary, male (% gross) | 2019 |
  
</div>

Observations with missing values in their respective rows are removed from the dataset, which results in the exclusion of 113 countries, leaving a total of 94 countries in the dataset.

The correlation coefficients between the variables are calculated and a correlation matrix is constructed from them. The resulting matrix values are displayed.

<div align="center">

![alt text](https://github.com/gretapoc/duomenu-statistine-analize/blob/main/pics/kor.PNG)

</div>

The blue color denotes a positive correlation between variables, whereas the red color represents a negative correlation. The correlation matrix depicts several interesting relationships between the variables:
- Access to electricity is strongly positively correlated with access to at least basic drinking water services. Access to electricity and drinking water are basic needs in society. Since both are essential requirements of a society and are being developed at a similar rate, they should be accessible at a similar level in countries.
- Population has a very strong positive correlation with labour force. It is natural that countries with a larger population tend to have a higher number of people who are employed or looking for work.
- The share of urban population is strongly positively correlated with access to the internet. The higher the share of urban population, the more developed the country's economy is.
- Birth rate, fertility rate and infant mortality are strongly negatively correlated with life expectancy, access to electricity, internet, at least basic drinking water services and the number of men and women who have completed secondary education. In general, countries with higher birth rates and infant mortality rates tend to have lower access to basic public services, such as access to electricity and internet.
- Mortality is weakly positively correlated with access to secondary education and the number of employees. The stress levels experienced by individuals at schools or workplaces can contribute to higher mortality rates in countries.

Indeed, there are many other interesting relationships between variables. In order to identify clearly understandable relationships, the 24 variables can be reduced to a smaller number of factors.


### Factor extraction and interpretation

It is checked whether the data is suitable for factor analysis. Bartlett's test of sphericity is applied. After performing the test, it is found that the _p_-value is smaller than the chosen significance level _α_ = 0.05. Therefore, the null hypothesis is rejected. The data is suitable for factor analysis.

The Kaiser-Meyer-Olkin measure is calculated. The obtained measure value of 0.83 indicates strong partial correlation. Thus, factor analysis can be applied.

The number of factors is determined by applying the Kaiser criterion and drawing a scree plot. The plot shows the scree plot, where the _x_-axis indicates the number of factors, and the _y_-axis shows the corresponding eigenvalues.


<div align="center">

![alt text](https://github.com/gretapoc/duomenu-statistine-analize/blob/main/pics/tikr-reiksmes.PNG)

</div>

The number of factors to be extracted is the number of points on the graph with test values greater than 1. Five factors have test values greater than 1, but we choose to extract only four factors for better interpretability. In this case, therefore, 4 factors are distinguished.

The correlation matrix of the original variables is subjected to factor analysis using the maximum likelihood method.


<div align="center">

|                               | Factor 1    | Factor 2    | Factor 3    | Factor 4    | 
|-------------------------------|:-----------:|:-----------:|:-----------:|:-----------:|
| SS Loadings  | 10,169      | 2,356       | 2,237       | 2,104       | 
| Proportion Variance | 0,424       | 0,098       | 0,093       | 0,088       | 
| Cumulative Variance        | 0,424       | 0,522       | 0,615       | 0,703       | 

</div>


The table indicates the proportion of the total variance of the variables explained by each factor. The cumulative variance indicates the proportion of the total variance of the explanatory variables explained by each factor. Factor 1 explains 42% of the total variance, Factor 2 10%, Factor 3 9% and Factor 4 9%. The identified factors explain 70% of the total variance of the variables, which indicates a reasonably good model.

The weights of the factors in the expression of the original variables through the factors are given.


<div align="center">
  
|                                                                            | Factor 1 | Factor 2 | Factor 3 | Factor 4|
| ---------------- | :--------:| :-------:| :-------:| :------:| 
| Population, total                                                          | -0,106  |         |         |  0,989 | 
| Population growth (annual %)                                               | -0,276  | -0,571  | -0,583  |        | 
| Urban population (% of total population)                      | 0,793   |         |         |        | 
| Population density (people per sq. km of land area)             |         | -0,343  |  0,134  |        | 
| Birth rate, crude (per 1,000 people)                                                 | -0,755  | -0,228  | -0,605  |        | 
| Death rate, crude (per 1,000 people)                                                 |         | 0,900   | 0,260   |        | 
| GDP per capita (current US$)                                         | 0,735   | 0,153   |         |        | 
| GDP growth (annual %)                                              | -0,438  | -0,134  |         |        | 
| Life expectancy at birth, male (years)                                    | 0,878   |         | 0,346   |        | 
| Life expectancy at birth, female (years)                                  | 0,888   |         | 0,264   |        | 
| Fertility rate, total (births per woman)                           | -0,716  |         | -0,679  |        | 
| Mortality rate, infant (per 1,000 live births)                                   | -0,844  | -0,113  | -0,342  |        | 
| Current health expenditure (% of GDP)                                               | 0,517   | 0,370   |         |        | 
| Suicide mortality rate, female (per 100,000 female population)                   | 0,320   | 0,540   |         | 0,257  | 
| Suicide mortality rate, male (per 100,000 female population)                     | 0,255   | 0,612   | 0,110   |        | 
| Immunization, DPT (% of children ages 12-23 months)                          | 0,485   |         | 0,107   |        | 
| Access to electricity (% of population)                              | 0,687   |         | 0,492   |        | 
| Individuals using the Internet (% of population)               | 0,909   | 0,159   | 0,160   |        | 
| People using at least basic drinking water services (% of population)     | 0,757   |         | 0,495   |        | 
| Wage and salaried workers, female (% of female employment)                  | 0,855   | 0,253   | 0,182   |        | 
| Wage and salaried workers, male (% of male employment)                      | 0,836   | 0,160   | 0,138   | -0,128 | 
| Labor force, total                                                               |         |         |         |  0,991 | 
| School enrollment, secondary, female (% gross)      | 0,822   | 0,136   | 0,193   |        | 
| School enrollment, secondary, male (% gross)      | 0,840   | 0,150   | 0,188   |        | 

</div>

These values represent the extent of the variability explained by each variable in each factor.The weights of the factors are utilized for interpreting them as:

- Factor 1 has the greatest weights for urban population, GDP per capita, life expectancy, number of employees, number of inhabitants with secondary education, access to the internet, access to basic drinking water services, electricity. Therefore, this factor is reflective of the economic development of a country.
- Factor 2 has the highest weights on mortality and suicide. This factor represents the overall quality of life in a country.
- Factor 3 has the highest weights on access to electricity and basic drinking water services. This factor reflects access to fundamental services in society.
- Factor 4 has the highest weights on population and labor force. This factor is indicative of the number of individuals working or looking for work in the country.

The original data is plotted on the coordinate plane of the first two factors.

<div align="center">

![alt text](https://github.com/gretapoc/duomenu-statistine-analize/blob/main/pics/fakt-svor1.PNG)

</div>

The graph illustrates that the lowest quality of life is observed in European countries such as Latvia, Lithuania, and Bulgaria, whereas the highest quality of life is seen in the Maldives, Bahrain, and the United Arab Emirates. The countries in the Middle East (Bahrain, UAE, Oman, Saudi Arabia, etc.) exhibit strong economic development and a very high quality of life. Chad is distinctive from the rest in that it has both a very poor economic development and a very poor overall quality of life.

### Country clustering

As the units of measurement of the variables in the dataset differ, standardization of the data is performed. Once the units of measurement are standardised, cluster analysis can be performed. The Ward method is applied to the standardized data, and a dendrogram is generated.

<div align="center">

![alt text](https://github.com/gretapoc/duomenu-statistine-analize/blob/main/pics/dendr.PNG)

</div>

A review of the dendrogram concluded that 6 clusters will be used in the further analysis. The clusters with their associated countries are listed in a table.

<div align="center">
  
| Cluster 1  | Cluster 2        | Cluster 3          | Cluster 4          | Cluster 5           | Cluster 6 | 
|--------------|--------------------|----------------------|-----------------------|------------------------|-------------|
| <sub>Armenia</sub>     | <sub>Australia</sub>         | <sub>Azerbaijan</sub>        | <sub>Bahrain</sub>             | <sub>Bangladesh</sub>            | <sub>India</sub>      | 
| <sub>Austria</sub>     | <sub>Belgium</sub>            | <sub>Belize</sub>              | <sub>Brunei Darussalam</sub> | <sub>Burkina Faso</sub>          |             | 
| <sub>Bulgaria</sub>    | <sub>Canada</sub>             | <sub>Bolivia</sub>             | <sub>Cyprus</sub>                | <sub>Burundi</sub>                |             | 
| <sub>Cuba</sub>         | <sub>Chile</sub>               | <sub>Brazil</sub>            | <sub>Israel</sub>              | <sub>Chad</sub>                  |             | 
| <sub>Czechia</sub>       | <sub>Costa Rica</sub>         | <sub>Cape Verde</sub>     | <sub>Malaysia</sub>             | <sub>Ivory Coast</sub> |             | 
| <sub>Estonia</sub>       | <sub>Denmark</sub>             | <sub>Colombia</sub>            | <sub>Maldives</sub>              | <sub>Djibouti</sub>               |             | 
| <sub>France</sub>   | <sub>Finland</sub>            | <sub>Dominican Republic</sub> | <sub>Malta</sub>                 | <sub>Ghana</sub>                   |             | 
| <sub>Georgia</sub>  | <sub>Iceland</sub>          | <sub>Ecuador</sub>            | <sub>Oman</sub>                | <sub>Laos</sub>                 |             | 
| <sub>Germany</sub>    | <sub>Ireland</sub>             | <sub>Egypt</sub>              | <sub>Saudi Arabia</sub>         | <sub>Malawi</sub>                |             | 
| <sub>Greece</sub>     | <sub>Luxembourg</sub>      | <sub>Salvador</sub>           | <sub>Turkey</sub>               | <sub>Mauritania</sub>            |             | 
| <sub>Hungary</sub>     | <sub>Netherlands</sub>           | <sub>Guatemala</sub>            | <sub>United Arab Emirates</sub>                   | <sub>Nepal</sub>                |             | 
| <sub>Italy</sub>      | <sub>New Zealand</sub>  | <sub>Honduras</sub>             | <sub>Pakistan</sub>            |                        |             | 
| <sub>South Korea</sub> | <sub>Norway</sub>          | <sub>Kazakhstan</sub>         | <sub>Rwanda</sub>                |                        |             | 
| <sub>Latvia</sub>      | <sub>Spain</sub>           | <sub>Kyrgyzstan</sub>            | <sub>Senegal</sub>             |                        |             | 
| <sub>Lithuania</sub> | <sub>Sweden</sub> | <sub>Mexico</sub> | <sub>Tanzania</sub> | | |
| <sub>Mauritius</sub> | <sub>Switzerland</sub> | <sub>Mongolia</sub> | <sub>East Timor</sub> | | |
| <sub>Montenegro</sub> | <sub>United Kingdom</sub> | <sub>Morocco</sub> | | | |
| <sub>Poland</sub> | | <sub>Peru</sub> | | | |
| <sub>Portugal</sub> | | <sub>Philippines</sub> | | | |
| <sub>Romania</sub> | | <sub>Uzbekistan</sub> | | | |
| <sub>Russia</sub> | | | | | |
| <sub>Serbia</sub> | | | | | |
| <sub>Slovakia</sub> | | | | | |
| <sub>Slovenia</sub> | | | | | |
| <sub>South Africa</sub> | | | | | |
| <sub>Saint Lucia</sub> | | | | | |
| <sub>Thailand</sub> | | | | | |
| <sub>USA</sub> | | | | | |
| <sub>Uruguay</sub> | | | | | |
  
  
</div>

The countries assigned to the clusters are shown on the map with different colours.

<div align="center">

![aaaauikyjhfhfgh](https://github.com/gretapoc/duomenu-statistine-analize/blob/main/pics/klast1.PNG)

</div>

Countries that belong to different clusters are marked on the map. You can see how the clusters of countries are distributed geographically. The countries in the first cluster are widely spread across Africa, Asia, Australia, South and North America, and mostly in Europe. The second cluster covers parts of Europe, South and East America. The countries of the third and fourth clusters are spread mainly over the Asian continent. The countries of the fifth cluster are located on the African continent and Asia. The sixth cluster is India.

A _k_-means clustering is also performed. In this non-hierarchical cluster analysis method, the number of clusters is chosen in advance. Since the hierarchical cluster analysis resulted in 6 clusters in the printed dendrogram, the same number of clusters are used for _k_-means clustering. The clusters with the countries assigned to them are listed in a table.


<div align="center">
  
| Cluster 1  | Cluster 2        | Cluster 3          | Cluster 4           | Cluster 5            | Cluster 6 | 
|--------------|--------------------|----------------------|-----------------------|------------------------|-------------|
| <sub>Australia</sub> | <sub>Armenia</sub> | <sub>Bulgaria</sub> | <sub>Burkina Faso</sub> | <sub>Bahrain</sub> | <sub>India</sub> |
| <sub>Austria</sub> | <sub>Azerbaijan</sub> | <sub>Cuba</sub> | <sub>Burundi</sub> | <sub>Brunei Darussalam</sub> | |
| <sub>Belgium</sub> | <sub>Bangladesh</sub> | <sub>Czechia</sub> | <sub>Chad</sub> | <sub>Chile</sub> | |
| <sub>Canada</sub> | <sub>Belize</sub> | <sub>Estonia</sub> | <sub>Ivory Coast</sub> | <sub>Costa Rica</sub> | |
| <sub>Denmark</sub> | <sub>Bolivia</sub> | <sub>Georgia</sub> | <sub>Djibouti</sub> | <sub>Cyprus</sub> | |
| <sub>Finland</sub> | <sub>Brazil</sub> | <sub>Greece</sub> | <sub>Ghana</sub> | <sub>Israel</sub> | |
| <sub>France</sub> | <sub>Greenland</sub> | <sub>Hungary</sub> | <sub>Malawi</sub> | <sub>Malaysia</sub> | |
| <sub>Germany</sub> | <sub>Colombia</sub> | <sub>Italy</sub> | <sub>Mauritania</sub> | <sub>Maldives</sub> | |
| <sub>Iceland</sub> | <sub>Dominican Republic</sub> | <sub>Kazakhstan</sub> | <sub>Pakistan</sub> | <sub>Malta</sub> | |
| <sub>Ireland</sub> | <sub>Ecuador</sub> | <sub>Latvia</sub> | <sub>Rwanda</sub> | <sub>Oman</sub> | |
| <sub>South Korea</sub> | <sub>Egypt</sub> | <sub>Lithuania</sub> | <sub>Senegal</sub> | <sub>Saudi Arabia</sub> | |
| <sub>Luxembourg</sub> | <sub>El Salvador</sub> | <sub>Mauritius</sub> | <sub>Tanzania</sub> | <sub>Turkey</sub> | |
| <sub>Netherlands</sub> | <sub>Guatemala</sub> | <sub>Montenegro</sub> | <sub>East Timor</sub> | <sub>UAE</sub> | |
| <sub>New Zealand</sub> | <sub>Honduras</sub> | <sub>Poland</sub> | | | |
| <sub>Spain</sub> | <sub>Laos</sub> | <sub>Romania</sub> | | | |
| <sub>Sweden</sub> | <sub>Mexico</sub> | <sub>Russia</sub> | | | |
| <sub>Switzerland</sub> | <sub>Mongolia</sub> | <sub>Serbia</sub> | | | |
| <sub>United Kingdom</sub> | <sub>Morocco</sub> | <sub>Slovakia</sub> | | | |
| <sub>USA</sub> | <sub>Nepal</sub> | <sub>Slovenia</sub> | | | |
| | <sub>Peru</sub> | <sub>South Africa</sub> | | | |
| | <sub>Philippines</sub> | <sub>Uruguay</sub> | | | |
| | <sub>Saint Lucia</sub> | | | | |
| | <sub>Thailand</sub> | | | | |
| | <sub>Uzbekistan</sub> | | | | |
  
</div>

The countries assigned to the clusters are shown on the map with different colours.

<div align="center">

![aaaauikyjhfhfgh](https://github.com/gretapoc/duomenu-statistine-analize/blob/main/pics/klast2.PNG)

</div>

You can see how the clustered countries are geographically distributed. The countries in the first cluster are spread over the North American continent, Australia, and Europe, mainly northern and western parts of the world. The countries in the second cluster are widely spread over several continents: Asia, Africa, North and South America. The third cluster covers Russia, the Baltic States, Eastern and Southern Europe. One country in this cluster is also located on the continents of Africa and South America. The countries of the fourth cluster are mainly visible on the African continent, but the cluster also includes one country in Asia. Countries in the fifth cluster are located in the Middle Eastern countries and South America. The sixth cluster is solely composed of India.

Often, countries that are geographically close have more similarities in terms of historical background and existing culture. These similarities also affect the socio-economic indicators of the countries. It can be observed that in the map showing countries extracted using non-hierarchical cluster analysis, the countries belonging to each cluster are geographically slightly closer to each other than in the map showing countries extracted using hierarchical cluster analysis. For this reason, the countries extracted by the k-means method will be used for further interpretation and analysis.

In the light of the factors highlighted above, the countries extracted by the k-means method are subject to cluster interpretation:

- The countries in the first cluster (e.g., Australia, Sweden, South Korea,...) are strongly economically developed. The population has full access to basic services in society but the overall quality of life is poor. A large portion of the population is employed or looking for work.
- The countries in the second cluster (e.g., Colombia, Nepal, Azerbaijan,...) are economically underdeveloped. The overall quality of life is good, but the population has poor access to basic services in society.
- The countries in the third cluster (e.g., Lithuania, Greece, Cuba,...) are economically developed. The population has full access to basic services in society, but the overall quality of life is poor. Low number of people working and looking for work.
- The countries in the fourth cluster (e.g., Djibouti, Pakistan, Tanzania,...) are economically very underdeveloped. The overall quality of life is average, but the population has poor access to basic services in society. Low number of people working and looking for work.
- The countries in the fifth cluster (e.g., Cyprus, Oman, Chile,...) are economically developed. The population has full access to basic services in society and the overall quality of life is good.
- The country in the sixth cluster (India) is economically underdeveloped. Population has poor access to basic services in society, overall quality of life is average. The number of people working and looking for work is exceptionally high.


### Identification and interpretation of the main components

For standardised baseline data, a principal components analysis is carried out.

<div align="center">

|                            | Comp. 1 | Comp. 2 | Comp. 3 | Comp. 4 | Comp. 5 | 
|----------------------------|:------------:|:------------:|:------------:|:------------:|:------------:|
| **Standard deviation** | 3,47         | 1,59         | 1,43         | 1,17         | 1,08         | 
| **Proportion of Variance**      | 0,51         | 0,11         | 0,09         | 0,06         | 0,05         | 
| **Cumulative Proportion**  | 0,51         | 0,61         | 0,70         | 0,76         | 0,81         |

</div>

<div align="center">

|                            | Comp. 6 | Comp. 7 | Comp. 8 | Comp. 9 | Comp. 10 | 
|----------------------------|:------------:|:------------:|:------------:|:------------:|:-------------:|
| **Standard deviation** | 0,92         | 0,87         | 0,79         | 0,74         | 0,63          | 
| **Proportion of Variance**      | 0,04         | 0,03         | 0,03         | 0,02         | 0,02          | 
| **Cumulative Proportion**  | 0,84         | 0,87         | 0,90         | 0,92         | 0,94          | 

</div>

There are 24 variables in total, which means there are 24 components. The tables show the standard deviations (or matrix test values) of the first 10 components and the proportion of variance explained and the cumulative proportion of variance explained of each component. The standard deviations of the first five components are greater than 1, indicating that they explain more variance than individual variables. The remaining components have standard deviations smaller than 1 and account for less variance than the individual variables. Each successive component explains less of the variance. The first three explain 70% of the total variance.

A plot of the first two principal components, that explain most of the variance.

<div align="center">

![aaaauikyjhfhfgh]()

</div>

This plot shows not only how countries are related to each other, but also which countries stand out. The grouping is made up of East African countries (Burundi, Tanzania, Malawi, Rwanda) and West African countries (Burkina Faso, Ivory Coast, Mauritania). The Central African country of Chad stands out from the others, but is grouped with other African countries. India also stands out from the rest, probably because of its exceptionally large population. Clusters are formed with a larger number of countries. Colombia, Morocco, Ecuador, Cape Verde, Belize, etc. are grouped. European countries are also grouped - Germany, France, Austria, Portugal, Estonia, etc.


### Hypothesis testing for clusters

The hypothesis to be tested is that the mean number of male suicides is less than or equal to the mean number of female suicides in each cluster. The results of the _t_-test to test the hypotheses on the mean number of suicides between men and women are presented.

<div align="center">

| _t_-test  | _p_-value      |
|-------------|------------------|
| Cluster 1 | 0,00000001013598 |
| Cluster 2 | 0,0000009300975  |
| Cluster 3 | 0,00000001204952 |
| Cluster 4 | 0,00000149202    |
| Cluster 5 | 0,00001267298    |

</div>

From the table, it can be concluded that the null hypothesis is rejected in all presented clusters because the _p_-values of the test performed are less than the significance level _α_ = 0.05. Therefore, the average number of male suicides is not lower than that of females in each of the presented clusters. In the sixth cluster, there is only one country - India. In this country, the number of male suicides (14.1 suicides per 100,000 male population) is also higher than that of females (11.1 suicides per 100,000 female population).

For each cluster, a two-sided hypothesis is tested that the average proportion of male employees who receive wages is equal to the average proportion of female employees who receive wages. The results of the _t_-test for testing hypotheses about the average proportion of male and female employees who receive wages are presented.

<div align="center">

| _t_-test  | _p_-value  |
|-------------|--------------|
| Cluster 1 | 0,0001058282 |
| Cluster 2 | 0,483654     |
| Cluster 3 | 0,01223224   |
| Cluster 4 | 0,02123974   |
| Cluster 5 | 0,8945943    |

</div>

From the table, it can be concluded that the null hypothesis is rejected in the first, third, and fourth clusters because the _p_-values of the test performed are less than the significance level _α_ = 0.05. Therefore, in these clusters, the difference between the average proportion of male employees who receive wages and the average proportion of female employees who receive wages is statistically significant. The first and third cluster countries are mostly located in Europe, and these clusters also include Russia, the United States, and Canada. These countries differ significantly from the countries in the fourth cluster, which are located throughout the African continent. In the second and fifth clusters, the _p_-values are greater than the significance level, so the null hypothesis is not rejected for these clusters. Therefore, in the second and fifth clusters, the difference between the average proportion of male employees who receive wages and the average proportion of female employees who receive wages is statistically insignificant. In India, the proportion of male employees differs from that of females by only one hundredth (male - 24.17% of total employment, female - 24.16% of total employment).

For each cluster, a two-sided hypothesis is tested that the average expected lifespan of men is equal to the average expected lifespan of women. The results of the _t_-test for testing hypotheses about the average expected lifespan of men and women are presented.

<div align="center">

| _t_-test  | _p_-value           |
|-------------|-----------------------|
| Cluster 1 | 0,0000000000001547953 |
| Cluster 2 | 0,000000001078688     |
| Cluster 3 | 0,000001663873        |
| Cluster 4 | 0,0640687             |
| Cluster 5 | 0,001144371           |

</div>

Based on the table, it can be concluded that the null hypothesis is rejected in the first, second, third, and fifth clusters since the test _p_-values are smaller than the significance level of _α_ = 0.05. Therefore, in these clusters, the difference between the expected average lifespan of men and women is statistically significant. These clusters are located throughout the world, so gender inequality in terms of the average expected lifespan prevails in both men and women on every continent. In the fourth cluster, the p-value is greater than the significance level, so the null hypothesis cannot be rejected. Therefore, in the fourth cluster, the difference in the expected average lifespan between men and women is statistically insignificant. Although there are some African countries where these indicators are statistically significant, this inequality does not apply to most African countries. In India, the average life expectancy for men is 70.95 and for women, it is 68.46, so the difference in this indicator is not significant.


## Conclusion

World countries can be divided into clusters or groups using various methods, such as factor analysis, hierarchical and non-hierarchical clustering analysis, and principal component analysis. The most accurate results are provided by the _k_-means method, which, when the results are displayed on a map, shows that the countries in each cluster are grouped geographically.

Clusters whose countries are located in certain continents have similarities and differences based on geographical position. When applying factor analysis to the data, four essential factors were identified that describe certain economic and social factors. Using the interpretations of these factors, the clusters are compared to each other.

Applying statistical methods reveals countries that stand out from others. The initial data, displayed on the first two factors' coordinate plane, visually showed that Chad stands out from other countries. Chad is a Central African country where the economy is underdeveloped, and the mortality and suicide rates are exceptionally high. By applying principal component analysis, a graph of the first two principal components was created. These two components explain the largest part of the variance. The graph not only shows Chad but also India, located in South Asia. India is the second most populous country in the world, with an exceptionally high number of people living there.

By formulating and testing hypotheses, it was found that the average number of suicides among men is higher than among women in all clusters. Differences between men and women also appear when testing the hypothesis about the equality of the expected life expectancy averages of men and women.



















