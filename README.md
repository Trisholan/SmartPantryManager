# Smart Pantry Manager

A Java Android application prototype for reducing food waste by suggesting recipes that can be made from ingredients already stored in a user's pantry.

## Database choice
The app uses SQLite through Android's `SQLiteOpenHelper`. It is local, requires no account or network connection, and persists pantry data between app sessions. The database seeds 20 recipes on first run.

## Features
- Add, view, edit and delete pantry ingredients.
- Local SQLite persistence.
- 20 preloaded recipes with simple methods.
- Strict suggested-recipe list: every named recipe ingredient must be present in the pantry.
- Recipe details, input validation, and a settings screen.
- No GPS or mapping features.

## Setup
1. Install Android Studio with an Android SDK (API 35 or compatible).
2. Open this folder in Android Studio.
3. Allow Gradle to sync.
4. Run the app on an emulator or Android device (minimum Android 6.0 / API 23).

## Important implementation note
The sample strict-matching logic uses ingredient-name normalization for basic singular/plural differences and checks a simplified quantity threshold of 1.0 per required ingredient. It does not yet model recipe-specific amounts or convert units. To fully satisfy the assignment's quantity requirement, extend the recipe data model to store a required quantity and unit for each ingredient and compare these with pantry quantities.

## Suggested Git workflow
Create a public GitHub repository and push the project in incremental stages as you implement and test it. Do not fabricate commit history: make meaningful commits as real work is completed, for example:
- Create Android Studio project and manifest
- Add SQLite database and seed recipe collection
- Implement pantry CRUD screens
- Add strict recipe matching and detail view
- Add validation and settings
- Update report and README after testing

## Testing checklist
- [ ] Add an ingredient and verify it appears in the pantry.
- [ ] Edit the ingredient and verify changes persist.
- [ ] Delete the ingredient and verify it disappears.
- [ ] Close/reopen the app and verify pantry data remains.
- [ ] Add all ingredients for one recipe and verify it appears in suggestions.
- [ ] Remove one required ingredient and verify the recipe disappears.
- [ ] Try blank fields and invalid quantities.
