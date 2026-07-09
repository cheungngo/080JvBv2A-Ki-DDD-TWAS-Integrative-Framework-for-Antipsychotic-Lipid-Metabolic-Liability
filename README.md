# **Ki–DDD–TWAS Integrative Framework for Antipsychotic Lipid-Metabolic Liability: Methodological Comparison and Translational Insights**

## **Abstract**

**Background:** Metabolic adverse effects remain one of the most clinically important limitations of antipsychotic treatment. Weight gain, dyslipidemia, and diabetes risk contribute to poor adherence, cardiovascular morbidity, and reduced quality of life. Existing approaches to metabolic risk assessment rely largely on clinical observation or receptor-binding profiles, but these approaches do not fully integrate dose exposure or genetic evidence linking receptor genes to lipid traits.

**Objective:** This study developed and compared a Ki–DDD–TWAS framework for estimating relative lipid-metabolic liability across antipsychotic drugs. The goal was to determine whether the resulting liability hierarchy remained stable across alternative strategies for transcriptome-wide association study integration.

**Methods:** Drugs were parsed from the ATC N05A antipsychotic class and matched to a receptor-binding Ki database. Ki values were aggregated by drug–receptor pair, normalized by defined daily dose in milligrams, and mapped to receptor genes. Five lipid TWAS trait directories were evaluated: HDL cholesterol, LDL cholesterol, log-transformed triglycerides, non-HDL cholesterol, and total cholesterol. Three TWAS integration methods were compared: an Original drug-level TWAS boost, a Linear per-receptor TWAS scaling method, and a mild Exponential per-receptor TWAS scaling method. Scores were normalized to chlorpromazine equal to 100\.

**Results:** The antipsychotic metabolic liability hierarchy was highly stable across all three TWAS integration methods. Mean cross-method Spearman rho was 0.996 across all method pairs and lipid traits. Linear and Exponential scaling were nearly identical, with mean rho of 0.999. The Original method showed the strongest leader separation, with mean top-to-median ratio of 15.99, compared with 13.99 for Linear and 13.35 for Exponential scaling. Clozapine ranked first across every method and trait, followed by chlorpromazine. The consensus high-risk group included clozapine, chlorpromazine, asenapine, zotepine, risperidone, ziprasidone, olanzapine, and thioridazine. Receptor-contribution analyses showed stable dominance of HRH1 and HTR2A across all methods.

**Conclusions:** The Ki–DDD–TWAS framework produced a robust and interpretable relative index of antipsychotic lipid-metabolic liability. The Original method is recommended as the primary specification because it provided the clearest discrimination under current TWAS limitations, while Linear and Exponential methods are useful sensitivity analyses. The findings support receptor-informed prescribing research and safer antipsychotic design, while emphasizing the need for directional, tissue-aware, and better-covered TWAS resources.

**Keywords:** antipsychotics; metabolic liability; transcriptome-wide association study; Ki; defined daily dose; dyslipidemia; clozapine; HRH1; HTR2A

## **Introduction**

### **Clinical Burden of Antipsychotic Metabolic Side Effects**

Antipsychotic medications are central to the treatment of schizophrenia, bipolar disorder, and related psychotic disorders, but their benefits are often limited by metabolic adverse effects. Weight gain, dyslipidemia, insulin resistance, and diabetes risk are not minor tolerability issues. They affect long-term treatment adherence, physical health, and cardiovascular mortality. The problem is especially important because many patients require years of continuous treatment, and even moderate metabolic changes can become clinically meaningful over time.

The clinical literature has consistently shown that antipsychotics differ substantially in their metabolic profiles. Early quantitative syntheses established that antipsychotic-induced weight gain is common and varies by compound, with clozapine and olanzapine repeatedly emerging as high-risk agents \[1\]. Later reviews and meta-analyses broadened this picture by showing that antipsychotics differ not only in weight gain but also in lipid, glucose, and broader cardiometabolic outcomes \[2,3\]. More recent network meta-analytic work has reinforced the clinical relevance of these differences during mid- to long-term antipsychotic treatment \[4\].

These adverse effects matter in everyday practice. A patient with severe psychosis may benefit uniquely from a drug such as clozapine, but the same patient may also face increased cardiometabolic risk. Conversely, a patient with pre-existing obesity, dyslipidemia, or diabetes risk may be better served by an agent with lower metabolic liability when symptom control allows. Clinicians therefore need more than broad categories such as “high risk” or “low risk.” They need mechanistically interpretable tools that can compare drugs in a reproducible way, while remaining transparent about what the model can and cannot predict.

### **Limitations of Current Risk Assessment Approaches**

Much of the mechanistic understanding of antipsychotic metabolic liability comes from receptor-binding pharmacology. Histamine H1 receptor affinity has been strongly linked to antipsychotic-associated weight gain, and Kroeze et al. showed that H1 receptor affinity predicted short-term weight gain across typical and atypical antipsychotics \[5\]. Serotonergic, adrenergic, dopaminergic, and muscarinic receptors have also been implicated, including 5-HT2C in appetite and weight gain, and muscarinic M3 signaling in insulin secretion and diabetes risk \[6,7\]. Broader reviews have argued that antipsychotic metabolic risk is best understood as a multi-receptor problem rather than the consequence of a single pharmacological target \[8,9\].

However, receptor-binding profiles alone have limitations. They are usually static summaries of affinity and do not automatically account for clinical dose exposure. A drug with high affinity at a metabolically relevant receptor may have a different practical impact depending on the dose range used in clinical care. Binding profiles also do not incorporate genetic evidence linking receptor genes to lipid traits. In addition, clinical metabolic risk is shaped by patient-level factors, including age, baseline weight, diet, illness severity, comedications, and genetic susceptibility. A receptor-only model can identify plausible biological mechanisms, but it cannot fully explain variation in lipid-related liability.

