---
id: litvis
follows: data.md   
permalink: /
layout: default
---

@import "../../css/datavis.less"

# Data Visualization Project Summary


{(questions|}

- Did the lockdown help put in place help "flatten the curve" in the UK?
- Were there better methods of approach in comparision to a lockdown in slowing down/stopping Covid-19?
- Was the lockdown in the Uk as effective as the ones put in place in other countries around the world?
- What would the most likely sceanrio have been if there was no methods of control established?

{|questions)}

{(visualization|}
**Figure 1**

```elm {l=hidden}
goldenRatio : Float
goldenRatio =
    1.618


ukData : Data
ukData =
    (dataFromColumns []
        << dataColumn "dateRep UK" (strColumn "dateRep UK" unitedKingdomTable |> strs)
        << dataColumn "Measures UK" (strColumn "Measures UK" unitedKingdomTable |> strs)
        << dataColumn "cases UK" (numColumn "cases UK" unitedKingdomTable |> nums)
        << dataColumn "sweden Cases Change" (numColumn "sweden Cases Change" unitedKingdomTable |> nums)
        << dataColumn "Projected Population" (numColumn "Projected Population" unitedKingdomTable |> nums)
        << dataColumn "sweden cases" (numColumn "sweden cases" unitedKingdomTable |> nums)
    )
        []
    
worldData : Data
worldData =
    (dataFromColumns []
        << dataColumn "dateRep" (strColumn "dateRep" allTenTable |> strs)
        << dataColumn "Measures" (strColumn "Measures" allTenTable |> strs)
        << dataColumn "cases" (numColumn "cases" allTenTable |> nums)
        << dataColumn "countriesAndTerritories" (strColumn "countriesAndTerritories" allTenTable |> strs)
        << dataColumn "LoggedValue" (numColumn "LoggedValue" allTenTable |> nums)
    )
        []


```

```elm {interactive v}

ukChart : Spec
ukChart =
    let
        ps =
            params
                << param "mySelection"
                    [ paSelect seInterval [ seEncodings [ chX ] ]
                    , paBindScales
                    ]

        cfg =
            configure
                << configuration (coView [ vicoStroke Nothing ])
                << configuration (coAxis [ axcoTicks False, axcoDomain False ])
       
        enc =
            encoding
                << position X [ pName "dateRep UK"
                , pTemporal
                , pAxis
                        [ axTitle "Date"
                        , axGrid True
                        ]
                    ]   
                << position Y
                    [ pName "cases UK"
                    , pQuant
                    , pAxis
                        [ axTitle "Cases"
                        , axGrid True
                        ]
                    ]   
                << tooltips
                    [ [ tName "dateRep UK", tTitle "Date", tTemporal ]
                    , [ tName "cases UK", tTitle "Cases" ]

                    , [ tName "Measures UK", tTitle "Measures" ]
                    ]
                << color[ mName "Measures UK", mScale ldColours ]
            
        ldColours =
            categoricalDomainMap [ ( "Lockdown", "rgb(199, 36, 60)" ), ( "Social Distancing and Wearing Masks Enforced", "rgb(44, 56, 191)" ) ]

    in
    toVegaLite
        [ width 850
        , height (800 / goldenRatio)
        , enc []
        , ukData
        , cfg []
        , ps []
        , bar [ maTooltip ttEncoding ]
        , title "UK Covid Data" []
        ]
```

![image caption](Msc\Figure 1 plan.png)
This is how I would improve the graph above. I am not sure how to add multiple lines of best fits based on date variable. This would allow trands based on events to be seen more easily. 

**Figure 2**

```elm {interactive v}

worldChart : Spec
worldChart =
    let
        ps =
            params
                << param "mySelection" [ paSelect seInterval [], paBindScales ]

        cfg =
            configure
                << configuration (coView [ vicoStroke Nothing ])
                << configuration (coAxis [ axcoTicks False, axcoDomain False, axcoLabelAngle 0 ])
       
        enc =
            encoding
                << position X [ pName "dateRep" 
                                , pAxis
                                    [ axTitle ""
                                    ,axLabels False
                                    ]
                ]
                << position Y
                    [ pName "LoggedValue"
                    , pQuant
                    , pStack stCenter
                    , pAxis []
                    ]
                << detail [ dName "countriesAndTerritories" ]
                << color [ mName "countriesAndTerritories", mScale [ scScheme "category10" [] ] ]
                << tooltips
                    [ [ tName "dateRep", tTitle "Date", tTemporal ]
                    , [ tName "cases", tTitle "cases" ]
                    , [ tName "Measures", tTitle "Measures" ]
                    , [ tName "countriesAndTerritories", tTitle "countriesAndTerritories" ]
                    ]

    in
    toVegaLite
        [ width 900
        , height (800 / goldenRatio)
        , enc []
        , worldData
        , cfg []
        , ps []

        , title "World Covid Data" []
        , area
            [ maLine (lmMarker []) 
            , maInterpolate miMonotone 
            ]
        ]
```

**Figure 3**

```elm {interactive v}

comparison : Spec
comparison =
    let
        cfg =
            configure
                << configuration (coView [ vicoStroke Nothing ])
                << configuration (coAxis [ axcoTicks False, axcoDomain False ])
        
        ps =
            params
                << param "userSelection"
                    [ paSelect seInterval [ seEncodings [ chX ] ]
                    , paBindScales
                    ]

        
        encDate =
            encoding
                << position X [ pName "dateRep UK"
                , pTemporal
                , pAxis
                        [ axTitle "Date"
                        , axGrid True
                        , axTitle ""
                        , axTitleColor "white"
                        , axLabelColor "white"
                        ]
                ]                
        
        encBar =
            encoding   
                << position Y
                    [ pName "cases UK"
                    , pQuant
                    , pAxis
                        [ axTitle ""
                        , axGrid True
                        ]
                    ]   
                << tooltips
                    [ [ tName "dateRep UK", tTitle "Date", tTemporal ]
                    , [ tName "cases UK", tTitle "Cases" ]
                    , [ tName "Measures UK", tTitle "Measures" ]
                    ]
                << color[ mName "Measures UK", mScale ldColours ]         
        
        specBar =
            asSpec [ encBar [], bar [] ]
        
        encLine =
            encoding
                << position Y
                    [ pName "Projected Population"
                    , pQuant
                    , pAxis
                        [ axTitle "Projected Cases"
                        , axTitleColor "white"
                        , axLabelColor "white"
                        ]
                    ]
                
                << tooltips
                    [ [ tName "sweden cases", tTitle "Sweden New Cases", tQuant]
                    , [ tName "sweden Cases Change", tTitle "Daily change in Sweden" ]
                    ]
        specLine =
            asSpec
                [ encLine []
                , line
                    [ maStroke "yellow"
                    , maStrokeWidth 0.8
                    , maPoint (pmMarker [ maFill "yellow", maStrokeWidth 0.5 ])
                    ]
                ]

        ldColours =
            categoricalDomainMap [ ( "Lockdown", "rgb(199, 36, 60)" ), ( "Social Distancing and Wearing Masks Enforced", "rgb(44, 56, 191)" ) ]


    in
    toVegaLite
        [ width 850
        , height (800 / goldenRatio)
        , encDate []
        , ukData
        , cfg []
        , ps []
        , layer [ specBar, specLine ]
        , bar [ maTooltip ttEncoding ]
        , background "rgb(169,169,169)"
        , title "Potential Projection Without Lockdown" [ tiColor "white" ]
        ]
```

{|visualization)}

