# Representations of violence and public appraisal

## Abstract 
After the Aurora shooting in Colorado in July 2012 (twelve people killed and 58 others injured), during the premiere of The Dark Knight Rises, controversy arose around the release of the film Joker. Considered too violent, very strict security measures were taken before its theatrical release, where it is rated R. Violence has always been a pillar in media. From tragic Greek theater to public executions, its powerful emotional impact stirs attention. In films, violence can manifest in increased sensory details. The representation of violence can be, depending on the audience's appreciation, the era, the culture, more or less explicit, more or less tolerated with different stereotypes in play. Our project aims to analyze the co-dependency between public appraisal, tolerance, and representations of violence, under different dimensions such as financial success, the tone of the films (comedy or drama), and geo-political context (nation, era).

## Research questions 

1.) [How does the public tolerate and appreciate violence in terms of tone and targets](https://maelysbillon.github.io/ada-template-website/public_appreciation) ?
> Following this first question, we evaluate the success of violent movies. In addition, we elaborate typical types of violence for each genre and the tolerance towards violence. 

2.) [How is violence represented in different countries and languages](https://maelysbillon.github.io/ada-template-website/countries_and_languages_differences)? 
> Here we identify typical types of violence per country / language and we also want to identify types of violence that are tabood in countries. Furtermore, we try to link the results of different countries trough their geo-political situation. 

3.) [How is violence represented through actors](https://maelysbillon.github.io/ada-template-website/actor_personas)? 
> For each type of violence we find a persona that represents this type of violence. 

## Proposed additional datasets

### Query wikidata

To use the IMDB database in a later step, we first have to retrieve the IMDB IDs because our dataset is indexed by the freebase ID. Luckily, the wikidata page of a movie contains both the freebase ID and the IMDB IDs. We queried the [wikidata SPARQL query service](https://query.wikidata.org/) resulting in a dataset that consists of one column each for wikidata ID, freebase ID, IMDB ID. The query in detail and the retrieved file are in the [wikidata_IDs folder](/wikidata_IDs/), and the processing of the retrieved file is in [data_handling.ipynb](/data_handling.ipynb). 

### Wars

In order to get a better idea of the geopolitical situation of the countries, we decided first to study their wars. For this we found several datasets from [CoW](https://correlatesofwar.org/data-sets/cow-war/). We decided to focus on inter-state and intra-state wars. In order to use this data in our analysis, we pre-processed it so that we could have a dataset containing only two columns: one with the names of the countries, the other containing the years in which they were at war. 

### Financial crisis

Another way to study the geopolitics of a country is to look at its financial situation. This is what we will be able to do thanks to [Data on financial crises: Global Crises by Country - Harvard Business School](https://www.hbs.edu/behavioral-finance-and-financial-stability/data/Pages/global.aspx).
This dataset does not need much pre-processing, we just had to select the columns we were interested in. As the dataset is very large, we removed rows concerning countries that have not made films (regarding of CMU dataset), and data that are too old (before the first films of our dataset).

However, as with the war datasets, we will have to think of a solution for the countries in the CMU dataset, but not in the new ones. The ideas we have are in part 4 of our notebook.



## Methods 

We assess violence and the type of violence in movies by detecting keywords in the plot summaries. Firstly, we tokenize the plot summary and remove linguistic variations in the words as upper and lower case. In the project, we can use the [lemmatization method](https://www.nltk.org/api/nltk.stem.wordnet.html?highlight=wordnetlemmatizer#nltk.stem.wordnet.WordNetLemmatizer) of the [natural language toolkit](https://www.nltk.org/). Lemmatization reduces words to their base for also considering lexical knowledge. If a plot summary contains tokens like “murder”, “kill” or “slaughter” we mark a film containing violence of the type of murder. For our initial analysis, we used a dictionary mapping the type of violence to keywords with 79 keywords which we enriched as a part of the final project. 

### Public tolerance and appreciation

We will evaluate the appreciation of violence in movies in two ways. First, we do a regression analysis with the presence of violence types in films as predictors and the box office revenue as an outcome. Secondly, we use the same bag of words pipeline for detecting violent movies to catch positive and negative movie reviews in our IMDB reviews dataset. Again we can do a regression analysis but now with the fraction of positive reviews as the outcome variable. The first analysis tells us about the perception of the film after its release and the second about how people perceive the film since the year 1990 when IMDB came online. 

We evaluate the tolerance of violence through our parental rating data set. Since each country issues parental ratings, we compare the parental ratings for a selection of countries for films having parental ratings in all countries. Furthermore, we analyze the tolerance of certain types of violence in countries as we did for sexual violence in France in our pre-analysis. 

Furthermore, we can test hypotheses about the relation between certain types of violence and movie tones. For example, in our pre-analysis we notice that there are more comedic films with torture than comedic films with sexual violence. In opposite, dramas have more sexual violence than torture. This would enable us to study the comedic tolerance for certain types of violence.

### Violence in countries and languages 

Firstly, we compute the fraction of violent movies for each type of violence per country and language. We did that in our pre-analysis for the overall presence of violence, where we identified Latin as the most violent language (with more than 60 movies), where 92% of all films using the Latin language are violent. On the other hand, only 49% of all films using Greek are violent.

### Actor personas for violence types 

Again, we compute the fraction of violent movies for each type of violence, but this time per actor. In our pre-analysis, we studied the overall presence of violence, where we identified two actors playing only in violent films (again more than 60), namely Hoot Gibson and Harry van Meter. However, Vivian Rich didn’t play in any violent movies. We extract personas for each type of violence by averaging all actor attributes that appear in movies of a type of violence. 

## Proposed timeline

| until | description |
| ----- | ------| 
|26.11. |  Refining the bag of words pipeline (lemmatization / dictionary) & create dictionaries for positive / negative words |
|02.12. |  Homework 2 deadline |
|10.12. |  Research questions answered|
|17.12. |  Visualizations and surrounding text for the project presentation prepared |
|23.12. |  Milestone 3 deadline|

## Organization within the team

| member | task |
| --- | --- |
| Maëlys | Bag of words pipeline, success of violent movies |
| Sebastian | Typical types of violence per genre, tolerance towards violence |
| Max| violence in countries and languages |
| Tanguy | representation of violence trough actors and personas |  
