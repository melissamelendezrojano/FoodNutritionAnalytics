#### Remark:
This is a competition from Datacamp called "What foods are the most nutritions?"
You can see the publication I submitted in the following [link](https://www.datacamp.com/datalab/w/a33a04b6-a134-40a4-9752-0c198f1a144f).

# What is good food?

## 📖 Background
You and your friend have gotten into a debate about nutrition. Your friend follows a high-protein diet and does not eat any carbohydrates (no grains, no fruits). You claim that a balanced diet should contain all nutrients but should be low in calories. Both of you quickly realize that most of what you know about nutrition comes from mainstream and social media.

Being the data scientist that you are, you offer to look at the data yourself to answer a few key questions.

## 💾 The data

You source nutrition data from USDA's FoodData Central [website](https://fdc.nal.usda.gov/download-datasets.html). This data contains the calorie content of 7,793 common foods, as well as their nutritional composition. Each row represents one food item, and nutritional values are based on a 100g serving. Here is a description of the columns:

- **FDC_ID**: A unique identifier for each food item in the database.
- **Item**: The name or description of the food product.
- **Category**: The category or classification of the food item, such as "Baked Products" or "Vegetables and Vegetable Products".
- **Calories**: The energy content of the food, presented in kilocalories (kcal).
- **Protein**: The protein content of the food, measured in grams.
- **Carbohydrate**: The carbohydrate content of the food, measured in grams.
- **Total fat**: The total fat content of the food, measured in grams.
- **Cholesterol**: The cholesterol content of the food, measured in milligrams.
- **Fiber**: The dietary fiber content of the food, measured in grams.
- **Water**: The water content of the food, measured in grams.
- **Alcohol**: The alcohol content of the food (if any), measured in grams.
- **Vitamin C**: The Vitamin C content of the food, measured in milligrams.

## 💪 Competition challenge

Create a report that covers the following:

1. Which fruit has the highest vitamin C content? What are some other sources of vitamin C?
2. Describe the relationship between the calories and water content of a food item.
3. What are the possible drawbacks of a zero-carb diet? What could be the drawbacks of a very high-protein diet?
4. According to the Cleveland Clinic [website](https://my.clevelandclinic.org/health/articles/4182-fat-and-calories), a gram of fat has around 9 kilocalories, and a gram of protein and a gram of carbohydrate contain 4 kilocalories each. Fit a linear model to test whether these estimates agree with the data.
5. Analyze the errors of your linear model to see what could be the hidden sources of calories in food.

# Executive Summary: Nutrition and Diet Analysis

![image1](image1.jpg)
## Introduction:
In response to a debate about nutrition between a friend and me, we decided to explore USDA's FoodData Central data to gain a deeper understanding of the relationship between nutrients in foods and popular diets. Our goal is to use concrete data to inform our discussions and decisions about healthy eating habits.

## Key Findings:
#### ✅  High in Vitamin C
According to the analysis, the fruit with the highest vitamin C content is acerola, with an impressive amount of 1,677.6 mg per 100 g serving. Acerola is a plant and the fruit is called acerola cherry, native to Paraguay and Brazil in South America, Central America and southern Mexico, Puerto Rico, Dominican Republic and Haiti, but is now also being grown as far noth as Texas and in subtropical areas of Asia such as India. Acerola cherry is similar to a cherry, is a red color when ripe and its flavor is slightly acidic. Acerola juice is in second position.

Guavas in in third position, with a vitamin C content of 228,3 mg per 100 g serving.

Other sources of vitamin C that don't fall under the "Fruits and Fruit Juices" category are:
- First is GERBER baby food, which includes apple, carrot and pumpkin (2732 mg per 100g serving). 

- In second and third place are two drinks, the first of assorted fruits with added vitamin C, and in third place an orange drink (both with 2400 mg per 100g serving).

- In fourth place is a vegetable: Peppers, sweet, red, freeze-dried (1900 mg per 100g serving).

It is possible that some of the foods described in this list have added vitamin C, one would have to analyze the ingredients in depth and look at their vitamin C content separately. 

Also, in the fifth position is acerola.


#### ✅ Relationship between Calories and Water Content
According to the Pearson correlation coeficient (-0.895) and the scatter plot, the relationship between calories and water is negative. It means that when a food has more content of water, the content of calories is lower and it happens because water is thermodynamically very stable.

This relationship suggests that foods with higher water content tend to be lower in calories, supporting the importance of hydration and consumption of fresh foods in a balanced diet.


#### ✅ Drawbacks of Extreme Diets
In analyzing the data, there are some triking differences between an all-product diet, a zero-carb diet and a high-protein diet.

                          ----------------- Mean of each nutritional characteristic -----------------
 
| Averages | All food  | Zero-carb diet | High-protein diet |
| ------------- | ---: | ---: | ---: |
| **Calories (kcal)** | 222.24 | `233.55` | `171.76` |
| **Protein (g)** | 11.92 | 22.28 | 19.40 |
| **Carbohydrate (g)** | 19.56 | `0.00` | `0.00` |
| **Total fat (g)** | 10.68 | 15.58 | 8.22 |
| **Cholesterol (mg)** | 42.73 | `93.45` | `75.81` |
| **Fiber (g)** | 1.83 | `0.00` | `0.99` |
| **Water (g)** | 56.03 | 61.08 | 66.02 |
| **Alcohol (g)** | 0.12 | 0.10 | 0.00 |
| **Vitamin C (mg)** | 8.44 | `0.66` | 5.19 |

According to the table, in a zero carb diet and a high-protein diet, the average content of carbohydrate is null in both cases. The average content of fiber is null in zero-carb diet and 0.99 g in a high-protein diet, that's half the fiber in a diet that include all kind of food.

The average content of calories is a litle higher in zero-carb diet and lower in a high-protein diet. The average content of cholesterol is increased significantly in a zero-carb diet (93.45 mg), and also in a high-protein diet (75.81 mg). The average content of vitamin C in a zero-carb diet is lower by far that other diets.

in addition to the variation of average in zero-carb diet and high-protein diet, the zero-carb diet exclude some categories:
- Vegetables and vegetables products
- Breakfast cereales
- Fruits and fruit juices
- Cereal grains and pasta
- Nut and seed products
- Meal, entrees and side dishes

While the dataset has 7.793 food items, zero-carb diet has 2.138 food items and high-protein diet has 3.745 food items. This represent a reduction of **72,56%** and **51'94%** food items for each diet.

With these data, I consider that isn't appropiate to follow niether a zero-carb diet not a high-protein diet for a long time.


#### ✅ Validation of Caloric Estimates
The calorie content is calculated based on the provided values for protein, carbohydrate and fat, and then compared to the actual calorie conten listed in the dataset.

Equation:  Y = 4Xp + 4Xc + 9Xf

Where:
- Xp: grams of protein
- Xc: grams of carbohydrate
- Xf: grams of fat
- Y: actual caloric content (in kcal)

The ecuation represents the expected caloric content based on the provided nutritional composition.

Linear regression modeling is used to test whether traditional estimates of calories per gram of nutrients (total fat, protein, carbohydrate) align with the data. Where the dependent variable (Y) is the actual caloric content, and the independent variables are the grams of protein (Xp), carbohydrate (Xc) and fat (Xf).


#### ✅ Error Analysis

The dataset has a total of 7,793 rows and 192 observations with higher residuals are obtained, which represents approximately 2.5% of the total dataset.

This could indicate that there is a notable proportion of data that isn't adequately explained by the linear regression model.
