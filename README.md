# Automated Dataset Fetcher

This dataset contains information on mine accidents from the year 2000 to 2022. The data has been collected from the Mine Safety and Health Administration (MSHA), and sensitive information has been excluded during the data encoding process. The dataset consists of 255,585 accidents, each described by 57 features.

## Dataset Source

The dataset can be downloaded from the following source:

[Accidents.zip](https://arlweb.msha.gov/OpenGovernmentData/DataSets/Accidents.zip)

## Installation and Usage

To use this dataset, follow these steps:

### Step 1: Download the zip file

Use the following code to download the zip file:

```python
import urllib.request
zip_url = "https://arlweb.msha.gov/OpenGovernmentData/DataSets/Accidents.zip"
urllib.request.urlretrieve(zip_url, "Accidents.zip")
```

### Step 2: Extract the target file from the zip file
Extract the relevant text file from the downloaded zip file. The code snippet below demonstrates how to extract the file using Python's zipfile module:
```python
import zipfile

with zipfile.ZipFile("Accidents.zip", "r") as zip_ref:
    file_names = zip_ref.namelist()
    target_file = [name for name in file_names if name.lower().endswith('.txt')]
    if len(target_file) > 0:
        zip_ref.extract(target_file[0], path="/content/extracted_files_directory")
    else:
        print("No text file found in the zip archive.")
```

### Step 3: Read the text file into a pandas DataFrame
Once the file has been extracted, you can read it into a pandas DataFrame using the read_csv function. Make sure to provide the correct file path and delimiter:

```python
import pandas as pd

file_path = "/content/extracted_files_directory/" + target_file[0]
df = pd.read_csv(file_path, delimiter="|", encoding='latin1')
```
### Final
You can visualize the data set with a tool of your liking or use this code to scrap any other site that downloads a zip file.
