FROM ghcr.io/compbiocore/hyao_trisomy:nov_24_10-06-02_2024

RUN R -e "BiocManager::install(c('BiocGenerics', 'DelayedArray', 'DelayedMatrixStats','limma', 'lme4', 'S4Vectors', 'SingleCellExperiment','SummarizedExperiment', 'batchelor', 'HDF5Array','terra', 'ggrastr'))"
RUN R -e "devtools::install_github('cole-trapnell-lab/monocle3')"
