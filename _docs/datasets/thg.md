---
title: Temporal Heterogeneous Graph Link Property Prediction
permalink: /docs/thg/
---

<style>
r { color: rgb(231, 41, 138) }
b { color: Blue }
g { color: rgb(27, 158, 119) }
</style>


<div class="container">
    <div class="row">
        <div class="col-md-6">
            <p class="lead">
                In TGB 2.0, we introduced novel temporal heterogeneous graph datasets, of <r>small</r>, <b>medium</b> and <g>large scales</g>. 
            </p>
            <p class="lead">
                <b>Large in size:</b> THG datasets (marked in green) are significantly larger than existing datasets.<br/>
            </p>
            <p class="lead">
                <b>Edge Relations:</b> For THG datasets, the edge relation information is also provided for each quadruple and the task is to predict the tail in a query.<br/>
            </p>
            <p class="lead">
                <b>Node Types:</b> For all THG datasets, we also include the node type for each node in the graph. <br/>
            </p>
        </div>
        <div class="col-md-6 text-center">
            <img src="{{ "/assets/img/thg_stats.png" | relative_url }}" class="img-responsive">
        </div>
    </div>
</div>




##### The task is to predict properties of edges (pairs of nodes) at a future time.

### Summary

#### - Datasets

Scale | Name      | Package | #Nodes | #Edges\* |  #Steps  | Metric       |
|:---------:|:--------|:---------:|----------:|----------:|:------------------:|:----------------:|
<r>small</r> | [thgl-software](#thgl-software) | 2.0.0  | 681,927 | 1,489,806 |  689,549  | MRR  |
<b>medium</b> | [thgl-forum](#thgl-forum)      | 2.0.0  | 152,816  | 23,757,707  | 2,558,457  |  MRR  | 
<b>large</b> |  [thgl-github](#thgl-github)    | 2.0.0  | 5,856,765 | 17,499,577 | 2,510,415 | MRR  |  
<b>large</b> |  [thgl-myket](#thgl-myket)      | 2.0.0  | 1,530,835 | 53,632,788 | 14,828,090 | MRR  |  

#### - Module
Datasets are available in <code>Numpy</code> arrays, <code>Pytorch</code> tensors and <code>PyG TemporalData</code> objects.
We also provide the evaluator. 


<a name="thgl-software"/>

----------

### Dataset `thgl-software` ([Leaderboard](../leader_thg/#thgl-software)):

**Temporal Graph:** The `thgl-software` dataset is based on Github data collected by GH Arxiv. Only nodes with at least 10 edges were kept in the graph, thus resulting in 14 types of relations and 4 node types. The dataset spans January 2024. 

**Prediction task:** The task is to predict the next activity of a given entity, e.g., which pull request the user will close at a given time.

#### References

[1] Kian Ahrabian, Daniel Tarlow, Hehuimin Cheng, and Jin LC Guo. Software engineering event modeling using relative time in temporal knowledge graphs. arXiv preprint arXiv:2007 01231, 2020.

##### License: [CC-BY-4.0 License](https://creativecommons.org/licenses/by/4.0/)



<a name="thgl-forum"/>

----------

### Dataset `thgl-forum` ([Leaderboard](../leader_thg/#thgl-forum)):

**Temporal Graph:** The `thgl-forum` dataset is based on the user and subreddit interaction network on Reddit. The node types encode users or subreddits, the edge relations are “user reply to user” and “user -post” in subreddits. The dataset contains interactions from January 2014. 

**Prediction task:** The task is to predict which user or subreddit a user will interact with at a given time.

#### References

[2] Amirhossein Nadiri and Frank W Takes. A large-scale temporal analysis of user lifespan
durability on the reddit social media platform. In Companion Proceedings of the Web Conference 2022, pages 677–685, 2022.

##### License: [CC BY-NC 2.0 DEED License](https://creativecommons.org/licenses/by-nc/2.0/deed.en)



<a name="thgl-github"/>

----------

### Dataset `thgl-github` ([Leaderboard](../leader_thg/#thgl-github)):

**Temporal Graph:** The `thgl-github` dataset is based on Github data collected from the GH Arxiv. This is a large dataset from a different period from thgl-software . We extract user, pull request, issue and repository nodes and track 14 edge types. The nodes with two or fewer edges are filtered out. The dataset contains the network as of March 2024. 

**Prediction task:** The task is to predict the next activity of an entity.

#### References

[1] Kian Ahrabian, Daniel Tarlow, Hehuimin Cheng, and Jin LC Guo. Software engineering event modeling using relative time in temporal knowledge graphs. arXiv preprint arXiv:2007 01231, 2020.

##### License: [CC-BY-4.0 License](https://creativecommons.org/licenses/by/4.0/)


<a name="thgl-myket"/>

----------

### Dataset `thgl-myket` ([Leaderboard](../leader_thg/#thgl-myket)):

**Temporal Graph:** The `thgl-myket` dataset is based on the Myket Android App market. Each edge documents the user installation or update interaction within the Myket market. The data spans six months and two weeks and when compared to an existing smaller version, this dataset contains the full data without downsampling. Overall, the dataset includes information on 206,939 applications and over 1.3 million anonymized users from June 2020 to January 2021.

**Prediction task:** The task is to predict which app a given user will install or upgrade next. 

#### References

[3] Erfan Loghmani and MohammadAmin Fazli. Effect of choosing loss function when using
t-batching for representation learning on dynamic networks, 2023.

##### License: [CC BY-NC 4.0 DEED license](https://creativecommons.org/licenses/by-nc/4.0/deed.en)





