# **A Weighted and Normalized Gould–Fernandez brokerage measure**

This repository contains a generalizable code to use the WNGF measure of the  following paper: https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0274475

## **Description**

This repository contains both a general-purpose, reusable implementation of the WNGF measure and a use case described in:

> Zádor, Zhu, Smith & Gorgoni (2022), *A Weighted and Normalized Gould–Fernandez brokerage measure*, PLOS ONE. https://doi.org/10.1371/journal.pone.0274475

The reusable implementation works on any weighted, directed network, as long as you can provide:
1. Edge weights between nodes (a full weight matrix, or an edge list), and
2. A group/category label for each node (e.g. location, department, country, community).

It reproduces the exact broker condition from the paper (Eq. 1):

$$\frac{1}{Z_{qr}} + \frac{1}{Z_{rs}} < \frac{1}{Z_{qs}}$$

where node **r** is a broker between its predecessor **q** and successor **s** if the combined "cost" of reaching s from q via r is lower than the direct cost from q to s. An edge weight of 0 (i.e. no edge) is treated as $Z=0$, so $1/Z_{qs}=\infty$ and the condition is automatically satisfied whenever both legs of the q→r→s path exist.

**Important assumption:** like the original paper, this code assumes edge weights represent *flow / strength / frequency* (bigger = a stronger, "cheaper" tie), e.g. trade value, money, messages, interactions. If your weights represent *cost or distance* (bigger = weaker tie), invert them first (e.g. `weight = 1 / distance`) before building the network.

Each node's role frequencies are also **normalized** for group size.

The use case notebook shows an example of WNGF usage on a company dataset from Cross, R., Parker, A. (2004). *The Hidden Power of Social Networks*. Harvard Business School Press.

## *Abstract*
The Gould and Fernandez local brokerage measure defines brokering roles based on the group membership of the nodes from the incoming and outgoing edges. This paper extends on this brokerage measure to account for weighted edges and introduces the Weighted–Normalized Gould–Fernandez measure (WNGF). The value added of this new measure is demonstrated empirically with both a macro level trade network and a micro level organization network. The measure is first applied to the EUREGIO inter-regional trade dataset and then to an organizational network in a research and development (R&D) group. The results gained from the WNGF measure are compared to those from two dichotomized networks: a threshold and a multiscale backbone network. The results show that the WNGF generates valid results, consistent with those of the dichotomized network. In addition, it provides the following advantages: (i) it ensures information retention; (ii) since no alterations and decisions have to be made on how to dichotomize the network, the WNGF frees the user from the burden of making assumptions; (iii) it provides a nuanced understanding of each node’s brokerage role. These advantages are of special importance when the role of less connected nodes is considered. The two empirical networks used here are for illustrative purposes. Possible applications of WNGF span beyond regional and organizational studies, and into all those contexts where retaining weights is important, for example by accounting for persisting or repeating edges compared to one-time interactions. WNGF can also be used to further analyze networks that measure how often people meet, talk, text, like, or retweet. WNGF makes a relevant methodological contribution as it offers a way to analyze brokerage in weighted, directed, and even complete graphs without information loss that can be used across disciplines and different type of networks.

## *Reference*
Zádor, Z., Zhu, Z., Smith, M., Gorgoni, S. (2022). A Weighted and Normalized Gould–Fernandez
brokerage measure. *PLOS ONE* 17(9): e0274475. https://doi.org/10.1371/journal.pone.0274475