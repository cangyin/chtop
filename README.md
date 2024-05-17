# chtop

A tool for monitoring ClickHouse realtime activities. Pure bash script that only depends on `clickhouse` binary.

- Realtime CPU usage per thread kind (MergeMutate, QueryPipelineEx, etc)
- Running Queries
- Top N of system.parts
- Current merges/mutations
- Current mutation commands

# Install

Download the script [content](https://raw.githubusercontent.com/cangyin/chtop/main/chtop) as `chtop`, and install it as executable

```
curl https://raw.githubusercontent.com/cangyin/chtop/main/chtop -o chtop

install ./chtop /usr/local/bin/

chtop --help
```
The script needs to run in where ClickHouse process lives.

# Usage


```sh
Usage:  chtop  [options]...
    -h | --help)      This help text.
    --port)           ClickHouse client port
    -n | --interval)  Interactive update interval.
    -C | --no-color)  No ANSI color and styles on text.
    -p | --preserve-screen)  Preserve last screen content on exit.
    -f | --format)    ClickHouse output format.
                      Changing formats to other than PrettyCompact* is not recommended.
    -b | --batch)     Batch mode. Zero means infinite loop.
    -E | --echo)      In batch mode, print query before execution.
                      Should be specified after --batch.
    -F | --freeze)    Freeze on first update.
                      Or press 'F' in interactive mode to toggle frozen state.
    -U | --no-cpu)    No threads CPU report.
                      Or press 'U' in interactive mode.
    -Q | --no-processes)  No queries report
                      Or press 'Q' in interactive mode.
    -P | --no-parts)  No parts report
                      Or press 'P' in interactive mode.
    -M | --no-merges)  No merges/mutations report. Mutation commands are still reported.
                      Or press 'M' in interactive mode.
    -T | --without-totals)  Report without totals.
                      Or press 'T' in interactive mode.
    --grouped-processes)  Group by query_kind in queries report.
                      Or press 'GQ' ('G' follwed by 'Q') in interactive mode.
    --grouped-merges)  Group by database,table,kind in merges/mutations report.
                      Or press 'GM' ('G' follwed by 'M') in interactive mode.
    --cpu-non-zero)   Only show threads with non zero CPU usage in threads CPU report.
                      Or press 'CO' ('C' follwed by 'O') in interactive mode.
    --limit-parts)    Limit number of rows in parts report.

   Press 'W' in interactive mode to save the state.

Note: options with no short names should be placed after --, for example:
      chtop -b1  --  --cpu-non-zero --limit-parts 5
```