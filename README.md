# Scale-Free Networks: An Interactive Demo

An in-browser demo of scale-free networks and power-law degree distributions. It compares random networks with scale-free networks and shows why the difference matters.

Created by Claude Opus 5.5, based on the lecture slides by Sang Hoon Lee.

## What's inside

The page is a single self-contained `index.html`. It has no build step and no dependencies apart from two Google Fonts, Source Serif 4 and IBM Plex Sans, and it falls back to system fonts if those fail to load. All networks are generated and analyzed live in the browser.

The demo has five sections:

1. **Random vs scale-free.** Two live force-directed drawings share the same number of nodes and the same average degree ⟨k⟩. One is an Erdős–Rényi random network and the other is a Barabási–Albert scale-free network. Hubs, meaning nodes with at least 3 × ⟨k⟩ links, are highlighted. Hovering over a node or tapping it shows its degree and neighbors.
2. **Poisson vs power law.** The degree distributions of large networks (2,000 to 50,000 nodes) are plotted on linear and log–log axes. Each plot includes the Poisson curve with the same ⟨k⟩ and a maximum-likelihood fit of the degree exponent γ. You can switch log-binning on or off.
3. **What "scale-free" means.** This section shows that the ratio P(bk)/P(k) equals b^−γ for every k under a power law, while the Poisson ratio collapses. You can choose γ, the multiplier b, and the starting k. It also shows which moments ⟨kⁿ⟩ are finite or diverge for the chosen γ; they diverge when γ ≤ n + 1.
4. **No typical degree.** A sampler draws 100 random nodes from each network. Growth experiments up to N = 100,000 show σ_k and the largest hub growing with N in scale-free networks, while both stay bounded in random ones.
5. **Why it matters in practice.** One experiment tests robustness by comparing random failures with targeted hub attacks on 10,000-node networks. Another measures the small-world effect by tracking average path length as N grows.

## Running it

Open `index.html` in any modern browser. To host it with GitHub Pages, push this repository and enable Pages for the branch that contains `index.html`.

## Models and methods

- **Random networks** use the G(N, M) model with M = N⟨k⟩/2 links placed uniformly at random.
- **Scale-free networks** use Barabási–Albert preferential attachment. Each new node attaches to m existing nodes with probability proportional to their degree, so ⟨k⟩ ≈ 2m and γ → 3 for large N.
- **The fitted γ** uses the discrete maximum-likelihood approximation γ = 1 + n [Σ ln(kᵢ / (k_min − ½))]⁻¹.
- **Robustness curves** are computed with a union-find sweep that adds nodes back in reverse removal order. Hub attacks remove nodes in order of their initial degree.
- **Average distances** come from breadth-first searches started at 24 randomly sampled nodes in the largest component.
- **The ratio and moment panels** use an ideal continuous power law.

## References

- A.-L. Barabási and R. Albert, "Emergence of scaling in random networks," *Science* 286, 509 (1999).
- R. Albert, H. Jeong, and A.-L. Barabási, "Diameter of the World-Wide Web," *Nature* 401, 130 (1999).
- A.-L. Barabási, *Network Science* (Cambridge University Press, 2016), Chapter 4.
