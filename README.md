# kNNProxy: Efficient Training-Free Proxy Alignment for Black-Box Zero-Shot LLM-Generated Text Detection

> **Note:** The code will be made publicly available upon acceptance of the paper.

## Overview

**kNNProxy** is a training-free framework for black-box, zero-shot detection of LLM-generated text. It addresses the challenge of distinguishing machine-generated content from human-written text without requiring access to the target model's internal parameters or any labelled training data.

The key idea is *proxy alignment*: rather than querying the target (black-box) LLM directly for every candidate token, kNNProxy identifies a small set of *k*-nearest-neighbour proxy tokens whose scoring behaviour closely mirrors that of the target model. This alignment step is performed once per context window and dramatically reduces the number of required API calls, making the approach both computationally efficient and cost-effective at scale.

## Key Features

- **Training-free** — no fine-tuning or labelled data required.
- **Black-box compatible** — works with any LLM accessible only via a generation/scoring API.
- **Zero-shot** — operates without any human/machine text examples at test time.
- **Efficient** — *k*-NN proxy alignment reduces API query overhead compared to naïve token-level scoring.

## Method

Given a text passage to evaluate, kNNProxy:

1. Retrieves the *k* nearest-neighbour proxy tokens for each position in the passage using a lightweight local model.
2. Aligns these proxies to the black-box target LLM's scoring distribution.
3. Aggregates aligned scores to produce a detection decision (human vs. machine).

## Citation

If you find this work useful, please cite our paper (BibTeX will be updated upon publication):

```bibtex
@article{kNNProxy2026,
  title   = {kNNProxy: Efficient Training-Free Proxy Alignment for Black-Box Zero-Shot LLM-Generated Text Detection},
  author  = {},
  journal = {},
  year    = {2026}
}
```

## License

This project is licensed under the [MIT License](LICENSE).
