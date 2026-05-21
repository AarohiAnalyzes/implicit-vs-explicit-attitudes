# Stars vs. Semantics: A WEAT Analysis of Implicit and Explicit Brand Attitudes

A computational study of dissociations between **explicit** consumer attitudes
(star ratings) and **implicit** consumer attitudes (word-embedding semantics)
toward Apple and Samsung, using the Word Embedding Association Test (WEAT)
on 413,840 Amazon mobile-phone reviews.

---

## Research Question

> Do consumers hold different implicit versus explicit attitudes toward
> Apple and Samsung, and what emotional associations drive the gap between
> these two levels of evaluation?

The hypothesis: a person's deliberate, conscious judgment (a star rating)
and their automatic, associative evaluation (the words they use in a review)
may not align. If they don't, the gap should be measurable in word-embedding
geometry and interpretable through dual-process theory (Kahneman, 2011).

---

## Key Findings

Three measures, three answers — and they don't agree:

| Measure | Result | Direction |
|---|---|---|
| Explicit (star ratings) | Samsung 3.97 vs. Apple 3.92 | Samsung marginally higher |
| Implicit valence (WEAT) | Cohen's *d* = 0.45 | Apple more positive |
| Discrete emotion (share-normalised) | Sadness gap ≈ −0.04 | Samsung carries more regret language |

**Interpretation.** The explicit and implicit measures *dissociate*, and
they dissociate in opposite directions. This is the pattern dual-process
theory predicts: System-2 deliberate judgment (the star rating) and System-1
automatic association (the embedding geometry) can produce conflicting
evaluations of the same object. The discrete-emotion analysis localises
the gap: Samsung's reviews carry disproportionately more sadness/regret
language, suggesting the implicit-vs-explicit gap is emotion-driven, not
valence-driven.

---

## Methodology

1. **Data preparation**: Filtered the Amazon Unlocked Mobile dataset
   (413,840 reviews → 127,820 brand-relevant reviews for Apple and Samsung).
2. **Explicit analysis**: Independent-samples *t*-test on star ratings;
   effect interpreted alongside practical magnitude.
3. **Word embeddings**: Trained a skip-gram Word2Vec model on the cleaned
   review corpus (`min_count=20`, 20 epochs, vocabulary = 4,734 words,
   `seed=42` and `workers=1` for full reproducibility).
4. **Implicit analysis (WEAT)**: Implemented the Word Embedding Association
   Test from scratch following Caliskan et al. (2017):
   - Cosine-similarity associations between target words (brands) and
     attribute words (positive/negative valence)
   - Effect size computed with population standard deviation (`ddof=0`),
     matching the original specification
   - Two-sided permutation test over all valid target-set permutations
5. **Validation**: Checked brand-neighbor structure (`iphone` ↔ `galaxy`,
   `apple`, `phone`) and the valence axis (`love` ↔ `great` similarity
   substantially exceeds `love` ↔ `hate`) before computing the main effect.
6. **Discrete-emotion analysis**: Mapped each brand's embedding to
   Plutchik's eight basic emotion categories, then share-normalised to
   recover each brand's *emotional profile* independent of overall
   association magnitude.

-----

## Limitations

  - **Permutation-test power.** With 4 target words per brand, only 70
    permutations are possible, so the permutation *p*-value has limited
    statistical power. The effect size is therefore the more informative
    quantity than the *p*-value alone: a structural limit of the test,
    not evidence against the effect.
  - **Lexicon coverage.** Brand-attribution and emotion word lists are
    finite and English-only; results may not transfer to multilingual
    review corpora or to product categories with different vocabularies.
  - **Temporal scope.** The dataset reflects a specific period of the
    mobile market; brand semantics shift over time and results may not
    generalise to current consumer attitudes.
  - **Platform effect.** Amazon's review demographic is not representative
    of all consumers; findings should not be extrapolated to the general
    population without further validation on other platforms.

-----

## References

  - Caliskan, A., Bryson, J. J., & Narayanan, A. (2017). Semantics derived
    automatically from language corpora contain human-like biases.
    *Science*, 356(6334), 183–186.
  - Greenwald, A. G., McGhee, D. E., & Schwartz, J. L. K. (1998). Measuring
    individual differences in implicit cognition: The implicit association
    test. *Journal of Personality and Social Psychology*, 74(6), 1464–1480.
  - Kahneman, D. (2011). *Thinking, Fast and Slow*. Farrar, Straus and
    Giroux.
  - Mikolov, T., Sutskever, I., Chen, K., Corrado, G., & Dean, J. (2013).
    Distributed representations of words and phrases and their
    compositionality. *NeurIPS*.
  - Plutchik, R. (1980). *Emotion: A Psychoevolutionary Synthesis*. Harper
    & Row.

-----

## Author

**Aarohi Mistry**: M.Sc. Data Science, Università degli Studi di Milano-Bicocca
Course: *Big Data in Behavioural Psychology* (Prof. Michela Vezzoli)

📧 [aarohimistry1106@gmail.com](mailto:aarohimistry1106@gmail.com)
🔗 [LinkedIn](https://www.linkedin.com/) · [GitHub](https://github.com/AarohiAnalyzes)

-----
