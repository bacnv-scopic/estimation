# 1. The project
### a. The Data
- **The input**: will include 2 audio files from the same movie.
- **The different**: The subtitle of the audio files will be different.
- **The audio files**: a full movie audio - and the quality is good.
### b. The Goal
- **Find the difference**: Where in the movie(timestamp) the subtitle is different. And what is the different.
- **The accuracy**: > 90%
- **False positive** < 500%  (the current tool have 16000% false positive)
Note:
- The accuracy: The percentage of the correct difference found.
- The False positive: The percentage of the wrong difference found. For example if the audio have 3 mismatchs and the model found 15 mismatchs. The false positive is 12/3=400%. I see this is acceptable for our use case.
# 2. What have been done?
### a. **Run with the old tool**:
- We tried to use the old logic from auto-confomance with some changes to find the difference.
=> It found some difference but the accuracy is low.
### b. **New approach with ASR**:
- Run the audio through ASR to get the transcript and compare the transcript to find the difference.
- There are some challenges with this approach:
    - The ASR is making up words where is none
    - The ASR change the word to another word
    - The ASR is not working with overlapping speech
    - etc...
# 3. What need to be done before we can deliver this?
### a. We need more data.
- Currently we work with 6 sample - this is clearly not enough for production use
=> Andrey need to help with this
### b. We need to improve the ASR
- The current model produce too much false positive
- We will need to change to some other model to test
### c. We need to implemenent some logic to handle ASR error cases mention above
# 4. Estimation
### Phase 1 : 2 months
- Create new repo + CI-CD
- Automate evaluation
- Improve ASR result - 1 week
### Phase 2 : 3 months
- Implement logic to handle ASR error cases - 3 months
=> This gonna take a lot of time because there are too many cases to handle.
### Phase 3 : 3 months
- Refactor the code to handle more data
- Improve the accuracy - Because when we try to reduce the false positive, the accuracy is reduced too. We need to find a balance here.
# 5. Caveats.
- The estimation is based on the current knowledge and data.
- The estimation above is assuming Bac working alone for 20h/week.
- Bac: I can not take on the responsibility for implement the solution + breaking task + manage team with 20h/week.
- I propose to choose 1 person to work on this full time, can be me or Mohamad, instead of 2 person working part time.