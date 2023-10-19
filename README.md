# ci-python-app.yml
Python app.
name: Python Hello World Deployment

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: 3.8

    - name: Install dependencies
      run: |
        pip install -r requirements.txt
      working-directory: ./python-app

    - name: Run Python App
      run: |
        python app.py
      working-directory: ./python-app
