# Smart Pantry Manager — Written Report Draft

**Student name:** [Enter your name]  
**Student number:** [Enter your ITS number]  
**Module:** Mobile App Development 700  
**Date:** [Enter submission date]  
**GitHub repository:** [Add your real repository URL after publishing]

## Table of Contents
1. Introduction
2. System Design
3. Implementation and Key Code
4. Testing and Screenshots
5. Challenges and Solutions
6. Conclusion and Reflection
7. References

## 1. Introduction
Smart Pantry Manager is a Java-based Android application intended to help users reduce food waste by recording ingredients available at home and identifying recipes that can be prepared from those ingredients. It is designed for users who want to make practical use of leftovers without being encouraged to shop for missing ingredients.

The app includes pantry management, recipe suggestions, recipe details and settings. SQLite is used to store pantry records locally so that data can remain available after the application is closed.

## 2. System Design

### 2.1 Screen flow
Home → My Pantry → Add/Edit Ingredient  
Home → Suggested Recipes → Recipe Detail  
Home → Settings

### 2.2 Data model
**Pantry table:** `_id` (primary key), `name`, `quantity`, `unit`, `expiry`.  
**Recipes table:** `_id` (primary key), `name`, `ingredients`, `method`.

The current prototype stores recipe ingredients as a comma-separated list. A production-ready implementation should use normalized recipe and recipe-ingredient tables with required quantities and units.

## 3. Implementation and Key Code

### 3.1 SQLite persistence
`DatabaseHelper` extends `SQLiteOpenHelper`, creates the pantry and recipes tables, seeds 20 recipes on first database creation, and implements insert, update, delete and read operations. SQLite is suitable for this project because the pantry is personal data and the application can work offline.

### 3.2 Pantry CRUD and validation
`IngredientFormActivity` validates that name, quantity and unit are supplied and rejects non-numeric or non-positive quantities. `PantryActivity` lists stored ingredients, opens an item for editing when tapped, and offers deletion on long press.

### 3.3 Strict recipe matching
`DatabaseHelper.getStrictMatches()` loops through every recipe and checks each required ingredient against the pantry. If any required ingredient is missing, the recipe is excluded. Basic singular/plural normalization is applied.

**Known limitation to address before submission:** the supplied starter implementation uses a simplified threshold of 1.0 pantry units for each ingredient; it does not yet compare recipe-specific required quantities or convert units. Extend the model and algorithm before claiming full quantity-aware matching.

## 4. Testing and Screenshots
Insert real screenshots from the running app and replace the placeholders below. Do not use mockups as evidence.

- **Figure 1:** Home screen.
- **Figure 2:** Pantry list with saved ingredients.
- **Figure 3:** Add ingredient form and validation message.
- **Figure 4:** Edited pantry item.
- **Figure 5:** Delete confirmation and updated list.
- **Figure 6:** Suggested recipes with a complete ingredient match.
- **Figure 7:** Suggested recipes after removing a required ingredient.
- **Figure 8:** Recipe detail screen.
- **Figure 9:** Settings screen.
- **Figure 10:** Data still present after closing and reopening the app.

## 5. Challenges and Solutions
Replace these with challenges you genuinely encountered while implementing and testing the application.

1. **Persistent storage:** Pantry records must remain after the app closes. SQLite was selected to store records locally.
2. **Strict recipe matching:** Partial matches must not be shown as suggestions. The matching method rejects a recipe as soon as a required ingredient is not found.
3. **Input validation:** Empty names and invalid quantities can lead to unusable records. The ingredient form validates required fields and positive numeric quantities.

## 6. Conclusion and Reflection
The Smart Pantry Manager prototype demonstrates how a Java Android application can combine Activities, Intents, input validation and SQLite persistence to support pantry management. The recipe suggestion feature applies a strict all-ingredients-present rule rather than recommending recipes with missing ingredients.

Further development should store recipe ingredient quantities and units separately, support unit conversion, add automated tests, and implement reliable expiry reminders. The final report should describe only features that have been tested on the actual running application.

## 7. References
Android Developers (n.d.) *Save data using SQLite*. Available at: https://developer.android.com/training/data-storage/sqlite

Android Developers (n.d.) *Activities*. Available at: https://developer.android.com/guide/components/activities

Android Developers (n.d.) *Intents and intent filters*. Available at: https://developer.android.com/guide/components/intents-filters

Android Developers (n.d.) *Build a list with RecyclerView*. Available at: https://developer.android.com/develop/ui/views/layout/recyclerview
