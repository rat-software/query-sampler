# Query Sampler App

## Introduction

The Query Sampler App is a Flask-based web application that generates keyword ideas using the Google Ads API. The application requires API access to Google Ads Services to function correctly. It is developed by the research group Search Studies at the Hamburg University of Applied Sciences in Germany. The Query Sampler is part of the RAT project is funded by the German Research Foundation (DFG –Deutsche Forschungsgemeinschaft) from 8/2021 until 10/2024, project number 460676551.

- The Query Sampler was originally developed by Nurce Yacgi - https://github.com/yagci
- The update and the expansion of a web interface were implemented by Sebastian Sünkler - https://github.com/sebsuenkler

For detailed instructions on setting up and using the Google Ads API, visit the [Google Ads API Documentation](https://developers.google.com/google-ads/api/docs/start?hl=en). You will need to create an account and apply for a developer token to use the API. For Python implementation, refer to [Daniel Heredia Mejias' guide](https://www.danielherediamejias.com/python-keyword-planner-google-ads-api/).

## Dependencies

To install the necessary dependencies, run:

```bash
pip install flask
pip install flask_simplelogin
pip install python-dotenv
pip install pandas
pip install google-ads
pip install psycopg2
```

## Folder Structure and Important Files
- `app/`: Contains the Flask application.

- static/: Static files for the application.
- templates/: Templates used to render the app.
- keywords/: Templates for managing keyword sets and forms for language and region selection.
- studies/: Templates for creating and viewing studies. Templates for editing studies are also included.
- base.html: Base template, index, static legal site, and login template (for Flask-SimpleLogin).
- db.py: Library for all database operations. Change the database connection information here.
- forms.py: Contains form classes used in the app.
- routes.py: Flask router with all route handlers.
- google_ads/: Contains scripts for generating keyword ideas using the Google Ads API.

- `generate_user_credentials.py`:
1. Run `python generate_user_credentials.py --client_secrets_path=client.json` to create a new refresh token.
2. Open the provided URL in your terminal.
3. Log in with your Google-Ads credentials
4. Replace the refresh token in the `google-ads.yaml` file.

- `generate_keywords.py`: Script for generating keyword ideas. This script imports db.py to read from and write to the database and cannot be used standalone.
- `generate_keywords_demo.py`: Standalone script to test API access.
- `install/`: Contains CSV files and a script to insert official language and region codes provided by Google (necessary only for setting up a new database).
- `.flaskenv`: Contains environment parameters for the Flask app.

## Running the App
To test the app locally, use the built-in Flask server. Run the following command from the root folder:

```bash
flask run --host=0.0.0.0
```
