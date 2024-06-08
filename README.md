# exv:  a simple Excel file viewer for the command line

Command line tool for viewing spreadsheets files, including Excel (.xls, .xlsx), Open Office (.ods), and similar.

The modules [openpyxl](https://pypi.org/project/openpyxl/), [xlrd](https://pypi.org/project/xlrd/), and [odsparsator](https://pypi.org/project/odsparsator/) are used for parsing and interpretation of the input files,
and [tabulate](https://pypi.org/project/tabulate/) is used for viewing worksheets in a tabular fashion.

No attempt is made to make use of embedded charts and other non-tabular objects.
In fact, nothing fancy has been dealt with. Formulas are not coming out very well from Open/Libre Office files.

## Usage

The basic usage is `exv <spreadsheet> [<worksheet>]`. If the given spreadsheet file has a single worksheet, then the worksheet is viewed.
A list of worksheet names are given if there is more than one worksheet defined in the file. You can give a format argument
to have the sheet displayed in a special way. 

### Example

```
$ exv single.xlsx
0  n  fib(n)
1  0  0
2  1  1
3  2  1
4  3  2
5  4  3
6  5  5
7  6  8

$ exv -f github single.xlsx
|---|---|--------|
| 0 | n | fib(n) |
| 1 | 0 | 0      |
| 2 | 1 | 1      |
| 3 | 2 | 1      |
| 4 | 3 | 2      |
| 5 | 4 | 3      |
| 6 | 5 | 5      |
| 7 | 6 | 8      |

$ exv three_sheets.xlsx
Available sheets:
fib
harmonic
euclid
$ exv three_sheets.xlsx harmonic
0  n  harmonic(n)
1  1  1
2  2  1.5
3  3  1.8333333333333333
4  4  2.083333333333333
5  5  2.283333333333333
6  6  2.4499999999999997
```

### Options

+ `-h`, `--help` -- Show basic usage.
+ `-nr`, `--no-row-numbers` -- suppress an initial column with row numbers.
+ `-f`, `--format` -- Choose from a large number of output formats. These are formats implemented by [tabulate](https://pypi.org/project/tabulate/), see list below.
+ `--version` -- Show version number.

### Output formats

+ asciidoc
+ double_grid
+ double_outline
+ fancy_grid
+ fancy_outline
+ github
+ grid
+ heavy_grid
+ heavy_outline
+ html
+ jira
+ latex
+ latex_booktabs
+ latex_longtable
+ latex_raw
+ mediawiki
+ mixed_grid
+ mixed_outline
+ moinmoin
+ orgtbl
+ outline
+ pipe
+ plain
+ presto
+ pretty
+ psql
+ rounded_grid
+ rounded_outline
+ rst
+ simple
+ simple_grid
+ simple_outline
+ textile
+ tsv
+ unsafehtml
+ youtrack