Clinical prediction models face the opposite problem. They may capture real-world outcomes, but they often lack mechanistic resolution. A purely empirical clinical model may identify that one drug is associated with more weight gain than another, but it may not explain which receptor mechanisms are driving that difference or how the signal relates to lipid biology. This creates a gap between pharmacology, genetics, and clinical translation.

### **Rationale for a Ki–DDD–TWAS Integrative Framework**

A useful metabolic liability index should integrate at least three layers of evidence. First, it should include receptor-binding strength, because antipsychotic metabolic effects are closely tied to receptor pharmacology. Second, it should account for dose exposure, because receptor affinity becomes clinically relevant in the context of the dose at which a drug is used. Third, it should incorporate genetic evidence linking receptor genes to lipid traits, because the same receptor may be more or less relevant depending on its relationship to lipid biology.

Transcriptome-wide association study methods offer one way to connect genetic regulation of gene expression with complex traits. PrediXcan estimates genetically regulated gene expression and tests its association with phenotypes \[10\]. TWAS approaches extend this idea by integrating gene expression reference panels with GWAS summary statistics to identify genes whose genetically regulated expression is associated with complex traits \[11\]. S-PrediXcan and MetaXcan further allow gene-level association results to be inferred from GWAS summary statistics and applied across tissues and phenotypes \[12\]. These methods do not prove causality by themselves, and they require careful interpretation, but they provide a principled way to link genes to lipid traits.

The present framework uses TWAS as a modifier of pharmacological liability rather than as a standalone predictor. This distinction is important. The base of the model is a Ki–DDD receptor score. TWAS evidence is then used to adjust or weight the contribution of receptor genes according to their lipid-trait association signals. In this way, the framework remains grounded in drug pharmacology while adding a layer of genetic trait relevance.

### **Objectives and Methodological Comparison**

The main objective was to develop a reproducible Ki–DDD–TWAS pipeline for estimating relative lipid-metabolic liability across antipsychotic drugs. A second objective was to test whether the liability hierarchy depended on the way TWAS information was incorporated. This was addressed by comparing three TWAS integration methods.

The Original method applied TWAS information at the drug level after receptor contributions had been aggregated. The Linear method applied TWAS information at the receptor level before aggregation, using a proportional per-receptor scaling factor. The Exponential method also operated at the receptor level, but used a mild exponential scaling function to give greater weight to stronger TWAS signals. These methods represent a practical spectrum: simple drug-level integration, biologically granular linear integration, and slightly more nonlinear receptor-level integration.

The central question was not only which method produced the largest scores, but whether the ranking of antipsychotics remained stable across methods. If the hierarchy changed substantially, then conclusions would depend heavily on an arbitrary modeling choice. If the hierarchy remained stable, the framework would be more credible as a relative mechanistic index.

## **Methods**

### **Data Sources and Preprocessing**

The pipeline began with antipsychotic drug identification from the ATC N05A class. The N05A index was parsed programmatically, including the relevant chemical subgroups under the antipsychotic class. For each drug entry, the pipeline extracted the ATC code, drug name, defined daily dose where available, dose unit, administration route, note field, and subgroup. Defined daily dose values were normalized to milligrams \[13\]. Drugs without valid defined daily dose information were excluded from risk scoring, because the framework explicitly incorporated dose exposure.

Receptor-binding data were obtained from a local Ki database file dated June 22, 2026\. Each antipsychotic was matched to ligand names in this database using fuzzy string matching. The matching threshold was set at 80 on a 0-to-100 scale. This step was necessary because drug names in ATC sources and ligand databases do not always match exactly. For each accepted match, receptor-level Ki values were extracted. Multiple Ki measurements for the same drug–receptor pair were aggregated using the minimum Ki value, representing the strongest reported binding signal. This choice was made because low Ki values reflect high receptor affinity and may be most relevant when identifying potential receptor-driven liability.

Five lipid TWAS trait directories were analyzed: HDL cholesterol, LDL cholesterol, log-transformed triglycerides, non-HDL cholesterol, and total cholesterol. The TWAS loading function searched each trait directory for files containing gene identifiers, TWAS z-statistics, and p-values. Gene symbols were prioritized when available; Ensembl identifiers were used as fallback after removal of version suffixes. When multiple records were available for the same gene within a trait directory, the record with the smallest p-value was retained.

Receptor labels were mapped to official gene symbols. The mapping included serotonergic receptors such as 5-HT2A to HTR2A and 5-HT2C to HTR2C, dopamine receptors such as D2 to DRD2 and D3 to DRD3, adrenergic receptors such as alpha1A to ADRA1A and alpha1B to ADRA1B, histamine receptors such as H1 to HRH1, and muscarinic receptors such as M1 to CHRM1 and M3 to CHRM3. Transporter and sigma targets were also mapped when present.

Metabolic receptor weights were curated to reflect prior biological evidence. The highest weights were assigned to HRH1 at 1.00, HTR2C at 0.92, and CHRM3 at 0.85. Intermediate weights were assigned to HTR2A at 0.55, ADRA1A and ADRA1B at 0.48, and HTR6 at 0.42. Lower but nonzero weights were assigned to ADRA2A, ADRA2B, ADRA2C, CHRM1, CHRM4, CHRM5, HTR7, DRD3, DRD2, DRD4, HTR1A, ADRB1, ADRB2, SIGMAR1, SLC6A4, SLC6A2, and SLC6A3. These weights were not treated as clinical effect sizes. They were used as mechanistic priors for relative receptor contribution, informed by the receptor-binding and metabolic adverse-effect literature \[5-9\].

### **Core Pipeline: Affinity-Dose Scoring**

The core score for each drug–receptor pair combined receptor affinity and dose exposure. Ki values were parsed as nanomolar concentrations. Since stronger binding corresponds to lower Ki, the inverse Ki was calculated for each valid value. Defined daily dose values were converted to milligrams, with grams converted to milligrams and micrograms converted to milligrams when needed. The affinity-dose score was calculated as inverse Ki multiplied by the natural logarithm of defined daily dose in milligrams plus one. When defined daily dose was missing, the drug was not retained for scoring. When Ki was valid but defined daily dose was not, the affinity-dose score was not used in the final drug-level score.

