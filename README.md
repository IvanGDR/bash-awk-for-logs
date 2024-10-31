# bash-awk-for-logs


```
paths="$(find . -name "cfstats" | sed 's/\.\//\//')"; while IFS= read -r line; do echo "Processing $line";done <<< $paths
```


```
 paths="$(find . -name "cfstats" | sed 's/\.\//\//')"; while IFS= read -r line; do awk -v l=$line '{print l }';done <<< $paths 
```


```
paths="$(find . -name "cfstats")"; while IFS= read -r line; do awk -v l=$line '{print l $1 }' <$line ;done <<< $paths

```
