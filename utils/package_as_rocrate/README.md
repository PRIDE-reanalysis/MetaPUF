# Package up a MetaPUF-created GFF file as an RO-Crate

This script is a helper that packages/publishes a GFF file, created by the [MetaPUF pipeline](https://github.com/pride-reanalysis/metapuf), as an [RO-Crate](https://www.researchobject.org/ro-crate/).

The schema of the RO-Crate is one that is supported by [MGnify](https://www.ebi.ac.uk/metagenomics): 
it contextualises the GFF file with enough metadata that it can be displayed in the MGnify Assembly Analsysis Contig Viewer (an [IGV.js](https://github.com/igvteam/igv.js/) instance) alongside other annotation tracks.

## Requirements
Python3 and pip.

## Installation
This util is not part of the MetaPUF Snakemake pipeline itself.

```bash
cd utils/package_as_rocrate/
pip install -r requirements.txt
```

## Usage
Call the `package_metapuf_as_crates` script with the path to a GFF, and the [PRIDE](https://www.ebi.ac.uk/pride/) PXD accession of the dataset that generated the GFF.

E.g.:

```bash
python package_metapuf_as_crates.py examples/*.gff PXD005780
```

Optionally, an output directory may be specified other than the default `./crates`:

```bash
python package_metapuf_as_crates.py examples/*.gff PXD005780 --output_dir my-crates-folder
```

## Sharing/browsing the crates
The resulting crates are .zip compressed archives, containing the GFF file alongside provenance metadata (the datasets and workflow information).
This means the crate .zip files can be helpful for distributing results in a FAIR manner.

MGnify's website also supports these crates: e.g. for the example dataset, browse to [Analysis page MGYA00579915 for ERZ1669337](https://www.ebi.ac.uk/metagenomics/analyses/MGYA00579915#contigs-viewer) and load the crate zip into the Contig browser's "Offline RO-Crate" feature.