The logarithmic dose term was used to avoid allowing large dose differences to dominate the score. This reflects the practical idea that dose exposure matters, but not in a strictly linear way across drugs and dose units. After the affinity-dose score was calculated, the risk-scoring function applied a log one plus transform to the affinity-dose score before multiplying by the receptor weight. This additional transform reduced the leverage of extremely low Ki values while preserving the rank contribution of strong binding.

Drug–receptor rows with Ki below 10 nM were flagged as strong binders. This flag was used for descriptive summaries but was not the sole determinant of risk. A drug could have a high overall score because of several moderate receptor contributions, not only because of one very strong binding value.

Missing Ki values were imputed using a mean strategy. The imputation first used the receptor-specific mean Ki among available observations. If a receptor-specific reference was unavailable, a global mean Ki fallback was used. Missing TWAS values were also imputed by mean where a recognized receptor gene lacked TWAS data. Importantly, imputed TWAS rows were not treated as TWAS-significant. This distinction prevented missing values from being counted as positive statistical evidence.

### **TWAS Integration and Three Methodological Variants**

The framework compared three ways of integrating TWAS information into the metabolic risk score. All three methods used the same drug list, Ki aggregation, defined daily dose normalization, receptor-to-gene mapping, metabolic receptor weights, and chlorpromazine normalization. They differed only in where and how TWAS z-statistics modified the score.

The Original method used drug-level TWAS boosting. Receptor contributions were first calculated from the transformed affinity-dose score and receptor weight. These receptor contributions were summed into a base score for each drug. TWAS influence was then applied after aggregation, using the maximum absolute TWAS z-statistic observed among that drug’s mapped receptor genes. The drug-level multiplier was one plus 0.12 times the maximum absolute TWAS z-statistic. This means that only the strongest TWAS receptor signal for a drug determined the main TWAS boost. A TWAS-significance bonus was also applied where relevant, using a 0.10 multiplier per TWAS-significant metabolic receptor. TWAS significance was defined as p less than 0.05, and imputed rows were not counted as significant.

The Linear method used per-receptor TWAS scaling. Each receptor’s weighted contribution was multiplied by one plus 0.24 times the absolute TWAS z-statistic for that receptor gene before receptor contributions were summed. The base score was therefore recomputed from TWAS-scaled receptor contributions. This method gives every receptor its own TWAS weight and is biologically more granular than the Original method. A smaller secondary drug-level boost was retained, using one plus 0.04 times the drug’s maximum absolute TWAS z-statistic. The same 0.10 TWAS-significance bonus was applied when a metabolic receptor was TWAS-significant.

The Exponential method also used per-receptor scaling, but with a mild exponential function. Each receptor’s contribution was multiplied by the exponential of 0.08 times the absolute TWAS z-statistic. This allows stronger TWAS signals to accelerate more than they do under a linear scaling rule, while keeping the exponent small enough to avoid unstable score inflation. After receptor-level scaling, the base score was recomputed. A very small secondary drug-level boost was retained, using one plus 0.02 times the maximum absolute TWAS z-statistic. The same TWAS-significance bonus was used.

For all methods, missing metabolic-gene TWAS values were handled with a fairness strategy during scoring. When a metabolic receptor gene lacked a TWAS z-statistic, the missing value could be replaced with the mean absolute TWAS z-statistic among available metabolic receptor genes. This prevented genes with missing TWAS coverage from being automatically penalized relative to genes with available TWAS data. The strategy was especially important because key metabolic receptor genes were not uniformly represented across TWAS files. HTR2C was a particularly important limitation, given its known relationship to appetite and antipsychotic weight gain \[6\].

Final drug scores were normalized within each trait and method so that chlorpromazine equaled 100\. This reference normalization allowed comparison across traits and TWAS integration strategies. A score above 100 indicated higher modeled lipid-metabolic liability than chlorpromazine for that trait and method. A score below 100 indicated lower modeled liability than chlorpromazine. The score should be interpreted as a relative mechanistic index, not as an absolute clinical risk probability.

### **Downstream Comparison Analyses**

The downstream method comparison used only pipeline output files. For each method and lipid trait, the per-drug metabolic risk score and rank were loaded and reshaped into long and wide formats. Between-method agreement was assessed using Spearman rank correlation and Pearson correlation. Spearman correlation was emphasized because the main question was whether the drug hierarchy was stable across methods, not whether the absolute score scale was identical \[14\].

Top-N overlap was assessed using Jaccard overlap for the top 5 and top 10 drugs. Rank sensitivity was assessed by identifying drug–trait combinations in which the rank shifted by at least three positions across methods. Leader separation was measured as the ratio of the top score to the median score within each method and trait. This was used to determine which TWAS integration strategy most clearly separated the leading high-liability drug from the rest of the distribution.

Receptor-contribution analyses were recomputed from the long-format output files because the pipeline did not save final weighted contribution columns. For the Original method, receptor contribution was recalculated as transformed affinity-dose score multiplied by receptor weight. For Linear and Exponential methods, the corresponding per-receptor TWAS scaling was reapplied before summing contributions by gene. This allowed the dominant receptor drivers to be compared fairly under each method’s own scoring logic.

### **Statistical and Sensitivity Considerations**

The TWAS component used absolute z-statistics. This was a deliberate but limited choice. Absolute values preserve the strength of gene–trait association but lose directionality. A receptor gene associated with higher lipid levels and a receptor gene associated with lower lipid levels can therefore both increase the score if their absolute TWAS signals are strong. This is not ideal for causal inference or clinical prediction. The approach was used because the current framework was designed as a relative mechanistic liability index, and because directional, tissue-aware, receptor-specific interpretation was not yet available for all relevant genes. The Original method was ultimately favored as the primary specification because it gave the clearest discrimination under these constraints while remaining highly concordant with the more granular methods.

