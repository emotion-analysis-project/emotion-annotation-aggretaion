## Emotion Aggregation Dataset Format

### Data Structure

- **text_id**: A unique identifier for the text sample.
- **text_content**: The actual text content that needs to be classified for emotions.
- **annotator_id**: A unique identifier for the annotator who provided the emotion labels for the given text sample.
- **happy, sad, anger, fear, surprise, disgust, neutral**: These columns represent the emotion labels provided by the annotator. Each column contains a binary value (0 or 1) indicating the absence or presence of that particular emotion in the text sample, as perceived by the annotator.

### Example Dataset Structure

| `text_id` | text_content         | `annotator_id` | happy | sad | anger | fear | surprise | disgust | neutral |
|-----------|----------------------|----------------|-------|-----|-------|------|----------|---------|---------|
| 1         | This is a happy text | 1001           | 1     | 0   | 0     | 0    | 0        | 0       | 0       |
| 2         | This is a sad text   | 1002           | 0     | 1   | 0     | 0    | 0        | 0       | 0       |
| 3         | This is an angry text| 1003           | 0     | 0   | 1     | 0    | 0        | 0       | 0       |
| 4         | This is a fearful text| 1004          | 0     | 0   | 0     | 1    | 0        | 0       | 0       |
| 5         | This is a surprise text| 1005         | 0     | 0   | 0     | 0    | 1        | 0       | 0       |
| 6         | This is a disgust text| 1006          | 0     | 0   | 0     | 0    | 0        | 1       | 0       |
| 7         | This is a neutral text| 1007          | 0     | 0   | 0     | 0    | 0        | 0       | 1       |


