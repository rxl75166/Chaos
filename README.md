# Chaos

Bash Script to Hunt all the targets/Subdomains from Chaos by Project Discovery who pay bounty, no paying bounty company is filter out.

Actual script is collect from Hacktify and modified by me.

wget "https://chaos-data.projectdiscovery.io/index.json" -O index.json
cat index.json | jq -r '.[] | select(.bounty == true) | .URL' | sed 's/"URL": "//;s/",//' | while read host do;do wget "$host";done && for i in `ls -1 | grep .zip$`; do unzip $i; done && rm *.zip && cat *.txt >> alltargets.txt
