
# Table of Contents



Found the following script [here:](https://stackoverflow.com/questions/39584842/using-bash-to-curl-a-website-and-grep-for-keywords)

    #!/bin/bash
    keywords="$(<./keywords.txt)"
    while IFS= read -r url; do
        curl -L -s "$url" | grep -ioF "$keywords"
    	while IFS= read -r keyword; do
    	    echo "$url: $keyword"
    	done
    done < ./url_list.txt

I added the position descriptions I'm interested in to **keywords.txt** file and added the list of remove-friendly companies to **url<sub>list.txt</sub>** file.

Run the script:

    ./url_search.sh | uniq -u

Companies with positive matches will appear. Pick the ones you are interested and check out their websites. Easy peasy lemon squeezy.