{(insights|}

1. Figure 1 can be used to answer question 1. From initial inspection we can see there is a drop in new cases in about 2-3 weeks [1] after a lockdown is established. The bar heights follow a slump after they turn, red - signifying the country is a lockdown state. The data does not to go beyond December 2020, nevertheless, we can see the second lockdown seems to follow a similar trend to the first one. From all this one could conclude, that the lockdown did help "flatten the curve" evidently shown by the graph, but thinking very critically new cases may have gone down as people were getting tested less and even if they did show symptoms they were no longer reported as they did not have a reason to. Based on purely on the data visualisation, the question can be answered in favour of the lockdown, but considering other factors it cannot be concluded with high certainty (which will be a running theme throughout the insights).
2. Figure 2 can be used to answer questions 2 and question 3. I tried to take a high-data ink approach to this as most of the inferences can be made by the width of the streams alone. Some countries were able to use mathematical modelling, a variation of track and trace and early education instead of establishing a lockdown. We can see countries that never implemented lockdown measures such as South Korea, Loas and New Zealand performed far better with great consistency. The mentioned countries had narrower widths with little fluctuation suggesting, far fewer new cases arising every day and the number of cases were consistently low. This strongly indicates, a lockdown was not necessarily required in order to mitigate the impacts of the pandemic. Orignially, the range of the data was very large as countries like New Zealand were consistently getting 0 new cases everyday whereas the USA population could get as many as 20000 new cases per day. This led to a very bad data-vis see "Msc\Bad Datavis.png" graphs. Based on prior understanding I used logarithm transformations to significantly decrease the range to make the graphs more fit their function. Although this makes it easier to read, it can be very misleading to those who are not as well versed in effects of performing these types of calculations. The base was 5, so for every unit of measure in reality it would be 5 powers that amount. Based on this information, even though, on initial inspection most of the countries had similar widths with the UK reaping very average rewards, countries like Belgium and Germany had far more success with their lockdowns than the UK as there were very tiny discrepancies in the numbers/ width. Based purely on the data visualisation, the UK should have used other methods of prevention as they performed far better and the lockdown UK imposed was not as successful as other countries. But, to conclude on that would be omission of many other factors such as Geography, culture, general population's attitude towards the Government and malpractice - there have been many reports [2] on how different countries classify covid cases, deaths and infection rates.
3. Figure 3 can be used to answer question 4. This was a particular difficult question to approach both in terms of Data-vis and calculations that would be needed to be performed. A lot of assumptions was required to be made and again a concrete conclusion cannot be made based on the Data-vis alone. Sweden was chosen as it has very similar HDI, climate, GDP per capita and numerous other factors. Sweden did not impose any lockdown during the year of 2020 in favour of trying to achieve Herd Immunity. This makes it the most ideal case study available. The day-to-day change in Sweden’s cases of the virus was added to the UK day to day case to see if it would be higher or lower. Based on inspection of the graphs, most days the UK would have theoretically done better had they adopted the ideology of the Swedish government as the yellow line dips below the bars. Based on Data-vis alone, the UK would have fared better if no method of control was established. However, this is a very shaky conclusion due to the numerous assumptions made and also it does not account ethics and morals of purposely letting thousands die in the hope of herd immunity.

{|insights)}

