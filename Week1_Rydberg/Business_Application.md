

![CDL 2022 Cohort Project](../CDL_logo.jpg)
# Business Application : Oracle of assets

*Quantum in economics, it changes everything and we help you make your decisions!*



<center><img src="Images/Oracle.png" width="200"></center>

<center>Figure 1. Logo for Oracle of assets. </center>



## Introduction

One of the challenges of computing is to solve problems with a large amount of data, but there are some problems due to their complexity that take a long time to solve, these are known as NP problems, and one of these is the Maximum Independent set (MIS), there are different proposals to solve but they fail to reduce its complexity as the greedy strategy [1](#References). There is possible in  a graph $G(n, m)$ that contains $n$ vertices and $m$ edges, it is known that unless $P=NP$ no polynomial algorithm can find a $O\left(n^{1-\epsilon}\right)$ approximate solution in the worst case[2](#References).


![Example of a Graph](Images/graph.png)
<center>Figure 2. Example of a graph. </center>



One of the latest efforts in quantum computation research is to use a sizable quantum many-body system to solve non-deterministic polynomial-time (NP)-optimization problems. One proposal is the design of the Rydberg Blockade, one of the most important properties of neutral-atom quantum computing based on Rydberg states. It naturally encodes the independent set constraint. Other is using The Quantum Approximate Optimization Algorithm (QAOA), where a quantum state is created by a p-depth circuit specified by 2p variational parameters and using a classical optimizer to find the  best states[3](#References). 



In the financial markets are complex environments that produce huge amounts of noisy data. Therefore, there are difficulties in dealing with these, one of the problems, online portfolio selection, aims to exploit data from different stocks to select asset portfolios in order to obtain positive investment results considering to decrease the different possible risks. One option is use the quantum advantage to improve this kind of  problems[4](#References).



## Problem: Portfolio optimization 

By considering the above case, the portfolio optimization problem can be implemented. Where each stock has time-dependent returns, which may or may not be correlated with other stocks. For this, a graph must be considered where each vertex is a stock, and there is an edge between the vertices if the assets are correlated or not within a certain threshold[4](#References). 

To solve this problem can be based on the maximum clique problem, where this is represented in a graph is the largest subset of vertices that are completely connected. That is, each vertex is adjacent to all other vertices in the clique.  The natural complement to this problem is MIS[4](#References). 



## What is Oracle Of Assets?


The oracle of assets is a tool for investors that identifies a subgroup of assets that minimize the risk to lose money. Using neutral atoms, we can identify such a subgroup using an algorithm known as Maximum Independent Set (MIS). The subgroup of assets will not share a correlation between them, therefore if the price in the market of one of the assets decreases it won't affect the price of the others. Our algorithm will ensure that the subgroup will have the greater variety of assets possible for an investor to invest in [4](#References)[5](#References).


![Assets](Images/Stocks.png)
<center>Figure 3. Eight stock prices. </center>


## Business

Any system that has multiple processes that are altered in the evolution of time, through certain factors that we cannot control, as is the case of the complex environment in which technology, media and telecommunications companies or investors who want to value their assets considering the risks and current situations of the companies of their interest. Where they are trying to drive growth by optimizing their asset portfolios. It consists of two phases, the quantitative finance problems, which is the prediction, and the decision-based optimization of these predictions [6](#References) [7](#References) . Therefore, covariance forecasting models are important, they are optimized with unique objectives and constraints based on the prediction. In the case of identifying the shares of a company, when investing it is important to consider the positions, the line of business and that some depend on another company for their relationships or that they are a block of a larger company, such as the shares of their CEOs. 

Like the case Multiverse & BBVA mentioned in their news, we need to find a way that we can tell investors where to put their money. Where the best sequence of buying and selling is most accurate with our proposal. But this will depend on time with multiple conditions where the objective is to increase profits and decrease losses, being a rational being is what we are looking for[8](#References).


## Example 


In order to demonstrate our project, we used 8 stocks from 8 conglomerates based on the work from Xu et al. [9](#References):

- Basic Materials: TOTAL S.A. "TOT"
- Consumer Goods: Appel Inc. "AAPL"
- Healthcare: AbbVie Inc. "ABBV"
- Services: Wall-Mart Stores Inc. "WMT"
- Utilites: Duke energy corporation "DUK"
- Financial: HSBS Holding pcl "HSBC"
- Industrial Goods: ABB Ltd. "ABB"
- Technology: China Mobile Limited "CHL"


The information comes from Sep 2012 to Sep 2017 with daily Technical information of Open, High, Low, Close, Adj Close, and Volume for the stocks price.


![Assets](Images/stock_predictions.png)
<center>Figure 4. Eight stock prices predictions. </center>


For this purpose, a hybrid classical-quantum algorithm is used for forecasting. With those values now, covariance matrix can be  obtained.



![Covariance matrix](Images/cor.png)
<center>Figure 5. Covariance matrix. </center>



If the correlation between the two stocks exceeds a threshold during a period of time it means they are connected. We use a graph representation to show such a correlation as an edge between two nodes (the stocks).


![Example of a Graph](Images/graph_init.png)
<center>Figure 6.  Graph for the Portfolio optimization. </center>


### Proposals 1

We made two solution proposals in different frameworks, the first one using neutral atom.


The graph for this architecture is designed with the representation of the covariance matrix. And exists a natural connection between the independent set constraint, and the Rydberg Blockade phenomenon in neutral-atom quantum computing using Rydberg states. we chose an arbitrary lattice for certain points and the smallest spacing was 0.5 μm and the largest was 7.5μm. For all the previous considerations the blockade radius to be 7.5 μm [10](#References).


![Matom list](Images/atom_list.png)
<center>Figure 7. Atom list. </center>


Is important considr that the Rydberg blockade radius can be computed with

$$
C_{6} / R_{b}^{6} \sim \sqrt{\Delta^{2}+\Omega^{2}}
$$

The default $C_{6}=2 \pi * 862690 \mathrm{MHz} \mu \mathrm{m}^{6}$. For encoding the corresponding MIS problem at $\Omega=0$, the detuning can be set around $2 \pi \times 11 \mathrm{MHz}$ for a blockade radius of $7.5 \mu \mathrm{m}$ (see the parameters in $\mathrm{S}$. Ebadi, et al.) [11](#References).


The histogram result you can see different state with probability in the figure 8.


![histogram's atom list](Images/probability.png)
<center>Figure 8. Histogram for atom list.</center>

For those we select  all the states with more probability and the correct answer is in that subset, where is 3,4.


![graph solution aotm list](Images/atom_sol.png)
<center>Figure 9. Graph solution using proposal 1.</center>


### Proposals 2


Using the other using QAOA in Qiskit form IBM. We cna obtain the same graph but in a quantum circuit.

![Quantum circuit](Images/qc.png)
<center>Figure 10. Quantum circuit for QAOA.</center>


The cost function is obtained in the following plot.

![Cost fun](Images/cost_func.png)
<center>Figure 11. Cost function.</center>
 

The result is the same like in the previous proposal, we cna compare both graph.


![QAOA's result](Images/graph_sol.png)
<center>Figure 12. QAOA's result.</center>


### Competitors


Our main competitor for this work is Multiverse computing, as it is the direct and benchmarked company that we can compare and it had a grant of $2.8 million on December 17, 2021 [12](#References).


### Potential Customers

Aimed at banks and investors who need to identify possible actions and conditions to identify risks when investing in different assets.



## Video Presentation

[Video presentation](https://www.youtube.com/watch?v=UE8o_7odF_M)


![Cover video](Images/cover.png)

# References

[1] Nyikosa, Favour & Osborne, Michael & Roberts, Stephen. (2019). Adaptive Configuration Oracle for Online Portfolio Selection Methods. 

[2] Yu, Hongye & Wilczek, Frank & Wu, Biao. (2020). Quantum Algorithm for Approximating Maximum Independent Sets. 

[3] Saleem, Zain. (2020). Max-independent set and the quantum alternating operator ansatz. International Journal of Quantum Information. 18. 2050011. 10.1142/S0219749920500112. 

[4] Wurtz, J., Lopes, P., Gemelke, N., Keesling, A., & Wang, S. (2022). Industry applications of neutral-atom quantum computing solving independent set problems. http://arxiv.org/abs/2205.08500

[5] Minhyuk, Kim & Kim, Kangheun & Hwang, Jaeyong & Moon, Eun-Gook & Ahn, Jaewook. (2021). Rydberg Quantum Wires for Maximum Independent Set Problems with Nonplanar and High-Degree Graphs. 

[6] Zhang, Chao & Zhang, Zihao & Cucuringu, Mihai & Zohren, Stefan. (2021). A Universal End-to-End Approach to Portfolio Optimization via Deep Learning. 

[7] Zhao, Longfeng & Wang, Chao & Wang, Gang-Jin & Stanley, H. & Chen, Lin. (2021). Community detection and portfolio optimization. 

[8] Multiverse & BBVA work on Portfolio Optimization (2020),https://www.multiversecomputing.com/news/multiverse-bbva-work-on-portfolio-optimization/

[9] Stock Movement Prediction from Tweets and Historical Prices](https://aclanthology.org/P18-1183) (Xu & Cohen, ACL 2018)

[10] Bloqade, https://queracomputing.github.io/Bloqade.jl/dev/lattices/#BloqadeLattices.random_dropout-Union{Tuple{T},%20Tuple{D},%20Tuple{AtomList{D,%20T},%20Real}}%20where%20{D,%20T}

[11] The Maximum Independent Set Problem,https://queracomputing.github.io/Bloqade.jl/dev/tutorials/4.MIS/main/#mis-tutorial


[12] Multiverse Computing Funding, Multiverse Computing Valuation & Multiverse Computing Revenue, https://www.cbinsights.com/company/multiverse-computing/financials