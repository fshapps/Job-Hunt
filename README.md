I need a job.

But not just any job. Ideally a job at a cool company that treats remote workers as first class citizens.

The good news is there are a lot of them out there. The bad news is checking their job pages manually is a real drag.

So I decided to automate it a bit.

My bash scripting skills are super rusty so I decided to see what I could google. I found the following script which looked promising [here:](https://stackoverflow.com/questions/39584842/using-bash-to-curl-a-website-and-grep-for-keywords)

```shell
#!/bin/bash
keywords="$(<./keywords.txt)"
while IFS= read -r url; do
    curl -L -s "$url" | grep -ioF "$keywords"
	while IFS= read -r keyword; do
	    echo "$url: $keyword"
	done
done < ./url_list.txt
```

I added the position descriptions I'm looking for to **keywords.txt** file and added the list of companies I am interested in to **url<sub>list.txt</sub>** file.

Then run the script from the command-line:

```shell
./url_search.sh | uniq -u
```

Companies with positive matches will list in the terminal. Pick the ones you are interested and check out their websites. Easy peasy lemon squeezy.
