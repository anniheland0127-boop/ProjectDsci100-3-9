# ProjectDsci100-3-9
Project file for DSCI100 group 3-9
### Players dataset

#Number of observations:** 196  
#Number of variables:** 7  
#Variables:
  # - `experience` (character): player experience level (e.g., Beginner, Amateur, Regular, Pro, Veteran).  
  # - `subscribe` (logical): whether the player subscribes to the game-related newsletter (TRUE/FALSE).  
  # - `hashedEmail` (character): anonymized unique player identifier.  
  # - `played_hours` (double): total hours played at the time of data collection.  
  # - `name` (character): in–game player name (not useful for prediction).  
  # - `gender` (character): self-reported gender.  
  # - `Age` (double): player age in years (a few values are missing).

### Sessions dataset

# - **Number of observations:** 1535  
# - **Number of variables:** 5  
# - **Variables:**
#   - `hashedEmail` (character): links back to the same player ID in `players.csv`.  
#   - `start_time`, `end_time` (character): recorded start and end time for each game session (string timestamps).  
#   - `original_start_time`, `original_end_time` (double): Unix-format timestamps for session start and end.

### Notes and potential issues

# - Each row in `sessions.csv` is **one gameplay session**, so there are multiple rows per player.  
# - Time variables appear in different formats (character timestamps and Unix time); for modelling, we will mainly use the numeric Unix times.  
# - We will need to **join** the two datasets on `hashedEmail` to create per-player summary features such as total play time and number of sessions.  
# - Some variables (e.g., `name`) are not useful for predictive modelling but help with data checks.  
# - A few values for age and play time are missing or extreme and will need to be handled carefully in later analysis.

(4) Methods and Plan
# I plan to use a **classification model** to predict whether a player subscribes to the newsletter (`subscribe`) based on engagement and demographic variables.

# ### Why this method is appropriate

# The response variable is binary (TRUE/FALSE), so classification models such as **logistic regression** or **k-nearest neighbours (k-NN)** are appropriate. These methods can handle numerical predictors (e.g., total play time, number of sessions, age, played_hours) and categorical predictors (experience level, gender).

# ### Assumptions required

# - Logistic regression assumes a linear relationship between predictors and the log-odds of subscribing.  
# - k-NN assumes that distances in the predictor space are meaningful, so numerical variables may need to be scaled or normalised.  
# - Both methods require that missing values and extreme outliers are addressed before modelling.

# ### Potential limitations

# - Engagement variables such as total play time are highly skewed and may require transformation or robust methods.  
# - Outliers (players with extremely high play time) may affect model fit.  
# - The model will be predictive rather than causal; it can identify patterns associated with subscription but cannot prove why players subscribe.

# ### Model comparison and selection

# I plan to compare at least two models (e.g., logistic regression vs. k-NN) using performance metrics on held-out data, such as **accuracy, sensitivity, specificity**, and possibly **ROC-AUC**. The model that performs best on the validation or test set will be selected.

# ### Data processing plan

# - Join `players.csv` and `sessions.csv` by `hashedEmail`.  
# - Create per-player summary features, including total play time (minutes) and number of sessions.  
# - Split the data into **training (75%)** and **testing (25%)** sets, with an optional validation split or cross-validation during training.  
# - Scale or normalise numerical predictors if using distance-based methods such as k-NN.  
# - Encode categorical variables (experience, gender) appropriately for the chosen models.

# This plan will allow me to address my research question about which player characteristics and behaviours are most predictive of newsletter subscription.

