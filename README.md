# Extract Statistics from cutadapt logs

The `cutadapt-stats` script allows basic statistics to be extracted from a set of [cutadapt](http://cutadapt.readthedocs.io/en/stable/) log files.

## Usage

~~~
usage: cutadapt-stats [-h] [-v] [-n | -c] <filename> [<filename> ...]

Summarize cutadapt log files

positional arguments:
  <filename>       cutadapt log file(s) to process

optional arguments:
  -h, --help       show this help message and exit
  -v, --version    show program's version number and exit
  -n, --no-header  suppress column headers
  -c, --csv        output data as CSV (ignores -n)
~~~

## Output

For each log file specified, either a single entry (if it was a single read) or two
entries (if it was a pair) are returned. The output columns are:

column | description
:----- | :----------
id | The log file ID
file | The log file
type | The type (`single`, `pair_1`, or `pair_2` depending on the file type)
r\_total | Total reads processed
b\_total | Total bases processed
r\_out | Total reads passing filter
b\_out | Total bases passing filter
r\_adapt | Number of reads with adapter contamination
r\_rm\_long | Reads rejected as too long (flag `-M`)
r\_rm\_short | Reads rejected as too short (flag `-m`)
r\_rm\_other | Reads rejected for any other reason
b\_rm\_adapt | Bases trimmed as adapter
b\_rm\_qual | Bases trimmed as low quality (flag `-q`)
b\_rm\_other | Reads trimmed for any other reason

