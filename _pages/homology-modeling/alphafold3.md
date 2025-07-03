---
layout: single
title: "AlphaFold3"
permalink: /homology-modeling/alphafold3/
sidebar:
        nav: homology-modeling-nav
jonlist: 
  - title: Piper
    language: python
    code_content: |
      print("Hello World");
    text_content: |
      Additional area under the code content where one
      can add text that is also formatted in **markdown**.
      You can add [links](https://qiujames.github.io/) or even images!
      ![birdie!](/assets/images/favicon.ico)
  - title: Jonathan
    language: python
    code_content: |
      print("Hello World");
    text_content: |
      blah blah blah blah
annelist: 
  - title: Seven
    language: python
    code_content: |
      print("Hello World");
    text_content: |
      Additional area under the code content where one
      can add text that is also formatted in **markdown**.
      You can add [links](https://qiujames.github.io/) or even images!
      ![birdie!](/assets/images/favicon.ico)
  - title: Anne
    language: python
    code_content: |
      print("Hello World");
    text_content: |
      blah blah blah blah
---

```mermaid
block-beta
    columns 3
    prep_HM["<a href='/sops/homology-modeling' target='_self'><strong>Prepare</strong></a>"]
    block:prep_HM_block:2
      prep_HM_seq_align["<a href='/sops/homology-modeling/sequence-alignment/' target='_self'>Sequence Alignment: UGENE</a>"]
    end
    expl_HM["<a href='/sops/homology-modeling' target='_self'><strong>Explore</strong></a>"]
    block:expl_HM_block:2
      expl_HM_similarity["Similarity Percentage"]
    end
    gene_HM["<a href='/sops/homology-modeling' target='_self'><strong>Generate</strong></a>"]
    block:gene_HM_block:2
      columns 2
      gene_HM_alphafold3["<a href='/sops/homology-modeling/alphafold3/' target='_self'>AlphaFold3</a>"]
      gene_HM_boltz["BOLTZ"]
      gene_HM_robetta["Robetta/Rosetta"]
    end
    vali_HM["<a href='/sops/homology-modeling' target='_self'><strong>Validate</strong></a>"]
    block:vali_HM_block:2
      columns 3
      vali_HM_dataWrangling["Data Wrangling"]
      vali_HM_swiss["SwissModel"]
      vali_HM_prosa["ProSA"]
      vali_HM_verify3d["Verify3D"]
      vali_HM_top["Chosing Top Model"]
    end
    repo_HM["<a href='/sops/homology-modeling' target='_self'><strong>Report</strong></a>"]
    block:repo_HM_block:2
      repo_HM_report["Protein Modeling Results Template"]
    end

    classDef parent fill:transparent,stroke:none;
    class prep_HM,expl_HM,gene_HM,vali_HM,repo_HM parent
    
    classDef blocks
    class prep_HM_block,expl_HM_block,gene_HM_block,vali_HM_block,repo_HM_block blocks

    classDef subBlocks fill:#B2E3F5,stroke:none
    class prep_HM_seq_align,expl_HM_similarity,gene_HM_boltz,gene_HM_robetta,vali_HM_dataWrangling,vali_HM_swiss,vali_HM_prosa,vali_HM_verify3d,vali_HM_top,repo_HM_report subBlocks

    style gene_HM_alphafold3 fill:#9C7AC7
```

{% include tablist id="annelist" %}


# AlphaFold3

### Preparing Your Files

*Scripts can be found in the Brown Lab OSF or SOP GitHub Repository*

**Files needed**: run_alphafold.py, af3-json.py, FASTA file for your protein sequence

Once you have downloaded these files, upload them to a folder in your ARC directory (or other working directory) using `sftp put`.

You first must convert your FASTA file to the AlphaFold3 supported JSON file. 
Basic command and flag options are as follows:
        `python af3-json.py`
        -f --file_input, name of fasta file input
        -d --directory, name of directory containing fasta files for input
        -o --output, desired name of output file (.json flag not needed)
        -v --verbose, turns on verbose mode for action monitoring

### Run AlphaFold3

Once you have generated the appropriate json file(s), initiate the alphafold python scripts by typing `python run_alphafold.py` using the `--help` flag to determine any flags desired for your specific model.

{% include tablist id="jonlist" %}

AlphaFold3 can be run either by use of this run_alphafold.py script *or* by directly calling AlphaFold by typing `alphafold3`. Using the latter option does not allow for multiple models to run in parallel as the .py script does, decreasing overall efficiency when being used in high throughput research. Therefore, we recommend *only directly calling AlphaFold to test the installation of the program*, and not for modeling studies.

### The Outcome

Expected outputs: Models generated (seed-#-sample-#) in cif format, csv file of model rankings, json file listing the confidences of each model.

These outputs can be visualized in a molecular visualization software, such as PyMOL, and can be validated using various techniques, described in later portions of this SOP. Validated models can readily be used for further computational analysis such as molecular docking or molecular dynamics.