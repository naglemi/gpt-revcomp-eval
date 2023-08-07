# gpt-revcomp-eval
A key goal in the development of artificial general intelligence (AGI) is the ability to handle diverse tasks across domains of science. This requires abilities to work with diverse types of information, including not only verbal languages and programming languages, but also arithmetic and DNA sequence data. While large language models (LLMs) demonstrate impressive performance with verbal languages and programming languages, they are subject to marked rates of errors when dealing with tasks such as arithmetic or operations involving DNA sequence data.

Several common biological tasks involving DNA sequences are PCR primer design and CRISPR/Cas9 sgRNA design. State-of-the-art LLMs consistently underperform compared to standard programmatic pipelines for these tasks (e.g., [Primer3](https://primer3.ut.ee) and [CRISPRDirect](https://crispr.dbcls.jp)). One key root of errors appears to be the reliable determination of reverse complement DNA sequences. To find a reverse complement is a common exam question for general biology, and can be performed quite reliably by careful high school or undergraduate students with appropriate training. For those not familiar with the concept of reverse complements, you can see a tutorial on [WikiHow](https://www.wikihow.life/Find-the-Reverse-Complement-of-a-DNA-Sequence).

In this repository, I demonstrate the generation and deployment of an "eval" to evaluate the abilities of OpenAI GPT models to determine reverse complements of DNA sequences. This is distinct from the existing `reverse-string` eval, because we need to not only reverse a string, but also accurately identify complementary bases.

## Generating the eval
See notebook 1, `1_generate_eval.ipynb`, for how we can produce our eval dataset. The current eval includes 100 DNA sequences selected from the _Populus trichocarpa_ genome, ranging in length from 10-511 bases. By tweaking inputs and parameters, you can produce larger eval datasets, and use DNA sequences from other genome fasta files.

## Running the eval
See notebook 2, `2_run_eval.ipynb`, for deployment of the eval and results.

## Observations
- Errors are more frequent for longer sequences.
- Errors commonly appear when dealing with polynucleotide sequences (e.g., extra A added to AAAAA).
- GPT4 greatly outperforms GPT3.5 and GPT3.5-turbo.

## Next steps
- It would be fun to do statistical analysis to see how error rates depend on sequence lengths and polynucleotide frequency. However, powerful statistical analysis will require a large dataset (which can be obtained by tweaking parameters in `1_generate_eval.ipynb`), and a lot of API credits. We could also do analysis to measure signficance of differences in performance across GPT models (3.5, 3.5-turbo, 4.0).
- My hope is that this eval can help to evaluate and improve the abilities of GPT models to work with DNA sequences. Once reliable performance for reverse complements is achieved, GPT or GPT-like models will be closer to being able to handle common tasks involving DNA sequences, including basic tasks such as primer/sgRNA design, and perhaps one day more advanced and data-hungry tasks such as DNA/RNA sequence alignment and statistical -omics.

## Citation for Genome Data
Tuskan, Gerald A., et al. "The genome of black cottonwood, Populus trichocarpa (Torr. & Gray)." Science 313.5793 (2006): 1596-1604.

## Contact
Feel free to reach out to me with any questions.<br>
michael.nagle@oregonstate.edu<br>
website: michaelnagle.bio