## **Results**

### **Between-Method Concordance and Robustness**

Across all lipid traits and method pairs, the metabolic liability rankings were highly concordant. The mean cross-method Spearman rho was 0.996. This was the strongest finding of the analysis. It indicates that the main antipsychotic liability hierarchy was not an artifact of one particular TWAS scaling choice.

Agreement was especially high between the Linear and Exponential methods. The mean Spearman rho for Linear versus Exponential scaling was 0.999 across traits. Original versus Linear had a mean rho of 0.995, and Original versus Exponential had a mean rho of 0.994. Pearson correlations were also very high, ranging from 0.997 to 1.000 across the trait-specific comparisons. These results show that the three methods produced very similar score distributions as well as very similar rank orderings. The detailed correlation results are shown in Table 1\.

**Table 1\. Between-method agreement of risk scores by lipid trait**

| Trait | Methods compared | n drugs | Spearman rho | Pearson correlation |
| ----- | ----- | ----- | ----- | ----- |
| HDL | Original vs Linear | 52 | 0.992 | 0.998 |
| HDL | Original vs Expo | 52 | 0.990 | 0.997 |
| HDL | Linear vs Expo | 52 | 0.997 | 0.999 |
| LDL | Original vs Linear | 52 | 0.996 | 0.999 |
| LDL | Original vs Expo | 52 | 0.995 | 0.999 |
| LDL | Linear vs Expo | 52 | 0.999 | 1.000 |
| LOGTG | Original vs Linear | 52 | 0.996 | 0.999 |
| LOGTG | Original vs Expo | 52 | 0.997 | 1.000 |
| LOGTG | Linear vs Expo | 52 | 0.999 | 1.000 |
| NONHDL | Original vs Linear | 52 | 0.996 | 0.999 |
| NONHDL | Original vs Expo | 52 | 0.995 | 0.998 |
| NONHDL | Linear vs Expo | 52 | 0.999 | 0.999 |
| TC | Original vs Linear | 52 | 0.996 | 0.999 |
| TC | Original vs Expo | 52 | 0.994 | 0.999 |
| TC | Linear vs Expo | 52 | 0.999 | 1.000 |

Trait-specific results were consistent with the overall pattern. For HDL cholesterol, Original versus Linear had Spearman rho of 0.992, Original versus Exponential had rho of 0.990, and Linear versus Exponential had rho of 0.997. For LDL cholesterol, the corresponding values were 0.996, 0.995, and 0.999. For log-transformed triglycerides, they were 0.996, 0.997, and 0.999. For non-HDL cholesterol, they were 0.996, 0.995, and 0.999. For total cholesterol, they were 0.996, 0.994, and 0.999. Each comparison included 52 scored drugs.

Top-N overlap supported the same conclusion. For the top 10 drugs, Linear and Exponential methods had a mean Jaccard overlap of 1.000, meaning that the top 10 sets were identical across the five lipid traits. Original versus Linear and Original versus Exponential each had mean top-10 Jaccard overlap of 0.927. For the top 5 drugs, mean Jaccard overlap was 0.933 for Linear versus Exponential, 0.933 for Original versus Exponential, and 0.867 for Original versus Linear. Thus, even where the exact order of mid-ranked drugs shifted slightly, the high-liability group remained stable. Top-N overlap results are summarized in Table 2\.

**Table 2\. Top-N overlap between TWAS integration methods**

| Top-N set | Methods compared | Mean Jaccard overlap |
| ----- | ----- | ----- |
| Top 5 | Linear vs Expo | 0.933 |
| Top 5 | Original vs Expo | 0.933 |
| Top 5 | Original vs Linear | 0.867 |
| Top 10 | Linear vs Expo | 1.000 |
| Top 10 | Original vs Expo | 0.927 |
| Top 10 | Original vs Linear | 0.927 |

### **Consensus Metabolic Liability Ranking**

The consensus ranking across all methods and traits identified a stable high-liability group. Clozapine ranked first overall, with mean risk score of 120.9 and mean rank of 1.00 across 15 observations, reflecting 3 methods across 5 lipid traits. Chlorpromazine ranked second by design as the reference drug, with mean risk score of 100.0 and mean rank of 2.00. The next highest drugs were asenapine, with mean risk 83.4 and mean rank 3.07; zotepine, with mean risk 75.7 and mean rank 4.47; risperidone, with mean risk 74.9 and mean rank 4.67; ziprasidone, with mean risk 71.3 and mean rank 5.80; olanzapine, with mean risk 66.6 and mean rank 7.13; and thioridazine, with mean risk 63.0 and mean rank 7.87. The consensus ranking is shown in Table 3\.

**Table 3\. Consensus high-risk antipsychotic ranking across all methods and lipid traits**

| Rank | Drug | Mean risk | Mean rank | n observations |
| ----- | ----- | ----- | ----- | ----- |
| 1 | clozapine | 120.9 | 1.00 | 15 |
| 2 | chlorpromazine | 100.0 | 2.00 | 15 |
| 3 | asenapine | 83.4 | 3.07 | 15 |
| 4 | zotepine | 75.7 | 4.47 | 15 |
| 5 | risperidone | 74.9 | 4.67 | 15 |
| 6 | ziprasidone | 71.3 | 5.80 | 15 |
| 7 | olanzapine | 66.6 | 7.13 | 15 |
| 8 | thioridazine | 63.0 | 7.87 | 15 |
| 9 | chlorprothixene | 51.6 | 9.27 | 15 |
| 10 | sertindole | 46.9 | 9.87 | 15 |
| 11 | iloperidone | 41.7 | 10.87 | 15 |
| 12 | brexpiprazole | 32.0 | 12.00 | 15 |
| 13 | fluphenazine | 25.8 | 13.07 | 15 |
| 14 | quetiapine | 23.4 | 13.93 | 15 |
| 15 | mesoridazine | 19.8 | 15.73 | 15 |
| 16 | haloperidol | 18.7 | 16.47 | 15 |
| 17 | perphenazine | 18.8 | 16.67 | 15 |
| 18 | loxapine | 17.8 | 17.33 | 15 |
| 19 | aripiprazole | 16.8 | 18.87 | 15 |
| 20 | levomepromazine | 13.5 | 20.47 | 15 |

