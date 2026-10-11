# Data Setup

Download the dataset from:
https://data.mendeley.com/datasets/3hckgznc67/1

After downloading, extract it (or place `skin_dataset.zip` here and let the notebook extract it) so the structure looks like:

data/
├── Nail_psoriasis/
├── SJS-TEN/
├── Vitiligo/
├── acne/
└── hyperpigmentation/

Folder names are case-sensitive and must match exactly.

**Note:** the 9,548 files are 341 unique photos, each provided as 28 pre-augmented variants (file names start with `Crop-`, `padd-`, `Resize-`, `hue-`, `saturation-`, `flip-`, or `superpixels-`). The notebook groups files by source photo so that no photo appears in more than one of the train/validation/test splits.
