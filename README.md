## Emotion Aggregation Dataset Format

### Data Structure

- **text_id**: A unique identifier for the text sample.
- **text_content**: The actual text content that needs to be classified for emotions.
- **annotator_id**: A unique identifier for the annotator who provided the emotion labels for the given text sample.
- **happy, sad, anger, fear, surprise, disgust, neutral**: These columns represent the emotion labels provided by the annotator. Each column contains a binary value (0 or 1) indicating the absence or presence of that particular emotion in the text sample, as perceived by the annotator.

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
