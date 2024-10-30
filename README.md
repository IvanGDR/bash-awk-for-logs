# bash-awk-for-logs



paths="$(find . -name "cfstats" | sed 's/\.\//\//')"; while IFS= read -r line; do echo "Processing $line";done <<< $paths
