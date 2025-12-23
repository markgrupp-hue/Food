# Food
Four ingredient recipe 
import random

import requests
import os

# Set your Spoonacular API key here (get it from https://spoonacular.com/food-api)
API_KEY = "d90ff91f033248dcbe8c15c03993a8be"  # Replace with your actual key

if API_KEY == "d90ff91f033248dcbe8c15c03993a8be":
    print("Please replace 'YOUR_API_KEY_HERE' with your actual Spoonacular API key.")
    exit()

BASE_URL = "https://api.spoonacular.com/recipes"

def search_recipes(max_ingredients=4, number=20):
    url = f"{BASE_URL}/complexSearch"
    params = {
        "apiKey": API_KEY,
        "maxIngredients": max_ingredients,
        "number": number,
        "addRecipeInformation": True,  # Gets summary info including time/servings
        "fillIngredients": True,      # Ensures ingredients are included
        "sort": "random"               # Optional: for variety
    }
    
    response = requests.get(url, params=params)
    if response.status_code != 200:
        print(f"Error: {response.status_code} - {response.text}")
        return []
    
    data = response.json()
    return data.get("results", [])

def get_recipe_details(recipe_id):
    url = f"{BASE_URL}/{recipe_id}/information"
    params = {"apiKey": API_KEY}
    response = requests.get(url, params=params)
    if response.status_code == 200:
        return response.json()
    return None

if __name__ == "__main__":
    print("Fetching recipes with up to 4 ingredients...\n")
    recipes = search_recipes(max_ingredients=4, number=20)
    
    if not recipes:
        print("No recipes found or API error.")
    else:
        print(f"Found {len(recipes)} recipes:\n")
        for i, recipe in enumerate(recipes, 1):
            title = recipe["title"]
            ready_in = recipe.get("readyInMinutes", "N/A")
            servings = recipe.get("servings", "N/A")
            source_url = recipe["sourceUrl"]
            ingredients = [ing["name"] for ing in recipe.get("extendedIngredients", [])]
            
            print(f"{i}. {title}")
            print(f"   Ready in: {ready_in} minutes | Servings: {servings}")
            print(f"   Ingredients ({len(ingredients)}): {', '.join(ingredients)}")
            print(f"   Full recipe: {source_url}\n")
