# bash-awk-for-logs


```
paths="$(find . -name "cfstats" | sed 's/\.\//\//')"; while IFS= read -r line; do echo "Processing $line";done <<< $paths
```


```
 paths="$(find . -name "cfstats" | sed 's/\.\//\//')"; while IFS= read -r line; do awk -v l=$line '{print l }';done <<< $paths 
```


```
paths="$(find . -name "cfstats")"; while IFS= read -r line; do awk -v l=$line '{print l,$1 }' <$line ;done <<< $paths

```


Note to get only keyspace name and table name

```
nodetool cfstats | awk '/Keyspace/ {keyspace=$3} /Table: / {print keyspace "." $2}'
```



```
paths="$(find . -name "cfstats")"; while IFS= read -r line; do awk -v l=$line '/Keyspace/ {keyspace=$3} /Table: / {table=$2} /Space used \(total\):/ {print l "     " keyspace "." table, $4 " Space Used Total bytes" }' <$line ;done <<< $paths

```


```
 paths="$(find . -name "cfstats")"; while IFS= read -r line; do awk -v l=$line '/Keyspace/ {keyspace=$3} /Table: / {table=$2} /Space used \(total\):/ {split(l,a,"\/"); print a[4] "     " keyspace "." table, $4 " Space Used Total bytes" }' <$line ;done <<< $paths
```