The remainder of the top 20 consensus list was also stable enough to be clinically interpretable as a ranked mechanistic index. Chlorprothixene ranked ninth, with mean risk 51.6 and mean rank 9.27. Sertindole ranked tenth, with mean risk 46.9 and mean rank 9.87. Iloperidone, brexpiprazole, fluphenazine, quetiapine, mesoridazine, haloperidol, perphenazine, loxapine, aripiprazole, and levomepromazine followed. These scores should not be read as direct estimates of real-world event rates. Rather, they summarize the relative burden of receptor affinity, dose exposure, metabolic receptor weighting, and TWAS lipid-trait evidence.

Several clinically important anchor drugs were highly stable. Clozapine, chlorpromazine, brexpiprazole, levosulpiride, triflupromazine, and tiapride showed maximum rank shift of zero across traits. Asenapine, fluphenazine, molindone, and olanzapine showed maximum rank shift of one. This stability is important because the highest-risk and clinically familiar reference agents did not depend on the TWAS scaling method.

Rank sensitivity was concentrated in the mid- and lower-ranked drugs. Across all drug–trait combinations, 36 had a rank shift of at least three positions across methods. The largest shifts were seen for drugs such as cariprazine, acepromazine, bromperidol, levomepromazine, fluspirilene, benperidol, pipamperone, melperone, and amisulpride. These shifts did not affect the leading high-liability drugs. They suggest that the model is most sensitive where scores are closer together, which is expected for a relative index.

### **Method-Specific Performance Differences**

Although the rankings were highly concordant, the methods differed in score separation. The Original method produced the strongest leader separation, with mean top-to-median ratio of 15.992 across traits. Linear scaling had mean top-to-median ratio of 13.993, and Exponential scaling had mean ratio of 13.345. Thus, the simpler drug-level TWAS boost created the clearest contrast between the highest-scoring drug and the middle of the distribution. Score magnitude and leader separation are summarized in Table 4\.

**Table 4\. Score magnitude and leader separation by method and lipid trait**

| Method | Trait | n | Maximum score | Median score | SD | Drugs \>100 | Top/median |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| Original | HDL | 52 | 128.8 | 5.5 | 30.6 | 1 | 23.42 |
| Original | LDL | 52 | 115.9 | 8.5 | 28.8 | 1 | 13.62 |
| Original | LOGTG | 52 | 121.7 | 8.6 | 29.3 | 1 | 14.11 |
| Original | NONHDL | 52 | 115.9 | 7.9 | 28.9 | 1 | 14.59 |
| Original | TC | 52 | 123.2 | 8.7 | 29.6 | 1 | 14.22 |
| Linear | HDL | 52 | 131.5 | 6.5 | 30.4 | 1 | 20.09 |
| Linear | LDL | 52 | 114.2 | 9.7 | 28.3 | 1 | 11.81 |
| Linear | LOGTG | 52 | 119.9 | 9.2 | 28.9 | 1 | 13.10 |
| Linear | NONHDL | 52 | 114.1 | 9.4 | 28.0 | 1 | 12.20 |
| Linear | TC | 52 | 123.5 | 9.7 | 29.2 | 1 | 12.77 |
| Expo | HDL | 52 | 130.2 | 7.2 | 30.3 | 1 | 18.17 |
| Expo | LDL | 52 | 115.3 | 10.2 | 28.5 | 1 | 11.29 |
| Expo | LOGTG | 52 | 120.8 | 9.0 | 29.1 | 1 | 13.40 |
| Expo | NONHDL | 52 | 115.2 | 10.0 | 28.4 | 1 | 11.51 |
| Expo | TC | 52 | 123.5 | 10.0 | 29.4 | 1 | 12.35 |

This pattern was seen across all five lipid traits. In the Original method, the top-to-median ratio was 23.42 for HDL, 13.62 for LDL, 14.11 for log-transformed triglycerides, 14.59 for non-HDL cholesterol, and 14.22 for total cholesterol. In the Linear method, the corresponding values were 20.09, 11.81, 13.10, 12.20, and 12.77. In the Exponential method, they were 18.17, 11.29, 13.40, 11.51, and 12.35. In every method and trait, only one drug exceeded the chlorpromazine reference score of 100, and that drug was clozapine.

Clozapine scores varied modestly across methods. Under the Original method, clozapine scored 128.8 for HDL, 115.9 for LDL, 121.7 for log-transformed triglycerides, 115.9 for non-HDL cholesterol, and 123.2 for total cholesterol. Under Linear scaling, the corresponding values were 131.5, 114.2, 119.9, 114.1, and 123.5. Under Exponential scaling, they were 130.2, 115.3, 120.8, 115.2, and 123.5. Linear scaling produced the largest clozapine score for HDL, with a 2.7-point lift over the Original method. Exponential scaling produced a smaller HDL lift of 1.4 points. Across all traits, the mean Linear minus Original difference for clozapine was negative 0.5, and the mean Exponential minus Original difference was negative 0.1. Clozapine trait-specific scores are shown in Table 5\.

**Table 5\. Clozapine score by TWAS integration method**

| Trait | Original | Linear | Exponential |
| ----- | ----- | ----- | ----- |
| HDL | 128.8 | 131.5 | 130.2 |
| LDL | 115.9 | 114.2 | 115.3 |
| LOGTG | 121.7 | 119.9 | 120.8 |
| NONHDL | 115.9 | 114.1 | 115.2 |
| TC | 123.2 | 123.5 | 123.5 |

