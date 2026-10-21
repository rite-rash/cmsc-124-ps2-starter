# Vector and Scalar Evaluation

We use c(Ada = 8, Grace = NA_real_, Linus = 12, Barbara = 4) to trace both functions.

## Input tracing using clean_scores_vector()
First, we convert the scores to type double, then copy them into a vector of type double.
Next, out[is.na(out)] <- 0 replaces the NA scores with 0. Here, is.na takes the vector out and flags only Grace's score, so only she gets 0.
Next, we multiply all the scores by 2, which gives us [16, 0, 24, 8]. Then, out[out > 20] <- 20 sensures that no values go over 20. Thus, the third value, 24, becomes 20. Lastly, we return the vector, which is [16, 0, 20, 8].

## Input tracing using clean_scores_scalar()
First, we ensure that the scores are of type double, then copy them to a vector of type double. Then we use a loop here that visits one element per pass. Each pass can only do one of two things depending on the condition. That is, if the value is NA, write 0. Otherwise, multiply the value by 2, then get the min between that and 20. So for the first pass, Ada is not missing so we multiply by 2 and she gets 16. On the second pass, Grace is missing so she gets 0. On the third pass, Linus is not missing so he gets 24, then the min with 20 caps it at 20. Lastly, on the fourth pass, Barbara is not missing so she gets 8. Hence we arrive at [16, 0, 20, 8].

## Comparing the evaluation models
The vector version applies each operation across out using vector expressions and logical subassignment. The scalar version uses seq_along(out) to handle one element per pass; each selected element is still a length-one vector in R.

In out * 2, the single multiplier is recycled across all scores. Replacing it with c(2, 3) repeats those multipliers, giving [16, 0, 24, 12] before capping and [16, 0, 20, 12] afterward. Barbara's result changes without a warning because 4 is divisible by 2.

I would keep the vector version because its replacement, multiplication, and cap directly express the same rules for all scores. The loop is useful for following each student's result step by step.
