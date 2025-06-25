# 🍲 OpenAI Recipe Blog Generator

This project uses the OpenAI API and Python to generate blog-style recipe posts based on a user’s dietary preferences, favorite cuisines, and ingredients on hand.

## 🧠 Objective

Use prompt engineering and the OpenAI Chat API to automate content creation for food bloggers.

## ⚙️ How It Works

- You define a user profile with:
  - Dietary restrictions
  - Cuisine preferences
  - Ingredients available
- The system sends this data to GPT to generate a formatted recipe post in **HTML**.
- Output includes title, description, ingredient list, and 6-step instructions.

## 💻 Example User Profile

```python
user_profile = {
    "dietary_restrictions": "vegetarian, no dairy",
    "cuisine_preferences": "Mediterranean, Thai",
    "ingredients_available": "chickpeas, bell peppers, garlic, lemon, olive oil"
}


# OpenAI-Python-API-Recipe-Blog
Codecademy
# Clone the repo
git clone https://github.com/adopt-adapt/OpenAI-Python-API-Recipe-Blog.git  
cd OpenAI-Python-API-Recipe-Blog

# Install dependencies (if any, or skip this)
pip install openai

# Run the script
python generate_blog.py

import openai

# Task 1: Import OpenAI and set up client
client = openai.OpenAI()

# Task 2–6: Create user profile dictionary
user_profile = {
    "dietary_restrictions": "vegetarian, no dairy",
    "cuisine_preferences": "Mediterranean, Thai",
    "ingredients_available": "chickpeas, bell peppers, garlic, lemon, olive oil"
}

# Task 7: System prompt dictionary
system_prompt = {
    "role": "system",
    "content": (
        "You are a recipe-generating assistant. Generate an HTML-formatted blog post "
        "based on the user's dietary restrictions, cuisine preferences, and ingredients on hand."
    )
}

# Task 8: User content part 1
user_content1 = (
    "I am creating a recipe blog post.\n"
    f"Dietary restrictions: {user_profile['dietary_restrictions']}\n"
    f"Cuisine preferences: {user_profile['cuisine_preferences']}\n"
    f"Ingredients available: {user_profile['ingredients_available']}"
)

# Task 9: User content part 2
user_content2 = (
    "\n\nThe blog post should include:\n"
    "- A title\n"
    "- A short introduction or description of the recipe\n"
    "- A list of ingredients\n"
    "- Step-by-step instructions (formatted as a list)\n"
    "Example format for ingredients: <ul><li>Ingredient 1</li><li>Ingredient 2</li></ul>\n"
    "Example format for steps: <ol><li>Step 1</li><li>Step 2</li></ol>"
)

# Task 10: User content part 3
user_content3 = (
    "\n\nOnly use the ingredients listed above. The recipe should be limited to one blog post, "
    "and the instructions should not exceed six steps."
)

# Task 11: Final user prompt dictionary
user_prompt = {
    "role": "user",
    "content": user_content1 + "\n" + user_content2 + "\n" + user_content3
}

# Task 12: Make the API call
response = client.chat.completions.create(
    model="gpt-3.5-turbo",
    messages=[system_prompt, user_prompt]
)

# Task 13: Print the generated HTML content
print(response.choices[0].message.content)

response = client.chat.completions.create(
    model="gpt-3.5-turbo",  # or "gpt-4-turbo-preview"
    messages=[system_prompt, user_prompt]
)

print(response.choices[0].message.content)


