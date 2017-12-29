# meal-planning

## Fast grocery lists from meal plans.

### Background
Food waste is an important issue. In the developed countries, about [220 pounds (100kg) of food is wasted per year per person](http://large.stanford.edu/courses/2012/ph240/briggs1/docs/mb060e00.pdf).

From my own experience, it seems like a lot of the food I've thrown out has been from these two cases:
1. I intended to make something, but never did.
2. I put making something off too long, and the associated food went bad (especially with vegetables and fruits).

The FAO report I linked above pretty much agrees: (pg.7)
```
At the consumer level, insufficient purchase planning and expiring ‘best-before-dates’ 
also cause large amounts of waste, in combination with the careless attitude of those 
consumers who can afford to waste food.
```

Given that food waste in developed nations is primarily the fault of the consumer, I wrote this code to empower grocery decision making.

### Basic Description
First, input a bunch of recipes you're willing to make:
```
Dan Dan Noodles|1tbsp peanut oil,18oz chopped ham,3tbsp ginger,1.125cups chicken broth,3tbsp chili sauce,1.5tbsp rice vinegar,3tbsp soy sauce,3tbsp peanut butter,1.5tsp sichuan peppercorns,pinch salt,pinch pepper,12oz egg noodles,3tbsp roasted peanuts,4.5 scallions
Sweet Chili Shrimp|8oz cellophane noodles,1lb shrimp,2tsp cornstarch,0.5tsp salt,0.25tsp black pepper,1tbsp soy sauce,1tbsp honey,1tbsp rice vinegar,2tbsp chili sauce,1tbsp Shaoxing rice wine,1tbsp peanut oil,2tbsp minced garlic,1tsp ginger
Shrimp With Lobster Sauce|2tbsp peanut oil,3 garlic cloves,16oz shrimp,4tsp Shaoxing rice wine,2cups chicken broth,0.5tsp sesame oil,0.66tsp sugar,0.66tsp salt,pinch white pepper,0.66cups peas,4tsp cornstarch,2 eggs,2 scallions
Egg Drop Soup|6cups chicken broth,1tsp Shaoxing rice wine,0.25tsp ginger,1tsp sugar,0.25tsp white pepper,1tbsp cornstarch,2 eggs,pinch salt,1 scallions
...
```

Second, input recipe names and meal quantities into the toIngredients() call.
![meal inputs](https://i.imgur.com/AjUxAPY.png)

You're done! It prints out a grocery list for the given meals.

You can also check all the meal names you put in \_INFO.txt by calling checkMenu().

### Some usage details

The .txt folder that holds the recipe info is called \_INFO.txt. It accepts recipe information as follows:

```Recipe Name|2units Ingredient 1,3units Ingredient 2,...```

The splitting happens at the pipe (|) character and at the spaces after the commas, so it's important to properly format those.

Be sure not to leave a newline (\n) at the end of the text file when you're done. Otherwise getInfo() will throw errors.

Fundamentally, unit_sums() is unable to deal with situations like "2 chopped cabbages + 1 cup chopped cabbage". The units are different and it's not clear to how add them together without prior knowledge. When these situations pop up, unit_sums() will throw errors between the two dotted lines. Keep those in mind and edit the final answer as necessary.
