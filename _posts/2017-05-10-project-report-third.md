---
layout: post
title:  "Project progress report 3.0"
date:   2017-05-10 9:36:12 +0100
categories: wpub projects updates
author: Bernád
---

#### Third publication of version 3.0 for school subject "web publishment". This post contains information for school practice lector. Furthermore, this post contain respond for requirements for upper defined school subject.

* * *

#### I've used these technologies to construct my bachalor project documentation:
1. ##### XML
2. ##### XSL
3. ##### DocBook
4. ##### XSL Processor
5. ##### FO Processor
6. ##### XMLmind XML Editor
7. ##### DTD
8. ##### RELAX NG
9. ##### XMLBlueprint v.13

* * *


#### How does conversion from rare structured formats to pdf works?

<img src="https://static.osdn.net/thumb/g/1/199/800x600_0.png" alt="hobby.title" />


* * *
##### These requirements are required: :point_right: <a href ="https://wiki.fiit.stuba.sk/study/bc/info/wp/2016-17/zadanie3/" target="_blank"> requirements </a> :point_left:
* * *

#### This XML presentation about my bachalor project contains these concrete fulfilled parts of specification:

1. ##### Data type definition ✅:
   1. ###### DTD (done but problem with slide order, 1 error with root element "presentation") ❌
   2. ###### RELAX NG (recursively nice made control schema, succesfully working)
   
2. ##### Creation of XML data structure document containing that has this list(only basic) of different elements ✅:
   1. ###### < presentation > [main root element containg all types of slides]
   2. ###### < first_slide > [contains main title, subtitle, author group and their data, as well as tutor name] ⬅️
   3. ###### < slide_content > [contains all ordered presentation slides headings in one place] ⬅️
   4. ###### < slide_common_point_list > [contains common list of text lines started with points] ⬅️
   5. ###### < slide_common_table_data > [contains whole table with design + some table description] ⬅️
   6. ###### < slide_common_picture_data > [contains centered picture in the middle with its description] ⬅️
   7. ###### < slide_last_references > [this is a list of all presentation references with clickable reference] ⬅️
   8. ###### < line_points > [just group of points containg minimal one point]
   9. ###### < author_group > [it is able to include more than one author]
   10. ###### < author > [contains several data information]
   11. ###### < table > [contains description for table and its rows]
   12. ###### < row > [every row contains head_cell or basic cell]
   13. ###### < picture > [every picture has its own url and description]
   14. ###### < reference_list > [contains at least one, or more references]
   15. ###### < reference > [every reference consist of about information and link]
   16. ###### [other cdata types elements]

    - ⬅️ = types of slides [6x]

3. ##### Parametrization (special "parametrization.xsl" file contains few parameters to set in variables) ✅:
    1. ###### Changing slide numbers - visible or not visible
    2. ###### Changing main title slide heading size (every parameter is explained in comment)

4. ##### All XSL transformations for ✅:
    1. ###### Creation of XHTML files(with own .CSS) from XML with "saxon_controller.xsl" XML stylesheet ✅
    2. ###### Creation of PDF file from XML with "fo_data_to_process.xsl" XML-FO stylesheet ✅
    - every process from both above has available parametrization wih "parametrization.xsl" that is included to .xsls above

5. ##### List of used elements in XSLs:
    1. ###### < xsl:stylesheet />, < xsl:include />, < xsl:template />, < xsl:for-each />, < xsl:variable />, < xsl:result-document />, < xsl:apply-templates >
    2. ###### < xsl:choose />, < xsl:when />, < xsl:otherwise />, < xsl:if />, < xsl:text />, < xsl:value-of />, < xsl:output />,
    3. ###### < fo:root />, < fo:layout-master-set />, < fo:simple-page-maste />, < fo:region-body />, < fo:region-before />, < fo:page-sequence />, < fo:flow />, 
    4. ###### < fo:block />, < fo:leader />, < fo:table />, < fo:table-body />, < fo:table-row />, < fo:table-cell />, < fo:inline />, < fo:list-block />, 
    5. ###### < fo:external-graphic />, < fo:list-item-label />, < fo:list-item-body />, < fo:table-and-caption />

* * *

##### Code examples:

###### Parametrization from file "parametrization.xsl" looks like:
{% highlight ruby %}
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="2.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

        <!-- val = 0 [no slide numbers], val = 1 [slide numbers available] -->
        <xsl:variable name="areSlideNumbers">1</xsl:variable>

        <!-- val = 0 [default heading size], val > 0 [will set that size] -->
        <xsl:variable name="titleHeadingSize">0</xsl:variable>

</xsl:stylesheet>
{% endhighlight %} 

###### Parametrization implementation (setting title size):
{% highlight ruby %}
<xsl:template match="title_first_slide">

    <xsl:choose>
        <xsl:when test="$titleHeadingSize=0">
            <div class="inner_title_first_slide">
                <xsl:value-of select="."/>
            </div>
        </xsl:when>
        <xsl:otherwise>
            <div class="inner_title_first_slide" style="font-size:{$titleHeadingSize}px">
                <xsl:value-of select="."/>
            </div>    
        </xsl:otherwise>
    </xsl:choose>

</xsl:template>
{% endhighlight %}

###### Parametrization implementation 2 (delete or add slide numbers):
{% highlight ruby %}
    <xsl:if test="$areSlideNumbers=1">
        <fo:block text-align="right"  margin-right="10mm"  font-weight="bold" font-size="11pt">
            <xsl:text>Slajd: </xsl:text>         
            <xsl:for-each select="//*[starts-with(name(), 'slide_')]">
                <xsl:if test="title=$titleVar">
                <xsl:value-of select="position()"/>
                </xsl:if> 
            </xsl:for-each>
        </fo:block>
    </xsl:if>
{% endhighlight %} 


* * *

##### Additional important notes:
###### I've done all sections to fulfill all tasks of this project. Most of them are succesfull. Moreover, there are some negatives that could be done better
###### in the future. The negatives are as follows:
######   1. In document type definition I did not have any time left for creating top border of maximum elements that can be added, for example maximal 7 dot lines per slide
######   2. Parametrization could be done through script, but this option, I think, is more convinient.
######   3. My DTD for validation of my XML has one error, but I've made full RELAX NG solution
######   4. I had problems with using XSLT 2.0 functions for actual date that didn't worked, due to this I had to make extra JavaScript file
###### In files that I send to AIS in every folder is a specific file README.txt with explanation of concrete folder area.
###### In all XSLs I am using XSLT 2.0 version. Even if 1.0 should still work with my code.

