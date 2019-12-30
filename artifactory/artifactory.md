
## AQL

### [Relative Time Operators](https://www.jfrog.com/confluence/display/RTF/Artifactory+Query+Language#ArtifactoryQueryLanguage-RelativeTimeOperators)
AQL supports specifying time intervals for queries using relative time. In other words, the time interval for the query will always be relative to the time that the query is run, so you don't have to change or formulate the time period, in some other way, each time the query is run. For example, you may want to run a query over the last day, or for the time period up to two weeks ago.

Relative time is specified using the following two operators:

| operators | paraphrase                                                                  |
| --        | --                                                                          |
| $before   | The query is run over complete period up to specified time.                 |
| $last     | The query is run over period from the specified time until the query is run |

Time periods are specified with a number and one of the following suffixes:

| time period  | suffixes       |
| --           | --             |
| milliseconds | "mills", "ms"  |
| seconds      | "seconds", "s" |
| minutes      | "minutes"      |
| days         | "days", "d"    |
| weeks        | "weeks", "w"   |
| months       | "months", "mo" |
| years        | "years", "y"   |


### find items (folder) some times ago by aql

- e.g. find root folder &&  4 weeks ago

    ```bash
    items.find(
      {
        "repo": "my-repo",
        "type" : "folder" ,
        "depth" : "1",
        "created" : {
          "$before" : "4w"
        }
      }
    )

    $ curl -X POST -uadmin:password https://my.artifactory.com/artifactory/api/search/aql -T find.aql 
    ```

- e.g.: delete all in `my-repo` 4 weeks ago

    ```bash
    username='admin'
    password='password'
    curlOpt= "-u${username}:${password}"
    rtURL='https://my.artifactory.com/artifactory'

    for _i in $(curl -s -X POST ${curlOpt} ${rtURL}/api/search/aql -T find.aql | jq --raw-output .results[].name); do
        echo ${_i}
        curl -X DELETE ${curlOpt} ${rtURL}'/my-repo/'${_i}
    done
    ```
