---
layout: post
title:  "Project progress report 2.0"
date:   2017-03-24 9:36:12 +0100
categories: wpub projects updates
author: Bernád
---

#### Second publication of version 2.0 for school subject "web publishment". This post contains information for school practice lector. Furthermore, this post contain respond for requirements for upper defined school subject.

* * *

#### I've used these technologies to construct my bachalor project documentation:
1. ##### XML
2. ##### XSL
3. ##### DocBook
4. ##### XSL Processor
5. ##### FO Processor
6. ##### XMLmind XML Editor

* * *


#### How does conversion from rare structured formats to pdf works?

<img src="https://static.osdn.net/thumb/g/1/199/800x600_0.png" alt="hobby.title" />


* * *
##### These requirements are required: :point_right: <a href ="https://wiki.fiit.stuba.sk/study/bc/info/wp/2016-17/zadanie2/" target="_blank"> requirements </a> :point_left:
* * *

#### Project bachalor documentation contains these concrete fulfilled parts of specification:

1. ##### Standard breakdown of the text on the section, subsection:
   1. ###### Main section: 1.Úvod
   2. ###### Main section: 2.Gamifikácia
   3. ###### Sub section: 2.1 Definícia gamifikácie
   4. ###### Sub section: 2.2. Pôvod a vývoj gamifikácie
   5. ###### Sub section: 2.3. Princípy a nástroje gamifikácie
   6. ###### Sub section: 2.4. Využitie gamifikácie
   7. ###### Sub Sub section: 2.4.1 Využitie gamifikácie v rôznych oblastiach
   8. ###### Sub Sub section: 2.4.2. Využitie gamifikácie v knižniciach
   
2. ##### Appendix
   1. ###### Používateľská príručka

3. ##### Generated content:
    1. ###### at the beggining of a document (in xsl it is generate.toc reference)

4. ##### Highlighted words:
    1. ###### More than five

5. ##### Text segmentation with numbered content:
    1. ###### on page n.11
    2. ###### on page n.13
    3. ###### on page n.21

6. ##### Links to other parts of its own document or URL links:
    1. ###### p.22 x-reference link to table "Percentuálny podiel využitia IT technológií v knižniciach v závislosti od času"
    2. ###### p.22 x-reference link to list "Zoznam elementov gamifikácie"
    3. ###### p.12 h-reference link to GoogleTrends site referenced with word "príklady"

7. ##### Footnotes:
    1. ###### on page n.12 (fn1,fn2)
    2. ###### on page n.13 (fn3)
    3. ###### on page n.14 (fn4,fn5) 
    4. ###### on page n.15 (fn6) 
    5. ###### on page n.19 (fn7) 
    6. ###### on page n.20 (fn8,fn9,fn10,fn11,fn12) 
    7. ###### on page n.21 (fn13,fn14) 
    8. ###### on page n.22 (fn15) 

8. ##### List of used literature (references/bibliography p.24):
    1. ###### link [1] on page n.9
    2. ###### link [2] on page n.9
    3. ###### link [3] on page n.9
    4. ###### link [4] on page n.11
    5. ###### link [5] on page n.11

9. ##### Used imported pictures:
    1. ###### on page n.12
    2. ###### on page n.14
    3. ###### on page n.17
    4. ###### on page n.17
    5. ###### on page n.18
    6. ###### on page n.22

10. ##### Used tables:
    1. ###### on page n.20

11. ##### Generating tables and pictures in list on the document start:
    1. ###### Editing thesis.xsl file with figure and content

12. ##### Register/Index - on the last page:
    1. ###### There are 12 different pairs of indexes with references to parts of document or keyword with hierarchical level division

* * *

##### Code examples:

###### Highliting words implementation:
{% highlight ruby %}<emphasis role="strong">bold_text</emphasis>{% endhighlight %}

###### Editin thesis.xls:
{% highlight ruby %}
<xsl:param name="generate.toc">
    book title,toc,figure,table
</xsl:param>
{% endhighlight %} 

###### Using literallayouts:
{% highlight ruby %}
      <literallayout>
<emphasis role="strong">GAMIFIKÁCIA V KNIŽNICIACH</emphasis>
Študijný program: Informatika
Autor: Marek Bernád
Vedúca bakalárskej práce: Ing. Nadežda Andrejčíková, PhD.
marec 2017
      </literallayout>
{% endhighlight %} 

###### Workaround with xsl (setting space after and role):
{% highlight ruby %}
<fo:block xmlns:fo="http://www.w3.org/1999/XSL/Format" space-before="6pt" space-after="170pt" text-align="center" font-size="14pt" font-family="sans-serif">
      <xsl:value-of select="/book/bookinfo//affiliation/orgdiv[@role='ustav']"/>
</fo:block>
{% endhighlight %} 

###### Important parts for generating index at the end:
{% highlight ruby %}
<envar>čitateľ</envar>
<indexterm type="reader">
    <primary>Čitateľ</primary>
    <secondary>používateľ</secondary>
</indexterm>
{% endhighlight %} 

* * *

##### Additional important notes:
###### I have together 25 pages and max-required are 15, but I have 8 pages at the start of document that are not counting to whole required contain, and 3 at the
###### end of document like bibliography, index or appendix. I used only 5 reference links in bibliography as good example, because I have very detailed bibliography
###### structure and in document I have more than 30 different bibliography links, therefore I decided to use only 5 references.

