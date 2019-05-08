---
layout: post
title:  "Web scraping on Game Of Thrones"
date:   2019-04-20
excerpt: "Web Scraping"
tag:
- sample post
- post
- images
- feature
feature: ../imgs/beautiful_soup.jpg
comments: true
---

<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Motivation</span>

<span style="color:black; font-family: Tahoma;font-size:1.1em;">
The season 8 of the Game Of Thrones is the topic of discussion these days. While discussing on the lunch table a friend gave me a challenge to list all the episodes of GOT for $1000. I am a GOT fan but failed to recite all the episode names. When I came back to my room I decided the check all the episode names. Again with Data Science tool box in hand I thought of doing something fancy. She had asked me the episode names, I scraped: <br> </span>
<span style="color:black; font-family: Tahoma;font-size:1.1em;">1. Episode names for all 8 seasons.</span> <br>
<span style="color:black; font-family: Tahoma;font-size:1.1em;">2. Number of viewers for each episode.</span> <br>
<span style="color:black; font-family: Tahoma;font-size:1.1em;">3. Duration of each episode </span>
<br>

<br>

<span style="color:black; font-family: Tahoma;font-size:1.1em;">Extracting season, episode name, Number of US viewers and the URL of wikipedia page for each episode.</span>

```python
got_request=requests.get('https://en.wikipedia.org/wiki/List_of_Game_of_Thrones_episodes')
got=BeautifulSoup(got_request.text)

got_tables = got.find_all("table")

seasons=[]
titles=[]
viewers=[]
url=[]
url_start="https://en.wikipedia.org"

for i in range(8):
    table_num=i+1

    table=got_tables[table_num].find_all('tr',{'class':'vevent'})

    for m in range(len(table)):
        if table[m].find_all('td')[1].text !='TBA':
            seasons.append(i+1)
            titles.append(table[m].find_all('td')[1].text)
            viewers.append(table[m].find_all('td')[5].text.split('[')[0])
            url.append(url_start+table[m].find_all('a', {'href':True})[0]['href'])
        else:
            pass

GameOfThrones=pd.DataFrame({'Seasons':seasons,'Title':titles,'Viewers (Millions)':viewers, 'url':url})


```



<span style="color:black; font-family: Tahoma;font-size:1.1em;">Follow the URL of each episode wikipedia page and extracting the running time for each episode.</span>

```python
duration_list=[]

for url_link in GameOfThrones.url:
    duration=requests.get(url_link)
    duration_got=BeautifulSoup(duration.text)
    duration_list.append(duration_got.find_all('table',{'class':'infobox vevent'})[0].find('th', text='Running time').next_sibling.text.split('[')[0])

GameOfThrones['Duration']=duration_list


```

The DataFrame looks like this :

![](../imgs/GOTR_dataframe.PNG)

<span style="color:black; font-family: Tahoma;font-size:1.1em;">This is just sample, actual DataFrame contains the details for all the episodes till date.</span>

<p align="center">
  <img src="../imgs/Game_of_Thrones_title_card.jpg">
</p>

<span style="color:black; font-family: Tahoma;font-size:1.1em;">The code is available on my GitHub repository: [GitHub Repository](https://github.com/Birinder1469/web_scraping_GOT)</span>
<br>
<span style="color:blue;  font-family: Helvetica;font-size:1.5em;">Reference</span>

1. [Game of Thrones Wikipedia](https://en.wikipedia.org/wiki/Game_of_Thrones) <br>
2. [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

<br>