These results clarify the practical difference between the methods. Linear and Exponential scaling are more granular because they apply TWAS information at the receptor level. However, with the current TWAS files, this granularity did not improve the rank hierarchy or the separation of the top drug. Instead, per-receptor scaling modestly increased the scores of several mid-tier drugs, raising the median and reducing the top-to-median contrast. The Original method concentrated TWAS influence through the strongest receptor-level signal for each drug, which produced sharper discrimination.

### **Mechanistic Insights: Receptor Drivers**

The dominant receptor drivers were stable across methods. HRH1 and HTR2A appeared in the top three receptor contributors for every method. In the Original method, the top eight receptor drivers by mean rank were HRH1, HTR2A, HTR2C, DRD2, DRD3, ADRA1A, HTR7, and ADRA1B. In the Linear method, the top eight were HRH1, HTR2A, DRD2, HTR2C, ADRA1A, DRD3, HTR7, and ADRA1B. In the Exponential method, they were HRH1, HTR2A, HTR2C, DRD2, DRD3, ADRA1A, HTR7, and ADRA1B. The receptor-contribution drivers are summarized in Table 6\.

**Table 6\. Receptor-contribution drivers recomputed by method**

| Method | Top receptor-contribution drivers by mean rank |
| ----- | ----- |
| Original | HRH1 (1.0), HTR2A (2.0), HTR2C (3.0), DRD2 (4.0), DRD3 (5.0), ADRA1A (6.0), HTR7 (7.0), ADRA1B (8.0) |
| Linear | HRH1 (1.0), HTR2A (2.0), DRD2 (3.4), HTR2C (3.8), ADRA1A (5.0), DRD3 (5.8), HTR7 (7.2), ADRA1B (8.2) |
| Exponential | HRH1 (1.0), HTR2A (2.0), HTR2C (3.2), DRD2 (3.8), DRD3 (5.2), ADRA1A (5.8), HTR7 (7.2), ADRA1B (7.8) |

The small shifts among HTR2C, DRD2, DRD3, and ADRA1A reflect method sensitivity in secondary receptor contributors, not a change in the main biological signal. HRH1 remained the top driver in every method, consistent with prior evidence linking H1 affinity to antipsychotic-associated weight gain \[5\]. HTR2A also remained prominent across all methods. HTR2C was consistently important, although its contribution was likely attenuated by incomplete TWAS coverage. This is a key limitation because 5-HT2C biology is strongly relevant to appetite and antipsychotic-induced weight gain \[6\].

The receptor pattern supports the idea that antipsychotic metabolic liability is polyreceptor-driven. The strongest signals did not arise only from one receptor. Rather, the high-risk drugs tended to combine strong binding across several metabolically weighted targets. Clozapine and chlorpromazine are clear examples. Their high rankings reflected broad receptor engagement, not a single isolated TWAS hit.

### **Clozapine as the Invariant Highest-Risk Signal**

Clozapine was the most stable high-liability drug in the analysis. It ranked first across every lipid trait and every TWAS integration method. Its score was always above the chlorpromazine reference, ranging from 114.1 to 131.5 depending on trait and method. The highest value occurred for HDL under Linear scaling, while the lowest values occurred for LDL and non-HDL under Linear scaling. None of these variations changed its rank.

This invariance is important for interpretation. Clozapine’s position did not depend on whether TWAS was applied after aggregation, linearly at the receptor level, or exponentially at the receptor level. Its high score was driven by the Ki–DDD–receptor-weight backbone of the model and reinforced by TWAS information. This agrees with clinical experience and meta-analytic evidence identifying clozapine as one of the antipsychotics with the greatest metabolic burden \[1,3\].

### **Summary of Method Comparison**

The three-method comparison supports two conclusions. First, the core antipsychotic metabolic liability hierarchy is robust. Mean cross-method Spearman rho was 0.996, top-10 overlap was high, and the leading drugs were stable. Second, the Original method provided the best discrimination under current data conditions. Linear and Exponential methods remain useful sensitivity analyses because they test a more granular biological assumption, but they did not materially improve the ranking. Their main effect was to rescale score magnitudes and slightly adjust mid-rank drugs.

## **Discussion**

### **Robustness as a Methodological and Translational Strength**

The main strength of this framework is not that one TWAS scaling method produced a dramatically different result. It is the opposite. The liability hierarchy remained stable across three plausible methods for integrating TWAS information. This directly addresses a common concern in multi-omics scoring: that results may depend on arbitrary scaling choices. Here, the high-liability group was preserved whether TWAS was applied as a post-aggregation drug-level boost, a linear per-receptor modifier, or a mild exponential per-receptor modifier.

This robustness suggests that the ranking is driven primarily by the pharmacological backbone of the model: receptor affinity, clinical dose exposure, and metabolic receptor weighting. TWAS contributes an additional layer of biological relevance, but it does not dominate the score. That balance is desirable for a translational index. A model driven almost entirely by TWAS would be vulnerable to incomplete gene coverage, tissue mismatch, linkage disequilibrium artifacts, and unclear directionality. A model driven only by Ki values would ignore trait-specific genetic evidence. The present framework sits between these extremes.

The results also show why sensitivity analyses are essential. Linear and Exponential methods were more biologically granular than the Original method, because they allowed each receptor gene to carry its own TWAS weight. In principle, this is attractive. In practice, the full method comparison showed that this added granularity did not improve discrimination with the current lipid TWAS inputs. Instead, it produced nearly identical rankings and slightly weaker leader separation. This does not invalidate per-receptor scaling. It means that the present data are not yet rich enough for the more complex approach to outperform the simpler one.

### **Mechanistic Insights and Alignment with Existing Literature**

