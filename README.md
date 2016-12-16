# mCGfinder
A novel network regularized matrix decomposition model to detect mutated cancer genes in heterogeneous cancer samples

=======================
Instructions to mCGfinder software (version 1.0.0)

Developer: Jianing Xi <xjn@mail.ustc.edu.cn>
Health Informatics Lab, School of Information Science and Technology,
University of Science and Technology of China


Requirement
------------------------
* 4GB memory
* MATLAB 2013a or later

Network preprocessing
------------------------
The default 
If you want to use the default gene interaction network [iRefIndex 9] (http://irefindex.org), just
ignore this step. Ohterwise, if you want to use a user-defined network, replace the two files below
with the files of the user-defined network:

* `./network/index_genes`
* `./network/edge_list`

The first text file `index_genes` is a table of the connection between the node id and the related 
gene names. The second text file `edge_list` is the edges table that assigns the source nodes to 
the target nodes.


Run mCGfinder
------------------------
If you want to analyze the demo data (TCGA BRCA somatic mutation data) through mCGfinder on with
the default configures, please run `./demo_mCGfinder.m` and then the result file will be saved
in the directory `./output/` as `./output/Result.mat`.

If you want to analyze a user-specific data, the mutation binary matrix (samples x genes), the sample
names and the gene symbols of the samples must be provided. Save the three variables as 'mutation_mat',
'sample_id' and 'gene_id_symbol'  as the demo data file in the `./data` directory . Then update the 
string variable 'dir_data' in file `./demo_mCGfinder.m` with the directory of the new data file.

The configurations of mCGfindercan be changed in script file `./demo_mCGfinder.m`, and the discriptions
of these parameters are provided below:

        ========================================================================================
        | PARAMETER NAME          | DESCRIPTION                                                |
        ========================================================================================
        |CompLeastProportion      |Least sample proportion included in each components. The    |
        |                         |default proportion is set to 15%.                           |
        ----------------------------------------------------------------------------------------
        |maxCompoent              |Maximum number of components. The default number is 5.      |
        ----------------------------------------------------------------------------------------
        |NetConf.lambda_T         |Tuning parameter . The default number is 5.                 |
        ----------------------------------------------------------------------------------------

Example data files
------------------------
In the `./data` directory, we provide example data files `./data/somatic_data_BRCA.mat` of somatic 
mutations in breast invasive carcinoma (BRCA) samples, bladder urothelial carcinoma (BLCA), glioblastoma
multiforme (GBM), head and neck squamous cell carcinoma (HNSC) from [UCSC Cancer Genomics Browser]
(https://genome-cancer.soe.ucsc.edu/proj/site/hgHeatmap/).


Contact
------------------------
Please feel free to contact us if you need any help: <xjn@mail.ustc.edu.cn>.