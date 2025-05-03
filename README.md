# VYB-AI
# 🥘 VYB AI Nutrition Estimator

This tool estimates nutrition values for common Indian dishes based on ingredient lists, standard unit conversions, and a nutrition database.

---

## 📌 Problem Statement

Estimate the nutritional value per **standard serving** of a home-cooked Indian dish, accounting for real-world variability in:
- Recipe structure
- Household measurements
- Ingredient naming
- Serving sizes

---

## 🧱 Project Structure & Modularization

- `fetch_recipe(dish_name)` – Simulates or fetches a generic ingredient list
- `normalize_ingredients(ingredients)` – Extracts quantity/unit from text
- `map_to_nutrition_db(ingredients, db)` – Synonym/spelling matching to nutrition DB
- `convert_to_grams(ingredients, conversion_table)` – Converts household units to grams
- `calculate_nutrition(ingredients, nutrition_db)` – Uses sum-product for nutrients
- `classify_dish(dish_name)` – Maps dish to a type (e.g., Wet Sabzi)
- `extrapolate_per_serving(nutrition_totals, total_weight)` – Scales to 1 serving

---

## ✅ Assumptions Made

- Ingredient weights are approximated using household measure mappings (e.g., 1 cup chopped onion ≈ 80g)
- Recipes are assumed to be for 3–4 people (total ~600–800g cooked weight)
- Per-serving standard is: `Wet Sabzi = 180g`, `Dal = 200g`, etc.
- Ingredient synonyms are handled with partial string matching
- If ingredient is missing or unit unrecognized, it is skipped (gracefully)

---

## 🧪 Sample Input/Output

### Input: `"Paneer Butter Masala"`

```json
{
  "estimated_nutrition_per_200ml_katori": {
    "calories": 280.24,
    "protein": 11.77,
    "carbs": 5.25,
    "fat": 22.17
  },
  "dish_type": "Wet Sabzi",
  "ingredients_used": [
    { "ingredient": "Paneer", "quantity": "0.75 cup cubes" },
    { "ingredient": "Butter", "quantity": "2 teaspoons" },
    { "ingredient": "Tomato", "quantity": "0.5 cup puree" },
    { "ingredient": "Onion", "quantity": "0.5 cup chopped" },
    { "ingredient": "Cream", "quantity": "1 tablespoon" }
  ]
}

{

Here is the working version of your nutrition estimation program.
For the test input "Paneer Butter Masala", it outputs:
  "estimated_nutrition_per_200ml_katori": {
    "calories": 339.1,
    "protein": 15.59,
    "carbs": 6.33,
    "fat": 28.41
  },
  "dish_type": "Wet Sabzi",
  "ingredients_used": [
    { "ingredient": "Paneer", "quantity": "0.75 cup cubes" },
    { "ingredient": "Butter", "quantity": "2 teaspoons" },
    { "ingredient": "Tomato", "quantity": "0.5 cup puree" },
    { "ingredient": "Onion", "quantity": "0.5 cup chopped" },
    { "ingredient": "Cream", "quantity": "1 tablespoon" }
  ]
}

