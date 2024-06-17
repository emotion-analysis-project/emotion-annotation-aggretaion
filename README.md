## Emotion Aggregation Dataset Format

### Data Structure

- **text_id**: A unique identifier for the text sample.
- **text_content**: The actual text content that needs to be classified for emotions.
- **annotator_id**: A unique identifier for the annotator who provided the emotion labels for the given text sample.
- **happy, sad, anger, fear, surprise, disgust, neutral**: These columns represent the emotion labels provided by the annotator. Each column contains a binary value (0 or 1) indicating the absence or presence of that particular emotion in the text sample, as perceived by the annotator.

### Example Dataset

| `te_id` | text_content                              | `anno_id` | happy | sad | anger | fear | surprise | disgust | neutral |
|-----------|-------------------------------------------|----------------|-------|-----|-------|------|----------|---------|---------|
| 1         | I had a great day today!                  | 1              | 1     | 0   | 0     | 0    | 0        | 0       | 0       |
| 1         | I had a great day today!                  | 2              | 1     | 0   | 0     | 0    | 0        | 0       | 0       |
| 1         | I had a great day today!                  | 3              | 1     | 0   | 0     | 0    | 0        | 0       | 0       |
| 2         | My dog passed away this morning.          | 1              | 0     | 1   | 0     | 0    | 0        | 0       | 0       |
| 2         | My dog passed away this morning.          | 2              | 0     | 1   | 0     | 0    | 0        | 0       | 0       |
| 2         | My dog passed away this morning.          | 3              | 0     | 1   | 0     | 0    | 0        | 0       | 0       |

