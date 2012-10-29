README for dptscan (0.7.1)
==========================
Introduction
------------
*dptscan* implements the iDPT method(1,2), which integrates signal Deconvolution, whole genome Pattern recognition and scan, and differential Testing into a consolidated pipeline, to address the group-wise comparison of genome-wide, enrichment-based profiles generated by massively parallel sequencing.
*dptscan* project website: [http://idpt.github.com/dptscan/](http://idpt.github.com/dptscan/)

Requirement
-----------
- Linux servers (recommend multicore servers with > 128G memory)
- R 2.14 or greater with `RScript` installed. R packages required:`MCMCpack, snowfall, nlme, gmodels, MASS, plyr, preprocessCore, inline, Rcpp, IRanges, Biostrings, mmap, getopt, multicore, qvalue`.

Install
------------
- Follow [the Data preparation and Profile binning steps](https://github.com/iDPT/dptscan/wiki).
- Create a project folder. Copy the binned profile data to the data input subfolder, `InputData` (default).
- Download [the dptscan zipball](https://github.com/iDPT/dptscan/zipball/master) and unzip the files into the project folder. Make `dptscan` executable with `chmod +x dptscan`.
- Modify `samplesheet.text` and `experiment-config.r` files. 
- Initialize the workspace with  

>    dptscan -s

- Start analysis. (see Usuage)

Usage
-----
>   dptscan [options]  

Example:  
>   dptscan --batch=1,1,5,5,5 --core=1,10,4,4,4

Options:

<table>
  <tr>
    <td width="33%"><code>--verbose</code></td>
     <td>Show more onscreen information.<br></td>
  </tr>
  <tr>
    <td><code>-s</code></td>
    <td>Setup dptscan workspace.</td>
  </tr>
  <tr>
    <td><code>--task=TASK</code></td>
    <td>Select one or more modules from <code>"preprocess", "mixPoi", "pattRecog", "diffTest", "report"</code>.
      DEFAULT: <code>"preprocess, mixPoi,  pattRecog,  diffTest, report"</code>, which applies the complete dpscan process with all the modules in a proper order.</td>
  </tr>
  <tr>
    <td><code>--chr=CHR</code></td>
    <td>Select one or a set of chromosomes to run. <br>
      DEFAULT:<code>1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,X,Y,M</code>, which processes on all the chromosomes.</td>
  </tr>
  <tr>
    <td><code>--core=CORE</code></td>
    <td>Number of computer cores used in parallel for each batch.</td>
  </tr>
  <tr>
    <td><code>--batch=BATCH</code></td>
    <td>Number of batch tasks in parallel.</td>
  </tr>
  <tr>
    <td><code>--samplesheet=file</code></td>
    <td>Sample sheet file. DEFAULT: <code>"samplesheet.txt"</code>.</td>
  </tr>
  <tr>
    <td><code>--config=CONFIG</code></td>
    <td>Configuration file for running parameters.DEFAULT: <code>"experiment-config.r"</code>.</td>
  </tr>
  <tr>
    <td><code>--output=PATH</code></td>
    <td>Path to output result files. DEFAULT: <code>"./"</code>, current location.</td>
  </tr>
  <tr>
    <td><code>--analysis=methyl</code></td>
    <td>Analysis category. DEFAULT: <code>methyl</code>, DNA methylation analysis.</td>
  </tr>

</table>  


Reference
----------  
1. Xu Y, Hu B, Choi AJ, Gopalan B, Lee BH, Kalady MF, Church JM, and Ting AH. Unique DNA methylome profiles in CpG island methylator phenotype colon cancers. Genome Res 2012, Feb;22(2):283-91.
2. Ting AH, Hu B, Zhang L, Na J, Lee BH, and Xu Y. iDPT: an integrative approach for *de novo* identification of differentially enriched events in multi-sample sequencing studies (submitted).

