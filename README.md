# ML-Programming-Task

I approached this task by breaking it down into two distinct components: the NLP segment (1.1/1.3) and the machine learning aspect (1.2).

For the NLP section, I initially focused on processing the validated.tsv dataset. My goal here was to isolate the first 100 clips for analysis. In parallel, I zeroed in on the first 1000 clips with "male" or "female" gender labels to facilitate model training.

Regarding the NLP component, I evaluated the Whisper Model's performance by calculating the Word Error Rate (WER). I wrote a function to determine the distance between each word in the model's output (the hypothesis sentence) and the corresponding word in the reference sentence sderived from the validated dataset (considered the ground truth). The WER, expressed as a percentage, was computed using the formula (insertions + deletions + substitutions) divided by the total number of words. My analysis yielded a mean error rate of 15.36%. It's worth noting that the Whisper model typically achieves a WER of around 10%. Given my limited dataset of 100 clips, my results were reasonably close.

In addition to assessing WER, I also examined the cosine similarity among all the clips. To achieve this, I vectorized the clips using TfidfVectorizer and used cosine_similarity function from sklearn and got an output of a 100x100 matrix where matrix[i][j] represented the similarity between clip i and clip j.

Then, wth the NLTK library, I identified the 100 most common words within the dataset. The top five most frequently occurring words were "the," "of," "and," "The," and "to." These findings make sense, as these words are common conjunctions frequently used in English.

I proceeded to analyze sentiment within the clips, assessing both polarity and subjectivity. Polarity provides insight into whether the statement leans toward a negative or positive sentiment, while subjectivity gauges the degree of bias in the statement.

Finally, I explored the token-type ratio (TTR), which offers insight into vocabulary diversity. TTR measures the ratio of unique words to the total number of words. The TTR for the ten groups of clips were very high, but TTR becomes less meaningful as the texts become shorter, as the probability of words repeating drops. 

Shifting to the machine learning aspect, I began by creating a dataset for training a model capable of predicting the gender of the speaker in each clip. To achieve this, I utilized the librosa library to extract a range of acoustic features. Once I had assembled the feature data and target labels within a dataframe, I needed to select an appropriate machine learning model.

I considered three options: logistic regression, random forest trees, and a neural network. To mitigate the risk of overfitting, I opted against logistic regression. Furthermore, due to the limited dataset size, I decided against employing a neural network. Ultimately, I implemented a random forest classifier and achieved an impressive accuracy score of 87.50%.

In addition to accuracy, I evaluated the model's performance through the generation of a confusion matrix and an ROC curve. The model exhibited a strong ROC curve area of 0.95, which is considered highly favorable, and it successfully predicted the gender of the speakers.

In conclusion, this task provided an engaging opportunity for analysis and modeling, and I look forward to the possibility of contributing to the Voice Project.





 