{(designJustification|}

1. **Colour** I want my data-vis to be looked by all effected by the pandemic, essentially almost all parts of the population. This meant I had to keep colour-blindness and compromised sight among a large part of the population in mind. I ensured I avoided using common colour blindness combination colours [3] such as Red-Green and if I had to use them, I would ensure their were either spaced out - Figure 2 or clearly distinguishable - dots and infobox on Figure 3.
As stated by Robert Simmon, colour selection in data visualization is not merely an aesthetic choice, it is a crucial tool to convey quantitative information [4]. Based on this ideology I used contrasting colours to show the change between state of Lockdown and state of just social distancing. This helps people easily, even those who may not have the best vision to distinguish the dates at which the lockdown starts to be better able to see trends.
For Figure 2, I used "catagory10" colour scheme for the countries. The scheme is comprised mostly of primary and secondary colours, meaning they are all either contrasting or complimentary colours making it very easy to distinguish between each stream as the eyes are easily able to tell the colours apart. This removes any possible ambiguity had the colours been too similar to each other when trying to read for trends.  
For figure 3, I used the primary colours, again to make it easy to distinguish between the different forms of visualised data. However, I was concerned the yellow not stand out as clearly against the white background so to make it more visible I changed the background to a shade of grey. This increased the contrast between the yellow and the background as it went from two bright colours to one bright colour and one dull colour making the yellow stand out more.
2. **Interactions** Interactions in data-vis can provide numerous benefits one of them being faster processing of information and make data easier to understand.[5] I definitely wanted to use the pan and zoom interaction and it allows users to remove data muddiness epically as the graphs I created shows a lot of information. By panning and zooming it allows users who are long sighted users to see graphs more clearly. Furthermore, trying to hover over the right part of the graph becomes more easier when trying to see the infotool box as the bar/line/stream is larger making the graphs more user friendly and as discussed before, even after trying my best to accommodate for the large range using logarithm function there are still some data being shadowed by larger pieces of data. By zooming and panning this "hidden" data can be discovered or become clearer to read.
I contemplated for a long time whether the select/section fill/highlight interaction would be beneficial. I concluded that it would not be very beneficial as even though it may allow the highlighted information to be seen more clearly, most of my questions are answered by looking at the whole graph trend rather than bits of the graphs. Furthermore, (either I am not literate to it or it does not exist) this interaction feature does not seem to do anything in terms of manipulating values or creating new values based on what is highlighted. This limitation made me chose against using this feature.
3. **Layout**When deciding how the layout needed to be arranged, I thought about the different approach to data-vis. As I wanted to appeal to all parts of society, I had two approaches to my graphs either: show as much information as possible is the user can come to their own conclusion based on the most complete display of data as possible, or make it as abstract as possible with high-data ink to ensure most of the complicated information is taken out to make the graph easy to understand to patterns more recognisable.
For figure two, as discussed in the insight section I wanted to have high abstraction and high data ink - almost a Tufte approach. Looking at the raw data, there was over 3000 pieces of data, trying to make that digestible for normal users would have been almost impossible to I made it easier to understand by performing the relevant calculations and displaying it in a large graph with colour and interaction in mind. Streamline graphs are also one of the most graphical heavy graphs. This makes it more easier for people who do not quite have a good understanding of reading graphs to understand a large part of the information it is trying to convey matching with agenda.
With the other two graphs, although they both still showed a lot of data, it was more manageable so I took the other approach and layered on as many pieces of information as required. Figure three in particular has the most amount of varied information, with multiple infotool boxes. Although, I could not program it, I would have wanted there to be multiple lines of best fit on Figure 1 to show the changing trends based on each event that occurred. Normal, bar charts was the best to do all this on due to their easy recognisability and versatility as line graphs and scatter graphs could easily be put on top.

{|designJustification)}

