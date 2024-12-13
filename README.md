# Entity Matching Literature

A list of entity resolution and entity alignment papers on the relational data and knowledge graph data.

Papers are categorized by objects: ```Relational Data``` and ```Knowledge Graph``` and sorted by year.

## Sources

Top conferences: ```SIGMOD```, ```VLDB```, ```NIPS```, ```KDD```, ```ICDE```, ```SIGIR```, ```WWW```, ```ICLR```, ```ICML```, ```ACL```, ```IJCAI```, ```AAAI```

Top journals: ```TKDE```

## Entity Resolution (Table)

|Year   | Title  | Model | Type | Venue | Paper | Code |
|-------|--------|--------|--------|--------|--------|--------|
|2024|**MRG-SER: Self-supervised Spatial Entity Resolution Based on Multi-Relational Graph**|AttrGNN + BERT|Self-supervised|`VLDB`|[PDF](https://vldb.org/workshops/2024/proceedings/LSGDA/LSGDA24.03.pdf)|N/A|```
|2024|**MultiEM: Efficient and Effective Unsupervised Multi-Table Entity Matching**|Sentence-BERT + HNSW|Unsupervised|`ICDE`|[PDF](https://ieeexplore.ieee.org/document/10598123)|[Code](https://github.com/ZJU-DAILY/MultiEM)|
| 2024 | **Matching Feature Separation Network for Domain Adaptation in Entity Matching** | Pre-trained LM (BERT) + Transformer | Supervised | `WWW` | [PDF](https://doi.org/10.1145/3589334.3645397) | [Code](https://github.com/DMA-Group/MFSN-DAEM) |
| 2024 | **BoostER: Leveraging Large Language Models for Enhancing Entity Resolution** | LLM(GPT-4) | LLM | ``WWW`` | [PDF](https://dl.acm.org/doi/10.1145/3589335.3651245) | N/A|
| 2024 | **Cost-Effective In-Context Learning for Entity Resolution: A Design Space Exploration** | In-Context Learning + LLM (GPT-4) | LLM | `ICDE` | [PDF](https://ieeexplore.ieee.org/document/10597751) | [Code](https://github.com/fmh1art/BatchER) |
| 2023 | **The Battleship Approach to the Low Resource Entity Matching Problem** | Active Learning + BERT | Semi-supervised | `SIGMOD` | [PDF](https://doi.org/10.1145/3626711) | [Code](https://github.com/BarGenossar/The-Battleship-Approach-to-AL-of-EM-Problem) |
| 2023 | **REPLACE: A Logical Framework for Combining Collective Entity Resolution and Repairing** |  | Supervised | ```IJCAI``` | [PDF](https://www.ijcai.org/proceedings/2023/349) | N/A |
| 2023 | **CollaborEM: A Self-Supervised Entity Matching Framework Using Multi-Features Collaboration** | BERT + GNN + Multi-Feature | Self-supervised | `TKDE` | [PDF](https://ieeexplore.ieee.org/document/9647870) | [Code](https://github.com/ZJU-DAILY/CollaborEM) |
|2023|**CampER: An Effective Framework for Privacy-Aware Deep Entity Resolution**|RoBERTa + Collaborative Fine-tuning|Self-supervised|`KDD`|[PDF](https://doi.org/10.1145/3580305.3599266)|[Code]( https://github.com/ZJU-DAILY/CampER)|
|2023|**Benchmarking Filtering Techniques for Entity Resolution**||Unsupervised|`ICDE`|[PDF](https://ieeexplore.ieee.org/document/10184692)|[Code](https://github.com/gpapadis/ContinuousFilteringBenchmark) |
| 2023 | **FlexER: Flexible Entity Resolution for Multiple Intents** | FlexER (GNN + Multiplex Graph) | Supervised | `SIGMOD` | [PDF](https://doi.org/10.1145/3588722) | [Code](https://github.com/BarGenossar/FlexER/) |
| 2023 | **Ground Truth Inference for Weakly Supervised Entity Matching** | SIMPLE-EM (Random Forest) | Semi-supervised | `SIGMOD` | [PDF](https://doi.org/10.1145/3588712) | N/A |
| 2022 | **Bridging the Gap between Reality and Ideality of Entity Matching: A Revisting and Benchmark Re-Construction** |  |  | ```AAAI``` | [PDF](https://www.ijcai.org/proceedings/2022/552) | [Code](https://github.com/tshu-w/ember) |
| 2022 | **Unsupervised Entity Resolution With Blocking and Graph Algorithms** | | Unsupervised | `TKDE` | [PDF](https://ieeexplore.ieee.org/document/9079896) | [Code](https://github.com/uestc-db/Unsupervised-Entity-Resolution) |   
| 2022 | **Gradual Machine Learning for Entity Resolution** | Factor Graph + Gradual Learning | Self-supervised | `TKDE` | [PDF](https://ieeexplore.ieee.org/document/9130070) | N/A |
| 2022 | **Zero Matcher: A Cost-Off Entity Matching System** | BERT + GNN + Multi-type EM | Unsupervised | `SIGIR` | [PDF](https://doi.org/10.1145/3477495.3531661) | [Code](https://github.com/ZJU-DAILY/ZeroMatcher) |                                
|2022|**Effective Explanations for Entity Resolution Models**|LSTM + DistilBERT|Supervised|`ICDE`|[PDF](https://ieeexplore.ieee.org/document/9835425/)|[Code](https://github.com/tteofili/certa)|
|2022|**Synthesizing Privacy Preserving Entity Resolution Datasets**|Transformer + GAN|Unsupervised|`ICDE`|[PDF](https://ieeexplore.ieee.org/document/9835693)|N/A|
|2022|**Deep and Collective Entity Resolution in Parallel**|Logic Rules + ML|Supervised|`ICDE`|[PDF](https://ieeexplore.ieee.org/document/9835258)|N/A|
|2022|**Domain Adaptation for Deep Entity Resolution**|DADER(Pre-trained LMs (BERT) + RNN)|Semi-supervised |`SIGMOD`|[PDF](https://dl.acm.org/doi/10.1145/3514221.3517870)|[Code](https://github.com/ruc-datalab/DADER)|
|2022|**Entity Resolution with Hierarchical Graph Attention Networks**|HierGAT|Supervised|`SIGMOD`|[PDF](https://dl.acm.org/doi/10.1145/3514221.3517872)|[Code](https://github.com/CGCL-codes/HierGAT)|
|2022|**Hierarchical Entity Resolution using an Oracle**|Triplet Oracle|Semi-supervised|```SIGMOD```|[PDF](https://dl.acm.org/doi/10.1145/3514221.3526147)|N/A|```
|2021|**GNEW: A Generic One-to-Set Neural Entity Matching Framework**|gated GCN|Supervised|```WWW```|[PDF](https://dl.acm.org/doi/10.1145/3442381.3450119)|[Code](https://github.com/ChenRunjin/GNEM)|
|2021|**Rotom: A Meta-Learned Data Augmentation Framework for Entity Matching, Data Cleaning, Text Classification, and Beyond**|Meta Learning|Semi-supervised|```SIGMOD```|[PDF](https://dl.acm.org/doi/10.1145/3448016.3457258)|[Code](https://github.com/megagonlabs/rotom)|
|2021| **Dual-Objective Fine-Tuning of Bert for Entity Matching**   | Pre-trained model (JointBert) |Supervised|```VLDB```|[PDF](http://www.vldb.org/pvldb/vol14/p1913-peeters.pdf)|[Code](https://github.com/wbsg-uni-mannheim/jointbert)|
|2021|**Online Topic-Aware Entity Resolution Over Incomplete Data Stream**|topic-aware similarity|Unsupervised|```SIGMOD```|[PDF](https://dl.acm.org/doi/10.1145/3448016.3457238)|[Code](http://www.cs.kent.edu/~wren/TER-iDS/)|
|2021|**End-to-End Task Based Parallelization for Entity Resolution on Dynamic Data**|||```ICDE```|[PDF]()||
|2021|**Cost-effective Variational Active Entity Resolution**|VAER (VAE+Active learning)|Unsupervised|```ICDE```|[PDF](https://ieeexplore.ieee.org/document/9458760)||
|2021|**Automating Entity Matching Model Development**|AutoML-EM-Active|Semi-supervised|```ICDE```|[PDF](https://ieeexplore.ieee.org/document/9458781)||
|2021|**Improving the Efficiency and Effectiveness for BERT-based Entity Resoltion**|BERT-ER|Supervised|```AAAI```|[PDF]()|[Code]()|
|2020|**Efficient Entity Resoltion on Heterogeneous Records**|Super Record|Unsupervised|```TKDE```|[PDF](https://ieeexplore.ieee.org/document/8637043)||
|2020|**$r$-HUMO: A Risk-Aware Human-Machine Cooperation Framework for Entity Resolution with Quality Guarantees**|||```TKDE```|[PDF]()|[Code]()|
|2020|**Multi-Context Attention for Entity Matching**|multi-context attention (**MCA**)|Supervised|```WWW```|[PDF](https://dl.acm.org/doi/10.1145/3366423.3380017)||
|2020|**Deep Entity Matching with Pre-Trained Language Model**|Data Augment + BERT (**Ditto**)|Supervised|```VLDB```|[PDF](http://www.vldb.org/pvldb/vol14/p50-li.pdf)|[Code](https://github.com/megagonlabs/ditto)|
|2020|**ZeroER: Entity Resolution using Zero Labeled Examples**||Unsupervised|```SIGMOD```|[PDF]()|[Code]()|
|2020|**Towards Interpretable and Learnable Risk Analysis for Entity Resolution**|||```SIGMOD```|[PDF]()|[Code]()|
|2020|**Entity Matching Meets Data Science: A Progress Report from the Magellan Project**|||```SIGMOD```|[PDF]()|[Code]()|
|2020|**A Comprehensive Benchmark Framework for Active Learning Methods in Entity Matching**|||```SIGMOD```|[PDF]()|[Code]()|
|2020|**Hierarchical Matching Network for Heterogeneous Entity Resolution**|||```IJCAI```|[PDF]()|[Code]()|
|2020|**Keys as Features for Graph Entity Matching**|||```ICDE```|[PDF]()|[Code]()|
|2020|**Crowdsourced Collective Entity Resolution with Relational Match Propagation**|||```ICDE```|[PDF]()|[Code]()|
|2020|**GraphER: Token-Centric Entity Resolution with Graph Convolutional Neural Networks**|||```AAAI```|[PDF]()|[Code]()|
|2020|**Accelerating Column Generation via Flexible Dual Optimal Inequalities with Application to Entity Resolution**|||```AAAI```|[PDF]()|[Code]()|
|2018|**Deep Learning for Entity Matching: A Design Space Exploration**|Deep Learning|Supervised|```SIGMOD```|[PDF](https://dl.acm.org/doi/10.1145/3183713.3196926)|[Code](https://github.com/anhaidgroup/deepmatcher)|