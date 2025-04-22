# Automatically generated documentation for **Azure Data Factory (ADF)** pipelines

1. To generate a documentation page from pipeline code, save json file containing it next to **Jupyter Notebook** and paste its name as a value to the `FILE_WITH_PIPELINE` constant.
2. Run the Notebook.

The code in the Notebook parses the pipeline code, extracts parameters and variables, and puts them into separate tables. Also, it visualizes DAG structure as a **Mermaid** diagram (inner DAGs are visualized separately). At last, all the activities are being specified in a list with proper hierarchy and their description (if it's populated).

The example of a page with documentation is presented in a `result-example.md` file.

The file presents the structure and information which are suitable and important for my personal needs.  
For instance, it doesn't parse the objects which are marked as "not in use", since either I don't populate them or they are not required to specify in my documentation.  
Feel free to adjust the code to make it useful for you.

[Back to README](/README.md)
