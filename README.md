# Transformer Image Captioning

A PyTorch study of image-to-text generation that compares visual feature representations with a Transformer caption decoder. Upstream experiments use Flickr30k and beam search.

## Problem and model

The input is an image; the output is a natural-language caption. The code provides patch or grid visual encoders and an object-aware bottom-up feature path, followed by a Transformer decoder. Beam search produces the displayed captions.

![Upstream architecture](demo/transformer.PNG)

## Repository map

| Path | Purpose |
| --- | --- |
| `models/`, `configs/` | Captioning model and configuration |
| `preprocess/grid/cnn/` | Grid-feature preprocessing |
| `datasets/`, `augmentations/` | Data handling |
| `trainer/`, `metrics/` | Training and evaluation |
| `train.py`, `eval.py` | Entry points |
| `demo/` | Architecture diagrams and sample captions |

## Upstream reported results

The original README reports the following Flickr30k validation results after 100 epochs with beam width 3:

| Visual representation | BLEU-4 | METEOR | CIDEr |
| --- | ---: | ---: | ---: |
| DeiT tiny patches | 0.21026 | 0.18603 | 0.39589 |
| Faster R-CNN bottom-up | 0.22263 | 0.2128 | 0.4904 |

![Upstream caption example](demo/0.PNG)

Weights are linked in the [original README](UPSTREAM_README.md); external availability has not been revalidated. No new training or scoring was performed for this fork.

## Usage and attribution

The upstream guide documents `python train.py` and `python evaluate.py --weight=<checkpoint path>`; the actual root entry point here is `eval.py`, so inspect its arguments before using it. Based on and adapted from [kaylode/caption-transformer](https://github.com/kaylode/caption-transformer). The [original documentation](UPSTREAM_README.md), code references, and [MIT license](LICENSE) are retained.