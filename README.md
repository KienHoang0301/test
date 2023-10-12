## Accuracy

| Model                  | Language  | Accuracy     | 
| -------                | ---       | ---       |
| vinai/bartpho-syllable | Vietnamese | 66% |
| sentence-transformers/all-MiniLM-L6-v2 | English | 100% |
> Accuracy: given document for chatGPT generate pairs of questions and answer. Then use our model to predict the answer. The ground truth answer vs predict answer then compare again using chatGPT to check whether it relevant in context.


## Speed

- Pre:   
    - Check file for download    
    - Download
    - (*)Split(Embedding-count token)
    - Save to database(Embedding)

- Process:
    - (*)Embedding query
    - Query similarity
    - (*)OpenAI respone



## Speed 

### Process Data
- sentence-transformers/all-MiniLM-L6-v2

|               | min          | max          | mean         |
| ------------- | ------------ | ------------ | ------------ |
| check_time    | 0,3935205936 | 0,4887697697 | 0,4418483257 |
| download_time | 6,008579493  | 11,83309698  | 8,806444597  |
| split_time    | 143,6718614  | 149,8266532  | 147,3809088  |
| updatedb_time | 4,458030224  | 5,054760933  | 4,684390688  |
> Time(s): Calculate after 5 attemps, each time with 5 files, each file contains 1000 words.


- vinai/bartpho-syllable

|               | min          | max          | mean         |
| ------------- | ------------ | ------------ | ------------ |
| check_time    | 0,4006037712 | 0,5089709759 | 0,4599420547 |
| download_time | 7,536367655  | 14,22592688  | 10,85303836  |
| split_time    | 311,1386349  | 335,4096267  | 321,797969   |
| updatedb_time | 45,96313167  | 64,84789443  | 51,02981639  |
> Time(s): Calculate after 5 attemps, each time with 5 files, each file

### Process Query

- 5-40s base on varity of request:
    - Complexity of request
    - Hard to answer
    - Long document
