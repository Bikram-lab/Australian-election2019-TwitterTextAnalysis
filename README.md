# Australian-election2019-TwitterTextAnalysis

**1. Project Background**

In the age of digital communication, platforms like Twitter play a major role in shaping public opinion and trends. The goal of this project was to uncover the key elements that influence tweet popularity. Using a dataset of 10,000 tweets, I applied a structured data science approach that included preprocessing, feature engineering, association rule mining, and predictive modeling. The overall objective was to determine which tweet characteristics were most linked with high engagement and how these findings could be applied in real-world social media strategies.

**2. Analysis Approach**

**2.1 Dataset Overview**

-   **Total records analyzed:** 10,000 tweets
-   **Features created:** 121
    -   21 traditional metadata features
    -   100 text-derived n-gram features

**2.2 Data Preparation**

-   Resolved naming conflicts by renaming ambiguous columns (e.g., is_negative to sentiment_negative)
-   Applied manual feature scaling for better compatibility with discriminant models
-   Converted relevant variables into categorical form for association rule mining

**2.3 Exploratory Data Analysis (Refer Appendix A)**

I analyzed patterns related to:

-   Time-of-day and day-of-week posting behaviors
-   Weekend vs. weekday activity
-   The role of retweets, hashtags, mentions, and URLs in popularity
-   Account age in relation to engagement

**2.4 Association Rule Mining**

Using the Apriori algorithm, I derived interpretable rules that showed clear behavioral relationships. For instance, tweets with low engagement combined with afternoon timing or the absence of hashtags often predicted "Not Popular" outcomes. These rules provided clear, actionable insights for content planning.

**2.5 Modeling Strategy**

-   Algorithms used: Linear Discriminant Analysis (LDA), Quadratic Discriminant Analysis (QDA), and Regularized Discriminant Analysis (RDA)
-   Both binary and 3-class classification tasks were performed
-   Evaluation metrics: Accuracy, Precision, Recall, F1 Score

**3. Results and Discussion**

**3.1 Classification Performance**

**Binary Task:**

| **Model** | **Accuracy** | **F1 Score** |
|-----------|--------------|--------------|
| **LDA**   | **0.7906**   | **0.8100**   |
| RDA       | 0.6769       | 0.7279       |
| QDA       | 0.4972       | 0.6396       |


**3-Class Task:**

| **Model** | **Accuracy** | **F1 Score** |
|-----------|--------------|--------------|
| **LDA**   | **0.7276**   | **0.7147**   |
| RDA       | 0.6025       | 0.5603       |

LDA clearly outperformed the others in both tasks, showing strong accuracy and stability. QDA struggled due to sensitivity to feature count, while RDA offered a middle ground with decent performance and robustness.

**3.2 Role of N-Gram Features**

Adding n-gram features (bigrams and trigrams) only marginally improved prediction accuracy. This suggests that metadata (tweet length, time, retweet count, sentiment, etc.) provided most of the useful information for the models.

**3.3 Technical Lessons Learned**

1.  Manual scaling significantly improved LDA performance.
2.  QDA's performance degrades quickly with too many features.
3.  RDA’s regularization helped with correlated features.
4.  Even slight class imbalance can noticeably affect accuracy.
5.  Association rules offered additional transparency on categorical interactions.

**4. Conclusion**

This analysis showed that tweet popularity can be effectively predicted using metadata and basic linguistic features. LDA emerged as the best-performing method for both binary and multi-class classifications. While n-grams didn’t offer substantial improvements in this case, they may still be valuable in more semantically complex datasets. Association rules supported model findings by highlighting repeatable user behavior patterns. These insights can be useful for social media managers or digital strategists aiming to improve engagement.

For future work, incorporating more advanced text features (like embeddings or transformer-based vectors) or testing ensemble models could enhance accuracy further.

**5. References**

-   James, G., Witten, D., Hastie, T., & Tibshirani, R. (2021). *An Introduction to Statistical Learning with Applications in R* (2nd ed.). Springer.
-   Han, J., Kamber, M., & Pei, J. (2011). *Data Mining: Concepts and Techniques* (3rd ed.). Morgan Kaufmann.
