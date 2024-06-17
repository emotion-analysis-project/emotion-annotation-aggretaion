## Emotion Aggregation Dataset Format

### Data Structure

- **text_id**: A unique identifier for the text sample.
- **text_content**: The actual text content that needs to be classified for emotions.
- **annotator_id**: A unique identifier for the annotator who provided the emotion labels for the given text sample.
- **happy, sad, anger, fear, surprise, disgust, neutral**: These columns represent the emotion labels provided by the annotator. Each column contains a binary value (0 or 1) indicating the absence or presence of that particular emotion in the text sample, as perceived by the annotator. Note: A text can have multiple emotion (e.g., in the first example below, the first annotator has both happy and suprise). 

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
| 3         | The movie was boring. | happy     | 0           | 0           | 0           | 0             |
| 3         | The movie was boring. | sad       | 0           | 1           | 0           | 0             |
| 3         | The movie was boring. | anger     | 1           | 0           | 0           | 0             |
| 3         | The movie was boring. | fear      | 0           | 0           | 0           | 0             |
| 3         | The movie was boring. | surprise  | 0           | 0           | 0           | 0             |
| 3         | The movie was boring. | disgust   | 1           | 0           | 1           | 1             |
| 3         | The movie was boring. | neutral   | 0           | 0           | 0           | 0             |
