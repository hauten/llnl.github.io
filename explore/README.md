## How to Generate New Data

```bash
cd explore/scripts/
./MASTER.sh
```

_(Additional script functionality detailed in the [`./scripts` section below][jump2 scripts].)_

**IMPORTANT!**  
Data fetching scripts require an environment variable `GITHUB_API_TOKEN` containing a valid GitHub [OAuth token][oauth] or [personal access token][personaltoken].

## About the Contents of this Directory...

#### [./input_lists.json][inputs file]
Simple text files containing input lists. (e.g. list of organizations, list of independent repositories)

#### [./github-data][data dir]
Where all data used for the visualizations, as generated by the data fetching scripts, is stored.  
These data files are intended to be read by [the Explore page's js scripts][js dir] each time it is loaded, and should require little additional manipulation.  
Also included are scripts for viewing JSON data files in a more human-readable format, if necessary.

#### [./queries][queries dir]
The actual queries sent to [GitHub's GraphQL API][gitgraphql] when the data fetching scripts are run. This makes writing/editing queries easier, as it allows them to remain in individual, human-readable text files.

#### [./scripts][scripts dir]
Scripts for data fetching and manipulation. Data is written to [`./github-data`][data dir] in appropriate json formats.

New files are created for each type of data structure.  
For most files, data is overwritten each time the scripts are run.  
Other scripts may collect cumulative data with a daily timestamp. If one of these scripts is run multiple times in a single day, the entry for that day will be overwritten.

Running [`MASTER.sh`][mastersh] will run all of the necessary scripts in the appropriate order to fetch the latest data. It will also update [`LAST_MASTER_UPDATE.txt`][lastmasterup] to record when this complete data update was last run.

The scripts are only for gathering new data. You do not need them to run in order to view the webpage visualizations.

[jump2 scripts]: #scripts
[inputs file]: input_lists.json
[data dir]: github-data
[js dir]: ../js/explore
[queries dir]: queries
[scripts dir]: scripts
[mastersh]: scripts/MASTER.sh
[lastmasterup]: github-data/LAST_MASTER_UPDATE.txt
[gitgraphql]: https://developer.github.com/v4/
[oauth]: https://github.com/settings/developers
[personaltoken]: https://github.com/settings/tokens