{(references|}

**Reference for data:**
"COVID-19 Coronavirus Data - COVID-19 Cases Worldwide - European Union Open Data Portal". Data.Europa.Eu, 2020, https://data.europa.eu/euodp/en/data/dataset/covid-19-coronavirus-data/resource/55e8f966-d5c8-438e-85bc-c7a5a26f4863.
Steed, Les, and Niamh Cavanagh. "When Did Lockdown Start In The UK?". The Sun, 2020, https://www.thesun.co.uk/news/11304061/uk-coronavirus-lockdown-month-lasted-start-end/.
"Covid-19: PM Announces Four-Week England Lockdown". BBC News, 2020, https://www.bbc.co.uk/news/uk-54763956.
 World Encyclopedia. 2nd ed., INSIGHT GUIDES, 2008.
"WDI - Home". Datatopics.Worldbank.Org, 2020, https://datatopics.worldbank.org/world-development-indicators/.
affairs, European, and Orderly restrictions. "Orderly Andorra Has An Unusual System For Easing Lockdown Restrictions". Euronews, 2020, https://www.euronews.com/2020/04/21/orderly-andorra-has-an-unusual-system-for-easing-lockdown-restrictions.
"Europe Versus Coronavirus – Belgium: Successful Crisis Management Despite Political Fragility". Institut Montaigne, 2020, https://www.institutmontaigne.org/en/blog/europe-versus-coronavirus-belgium-successful-crisis-management-despite-political-fragility.
"湖北继续延迟复工开学：企业不早于2月20日24时前复工". Baijiahao.Baidu.Com, 2020, http://baijiahao.baidu.com/s?id=1658402162460563869.
"湖北：除疫情防控必需外各类企业不早于3月10日复工-新华网". Xinhuanet.Com, 2020, http://www.xinhuanet.com/2020-02/20/c_1125603476.htm.
"湖北荆州：17日起小区有序解封". Yicai.Com, 2020, https://www.yicai.com/news/100550418.html.
Reuters. "China Scrambles To Curb Rise In Imported Coronavirus Cases, Wuhan Eases Lockdown". India Today, 2020, https://www.indiatoday.in/world/story/china-scrambles-to-curb-rise-in-imported-coronavirus-cases-wuhan-eases-lockdown-1658550-2020-03-23.
"China To Lift Travel Restrictions In Hubei After Months Of Coronavirus Lockdown". The Guardian, 2020, https://www.theguardian.com/world/2020/mar/24/china-to-lift-travel-restrictions-in-hubei-after-months-of-coronavirus-lockdown.
"Bloomberg - Are You A Robot?". Bloomberg.Com, 2020, https://www.bloomberg.com/news/articles/2020-03-24/china-to-lift-lockdown-over-virus-epicenter-wuhan-on-april-8. 
"Laos Goes Into Total Lockdown | TTR Weekly". Ttrweekly.Com, 2020, https://www.ttrweekly.com/site/2020/04/laos-goes-into-total-lockdown/.
"NPR Cookie Consent And Choices". Npr.Org, 2020, https://www.npr.org/sections/coronavirus-live-updates/2020/05/17/856475752/with-19-confirmed-covid-19-cases-and-no-deaths-laos-to-loosen-lockdown?t=1607573158095. 
Falconer, Rebecca. "New Zealand Uses Science To Avoid Coronavirus Lockdown". Axios, 2020, https://www.axios.com/covid-new-zealand-science-lockdown-who-b8ed7a91-5008-4ce9-890d-8021e2d6fbb9.html. 
"How South Korea Avoided A COVID-19 Lockdown". Medpagetoday.Com, 2020, https://www.medpagetoday.com/meetingcoverage/aasld/89690.
"U.S. State And Local Government Responses To The COVID-19 Pandemic". En.Wikipedia.Org, 2020, https://en.wikipedia.org/wiki/U.S._state_and_local_government_responses_to_the_COVID-19_pandemic.
"Yahoo Is Now A Part Of Verizon Media". Uk.News.Yahoo.Com, 2020, https://uk.news.yahoo.com/sweden-covid-strategy-no-lockdown-did-it-work-145518288.html.
 Johnson, Kay. "Health Officials Praise Laos After Coronavirus-Free Declaration". U.S., 2020, https://www.reuters.com/article/us-health-coronavirus-laos-idUSKBN23P1XU.
"WHO Praises New Zealand For 'Unique' Approach To Coronavirus". Thehill, 2020, https://thehill.com/blogs/blog-briefing-room/news/526788-who-praises-new-zealand-for-unique-approach-to-coronavirus.
"Emerging COVID-19 Success Story: South Korea Learned The Lessons Of MERS". Our World In Data, 2020, https://ourworldindata.org/covid-exemplar-south-korea.

**Reference for data-vis report:**
[1] "Coronavirus | Lockdown’S Impact Can Be Gauged Only After Two Weeks, Say Experts". The Hindu, 2020, https://www.thehindu.com/news/national/lockdowns-impact-can-be-gauged-only-after-two-weeks/article31230053.ece.
[2] Khan, D., 2021. Why does India have so many COVID cases?. [online] Aljazeera.com.https://www.aljazeera.com/features/2021/4/25/why-does-india-have-so-many-covid-cases
[3] Nei.nih.gov. 2021. Types of Color Blindness | National Eye Institute. [online] Available at: https://www.nei.nih.gov/learn-about-eye-health/eye-conditions-and-diseases/color-blindness/types-color-blindness 
[4]Earthobservatory.nasa.gov. 2021. [online] Available at: https://earthobservatory.nasa.gov/resources/blogs/intro_to_color_for_visualization.pdf 
[5]Infogram. 2021. Interactive Data Visualization – 7 Main Benefits | Infogram. [online] Available at: https://infogram.com/blog/7-key-benefits-of-interactive-data-visualization/

Wood, J. (2021). Session 3: Representing Data with Colour.
Wood, J. (2021). Session 4: Representing Data with Visual Variables. Lecture Notes.
Wood, J. (2021). Session 6: Building Interaction. Lecture Notes.


{|references)}
