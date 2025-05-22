# CRCNS HC-3 Place Cell and Neuron Type Analysis

This repository presents an in-depth analysis of extracellular spike recordings from the dorsal hippocampus (CA1 region) of a freely moving rat. The dataset originates from the CRCNS hc-3 collection, which is widely used in neuroscience research related to spatial navigation and hippocampal coding. The primary objective of this project is to identify putative place cells and explore neuron classification based on spike waveform features. All analyses were conducted independently using standard computational tools and statistical methods.

## Dataset Description

The session analyzed in this project is labeled `ec013.922`, recorded from shank 1 of a high-density tetrode array. The CRCNS hc-3 dataset provides spike time data (`.res`), cluster assignments (`.clu`), waveform feature vectors (`.fet`), and an XML metadata file (`.xml`) describing the recording configuration. Spike times are given in units of samples and were converted to seconds using a sampling rate of 20,000 Hz as specified in the metadata. Each cluster ID corresponds to a putative single neuron obtained through offline spike sorting.

Due to the absence of a `.dat` file, continuous raw waveforms could not be extracted or visualized, which limited direct waveform analysis. Nevertheless, the `.fet` file provided sufficient waveform features for dimensionality reduction and classification.

## Spike Raster and Spatial Firing Analysis

The analysis began with the generation of a spike raster plot to visualize the timing and distribution of spikes across different clusters over the course of the recording. The raster revealed variability in temporal firing density between clusters. Some clusters, such as 6, 8, and 10, showed dense and sustained firing that could suggest high-frequency interneuron activity, while others, including clusters 2, 5, and 7, fired more sparsely and intermittently, characteristic of place cell behavior.

To examine spatial coding, I computed spatial tuning curves for each neuron by dividing the animal’s position into discrete spatial bins and calculating the mean firing rate within each bin. This analysis revealed that certain clusters exhibited strong spatial modulation. For instance, cluster 6 displayed a sharply localized peak in firing rate within a specific region of space, consistent with spatially selective place cells. Other clusters, such as 3, 4, 7, and 9, showed flat or diffuse tuning curves, suggesting they were not spatially tuned. Cluster 10 showed weak but potentially significant spatial preference toward the end of the linearized track.

These findings provide further evidence for the presence of place cells in the dorsal hippocampus and support the established role of this region in spatial memory and navigation.

## Waveform Feature Analysis and Neuron Classification

Although the lack of raw waveform data constrained the analysis to pre-extracted features, I utilized the `.fet` file to perform principal component analysis (PCA) on the spike waveform features. The features were first standardized and then reduced to two principal components for visualization. The PCA scatter plot showed clear cluster separation, confirming that spike sorting successfully isolated distinct neuronal units based on waveform characteristics.

To investigate neuron types, I performed unsupervised classification using k-means clustering with two clusters, aiming to distinguish between putative excitatory and inhibitory neurons. The k-means algorithm separated the PCA-reduced data into two distinct groups. Based on domain knowledge of hippocampal physiology, I interpreted one group as likely corresponding to pyramidal cells and the other to fast-spiking interneurons. Pyramidal neurons typically exhibit broader waveforms and lower firing rates, while interneurons have narrower spikes and higher activity levels.

To further support these findings, I applied UMAP, a nonlinear dimensionality reduction technique, to the same waveform feature space. The UMAP projection retained the separation between neuronal clusters and highlighted fine-grained distinctions that complemented the PCA results.

Finally, I computed the average waveform feature values for each neuron cluster and visualized them across all clusters. These profiles revealed consistent and interpretable differences in spike shape features between clusters, reinforcing the validity of the waveform-based neuron classification.

## Interpretation and Conclusions

Together, the spike raster plots, spatial tuning curves, PCA visualizations, and unsupervised clustering provide a multifaceted view of hippocampal activity during free behavior. The presence of neurons with clear spatial tuning supports their classification as place cells. The waveform-based analysis offers evidence for distinct neuronal types within the CA1 region, separating putative pyramidal neurons from interneurons based on spike shape features, even in the absence of raw waveform traces.

This project highlights the richness of the CRCNS hc-3 dataset for studying spatial coding and neuronal diversity. While the analysis was limited by the lack of a `.dat` file for raw waveform inspection, the results achieved using available metadata and feature vectors provide strong support for canonical hippocampal function.

## Future Directions

This work could be extended by incorporating precise behavioral tracking data to correlate firing activity with specific positions or trajectories in real time. Quantitative place cell classification using spatial information measures or mutual information could further improve accuracy. Additionally, manual curation or supervised classification of spike shapes, ideally using raw waveforms, would provide more definitive identification of neuron types.

## Data Source

The dataset analyzed in this project was obtained from the Collaborative Research in Computational Neuroscience (CRCNS) repository. The specific dataset is hc-3: "Tetrode recordings from the hippocampus of rats during a spatial navigation task." Full access is available at [https://crcns.org/data-sets/hc/hc-3](https://crcns.org/data-sets/hc/hc-3).

