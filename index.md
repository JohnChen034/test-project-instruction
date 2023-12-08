---
layout: page
title: Animal Shelter 🐕🐈🦔🦜
description: Description of the recipes and ratings dataset in Project 3.
parent: 'Project 3'
nav_exclude: true
---

# Animal Shelter 🐕🐈🦔🦜

{:.no_toc}

## Table of Contents

{: .no_toc .text-delta }

1. [Getting the Data](#getting-the-data)
2. [Sample Questions](#sample-questions)
3. [Cleaning and EDA](#cleaning-and-eda)
4. [Assessment of Missingness](#assessment-of-missingness)
5. [Hypothesis Testing](#hypothesis-testing)



---

This dataset contains animal shelter dataset from [petfinder.com](https://www.petfinder.com/). It was previously used in
[this](https://pudding.cool/2019/10/shelters/) "Finding Forever Homes" website.

---

## Getting the Data
```
We may do it in two ways:
1. let them download the data by themselves through the api, I will provide them the code to do so.
2. pre-download the data and provide them the link to download the data. If they have extra need, they can download the
   data by themselves through the api. (I prefer this way more)
   - In this case, I am not sure what range of pre-downloaded data should I provide, since they data can be range from
     years ago to now, animals can be different, locations can also be different, and so on. In the sense of creating
     instructions, I will just skip considering this part.
```
Download the data [here](https://github.com/the-pudding/data/blob/master/dog-shelters/allDogDescriptions.csv), this
link will be replaced with a formal one if this dataset is chosen, now I am jsut using the github one. You should see
the following files:

- `allDogDescriptions.csv` contains all the data.

This is only a small subset of the original data, which is quite large. The original data is available on the api, which
can be retrieved by yourselves if you want options/extra data. The instructions are provided later in this page. Lets
now
learn more about this data first before you decide whether to extend the data or not.

A description of each column in both datasets is given below.

### allDogDescriptions.csv

note: since the github include a great description on this data, I will borrow the words from them.

- **What is this?**: Data collected from the [PetFinder
  API](https://www.petfinder.com/developers/) for all adoptable
  dogs in each state on September 20, 2019.
- **Source(s) & Methods**: All data except for `description` was
  collected using PetFinder’s V2 API method `get-animals` as
  described in their
  [documentation](https://www.petfinder.com/developers/v2/docs/#get-animals).
  Since the V2 API doesn’t return the full animal description, I
  was encouraged by the API maintainers to query the same animal
  profiles using the V1 API to acquire that information. Thus, I
  used all of the shelter ID’s returned from the V2 API calls to
  find all descriptions of dogs in each shelter and combine the
  two results by the animal’s unique ID.
- **Last Modified**: September 29, 2019
- **Spatial Applicability**: All data was collected for querying
  the API for adoptable dogs in each of the US states and the
  District of Columbia.
- **Temporal Applicability**: This data represents *a single day*
  of data. It was all collected on September 20, 2019.
- **Observations (Rows)**: There are 58,180 rows in this dataset.
  Each row represents an individual adoptable dog in the US on
  September 20, 2019. Each dog has a unique ID number. Unless
  otherwise noted, all of the data is exactly is reported by the
  shelter or rescue that posted an individual animal for adoption
  on PetFinder.
- **Variables (Columns)**: There are 36 columns in this dataset.
  They are described

below:

```
This column descriptions is mostly good. However, when we download directly using api, 
the raw dataset looks differnt when I was processsing it. For instruction purpose, I think
it is enough to use this column description + the github scraped 2019 dataset; but if we 
are really using it, we still need to redesign a little bit (shouldn't take much time)
```


| Header           | Description                                                                                                                                                  | Data Type |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------|
| id               | The unique PetFinder identification number for each animal                                                                                                   | integer   |
| org\_id          | The unique identification number for each shelter or rescue                                                                                                  | character |
| url              | The URL for each animal’s listing                                                                                                                            | character |
| species          | Species of animal                                                                                                                                            | character |
| breed\_primary   | The primary (assumed) breed assigned by the shelter or rescue                                                                                                | character |
| breed\_secondary | The secondary (assumed) breed assigned by the shelter or rescue                                                                                              | character |
| breed\_mixed     | Whether or not an animal is presumed to be mixed breed                                                                                                       | logical   |
| breed\_unknown   | Whether or not the animal’s breed is completely unknown                                                                                                      | logical   |
| color\_primary   | The most prevalent color of an animal                                                                                                                        | character |
| color\_secondary | The second most prevalent color of an animal                                                                                                                 | character |
| color\_tertiary  | The third most prevalent color of an animal                                                                                                                  | character |
| age              | The assumed age class of an animal (`Baby`, `Young`, `Adult`, or `Senior`)                                                                                   | character |
| sex              | The sex of an animal (`Female`, `Male`, or `Unknown`)                                                                                                        | character |
| size             | The general size class of an animal (`Small`, `Medium`, `Large`, `Extra Large`)                                                                              | character |
| coat             | Coat Length for each animal (`Curly`, `Hairless`, `Long`, `Medium`, `Short`, `Wire`)                                                                         | character |
| fixed            | Whether or not an animal has been spayed/neutered                                                                                                            | logical   |
| house\_trained   | Whether or not an animal is trained to not go to the bathroom in the house                                                                                   | logical   |
| declawed         | Whether or not the animal has had its dewclaws removed                                                                                                       | logical   |
| special\_needs   | Whether or not the animal is considered to have special needs (this can be a long-term medical condition or particular temperament that requires extra care) | logical   |
| shots\_current   | Whether or not the animal is up to date on all of their vaccines and other shots                                                                             | logical   |
| env\_children    | Whether or not the animal is recommended for a home with children                                                                                            | logical   |
| env\_dogs        | Whether or not the animal is recommended for a home with other dogs                                                                                          | logical   |
| env\_cats        | Whether or not the animal is recommended for a home with cats                                                                                                | logical   |
| name             | The animal’s name (as given by the shelter/rescue)                                                                                                           | character |
| status           | Whether the animal is `adoptable` or not                                                                                                                     | character |
| posted           | The date that this animal was first listed on PetFinder                                                                                                      | character |
| contact\_city    | The rescue/shelter’s listed city                                                                                                                             | character |
| contact\_state   | The rescue/shelter’s listed state                                                                                                                            | character |
| contact\_zip     | The rescue/shelter’s listed zip code                                                                                                                         | character |
| contact\_country | The rescue/shelter’s listed country                                                                                                                          | character |
| stateQ           | The state abbreviation queried in the API to return this result                                                                                              | character |
| accessed         | The date that this data was acquired from the PetFinder API                                                                                                  | character |
| type             | The type of animal                                                                                                                                           | character |
| description      | The full description of an animal, as entered by the rescue or shelter. This is the only field returned by the V1 API                                        |           |



If you want to scrap your own data, you can follow this instruction to help to build your custom dataset:
1. GET your API and Secret
  - go to [website for developers](https://www.petfinder.com/developers/) and sign up your own account. 
  - Then, you should be lead into a page with title "Petfinder for Developers", where there is a "GET AN API KEY" on the bottum. 
  - Fill in the information in the directed page, you may put your github link to Application URL. 
  - You should be getting your own API key and Secret for your account. You can always view your key in [account page](https://www.petfinder.com/user/developer-settings/)

2. Scrap you data:
  - The detailed documentation is [here](https://www.petfinder.com/developers/v2/docs/).
  - While we can use terminal to attrieve data, we can also do it in python. You should be able to play around this example code to scrap the data you want:


```python
import requests
import pandas as pd
import re
import numpy as np

# Step 1: Obtain an Access Token
token_url = "https://api.petfinder.com/v2/oauth2/token"
client_id = "5e7QRVqojLxeJUYfYxzIibHQCrl2VsNtCfYAyMkZvqtfdcn4Je"  # Replace with your client ID
client_secret = "h3iyq0JqPUcTW9lWgmmTYt7Tv6VbM6iZqhrYJ47C"  # Replace with your client secret

# Data for the POST request to get the token
data = {
    "grant_type": "client_credentials",
    "client_id": client_id,
    "client_secret": client_secret
}

# Send the POST request
response = requests.post(token_url, data=data)

access_token = response.json()['access_token']
    
# Prepare to collect data from multiple pages
all_data = []

for status in ['adoptable', 'adopted']:
    # Fetch data from the first 200 pages
    for page in range(1, 10):
        api_url = f"https://api.petfinder.com/v2/animals?page={page}&status={status}"
        headers = {"Authorization": f"Bearer {access_token}"}

        response = requests.get(api_url, headers=headers)

        json_data = response.json()
        all_data.extend(json_data['animals'])

df = pd.json_normalize(all_data)
```  

In the example data, I want to select both adopted and adoptable dogs(default) in page 1 to 9, then I store the final data in the df. 
- In order to get the data you want, you should check out the full parameters descriptions, which is also in [detailed documentation](https://www.petfinder.com/developers/v2/docs/). 

```
Again, since it is a test, I did not include instructions on getting the specific format. Besides, if we covered web craping before project3, then we may choose not to provide code to them. 

```

---

## Sample Questions

- What type of animals are more likely to be adopted?
- Which locations has the most adoption rate?
- What is the relationship between adoption and missing contact information?
- What is the relationships between locations and kinds of animals?

There are a lot of other questions that can be asked from either the template data or your retrieved data, so be creative! You are not limited to the sample
questions above.

---

## Cleaning and EDA

Follow all of the steps in
the [Requirement: Cleaning and EDA](../#requirement-cleaning-and-eda-exploratory-data-analysis) section.

Tips:


```
Didnt include much instructions or tips on this part because we have not decide what columns to preserve or drop, and it is harder when students are able to retrieve their own data. 
```


---

## Assessment of Missingness

Follow all of the steps in the [Requirement: Assessment of Missingness](../#requirement-assessment-of-missingness)
section.

***Note***: There are only three columns in the merged dataset that contain missing values; make sure you're using the
merged dataset for all of your analysis (and that you followed the steps at the top of this page exactly).

---

## Hypothesis Testing

Follow all of the steps in the [Requirement: Hypothesis Testing](../#requirement-hypothesis-testing) section. You can
use the sample questions for inspiration.