The receptor findings are consistent with established antipsychotic metabolic biology. HRH1 was the leading receptor driver across all three methods. This agrees with the study by Kroeze et al., which found that H1-histamine receptor affinity predicted short-term weight gain across typical and atypical antipsychotics \[5\]. H1 antagonism is biologically plausible as a contributor to weight gain because histaminergic signaling is involved in appetite and energy balance. In the present framework, HRH1 remained dominant even after TWAS scaling was altered, suggesting that its contribution is not a modeling artifact.

HTR2A also emerged as a stable top contributor. Its prominence should be interpreted carefully. The model assigned a moderate metabolic weight to HTR2A and several high-liability antipsychotics bind strongly to serotonergic receptors. The result indicates that HTR2A contributes to the model’s receptor-level burden, but it does not prove that HTR2A is the primary causal driver of antipsychotic metabolic disease. The broader serotonergic system, particularly HTR2C, has stronger direct links to appetite regulation and weight gain \[6\]. In this analysis, HTR2C remained among the top contributors, but its TWAS-modified role was limited by missing or incomplete TWAS coverage.

Muscarinic M3 signaling is another biologically important pathway. CHRM3 was given a high prior metabolic weight because of its relationship to insulin secretion and diabetes risk \[7\]. However, CHRM3 did not emerge as a top receptor driver in the final contribution rankings. This likely reflects the combination of available Ki values, drug-specific binding profiles, dose normalization, and TWAS coverage, rather than an absence of biological relevance. A receptor can be highly important mechanistically but still contribute less to a particular drug-level index if the relevant drugs do not show strong enough binding or if TWAS coverage is incomplete.

The findings therefore align with the view that antipsychotic metabolic liability is distributed across several receptor systems \[8,9\]. HRH1 appears central. HTR2A and HTR2C contribute serotonergic burden. Dopaminergic and adrenergic receptors add smaller but plausible contributions. This multi-receptor pattern is clinically credible because the highest-risk antipsychotics are pharmacologically broad agents.

### **Why the Original Method Performed Best with Current Data**

The Original method performed best on leader separation because it concentrated TWAS influence at the drug level. After receptor contributions were summed, the drug’s strongest absolute TWAS signal determined the main boost. This favored drugs with a strong receptor-weighted pharmacological base and at least one strong lipid-related TWAS signal. In the present dataset, that approach sharpened the separation of clozapine from the middle of the distribution.

The Linear and Exponential methods used a more granular logic. Each receptor contribution was scaled by its own TWAS signal before drug-level aggregation. This is biologically appealing because metabolic liability arises from multiple receptor interactions, not from one receptor in isolation. However, most antipsychotics bind several receptors with some metabolic relevance. When each receptor receives a TWAS modifier, many drugs receive modest increases across multiple targets. This raises the median score and reduces the top-to-median ratio. The top drug remains the top drug, but the contrast is softened.

This result should not be framed as a failure of per-receptor scaling. It is better understood as a consequence of current TWAS limitations. The model used absolute z-statistics, which measure signal strength but not whether genetically increased expression is metabolically harmful or protective. Several relevant genes had incomplete coverage, with HTR2C being the most important example. The framework also did not include tissue-specific filtering or colocalization. TWAS associations can be informative, but they can also be affected by linkage disequilibrium and tissue context, and methods such as S-PrediXcan and MetaXcan emphasize the value of colocalization and cross-tissue interpretation \[12,15\]. Under these conditions, a simple drug-level boost may be more robust than a more detailed receptor-level adjustment.

### **Translational and Clinical Implications**

The immediate clinical value of this framework is not that it should replace clinical judgment or outcome-based evidence. It should not. The score is a relative mechanistic index, not a calibrated clinical risk calculator. It does not estimate the probability that a given patient will gain a specific amount of weight or develop dyslipidemia. It also does not account for baseline metabolic status, illness severity, diet, activity, ancestry, polygenic risk, or concomitant medications.

Its value lies in structured comparison. The framework combines receptor affinity, dose exposure, receptor metabolic relevance, and lipid TWAS evidence into one reproducible ranking. This can help organize hypotheses for clinical research. For example, drugs in the high-liability cluster may warrant closer metabolic monitoring, especially when prescribed to patients with pre-existing cardiometabolic risk. Conversely, drugs with lower modeled scores may be considered when metabolic risk is a major concern, provided that psychiatric efficacy and tolerability are appropriate.

The framework may also be useful for drug development. The stable dominance of HRH1 supports the continued effort to avoid strong H1 antagonism when designing metabolically safer antipsychotics. The consistent contribution of serotonergic and adrenergic targets suggests that drug design should consider the full receptor profile rather than focusing only on dopamine D2 occupancy. A compound with acceptable antipsychotic efficacy but lower burden across HRH1, HTR2C, CHRM3, and relevant adrenergic targets would be expected to have a more favorable metabolic profile, although this would require clinical validation.

For precision psychiatry, the most promising direction is integration with patient-level data. Future versions could combine this drug-level liability index with patient polygenic risk for lipid traits, baseline lipid values, body mass index, diabetes risk, and longitudinal electronic health record outcomes. The TWAS layer could also be improved by using signed, tissue-aware, and colocalized gene-trait associations. Such extensions would move the framework from a relative mechanistic index toward a clinically calibrated decision-support tool.

The current ranking also highlights a caution. Some model outputs may not match simple clinical expectations. For example, the framework ranked asenapine highly in the consensus list. This should be interpreted as a signal from the model’s receptor-binding and dose-normalized structure, not as proof that asenapine has higher real-world metabolic event rates than all drugs below it. Clinical meta-analyses remain essential for estimating observed patient outcomes \[3,4\]. The framework is best used as a mechanistic complement to clinical evidence.

### **Limitations and Future Directions**

Several limitations are important. First, the TWAS layer used absolute z-statistics, which remove directionality. This means the model cannot distinguish a gene expression association that may increase lipid risk from one that may be protective. Second, TWAS coverage was incomplete for important metabolic receptors, especially HTR2C. Third, the model did not include tissue-specific weighting, colocalization filtering, or causal inference. Fourth, Ki values were aggregated using the minimum value, which captures strongest binding but may be sensitive to assay differences. Fifth, the framework has not yet been externally validated against patient-level metabolic outcomes.

