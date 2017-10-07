---
layout: post
title: 'Wikipedia Search Engine'
---

I created an offline search engine for Wikipedia utilizing Google's PageRank algorithm in Java. Accepting an XML dump of all of Wikipedia's articles, the search engine created a weighted graph representation of all the articles and their inter-references, and used PageRank centrality calculations to assign a weighting to each article based on its importance. The search engine was then able to search through all articles, calculating the number of occurences of search terms in the article metadata and returning a ranked list of relevant articles. The project had the additional functionality of being able to solve the "Wikipedia Game": an activity where people try to traverse between two Wikipedia pages by clicking on internal links. Utilizing the PageRank algorithm to assist its graph traversal, my project could calculate the most efficient/likely sequence of articles linking any two arbitrary articles to each other.

{% include image.html url="http://www.gratisography.com" image="projects/proj-4/thumb.jpg" %}
