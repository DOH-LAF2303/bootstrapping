# bootstrapping
Adding bootstrap values to phylogenentic analysis - bare bones documentation

## Approach 1: Add bootstrap values to Nextstrain build
Following this GitIssue: [https://github.com/nextstrain/augur/issues/1456], download the python script `bootstrap_label.py` and add `-keep-polytomies` to augur refine 

Convert ending JSON to have labeled bootstrap values with python code
`python3 bootstrap_label.py --input INSERTJSONFILEHERE.json --output ENDINGJSON_bootstrap.json`


## Approach 2: Use iqtree on aligned fasta to generate bootstrap values

Align fastas with specified outgrout using mafft: 
`allfastas.fasta`
`mafft allfastas.fasta > allfastas_aligned.fasta`
 
Run through iqtree
`iqtree -s allfastas_aligned.fasta -o "OUTGROUPNAMEHERE"  -bb 1000 -bnni`
 
Write out files for auspice by converting .treefile into .nwk file
`cp allfasta_aligned_bootstrapped.treefile allfasta_aligned_bootstrapped.nwk`
