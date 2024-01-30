git clone <URL_Repository>
cd <Nama_Repository>

pip install requests
pip install pyserial
git add .
git commit -m "Menambahkan kode sumber dan mengonfigurasi ThingsSpeak"
git push origin main
python3 radiasi_sensor.py
name: Continuous Integration

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2

      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: 3.8

      - name: Install Dependencies
        run: |
          pip install requests
          pip install pyserial

      - name: Run Tests
        run: python radiasi_sensor.py
        
