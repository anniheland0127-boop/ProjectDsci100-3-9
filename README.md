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



