# An exploratory view of `grep` as the command-line tool

This report aims to extend on course material about `grep` in CSE 15L and provide a comprehensive view of this tool. There're mainly two parts, the first one introduces the file structure that the author is experimenting in, and the second one follows a series of 8 examples that contains four command-line options or alternate ways to use the command, each of which has two examples.

## Part 1 - File Structure / Setting
The files consists of several folders that contains text-as-data as `.txt` files, which includes conference papers and records. Our working directory will be mostly in the `docsearch` project. The project comes with four categories of data in `technical` folder - `911 report`, `biomed`, `government` and `plos`. It is highly possible that not all of the four folders of data will be applied in this report. But at least some of them leave us a good practice on the command tools. Below attached a tree representation of the folder structure: note that the author intentionally ignored some java files and bash files to make the overall structure more clear.

```
- docsearch (working dir)
  - technical
    - 911report
      - .txt files
    - biomed
      - .txt files
    - government
      - 6 sub-categories
        - .txt files
    - plos
      - .txt files
```
