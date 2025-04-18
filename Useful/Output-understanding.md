# Understanding ADAPT output

_objective-value_, weight of the prediction, the higher is better.x

_target-length_, amplicon size. Smaller the better for the overall assay.

_right/left-primer-frac-bound_, fraction of all input sequences predicted to be detected by the guide-target pair.

_total-frac-bound-by-guides_, fraction of all input sequences predicted to be detected by the guide-target pair.

_guide-set-5th-pctile-activity_, median and 5th percentile of predicted activity of the guide set over the input sequences. Better than the other 95% of computed guides.

_guide-expected-activities_, predicted activity of each separate guide in detecting the input sequences, in expectation over the input sequences.ut sequences

_guide-target-sequences_, spacer sequence. Remember to reverse-complement, convert to RNA, and append the DR sequence.

_guide-target-sequence-positions_, guide start position. It is recommended to use this as the ID of the guide-target pair.
