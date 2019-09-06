# Qwik PDF
Qwik PDF is a Qlik Sense Server Side Extension which enables table data to be read from a PDF. It is based on tabula-py: https://github.com/chezou/tabula-py

## Pre-Requisites 
1. Python 3.7.2 installed. This could work with other Python versions, however it has only be tested on this version. You can download 3.7.2 from here: https://www.python.org/ftp/python/3.7.2/python-3.7.2-amd64.exe
2. tabula-py is a wrapper of tabula-java, therefore Java 7 or 8 needs to be installed. For Windows please check this guide here if you get any Java related errors: https://github.com/chezou/tabula-py#get-tabula-py-working-windows-10
3. A local version of Tabula will be needed to create templates needed to interpret which data to take from a PDF. You can download Tabula from here https://tabula.technology/

## Installation
1. Clone or download this repository somewhere on your computer
2. Navigate to the qwik-pdf folder within a terminal and execute the following command `pip install -r requirements.txt`
3. Add a new analytic connection to Qlik Sense with the following properties: 
    * Name: PythonPDF
    * Host: localhost (or the host name where you are running this SSE)
    * Port: 50444

## Running The Example
Within this repository there is a sample app Python PDF, sample PDF fs2.pdf abd sample template template.json
1. Start the analytic connection by navigating to the qwik-pdf folder within a terminal and executing the following command `python __main__.py`
2. Restart the Qlik Sense Engine or the Qlik Sense Desktop if you are using the Qlik Sense Desktop
3. Import the app named Python PDF 
4. Open the load script and replace `PATH_TO_PDF` and `PATH_TO_TEMPLATE` with the path to the qwik-pdf folder
5. Reload the App and it should be working

## Using This With Your Own PDFs
**This SSE Works together with Tabula, therefore you will need to take some steps within this tool first before you can load your PDF data into Qlik Sense**
1. Open up Tabula and hit Browse and Select a PDF and then Import
2. Use the wizard to select data from the PDF. Use the preview to ensure you are extracting the correct data. Make note if the extraction method stream or lattice fits your data better.
3. Once you are sure you are extracting the correct data, click on the template button to download the JSON template
4. Within the Qlik Sense App, replace the template entry in the inline table with the path and file name of the template you downloaded in step 3.
5. Within the Qlik Sense App, replace the extraction_method in the inline table with the extraction method which fit your data better in step 2. (Note only stream and lattice can be given as options and all lowercase)