## Emotion Aggregation Dataset Format

### Data Structure

- **text_id**: A unique identifier for the text sample.
- **text_content**: The actual text content that needs to be classified for emotions.
- **annotator_id**: A unique identifier for the annotator who provided the emotion labels for the given text sample.
- **happy, sad, anger, fear, surprise, disgust, neutral**: These columns represent the emotion labels provided by the annotator. Each column contains a binary value (0 or 1) indicating the absence or presence of that particular emotion in the text sample, as perceived by the annotator. Note: A text can have multiple emotion (e.g., in the first example below, the first annotator has both happy and surprise). 




### Example Dataset

**tex_id** | **text_content** | **anno_id** | **happy** | **sad** | **anger** | **fear** | **surprise** | **disgust** | **neutral**
-----|-----|-----|-----|-----|-----|-----|-----|-----|-----
1 | It's a sunny day! | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 0
1 | It's a sunny day! | 2 | 1 | 0 | 0 | 0 | 0 | 0 | 0
1 | It's a sunny day! | 3 | 1 | 0 | 0 | 0 | 1 | 0 | 0
2 | I failed the exam. | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0
2 | I failed the exam. | 2 | 0 | 1 | 0 | 0 | 0 | 0 | 0
2 | I failed the exam. | 3 | 0 | 1 | 1 | 0 | 0 | 1 | 0
3 | The movie was boring. | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0
3 | The movie was boring. | 2 | 0 | 1 | 0 | 0 | 0 | 0 | 0
3 | The movie was boring. | 3 | 0 | 0 | 0 | 0 | 0 | 1 | 0


In this example:

- For the text "It's a sunny day!", one annotator labeled it as "happy" and "surprise", another labeled it as "happy", and the third labeled it as "happy" and "surprise".
- For the text "I failed the exam.", one annotator labeled it as "sad" and "anger", another labeled it as "sad", and the third labeled it as "sad", "anger", and "disgust".
- For the text "The movie was boring.", one annotator labeled it as "anger" and "disgust", another labeled it as "sad", and the third labeled it as "disgust".



## Data Agreegation

To aggregate the emotion labels using majority voting when there are three annotators, you can follow these steps:

For each text sample, create a separate row for each emotion category (happy, sad, anger, fear, surprise, disgust, neutral).
In each row, include the text content, emotion category, and the votes (0 or 1) from each annotator for that emotion category.
Calculate the majority vote for each emotion category by summing the votes from the three annotators. If the sum is greater than or equal to 2, the majority vote is 1 (indicating the presence of that emotion); otherwise, the majority vote is 0.


### Aggregated Dataset Format

| `text_id` | text_content          | emotion   | annotator_1 | annotator_2 | annotator_3 | majority_vote |
|-----------|-----------------------|-----------|-------------|-------------|-------------|---------------|
| 1         | It's a sunny day!     | happy     | 1           | 1           | 1           | 1             |
| 1         | It's a sunny day!     | sad       | 0           | 0           | 0           | 0             |
| 1         | It's a sunny day!     | anger     | 0           | 0           | 0           | 0             |
| 1         | It's a sunny day!     | fear      | 0           | 0           | 0           | 0             |
| 1         | It's a sunny day!     | surprise  | 1           | 0           | 1           | 1             |
| 1         | It's a sunny day!     | disgust   | 0           | 0           | 0           | 0             |
| 1         | It's a sunny day!     | neutral   | 0           | 0           | 0           | 0             |
| 2         | I failed the exam.    | happy     | 0           | 0           | 0           | 0             |
| 2         | I failed the exam.    | sad       | 1           | 1           | 1           | 1             |
| 2         | I failed the exam.    | anger     | 1           | 0           | 1           | 1             |
| 2         | I failed the exam.    | fear      | 0           | 0           | 0           | 0             |
| 2         | I failed the exam.    | surprise  | 0           | 0           | 0           | 0             |
| 2         | I failed the exam.    | disgust   | 0           | 0           | 1           | 0             |
| 2         | I failed the exam.    | neutral   | 0           | 0           | 0           | 0             |


In this format, each row represents a combination of a text sample and an emotion category. The votes from each annotator are provided, and the majority_vote column indicates the final label based on the majority vote across the three annotators. The majority_vote column is the ground truth label for our dataset.


###  Single-Label Emotion Classification and Multi-Label Emotion Classification

We can use the dataset above in two settings: Single-Label Emotion Classification and Multi-Label Emotion Classification

In single-label classification, we will filter the dataset to include only those instances where all three annotators agree on a single emotion class for each text. This filtered dataset will be used to analyze the presence or absence of a single emotion. Below is an example of single Emotion Classification Dataset

| `text_id` | text_content          | emotion   | annotator_1 | annotator_2 | annotator_3 | majority_vote |
|-----------|-----------------------|-----------|-------------|-------------|-------------|---------------|
| 1         | It's a sunny day!     | happy     | 1           | 1           | 1           | 1             |
| 2         | I failed the exam.    | sad       | 1           | 1           | 1           | 1             |



In multi-label classification, we will filter on instances where a text has more than one emotion class annotated by different annotators (majority vote). This filtered dataset will be used for multi-class emotion classification problems.
Below is an example Multi-Emotion Classification Dataset

## Multi-Emotion Classification Dataset

| `text_id` | text_content          | emotion   | annotator_1 | annotator_2 | annotator_3 | majority_vote |
|-----------|-----------------------|-----------|-------------|-------------|-------------|---------------|
| 4         | I missed the bus.     | sad       | 1           | 1           | 1           | 1             |
| 4         | I missed the bus.     | anger     | 1           | 1           | 0           | 1             |


