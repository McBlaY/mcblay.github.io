---
title: "Smarter Pressure Sensor Placement for Leak Detection"  # Page title
image: /assets/images/spp_entropy_optimization.jpg  # Banner image path
paper: https://doi.org/10.1016/j.aej.2024.03.037  # Link to paper
code:   # Link to code
date: 2026-04-08  # Publication date
categories: [tech, tutorial]  # Categories for organization
tags: [github, markdown]  # Tags for search
description: "How can Water Utilities with highly constrained budget place a number of limited pressure sensors in WDNs to maximize leakage identification and localization?"  # Meta description
author: "Michel Torny, Emmanuel Owusu-Ansah, Hadi Mohammed, Razak Seidu"  # Author name
layout: default  # Layout to use
---

# Pressure Sensor Placement for Leak Localization: Reducing Search Space with Entropy Optimization

Water utilities face a tough challenge: how to place a limited number of pressure sensors in large, complex water distribution networks (WDNs) to quickly detect leaks and minimize water loss. Just placing 20 pressure sensors in a 400 node WDN amounts to $ 2.7884 \times 10^{33} $ possibilities. It will interest you to note that these number of possibilities is more than the number of stars in the entire universe, 100 sextillion $(10^{20})$. Indeed, this is a classical problem of finding a needle in a haystack. 

Leveraging the inherent characteristics of WDNs and how they are managed and operated in real-life, we partition the network into homogenous segments analogous to DMAs or pressure zones. A novel algorithm leverages community detection and entropy calculations to preselect the most informative nodes subject to practical considerations such as suitability for sensor placement. This shrinks the search space significantly whiles maintaining network coverage with negligible loss. 

The sensor placement problem is formulated to maximize joint entropy (how informative the sensor position is) and coverage (the number of leaks localized within specified localization radius), while minimizing redundancy (total correlation or similarity) among sensors. The NSGA-II genetic algorithm finds the best trade-offs. To avoid human bias, the final sensor configurations are ranked using a hybrid Entropy-TOPSIS method, ensuring the most effective and objective sensor layout is prioritized.

The method was tested on the C-TOWN benchmark network. Results show only 21 sensors are needed to cover over $95\%$ of the network, demonstrating that smart search space reduction grounded in domain knowledge and optimization can deliver practical, cost-effective sensor layouts that maximize leak localization. The smart search space reduction shrank the search space by $67\%$ while losing less than $3\%$ in network coverage. 

### Key Practical Takeaways
 - Practical considerations such as minimum sensor resolution, measurement noise, and suitability of nodes to reliably host pressure is essential to practical smart sensor network design in WDNs.

 - Reducing the search space with data-driven pre-selection makes pressure sensor placement in large-scale WDNs ($\gt$ 10K nodes) computationally feasible and efficient.

 - Multi-objective and unbiased Multi Criteria ranking of optimal pressure sensor layouts ensure robust, cost effective and real-world sensor networks that accelerate leak localization in WDNs.

The framework presented and validated in this study empowers water utilities to deploy fewer sensors, detect and localize leaks faster, and save both water and money. Without optimal pressure sensor networks, water utilities will be flying blind and lack basic insights into their WDN. Optimal pressure sensors illuminate the network. 

---

$$ $$

DOI: [https://doi.org/10.1016/j.aej.2024.03.037](https://doi.org/10.1016/j.aej.2024.03.037)

```bibtex
@article{tornyeviadzi2024node,
  title={Node search space reduction for optimal placement of pressure sensors in water distribution networks for leakage detection},
  author={Tornyeviadzi, Hoese Michel and Owusu-Ansah, Emmauel and Mohammed, Hadi and Seidu, Razak},
  journal={Alexandria Engineering Journal},
  volume={94},
  pages={325--338},
  year={2024},
  publisher={Elsevier}, 
  doi={10.1016/j.aej.2024.03.037}
}
```