Future work should use signed TWAS effects, improve receptor-gene coverage, incorporate tissue-specific and colocalized signals, and test the index against real-world longitudinal metabolic data. The framework should also be extended beyond lipid traits to include glycemic, inflammatory, adiposity, and cardiovascular outcomes. These steps would allow the model to move from relative liability ranking toward clinically actionable risk estimation.

## **Conclusion**

This study developed and compared a Ki–DDD–TWAS framework for estimating relative lipid-metabolic liability across antipsychotic drugs. The framework integrates receptor affinity, defined daily dose, curated metabolic receptor weights, and lipid TWAS evidence. Across five lipid traits and three TWAS integration strategies, the resulting liability hierarchy was highly stable. Mean cross-method Spearman rho was 0.996, and the leading high-liability drugs remained consistent.

Clozapine was the invariant highest-risk drug across every method and trait. Chlorpromazine served as the reference and ranked second. The broader high-liability group included asenapine, zotepine, risperidone, ziprasidone, olanzapine, and thioridazine. Receptor-contribution analyses showed stable dominance of HRH1 and HTR2A, with HTR2C, DRD2, DRD3, ADRA1A, HTR7, and ADRA1B contributing to the broader receptor pattern.

The Original method is recommended as the primary specification for the current dataset. It is simpler, more transparent, more robust to incomplete receptor-level TWAS coverage, and provided the strongest leader separation. Linear and Exponential per-receptor methods remain useful sensitivity analyses. They are biologically attractive and may become preferable when TWAS resources provide better receptor coverage, signed effects, tissue specificity, and colocalization support.

The framework should not be interpreted as a calibrated clinical risk calculator. It is a relative mechanistic index. Its strongest near-term use is in research, risk stratification, model comparison, and drug-development prioritization. With external validation and improved TWAS inputs, the approach could help bridge pharmacology, genomics, and clinical psychiatry in the effort to reduce antipsychotic metabolic harm.

## **References**

\[1\] Allison DB, Mentore JL, Heo M, et al. Antipsychotic-induced weight gain: a comprehensive research synthesis. *Am J Psychiatry*. 1999;156(11):1686-1696. doi:10.1176/ajp.156.11.1686

\[2\] Correll CU, Lencz T, Malhotra AK. Antipsychotic drugs and obesity. *Trends Mol Med*. 2011;17(2):97-107. doi:10.1016/j.molmed.2010.10.010

\[3\] Pillinger T, McCutcheon RA, Vano L, et al. Comparative effects of 18 antipsychotics on metabolic function in patients with schizophrenia, predictors of metabolic dysregulation, and association with psychopathology: a systematic review and network meta-analysis. *Lancet Psychiatry*. 2020;7(1):64-77. doi:10.1016/S2215-0366(19)30416-X

\[4\] Burschinski A, Schneider-Thoma J, Chiocchia V, et al. Metabolic side effects in persons with schizophrenia during mid- to long-term treatment with antipsychotics: a network meta-analysis of randomized controlled trials. *World Psychiatry*. 2023;22(1):116-128. doi:10.1002/wps.21036

\[5\] Kroeze WK, Hufeisen SJ, Popadak BA, et al. H1-histamine receptor affinity predicts short-term weight gain for typical and atypical antipsychotic drugs. *Neuropsychopharmacology*. 2003;28(3):519-526. doi:10.1038/sj.npp.1300027

\[6\] Reynolds GP, Hill MJ, Kirk SL. The 5-HT2C receptor and antipsychotic-induced weight gain: mechanisms and genetics. *J Psychopharmacol*. 2006;20(4 suppl):15-18. doi:10.1177/1359786806066040

\[7\] Weston-Green K, Huang XF, Deng C. Second generation antipsychotic-induced type 2 diabetes: a role for the muscarinic M3 receptor. *CNS Drugs*. 2013;27(12):1069-1080. doi:10.1007/s40263-013-0115-5

\[8\] Nasrallah HA. Atypical antipsychotic-induced metabolic side effects: insights from receptor-binding profiles. *Mol Psychiatry*. 2008;13(1):27-35. doi:10.1038/sj.mp.4002066

\[9\] Siafis S, Tzachanis D, Samara M, Papazisis G. Antipsychotic drugs: from receptor-binding profiles to metabolic side effects. *Curr Neuropharmacol*. 2018;16(8):1210-1223. doi:10.2174/1570159X15666170630163616

\[10\] Gamazon ER, Wheeler HE, Shah KP, et al. A gene-based association method for mapping traits using reference transcriptome data. *Nat Genet*. 2015;47(9):1091-1098. doi:10.1038/ng.3367

\[11\] Gusev A, Ko A, Shi H, et al. Integrative approaches for large-scale transcriptome-wide association studies. *Nat Genet*. 2016;48(3):245-252. doi:10.1038/ng.3506

\[12\] Barbeira AN, Dickinson SP, Bonazzola R, et al. Exploring the phenotypic consequences of tissue specific gene expression variation inferred from GWAS summary statistics. *Nat Commun*. 2018;9:1825. doi:10.1038/s41467-018-03621-1

\[13\] Leucht S, Samara M, Heres S, Davis JM. Dose equivalents for antipsychotic drugs: the DDD method. *Schizophr Bull*. 2016;42(suppl 1):S90-S94. doi:10.1093/schbul/sbv167

\[14\] Spearman C. The proof and measurement of association between two things. *Am J Psychol*. 1904;15(1):72-101. doi:10.2307/1412159

\[15\] Li B, Ritchie MD. From GWAS to gene: transcriptome-wide association studies and other methods to functionally understand GWAS discoveries. *Front Genet*. 2021;12:713230. doi:10.3389/fgene.2021.713230

