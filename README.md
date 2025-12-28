# README.md

This is a Flask API for places review app. It uses SQLite database. Follow these simple steps to run it.

## Requirements

- Python 3.8 or higher
- Files needed: `app.py`, `data_population_script.py`, `requirements.txt`


## Step 1: Install Packages

Open terminal in this folder. Run this command:

```
pip install -r requirements.txt
```

This installs Flask, Flask-SQLAlchemy, and SQLAlchemy.

## Step 2: Add Sample Data

Run the data population script first:

```
python data_population_script.py
```

This creates 50 users, 100 places, and many reviews. It shows sample login phones at end.

## Step 3: Start the App

Run the main app:

```
python app.py
```

App runs on `http://127.0.0.1:5000`. Keep terminal open.

## API Endpoints

All need login token except register. Use tools like Postman or curl.

**Register (POST)** `/api/register`

```
{
  "name": "John Doe",
  "phone": "+919876543210"
}
```

Gets back a token.

**Login (POST)** `/api/login`

```
{
  "phone": "+919876543210"
}
```

Gets new token.

**Add Review (POST)** `/api/reviews`
Add `Authorization: Bearer YOUR_TOKEN` in headers.

```
{
  "place_name": "Starbucks",
  "address": "Bandra West, Mumbai",
  "rating": 5,
  "text": "Great coffee!"
}
```

Optional: add `"category": "Restaurant"`.

**Search Places (GET)** `/api/places/search`
Add `Authorization: Bearer YOUR_TOKEN`. Use query params:

- `?name=Starbucks`
- `?min_rating=4`
- `?category=Restaurant&min_rating=3`
Shows places sorted by rating.


## Test with Sample Data

After Step 2, use phones printed by script. App has restaurants, doctors, shops, salons, gyms in Mumbai areas.

## Database

File `places_review.db` created automatically. No setup needed.

## Stop App

Press `Ctrl+C` in terminal.
