---
#layout: post
title: "Query Charmander Info From Wikipedia using Pokemon's API"
date: 2019-10-21 15:40
author: escrowdis
comments: true
tags: [jq, curl]
---

It's been a long time to be lazy...Try to continue to record what I've learned!

I attended OpenUTD's workshop talking about linux and they demo how to retrieve data using Pokemon's API and use this data to get info from wiki.

Before running it, program jq needs to be downloaded using the code below:
`wget -O jq https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64`

Code is shown below. I learned how to use `jq` to parse data out from bunches of data by using ".name". And if the data is an array, use `.<arr_name>[]`.
After that, use for loop to retrieve info from Wiki.

```
echo "Get Wiki's info of charmander"
nameCharmander=$(curl https://pokeapi.co/api/v2/pokemon/charmander | ./jq ".name")
curl "https://en.wikipedia.org/w/api.php?action=opensearch&search=$nameCharmander&limit=1&format=json"

echo "Get Wiki's info of pokemons"
names=$(curl https://pokeapi.co/api/v2/pokemon/ | ./jq ".results[].name")
echo "result"
echo "${names}"
echo "result - End"

echo "print one by one"
for name in $names; do
  curl "https://en.wikipedia.org/w/api.php?action=opensearch&search=$name&limit=1&format=json"
  echo "$name"
done
echo "print one by one - End"
```
