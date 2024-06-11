---
title: TKG Link Property Prediction
permalink: /docs/tkg/
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
                In TGB 2.0, we introduced four novel temporal knowledge graph datasets, of <r>small</r>, <b>medium</b> and <g>large scales</g>. 
            </p>
            <p class="lead">
                <b>Large in size:</b> TKG datasets (marked in orange) are orders of magnitude larger than existing ones in terms of number of nodes, edges and timestamps.<br/>
            </p>
            <p class="lead">
                <b>Edge Relations:</b> For TKG datasets, the edge relation information is also provided for each quadruple and the task is to predict both the head or tail in a query (achieved by including inverse relations where the head and tail of an existing relation is inverted). <br/>
            </p>
            <p class="lead">
                <b>Static Relations:</b> For <r>tkgl-smallpedia</r> and <g>tkgl-wikidata</g>, we include additional static relation information which can be used to augment TKG methods. <br/>
            </p>
        </div>
        <div class="col-md-6 text-center">
            <img src="{{ "/assets/img/tkg_stats.png" | relative_url }}" class="img-responsive">
        </div>
    </div>
</div>

##### The task is to predict properties of edges (pairs of nodes) at a future time.

### Summary

#### - Datasets

Scale | Name      | Package | #Nodes | #Edges\* |  #Steps  | Time Granularity | Metric       |
|:---------:|:--------|:---------:|----------:|----------:|:----------------:|:------------------:|:----------------:|
<r>small</r> | [tkgl-smallpedia](#tkgl-smallpedia)      | 2.0.0  | 47,433 |  550,376  |  125  |  year   |  MRR  |
<b>medium</b> | [tkgl-polecat](#tkgl-polecat)      | 2.0.0  | 150,931 | 1,779,610  | 1,826  |  day    |   MRR  | 
<b>large</b> |  [tkgl-icews](#tkgl-icews)      | 2.0.0  | 87,856 | 15,513,446 | 10,224 | day | MRR  |  
<b>large</b> |  [tkgl-wikidata](#tkgl-wikidata)      | 2.0.0  |  1,226,440 | 9,856,203 | 2,025 | year |  MRR  |  

#### - Module
Datasets are available in <code>Numpy</code> arrays, <code>Pytorch</code> tensors and <code>PyG TemporalData</code> objects.
We also provide the evaluator. 


<a name="tkgl-smallpedia"/>

----------

### Dataset `tkgl-smallpedia` ([Leaderboard](../leader_tkg/#tkgl-smallpedia)):

**Temporal Graph:** The `tkgl-smallpedia` dataset is constructed from the Wikidata Knowledge Graph where it contains facts paired with Wikipedia pages. Each fact connects two entities via an explicit relation (edge type). This dataset contains Wikidata entities with IDs smaller than 1 million. The temporal relations either describe point in time relations (event-based) or relations with duration (fact-based). We also provide static relations from the same set of Wikidata pages which include 978,315 edges that can be used to enhance model performance. 

**Prediction task:** The task for this dataset is to predict future facts.

#### References

[1] Denny Vrandecic and Markus Krötzsch. Wikidata: a free collaborative knowledgebase. Communications of the ACM, 57(10):78–85, 2014.

##### License: [Wikidata License](https://www.wikidata.org/wiki/Wikidata:Licensing)


<a name="tkgl-polecat"/>

----------

### Dataset `tkgl-polecat` ([Leaderboard](../leader_tkg/#tkgl-polecat)):

**Temporal Graph:** The `tkgl-polecat` dataset is based on the POLitical Event Classification, Attributes, and Types (POLECAT) dataset which records coded interactions between socio-political actors of both cooperative or hostile actions. POLECAT utilizes the PLOVER ontology to analyze new stories in seven languages across the globe to generate time-stamped, geolocated events. These events are processed automatically via NLP tools and transformer-based neural networks. This dataset records events from January 2018 to December 2022. 

**Prediction task:** The task is to predict future political events between political actors.

#### References

[2] Grace I. Scarborough, Benjamin E. Bagozzi, Andreas Beger, John Berrie, Andrew Halterman, Philip A. Schrodt, and Jevon Spivey. POLECAT Weekly Data, 2023.

[3] Andrew Halterman, Benjamin E Bagozzi, Andreas Beger, Phil Schrodt, and Grace Scraborough. Plover and polecat: A new political event ontology and dataset. In International Studies Association Conference Paper, 2023.

##### License: [CC0 1.0 Deed](https://creativecommons.org/publicdomain/zero/1.0/)



<a name="tkgl-icews"/>

----------

### Dataset `tkgl-icews` ([Leaderboard](../leader_tkg/#tkgl-icews)):

**Temporal Graph:** This TKG dataset is extracted from the ICEWS Coded Event Data which spans a time frame from 1995 to 2022. The dataset records political events between actors. It is classified based on the CAMEO taxonomy of events which is optimized for the study of mediation and contains a number of tertiary sub-categories specific to mediation. When compared to PLOVER ontology in tkgl-polecat , the CAMEO codes have more event types (391 compared to 16). 

**Prediction task:** The task is to predict future interactions between political actors.

#### References

[4] Elizabeth Boschee, Jennifer Lautenschlager, Sean O’Brien, Steve Shellman, James Starz, and Michael Ward. ICEWS Coded Event Data, 2015.

[5] Andrew Shilliday, Jennifer Lautenschlager, et al. Data for a worldwide icews and ongoing research. Advances in Design for Cross-Cultural Activities, 455, 2012.

[6] Deborah J Gerner, Philip A Schrodt, Omür Yilmaz, and Rajaa Abu-Jabr. Conflict and mediation event observations (cameo): A new event data framework for the analysis of foreign policy interactions. International Studies Association, New Orleans, 2002.

##### License: [Custom Dataset License](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/28075&version=37.0&selectTab=termsTab)


<a name="tkgl-wikidata"/>

----------

### Dataset `tkgl-wikidata` ([Leaderboard](../leader_tkg/#tkgl-wikidata)):

**Temporal Graph:**  The `tkgl-wikidata` dataset is extracted from the Wikidata KG and constitutes a superset of tkgl-smallpedia . The temporal relations are properties between Wikidata entities. `tkgl-wikidata` is extracted from wikidata pages with IDs in the first 32 million. We also provide static relations from the same set of Wiki pages containing 71,900,685 edges. 

**Prediction task:** The task is to forecast future facts.

#### References

[1] Denny Vrandecic and Markus Krötzsch. Wikidata: a free collaborative knowledgebase. Communications of the ACM, 57(10):78–85, 2014.

##### License: [Wikidata License](https://www.wikidata.org/wiki/Wikidata:Licensing)




