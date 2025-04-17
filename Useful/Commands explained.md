>[!CAUTION]
>Some commands to work require '--' and others require '-'

See below example of error for missing a '-'

<img width="584" alt="image" src="https://github.com/user-attachments/assets/480a80c9-1292-411c-a831-19bcad1c645d" />


## design.py
Calls ADAPT. It needs a [SEARCH-TYPE] right after. [SEARCH-TYPE] can be either be complete-targets or sliding-window.

## complete-targets
Search for the best assay options, each containing primer pairs and guides between them. This is usually our recommended search type.

## fasta
the input is one or more FASTA files, each containing sequences for a taxon. If more than one file is provided, the search finds taxon-specific designs meant for differential identification of the taxa. This assumes the FASTA files contain aligned sequences, unless otherwise specified.

## -o
Specific output path (i.e., /SENTINELv1/output/[filename]. The output file is always a .TSV file.

## --obj maximize-activity
Rells ADAPT to design sets of guides having maximal activity, in expectation over the input taxon's genomic diversity

## --id-method
You have two options: "lshnn", "shard". shard is default and best.

## --id-m
Uses whole numbers, i.e., 4 (default). This tells ADAPT to allow up to 4 mismatches when determining whether a guide HITS a sequence. 
For example, if a spacer is designed but a closely related species has only 4 mismatches, it will be taken as HIT and discarded. Higher values of –id-m enforce higher specificity.

## --id-frac 
Fraction to determine if ADAPT hits a group of sequences (0.01 default). If a guide hits >1% of the sequences in a designated off-target group, then it is considered a hit, making the design be discarded. Lower numbers enforces higher specificity.

## --specific-against-fastas
Specific path has to be provided (i.e., /SENTINELv1/input/[filename]. ADAPT will use these fastas as an internal database to determine hits (using --id-m and --id-frac parameters).

## --max-target-length
Total amplicon size, very useful when using large datasets.

## -gl
Guide length. Default = 28. Uses whole numbers. Specific for LwaCas13a.

## -gm
Mismatches allowed in the spacer region. Uses whole numbers.

## -pl
Primer length. Uses whole numbers.

## -pm
Mismatches are allowed in the primer region. Uses whole numbers.

## -pp 
Same as –id-frac but for primers. Uses fractions (Recommended pp = 0.98).

## --primer-gc-content-bounds
Amount of GC content for primers. Use fractions (Recommended = 0.35 0.70 for RPA).

## --maximization-algorithm random-greedy 
Best to discover the best predicted activity under an unknown matrix, such as eDNA.

## --predict-cas13a-activity-model 
This is to activate the trained model of ADAPT. This will call the internal modelling of ~ 19,000 training set.

## --best-n-targets
This sets a hard total number, e.g., if =5, no more than 5 designs are going to be retrieved even if more are found. If ADAPT finds more, it will replace them by ranking.

## --seed: 
This is important for reproducibility, so it is recommended to be changed for every iteration.

## --verbose
Allows you to see every step (you also look like you are working hard, even if it is automatic after you run ADAPT).
