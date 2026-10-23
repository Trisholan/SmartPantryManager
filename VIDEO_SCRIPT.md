# 5–7 Minute Demonstration Script

Use this as a guide after you have built and tested the app. Narrate in your own words and show your real GitHub repository and running application.

## 0:00–1:00 — GitHub
Show the repository URL, README and genuine commit history. Explain the development stages represented by the commits. Do not create a false history or claim work was completed before it was.

## 1:00–3:30 — Live app
1. Open the home screen and describe the app's purpose.
2. Open My Pantry and add an ingredient with a quantity, unit and optional expiry date.
3. Tap the ingredient and edit it; show the updated list.
4. Long-press an ingredient and delete it.
5. Demonstrate validation by submitting a blank name or invalid quantity.
6. Add the ingredients needed for one recipe and open Suggested Recipes.
7. Remove one required ingredient and return to suggestions to show that the recipe is no longer listed.
8. Close and reopen the app and show that pantry data persists.

## 3:30–5:45 — Code explanation
- Explain that each Activity represents a screen and that Intents navigate between Activities and pass a selected ingredient ID or recipe name.
- Open `DatabaseHelper.java` and explain how `SQLiteOpenHelper` creates tables and how CRUD operations persist pantry items.
- Explain `getStrictMatches()`: each recipe is checked ingredient by ingredient; if one required ingredient is missing, the recipe is excluded.

## 5:45–6:30 — Database choice
Explain that SQLite is local, works offline, avoids server setup and persists the user's pantry on the device.

## Before recording
Test the full flow first. Keep the recording between 5 and 7 minutes, ensure your voice is audible, and include the final MP4 in the submission ZIP. This starter project must be compiled and tested in Android Studio before you describe it as fully working.
