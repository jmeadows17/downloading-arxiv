# How to download arXiv in anaconda python3

1. Extract the s3cmd folder to where you have the memory to store 2 million+ papers. 

2. In anaconda prompt, navigate to this folder (contains the "s3cmd" file, "setup.py", "setup.cfg" etc.) 

3. Move the download.py[^1] file from this repository into this folder

4. In anaconda run the command below, and input your AWS access and private keys:
    ```
    python s3cmd --configure
    ``` 

5. Download the arxiv manifest for PDFs:
    ```
    python s3cmd get --requester-pays s3://arxiv/pdf/arXiv_pdf_manifest.xml
    ```
    or the source files (mostly LaTeX):
    ```
    python s3cmd get --requester-pays s3://arxiv/src/arXiv_src_manifest.xml
    ```

6. Download arXiv:
    ```
    python download.py --manifest_file /path/to/src-manifest --mode X
    ```
   where X = src or pdf. 
   

[^1]: download.py file adapted from https://github.com/armancohan/arxiv-tools.
