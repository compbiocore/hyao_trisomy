FROM ghcr.io/compbiocore/hyao_trisomy:nov_24_11-09-20_2024

RUN R -e "install.packages(c('nloptr', 'terra', 'ggplot2', 'tidyr', 'dplyr', 'patchwork', 'magrittr','future', 'rsvd', 'stringr','gridExtra', 'data.table', 'xlsx', 'plyr', 'RColorBrewer', 'viridis', 'stringr', 'kable', 'kableExtra'))"
RUN R -e "BiocManager::install(c('BiocGenerics', 'DelayedArray', 'DelayedMatrixStats','limma', 'lme4', 'S4Vectors', 'SingleCellExperiment','SummarizedExperiment', 'batchelor', 'HDF5Array','terra', 'ggrastr', 'GenomeInfoDb', 'Biostrings'), update = TRUE)"
RUN R -e "devtools::install_github('cole-trapnell-lab/monocle3')"
