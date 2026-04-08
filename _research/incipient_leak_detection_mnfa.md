---
title: "Incipient Leak Detection: Deep Learning is Superior!"
image: /assets/images/dl_ae_mnfa.jpg
paper: https://doi.org/10.1016/j.aei.2023.102135
code: 
date: 2026-04-05
categories: [research, engineering]
tags: [leakage detection, water distribution networks, deep learning, BiLSTM, autoencoder]
description: "How can deep learning help identify small growing leaks that notoriously stay hidden for weeks in the presence of demand uncertainly and emergent sleepless nights in large cities?"
author: "Michel Torny, Hadi Mohammed, Razak Seidu"
layout: default
---

# Incipient Leak Detection: How Deep Learning Outperforms Traditional Methods

Water utilities worldwide face a major challenge: hidden leaks in their distribution networks. Across the world, about 30% of water is lost before it reaches consumers. Traditional methods like Minimum Night Flow (MNF) and Average Night Flow (ANF) try to spot leaks by looking for unusually high water use during the quietest hours (2–4 am). But these methods often fail in today’s unpredictable, “sleepless” cities, where late-night activity and random demand make leaks hard to spot.

A new approach that uses deep learning, specifically a sequence-to-sequence Bidirectional LSTM (BiLSTM) Autoencoder, to tackle this problem is introduced. Instead of relying on a single metric (like minimum night flow or average night flow), this method analyzes the entire night flow pattern, learning what “normal” looks like and flagging anything unusual. It only needs normal (non-leak) data for training, which is readily available for most water utilities.

This method is battle tested on real world data from Ålesund, Norway, covering residential, commercial, and industrial DMAs. The results were impressive: the BiLSTM Autoencoder detected leaks within 1–4 days, compared to 15 days or more for traditional night flow analysis methods. It also produced fewer false alarms, saving time and money by reducing unnecessary field checks.

### Key Practical Takeaways

- The method adapts to different types of DMAs, demand patterns with limited training data.
- Timely identification of unreported leaks in all types of DMAs with limited false alarms.
- Early leak detection means less wasted water, lower repair costs, and better service for customers.

Summarily, sequence-to-sequence deep autoencoder offers a smarter, faster, and more reliable way to catch leaks early in water distribution networks. As cities grow and water becomes more precious, these AI-powered tools will be essential for sustainable water management.

---

$$ $$

DOI: [https://doi.org/10.1016/j.aei.2023.102135](https://doi.org/10.1016/j.aei.2023.102135)

```bibtex
@article{tornyeviadzi2023semi,
  title={A semi-supervised sequence-to-sequence bidirectional long short-term memory deep autoencoder for night flow analysis in water distribution networks},
  author={Tornyeviadzi, Hoese Michel and Mohammed, Hadi and Seidu, Razak},
  journal={Advanced Engineering Informatics},
  volume={58},
  pages={102163},
  year={2023},
  publisher={Elsevier},
  doi={10.1016/j.aei.2023.102163}
}
```