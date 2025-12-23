# Food
Four ingredient recipe 
import random

# Categories of ingredients (with some overlaps for variety)
proteins = ["chicken", "beef", "tofu", "salmon", "eggs", "pork", "shrimp", "lentils", "turkey", "chickpeas"]
veggies = ["broccoli", "spinach", "tomatoes", "bell peppers", "onions", "carrots", "zucchini", "mushrooms", "potatoes", "garlic"]
carbs = ["rice", "pasta", "bread", "quinoa", "noodles", "couscous", "tortillas", "oats", "barley"]
dairies = ["cheese", "milk", "butter", "yogurt", "cream", "parmesan", "feta", "mozzarella"]
spices_herbs = ["salt", "pepper", "basil", "oregano", "garlic powder", "cumin", "paprika", "thyme", "rosemary", "chili powder"]
oils_sauces = ["olive oil", "soy sauce", "tomato sauce", "honey", "lemon juice", "vinegar", "sesame oil", "mustard", "hot sauce"]
fruits = ["apples", "bananas", "lemons", "berries", "oranges", "avocado", "pineapple", "mango"]
others = ["flour", "sugar", "chocolate", "nuts", "beans", "corn", "peas"]

# Combine all ingredients into one big pool
all_ingredients = proteins + veggies + carbs + dairies + spices_herbs + oils_sauces + fruits + others

def generate_random_recipe():
    # Pick 4 unique ingredients
    ingredients = random.sample(all_ingredients, 4)
    
    # Fun random title words
    title_words = ['Delight', 'Surprise', 'Bowl', 'Stir-Fry', 'Salad', 'Bake', 'Special', 'Fusion', 'Magic', 'Adventure']
    title = f"Random Four-Ingredient {random.choice(title_words)}"
    
    print("Recipe Title:", title)
    print("\nIngredients:")
    for ing in ingredients:
        print("- " + ing.capitalize())
    
    print("\nInstructions:")
    print("1. Gather and prepare your ingredients (chop, slice, etc. as needed).")
    print(f"2. Start by cooking or combining {ingredients[0].capitalize()} and {ingredients[1].capitalize()}.")
    print(f"3. Add {ingredients[2].capitalize()} along with {ingredients[3].capitalize()} for flavor.")
    print("4. Mix, cook, or bake until it looks/tastes ready. Be creative and enjoy your unique creation!")

# Run it to generate a recipe
generate_random_recipe()

# Optional: Uncomment to generate multiple
# for _ in range(3):
#     generate_random_recipe()
#     print("\n" + "-"*40 + "\n")
