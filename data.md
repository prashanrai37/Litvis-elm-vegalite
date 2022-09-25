---
id: litvis

narrative-schemas:
  - ../../narrative-schemas/project.yml

elm:
  dependencies:
    gicentre/elm-vegalite: latest
    gicentre/tidy: latest
---

@import "../css/datavis.less"

```elm {l=hidden}
import Tidy exposing (..)
import VegaLite exposing (..)
```

# UK Data On Covid

[Source](ReportExcel.xlsx)- created for PDIT project.

The countries with the lowest As of Population numbers were Laos, United Republic of Tanzania, and Vietnam. The countries with the highest As of Population numbers were Luxemburg, French Polynesia, and Andorra. Based on APP table I selected 10 countries (Sweden, Germany, China, Laos, New Zealand, Belgium, USA, South Korea, United Kingdom, and Andorra) for the PDIT and this DataVis project. The sample contained countries from all the quartiles to ensure a fair representation, however, high income countries with similar geographical location to the UK were favoured to ensure comparisons were fair when evaluating the data.

## All Ten Countries

^^^elm {m=(tableSummary 17 allTenTable)}^^^

## United Kingdom

^^^elm {m=(tableSummary 18 unitedKingdomTable)}^^^

---

```elm {l=hidden}
allTenTable: Table 
allTenTable =
    """dateRep,day,month,year,cases,deaths,countriesAndTerritories,geoId,countryterritoryCode,popData2019,continentExp,Cumulative_number_for_14_days_of_COVID-19_cases_per_100000,As of Population,Death Change ,Case change,Measures,LoggedValue
2020-12-09,9,12,2020,43,0,Andorra,AD,AND,76177,Europe,1018.680179,0.000564475,,,Social Distancing and Wearing Masks Enforced,2.336965028
2020-12-08,8,12,2020,34,0,Andorra,AD,AND,76177,Europe,1023.931108,0.000446329,0,-9,Social Distancing and Wearing Masks Enforced,2.191050986
2020-12-07,7,12,2020,45,0,Andorra,AD,AND,76177,Europe,1042.309358,0.000590729,0,11,Social Distancing and Wearing Masks Enforced,2.365212389
2020-12-06,6,12,2020,50,1,Andorra,AD,AND,76177,Europe,1047.560287,0.000656366,1,5,Social Distancing and Wearing Masks Enforced,2.430676558
2020-12-05,5,12,2020,51,0,Andorra,AD,AND,76177,Europe,1067.25127,0.000669493,-1,1,Social Distancing and Wearing Masks Enforced,2.442980622
2020-12-04,4,12,2020,62,1,Andorra,AD,AND,76177,Europe,1100.069575,0.000813894,1,11,Social Distancing and Wearing Masks Enforced,2.564332773
2020-12-03,3,12,2020,52,0,Andorra,AD,AND,76177,Europe,1081.691324,0.000682621,-1,-10,Social Distancing and Wearing Masks Enforced,2.455045757
2020-12-02,2,12,2020,45,0,Andorra,AD,AND,76177,Europe,1101.382307,0.000590729,0,-7,Social Distancing and Wearing Masks Enforced,2.365212389
2020-12-01,1,12,2020,33,0,Andorra,AD,AND,76177,Europe,1090.880449,0.000433202,0,-12,Social Distancing and Wearing Masks Enforced,2.172502297
2020-11-30,30,11,2020,42,0,Andorra,AD,AND,76177,Europe,1102.695039,0.000551348,0,9,Social Distancing and Wearing Masks Enforced,2.322344708
2020-11-29,29,11,2020,60,0,Andorra,AD,AND,76177,Europe,1240.531919,0.000787639,0,18,Social Distancing and Wearing Masks Enforced,2.543959311
2020-11-28,28,11,2020,76,0,Andorra,AD,AND,76177,Europe,1161.767988,0.000997676,0,16,Social Distancing and Wearing Masks Enforced,2.690835917
2020-11-27,27,11,2020,106,0,Andorra,AD,AND,76177,Europe,1205.08815,0.001391496,0,30,Social Distancing and Wearing Masks Enforced,2.897557624
2020-11-26,26,11,2020,77,0,Andorra,AD,AND,76177,Europe,1130.262415,0.001010804,0,-29,Social Distancing and Wearing Masks Enforced,2.698958058
2020-11-25,25,11,2020,47,0,Andorra,AD,AND,76177,Europe,1147.327934,0.000616984,0,-30,Social Distancing and Wearing Masks Enforced,2.392231208
2020-11-24,24,11,2020,48,0,Andorra,AD,AND,76177,Europe,1138.138808,0.000630111,0,1,Social Distancing and Wearing Masks Enforced,2.405312427
2020-11-23,23,11,2020,49,0,Andorra,AD,AND,76177,Europe,1146.015201,0.000643239,0,1,Social Distancing and Wearing Masks Enforced,2.41812391
2020-11-22,22,11,2020,65,0,Andorra,AD,AND,76177,Europe,1165.706184,0.000853276,0,16,Social Distancing and Wearing Masks Enforced,2.593692641
2020-11-21,21,11,2020,76,0,Andorra,AD,AND,76177,Europe,1321.921315,0.000997676,0,11,Social Distancing and Wearing Masks Enforced,2.690835917
2020-11-20,20,11,2020,48,0,Andorra,AD,AND,76177,Europe,1222.153668,0.000630111,0,-28,Social Distancing and Wearing Masks Enforced,2.405312427
2020-11-19,19,11,2020,67,0,Andorra,AD,AND,76177,Europe,1277.28842,0.000879531,0,19,Social Distancing and Wearing Masks Enforced,2.612522414
2020-11-18,18,11,2020,37,0,Andorra,AD,AND,76177,Europe,1366.554209,0.000485711,0,-30,Social Distancing and Wearing Masks Enforced,2.243589445
2020-11-17,17,11,2020,42,0,Andorra,AD,AND,76177,Europe,1346.863226,0.000551348,0,5,Social Distancing and Wearing Masks Enforced,2.322344708
2020-11-16,16,11,2020,147,1,Andorra,AD,AND,76177,Europe,1374.430602,0.001929716,1,105,Social Distancing and Wearing Masks Enforced,3.100730105
2020-11-15,15,11,2020,0,0,Andorra,AD,AND,76177,Europe,1272.037492,0,-1,-147,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-14,14,11,2020,109,0,Andorra,AD,AND,76177,Europe,1391.496121,0.001430878,0,109,Social Distancing and Wearing Masks Enforced,2.914898329
2020-11-13,13,11,2020,49,0,Andorra,AD,AND,76177,Europe,1377.056067,0.000643239,0,-60,Social Distancing and Wearing Masks Enforced,2.41812391
2020-11-12,12,11,2020,90,0,Andorra,AD,AND,76177,Europe,1378.368799,0.001181459,0,41,Social Distancing and Wearing Masks Enforced,2.795888947
2020-11-11,11,11,2020,40,0,Andorra,AD,AND,76177,Europe,1400.685246,0.000525093,0,-50,Social Distancing and Wearing Masks Enforced,2.292029674
2020-11-10,10,11,2020,54,0,Andorra,AD,AND,76177,Europe,1459.758195,0.000708875,0,14,Social Distancing and Wearing Masks Enforced,2.478495142
2020-11-09,9,11,2020,64,0,Andorra,AD,AND,76177,Europe,1765.624795,0.000840149,0,10,Social Distancing and Wearing Masks Enforced,2.584059348
2020-11-08,8,11,2020,184,0,Andorra,AD,AND,76177,Europe,1681.609935,0.002415427,0,120,Social Distancing and Wearing Masks Enforced,3.240221768
2020-11-07,7,11,2020,0,0,Andorra,AD,AND,76177,Europe,1440.067212,0,0,-184,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-06,6,11,2020,90,0,Andorra,AD,AND,76177,Europe,1738.057419,0.001181459,0,90,Social Distancing and Wearing Masks Enforced,2.795888947
2020-11-05,5,11,2020,135,0,Andorra,AD,AND,76177,Europe,1619.911522,0.001772188,0,45,Social Distancing and Wearing Masks Enforced,3.047818583
2020-11-04,4,11,2020,22,0,Andorra,AD,AND,76177,Europe,1689.486328,0.000288801,0,-113,Social Distancing and Wearing Masks Enforced,1.92057266
2020-11-03,3,11,2020,63,0,Andorra,AD,AND,76177,Europe,1660.60622,0.000827021,0,41,Social Distancing and Wearing Masks Enforced,2.574274344
2020-11-02,2,11,2020,69,0,Andorra,AD,AND,76177,Europe,1900.83621,0.000905785,0,6,Social Distancing and Wearing Masks Enforced,2.630798288
2020-11-01,1,11,2020,91,0,Andorra,AD,AND,76177,Europe,1810.257689,0.001194586,0,22,Social Distancing and Wearing Masks Enforced,2.802754596
2020-10-31,31,10,2020,98,2,Andorra,AD,AND,76177,Europe,1690.79906,0.001286478,2,7,Social Distancing and Wearing Masks Enforced,2.848800468
2020-10-30,30,10,2020,50,1,Andorra,AD,AND,76177,Europe,1807.632225,0.000656366,-1,-48,Social Distancing and Wearing Masks Enforced,2.430676558
2020-10-29,29,10,2020,107,0,Andorra,AD,AND,76177,Europe,1741.995615,0.001404623,-1,57,Social Distancing and Wearing Masks Enforced,2.903391798
2020-10-28,28,10,2020,85,0,Andorra,AD,AND,76177,Europe,1857.516048,0.001115822,0,-22,Social Distancing and Wearing Masks Enforced,2.760374428
2020-10-27,27,10,2020,287,3,Andorra,AD,AND,76177,Europe,1745.933812,0.003767541,3,202,Social Distancing and Wearing Masks Enforced,3.516434012
2020-10-26,26,10,2020,0,0,Andorra,AD,AND,76177,Europe,1761.686598,0,-3,-287,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-25,25,10,2020,0,0,Andorra,AD,AND,76177,Europe,1761.686598,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-24,24,10,2020,227,6,Andorra,AD,AND,76177,Europe,1761.686598,0.002979902,6,227,Social Distancing and Wearing Masks Enforced,3.370710964
2020-10-23,23,10,2020,0,0,Andorra,AD,AND,76177,Europe,1631.726112,0,-6,-227,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-22,22,10,2020,188,1,Andorra,AD,AND,76177,Europe,1631.726112,0.002467937,1,188,Social Distancing and Wearing Masks Enforced,3.253584324
2020-10-21,21,10,2020,0,0,Andorra,AD,AND,76177,Europe,1644.853433,0,-1,-188,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-20,20,10,2020,246,3,Andorra,AD,AND,76177,Europe,1644.853433,0.003229321,3,246,Social Distancing and Wearing Masks Enforced,3.42065481
2020-10-19,19,10,2020,0,0,Andorra,AD,AND,76177,Europe,1663.231684,0,-3,-246,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-18,18,10,2020,0,0,Andorra,AD,AND,76177,Europe,1663.231684,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-17,17,10,2020,187,0,Andorra,AD,AND,76177,Europe,1663.231684,0.002454809,0,187,Social Distancing and Wearing Masks Enforced,3.25027053
2020-10-16,16,10,2020,0,0,Andorra,AD,AND,76177,Europe,1496.514696,0,0,-187,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-15,15,10,2020,195,2,Andorra,AD,AND,76177,Europe,1496.514696,0.002559828,2,195,Social Distancing and Wearing Masks Enforced,3.276298836
2020-10-14,14,10,2020,0,0,Andorra,AD,AND,76177,Europe,1350.801423,0,-2,-195,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-13,13,10,2020,299,2,Andorra,AD,AND,76177,Europe,1350.801423,0.003925069,2,299,Social Distancing and Wearing Masks Enforced,3.541884735
2020-10-12,12,10,2020,0,0,Andorra,AD,AND,76177,Europe,1128.949683,0,-2,-299,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-11,11,10,2020,0,0,Andorra,AD,AND,76177,Europe,1128.949683,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-10,10,10,2020,128,1,Andorra,AD,AND,76177,Europe,1128.949683,0.001680297,1,128,Social Distancing and Wearing Masks Enforced,3.014735907
2020-10-09,9,10,2020,0,1,Andorra,AD,AND,76177,Europe,1069.876734,0,0,-128,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-08,8,10,2020,198,0,Andorra,AD,AND,76177,Europe,1069.876734,0.00259921,-1,198,Social Distancing and Wearing Masks Enforced,3.285785049
2020-10-07,7,10,2020,0,0,Andorra,AD,AND,76177,Europe,904.4724786,0,0,-198,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-06,6,10,2020,260,0,Andorra,AD,AND,76177,Europe,904.4724786,0.003413104,0,260,Social Distancing and Wearing Masks Enforced,3.455045757
2020-10-05,5,10,2020,0,0,Andorra,AD,AND,76177,Europe,716.7517755,0,0,-260,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-04,4,10,2020,0,0,Andorra,AD,AND,76177,Europe,716.7517755,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-03,3,10,2020,60,0,Andorra,AD,AND,76177,Europe,716.7517755,0.000787639,0,60,Social Distancing and Wearing Masks Enforced,2.543959311
2020-10-02,2,10,2020,0,0,Andorra,AD,AND,76177,Europe,744.3191515,0,0,-60,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-01,1,10,2020,84,0,Andorra,AD,AND,76177,Europe,803.3921,0.001102695,0,84,Social Distancing and Wearing Masks Enforced,2.753021266
2020-09-30,30,9,2020,0,0,Andorra,AD,AND,76177,Europe,693.1225961,0,0,-84,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-29,29,9,2020,130,0,Andorra,AD,AND,76177,Europe,693.1225961,0.001706552,0,130,Social Distancing and Wearing Masks Enforced,3.024369199
2020-09-28,28,9,2020,0,0,Andorra,AD,AND,76177,Europe,645.8642372,0,0,-130,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-27,27,9,2020,0,0,Andorra,AD,AND,76177,Europe,645.8642372,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-26,26,9,2020,83,0,Andorra,AD,AND,76177,Europe,645.8642372,0.001089568,0,83,Social Distancing and Wearing Masks Enforced,2.74558004
2020-09-25,25,9,2020,0,0,Andorra,AD,AND,76177,Europe,593.3549497,0,0,-83,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-24,24,9,2020,72,0,Andorra,AD,AND,76177,Europe,593.3549497,0.000945167,0,72,Social Distancing and Wearing Masks Enforced,2.657242063
2020-09-23,23,9,2020,0,0,Andorra,AD,AND,76177,Europe,551.3475196,0,0,-72,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-22,22,9,2020,117,0,Andorra,AD,AND,76177,Europe,551.3475196,0.001535897,0,117,Social Distancing and Wearing Masks Enforced,2.95890503
2020-09-21,21,9,2020,0,0,Andorra,AD,AND,76177,Europe,458.1435341,0,0,-117,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-20,20,9,2020,0,0,Andorra,AD,AND,76177,Europe,458.1435341,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-19,19,9,2020,81,0,Andorra,AD,AND,76177,Europe,458.1435341,0.001063313,0,81,Social Distancing and Wearing Masks Enforced,2.730424778
2020-09-18,18,9,2020,45,0,Andorra,AD,AND,76177,Europe,372.8159418,0.000590729,0,-36,Social Distancing and Wearing Masks Enforced,2.365212389
2020-09-17,17,9,2020,0,0,Andorra,AD,AND,76177,Europe,313.7429933,0,0,-45,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-16,16,9,2020,0,0,Andorra,AD,AND,76177,Europe,333.4339761,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-15,15,9,2020,94,0,Andorra,AD,AND,76177,Europe,343.9358337,0.001233968,0,94,Social Distancing and Wearing Masks Enforced,2.822907766
2020-09-14,14,9,2020,0,0,Andorra,AD,AND,76177,Europe,288.8010817,0,0,-94,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-13,13,9,2020,0,0,Andorra,AD,AND,76177,Europe,288.8010817,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-12,12,9,2020,43,0,Andorra,AD,AND,76177,Europe,288.8010817,0.000564475,0,43,Social Distancing and Wearing Masks Enforced,2.336965028
2020-09-11,11,9,2020,0,0,Andorra,AD,AND,76177,Europe,266.4846345,0,0,-43,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-10,10,9,2020,40,0,Andorra,AD,AND,76177,Europe,266.4846345,0.000525093,0,40,Social Distancing and Wearing Masks Enforced,2.292029674
2020-09-09,9,9,2020,0,0,Andorra,AD,AND,76177,Europe,263.8591701,0,0,-40,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-08,8,9,2020,46,0,Andorra,AD,AND,76177,Europe,263.8591701,0.000603857,0,46,Social Distancing and Wearing Masks Enforced,2.378868652
2020-09-07,7,9,2020,0,0,Andorra,AD,AND,76177,Europe,223.1644722,0,0,-46,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-06,6,9,2020,0,0,Andorra,AD,AND,76177,Europe,223.1644722,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-05,5,9,2020,16,0,Andorra,AD,AND,76177,Europe,223.1644722,0.000210037,0,16,Social Distancing and Wearing Masks Enforced,1.722706232
2020-09-04,4,9,2020,0,0,Andorra,AD,AND,76177,Europe,229.7281332,0,0,-16,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-03,3,9,2020,15,0,Andorra,AD,AND,76177,Europe,229.7281332,0.00019691,0,15,Social Distancing and Wearing Masks Enforced,1.682606194
2020-09-02,2,9,2020,8,0,Andorra,AD,AND,76177,Europe,234.9790619,0.000105019,0,-7,Social Distancing and Wearing Masks Enforced,1.292029674
2020-09-01,1,9,2020,52,0,Andorra,AD,AND,76177,Europe,224.4772044,0.000682621,0,44,Social Distancing and Wearing Masks Enforced,2.455045757
2020-08-31,31,8,2020,0,0,Andorra,AD,AND,76177,Europe,177.2188456,0,0,-52,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-30,30,8,2020,0,0,Andorra,AD,AND,76177,Europe,177.2188456,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-29,29,8,2020,26,0,Andorra,AD,AND,76177,Europe,177.2188456,0.00034131,0,26,Social Distancing and Wearing Masks Enforced,2.024369199
2020-08-28,28,8,2020,0,0,Andorra,AD,AND,76177,Europe,153.5896662,0,0,-26,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-27,27,8,2020,38,0,Andorra,AD,AND,76177,Europe,158.8405949,0.000498838,0,38,Social Distancing and Wearing Masks Enforced,2.260159359
2020-08-26,26,8,2020,0,0,Andorra,AD,AND,76177,Europe,127.3350224,0,0,-38,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-25,25,8,2020,15,0,Andorra,AD,AND,76177,Europe,127.3350224,0.00019691,0,15,Social Distancing and Wearing Masks Enforced,1.682606194
2020-08-24,24,8,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,-15,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-23,23,8,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-22,22,8,2020,21,0,Andorra,AD,AND,76177,Europe,118.1458971,0.000275674,0,21,Social Distancing and Wearing Masks Enforced,1.89166815
2020-08-21,21,8,2020,0,0,Andorra,AD,AND,76177,Europe,105.0185752,0,0,-21,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-20,20,8,2020,19,0,Andorra,AD,AND,76177,Europe,111.5822361,0.000249419,0,19,Social Distancing and Wearing Masks Enforced,1.8294828
2020-08-19,19,8,2020,0,0,Andorra,AD,AND,76177,Europe,86.64032451,0,0,-19,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-18,18,8,2020,16,0,Andorra,AD,AND,76177,Europe,89.26578889,0.000210037,0,16,Social Distancing and Wearing Masks Enforced,1.722706232
2020-08-17,17,8,2020,0,0,Andorra,AD,AND,76177,Europe,84.01486013,0,0,-16,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-16,16,8,2020,0,0,Andorra,AD,AND,76177,Europe,84.01486013,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-15,15,8,2020,8,0,Andorra,AD,AND,76177,Europe,84.01486013,0.000105019,0,8,Social Distancing and Wearing Masks Enforced,1.292029674
2020-08-14,14,8,2020,4,0,Andorra,AD,AND,76177,Europe,77.45119918,5.25E-05,0,-4,Social Distancing and Wearing Masks Enforced,0.861353116
2020-08-13,13,8,2020,14,1,Andorra,AD,AND,76177,Europe,77.45119918,0.000183783,1,10,Social Distancing and Wearing Masks Enforced,1.639738513
2020-08-12,12,8,2020,0,0,Andorra,AD,AND,76177,Europe,73.51300261,0,-1,-14,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-11,11,8,2020,7,0,Andorra,AD,AND,76177,Europe,73.51300261,9.19E-05,0,7,Social Distancing and Wearing Masks Enforced,1.209061955
2020-08-10,10,8,2020,0,0,Andorra,AD,AND,76177,Europe,77.45119918,0,0,-7,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-09,9,8,2020,1,0,Andorra,AD,AND,76177,Europe,77.45119918,1.31E-05,0,1,Social Distancing and Wearing Masks Enforced,0
2020-08-08,8,8,2020,11,0,Andorra,AD,AND,76177,Europe,86.64032451,0.000144401,0,10,Social Distancing and Wearing Masks Enforced,1.489896102
2020-08-07,7,8,2020,5,0,Andorra,AD,AND,76177,Europe,72.20027042,6.56E-05,0,-6,Social Distancing and Wearing Masks Enforced,1
2020-08-06,6,8,2020,0,0,Andorra,AD,AND,76177,Europe,65.63660948,0,0,-5,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-05,5,8,2020,2,0,Andorra,AD,AND,76177,Europe,72.20027042,2.63E-05,0,2,Social Distancing and Wearing Masks Enforced,0.430676558
2020-08-04,4,8,2020,12,0,Andorra,AD,AND,76177,Europe,69.57480604,0.000157528,0,10,Social Distancing and Wearing Masks Enforced,1.543959311
2020-08-03,3,8,2020,0,0,Andorra,AD,AND,76177,Europe,59.07294853,0,0,-12,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-02,2,8,2020,0,0,Andorra,AD,AND,76177,Europe,59.07294853,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-01,1,8,2020,3,0,Andorra,AD,AND,76177,Europe,59.07294853,3.94E-05,0,3,Social Distancing and Wearing Masks Enforced,0.682606194
2020-07-31,31,7,2020,4,0,Andorra,AD,AND,76177,Europe,59.07294853,5.25E-05,0,1,Social Distancing and Wearing Masks Enforced,0.861353116
2020-07-30,30,7,2020,11,0,Andorra,AD,AND,76177,Europe,73.51300261,0.000144401,0,7,Social Distancing and Wearing Masks Enforced,1.489896102
2020-07-29,29,7,2020,0,0,Andorra,AD,AND,76177,Europe,60.38568072,0,0,-11,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-28,28,7,2020,10,0,Andorra,AD,AND,76177,Europe,64.32387729,0.000131273,0,10,Social Distancing and Wearing Masks Enforced,1.430676558
2020-07-27,27,7,2020,0,0,Andorra,AD,AND,76177,Europe,55.13475196,0,0,-10,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-26,26,7,2020,8,0,Andorra,AD,AND,76177,Europe,55.13475196,0.000105019,0,8,Social Distancing and Wearing Masks Enforced,1.292029674
2020-07-25,25,7,2020,0,0,Andorra,AD,AND,76177,Europe,44.63289444,0,0,-8,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-24,24,7,2020,0,0,Andorra,AD,AND,76177,Europe,44.63289444,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-23,23,7,2020,5,0,Andorra,AD,AND,76177,Europe,44.63289444,6.56E-05,0,5,Social Distancing and Wearing Masks Enforced,1
2020-07-22,22,7,2020,0,0,Andorra,AD,AND,76177,Europe,38.0692335,0,0,-5,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-21,21,7,2020,4,0,Andorra,AD,AND,76177,Europe,38.0692335,5.25E-05,0,4,Social Distancing and Wearing Masks Enforced,0.861353116
2020-07-20,20,7,2020,0,0,Andorra,AD,AND,76177,Europe,32.81830474,0,0,-4,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-19,19,7,2020,0,0,Andorra,AD,AND,76177,Europe,32.81830474,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-18,18,7,2020,3,0,Andorra,AD,AND,76177,Europe,32.81830474,3.94E-05,0,3,Social Distancing and Wearing Masks Enforced,0.682606194
2020-07-17,17,7,2020,15,0,Andorra,AD,AND,76177,Europe,28.88010817,0.00019691,0,12,Social Distancing and Wearing Masks Enforced,1.682606194
2020-07-16,16,7,2020,1,0,Andorra,AD,AND,76177,Europe,9.18912533,1.31E-05,0,-14,Social Distancing and Wearing Masks Enforced,0
2020-07-15,15,7,2020,3,0,Andorra,AD,AND,76177,Europe,7.87639314,3.94E-05,0,2,Social Distancing and Wearing Masks Enforced,0.682606194
2020-07-14,14,7,2020,3,0,Andorra,AD,AND,76177,Europe,3.93819657,3.94E-05,0,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-07-13,13,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,-3,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-12,12,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-11,11,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-10,10,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-09,9,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-08,8,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-07,7,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-06,6,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-05,5,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-04,4,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-03,3,7,2020,0,0,Andorra,AD,AND,76177,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-02,2,7,2020,0,0,Andorra,AD,AND,76177,Europe,1.31273219,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-01,1,7,2020,0,0,Andorra,AD,AND,76177,Europe,1.31273219,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-30,30,6,2020,0,0,Andorra,AD,AND,76177,Europe,2.62546438,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-29,29,6,2020,0,0,Andorra,AD,AND,76177,Europe,2.62546438,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-28,28,6,2020,0,0,Andorra,AD,AND,76177,Europe,2.62546438,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-27,27,6,2020,0,0,Andorra,AD,AND,76177,Europe,2.62546438,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-26,26,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-25,25,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-24,24,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-23,23,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-22,22,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-21,21,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-20,20,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-19,19,6,2020,1,0,Andorra,AD,AND,76177,Europe,3.93819657,1.31E-05,0,1,Social Distancing and Wearing Masks Enforced,0
2020-06-18,18,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-17,17,6,2020,1,1,Andorra,AD,AND,76177,Europe,13.1273219,1.31E-05,1,1,Social Distancing and Wearing Masks Enforced,0
2020-06-16,16,6,2020,0,0,Andorra,AD,AND,76177,Europe,115.5204327,0,-1,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-15,15,6,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-14,14,6,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-13,13,6,2020,1,0,Andorra,AD,AND,76177,Europe,116.8331649,1.31E-05,0,1,Social Distancing and Wearing Masks Enforced,0
2020-06-12,12,6,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-11,11,6,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-10,10,6,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-09,9,6,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-08,8,6,2020,0,0,Andorra,AD,AND,76177,Europe,116.8331649,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-07,7,6,2020,0,0,Andorra,AD,AND,76177,Europe,118.1458971,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-06,6,6,2020,0,0,Andorra,AD,AND,76177,Europe,118.1458971,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-05,5,6,2020,1,0,Andorra,AD,AND,76177,Europe,118.1458971,1.31E-05,0,1,Social Distancing and Wearing Masks Enforced,0
2020-06-04,4,6,2020,7,0,Andorra,AD,AND,76177,Europe,116.8331649,9.19E-05,0,6,Social Distancing and Wearing Masks Enforced,1.209061955
2020-06-03,3,6,2020,79,0,Andorra,AD,AND,76177,Europe,108.9567717,0.001037058,0,72,Social Distancing and Wearing Masks Enforced,2.714890595
2020-06-02,2,6,2020,1,0,Andorra,AD,AND,76177,Europe,5.25092876,1.31E-05,0,-78,Social Distancing and Wearing Masks Enforced,0
2020-06-01,1,6,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-31,31,5,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-30,30,5,2020,1,0,Andorra,AD,AND,76177,Europe,3.93819657,1.31E-05,0,1,Social Distancing and Wearing Masks Enforced,0
2020-05-29,29,5,2020,0,0,Andorra,AD,AND,76177,Europe,2.62546438,0,0,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-28,28,5,2020,0,0,Andorra,AD,AND,76177,Europe,3.93819657,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-27,27,5,2020,0,0,Andorra,AD,AND,76177,Europe,6.56366095,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-26,26,5,2020,0,0,Andorra,AD,AND,76177,Europe,9.18912533,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-25,25,5,2020,1,0,Andorra,AD,AND,76177,Europe,10.50185752,1.31E-05,0,1,Social Distancing and Wearing Masks Enforced,0
2020-05-24,24,5,2020,0,0,Andorra,AD,AND,76177,Europe,10.50185752,0,0,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-23,23,5,2020,0,0,Andorra,AD,AND,76177,Europe,13.1273219,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-22,22,5,2020,0,0,Andorra,AD,AND,76177,Europe,13.1273219,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-21,21,5,2020,1,0,Andorra,AD,AND,76177,Europe,14.44005408,1.31E-05,0,1,Social Distancing and Wearing Masks Enforced,0
2020-05-20,20,5,2020,0,0,Andorra,AD,AND,76177,Europe,13.1273219,0,0,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-19,19,5,2020,0,0,Andorra,AD,AND,76177,Europe,14.44005408,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-18,18,5,2020,0,0,Andorra,AD,AND,76177,Europe,17.06551846,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-17,17,5,2020,0,2,Andorra,AD,AND,76177,Europe,18.37825065,0,2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-16,16,5,2020,0,0,Andorra,AD,AND,76177,Europe,19.69098284,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-15,15,5,2020,1,0,Andorra,AD,AND,76177,Europe,21.00371503,1.31E-05,0,1,Social Distancing and Wearing Masks Enforced,0
2020-05-14,14,5,2020,2,1,Andorra,AD,AND,76177,Europe,22.31644722,2.63E-05,1,1,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-13,13,5,2020,2,0,Andorra,AD,AND,76177,Europe,19.69098284,2.63E-05,-1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-12,12,5,2020,1,0,Andorra,AD,AND,76177,Europe,17.06551846,1.31E-05,0,-1,Social Distancing and Wearing Masks Enforced,0
2020-05-11,11,5,2020,1,0,Andorra,AD,AND,76177,Europe,19.69098284,1.31E-05,0,0,Social Distancing and Wearing Masks Enforced,0
2020-05-10,10,5,2020,2,1,Andorra,AD,AND,76177,Europe,27.56737598,2.63E-05,1,1,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-09,9,5,2020,0,0,Andorra,AD,AND,76177,Europe,27.56737598,0,-1,-2,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-08,8,5,2020,1,1,Andorra,AD,AND,76177,Europe,36.75650131,1.31E-05,1,1,Social Distancing and Wearing Masks Enforced,0
2020-05-07,7,5,2020,0,0,Andorra,AD,AND,76177,Europe,36.75650131,0,-1,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-06,6,5,2020,1,1,Andorra,AD,AND,76177,Europe,44.63289444,1.31E-05,1,1,Social Distancing and Wearing Masks Enforced,0
2020-05-05,5,5,2020,2,0,Andorra,AD,AND,76177,Europe,43.32016225,2.63E-05,-1,1,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-04,4,5,2020,1,1,Andorra,AD,AND,76177,Europe,45.94562663,1.31E-05,1,-1,Social Distancing and Wearing Masks Enforced,0
2020-05-03,3,5,2020,1,1,Andorra,AD,AND,76177,Europe,56.44748415,1.31E-05,0,0,Social Distancing and Wearing Masks Enforced,0
2020-05-02,2,5,2020,1,1,Andorra,AD,AND,76177,Europe,65.63660948,1.31E-05,0,0,Social Distancing and Wearing Masks Enforced,0
2020-05-01,1,5,2020,2,0,Andorra,AD,AND,76177,Europe,82.70212794,2.63E-05,-1,1,Social Distancing and Wearing Masks Enforced,0.430676558
2020-04-30,30,4,2020,0,1,Andorra,AD,AND,76177,Europe,91.89125327,0,1,-2,Social Distancing and Wearing Masks Enforced,#NUM!
2020-04-29,29,4,2020,0,1,Andorra,AD,AND,76177,Europe,110.2695039,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-04-28,28,4,2020,3,0,Andorra,AD,AND,76177,Europe,127.3350224,3.94E-05,-1,3,Social Distancing and Wearing Masks Enforced,0.682606194
2020-04-27,27,4,2020,7,0,Andorra,AD,AND,76177,Europe,133.8986833,9.19E-05,0,4,Social Distancing and Wearing Masks Enforced,1.209061955
2020-04-26,26,4,2020,2,0,Andorra,AD,AND,76177,Europe,145.713273,2.63E-05,0,-5,Social Distancing and Wearing Masks Enforced,0.430676558
2020-04-25,25,4,2020,7,3,Andorra,AD,AND,76177,Europe,170.6551846,9.19E-05,3,5,Social Distancing and Wearing Masks Enforced,1.209061955
2020-04-24,24,4,2020,1,0,Andorra,AD,AND,76177,Europe,185.0952387,1.31E-05,-3,-6,Social Distancing and Wearing Masks Enforced,0
2020-04-23,23,4,2020,6,0,Andorra,AD,AND,76177,Europe,208.7244181,7.88E-05,0,5,Social Distancing and Wearing Masks Enforced,1.113282753
2020-04-22,22,4,2020,0,1,Andorra,AD,AND,76177,Europe,225.7899366,0,1,-6,Social Distancing and Wearing Masks Enforced,#NUM!
2020-04-21,21,4,2020,4,0,Andorra,AD,AND,76177,Europe,250.7318482,5.25E-05,-1,4,Social Distancing and Wearing Masks Enforced,0.861353116
2020-04-20,20,4,2020,9,1,Andorra,AD,AND,76177,Europe,278.2992242,0.000118146,1,5,Social Distancing and Wearing Masks Enforced,1.365212389
2020-04-19,19,4,2020,8,0,Andorra,AD,AND,76177,Europe,312.4302611,0.000105019,-1,-1,Social Distancing and Wearing Masks Enforced,1.292029674
2020-04-18,18,4,2020,14,2,Andorra,AD,AND,76177,Europe,337.3721727,0.000183783,2,6,Social Distancing and Wearing Masks Enforced,1.639738513
2020-04-17,17,4,2020,9,0,Andorra,AD,AND,76177,Europe,333.4339761,0.000118146,-2,-5,Social Distancing and Wearing Masks Enforced,1.365212389
2020-04-16,16,4,2020,14,2,Andorra,AD,AND,76177,Europe,371.5032096,0.000183783,2,5,Social Distancing and Wearing Masks Enforced,1.639738513
2020-04-15,15,4,2020,13,2,Andorra,AD,AND,76177,Europe,371.5032096,0.000170655,0,-1,Social Distancing and Wearing Masks Enforced,1.593692641
2020-04-14,14,4,2020,8,0,Andorra,AD,AND,76177,Europe,362.3140843,0.000105019,-2,-5,Social Distancing and Wearing Masks Enforced,1.292029674
2020-04-13,13,4,2020,16,1,Andorra,AD,AND,76177,Europe,399.0705856,0.000210037,1,8,Social Distancing and Wearing Masks Enforced,1.722706232
2020-04-12,12,4,2020,21,2,Andorra,AD,AND,76177,Europe,412.1979075,0.000275674,1,5,Social Distancing and Wearing Masks Enforced,1.89166815
2020-04-11,11,4,2020,18,1,Andorra,AD,AND,76177,Europe,438.4525513,0.000236292,-1,-3,Social Distancing and Wearing Masks Enforced,1.795888947
2020-04-10,10,4,2020,19,2,Andorra,AD,AND,76177,Europe,471.270856,0.000249419,1,1,Social Distancing and Wearing Masks Enforced,1.8294828
2020-04-09,9,4,2020,19,1,Andorra,AD,AND,76177,Europe,493.5873033,0.000249419,-1,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-04-08,8,4,2020,19,1,Andorra,AD,AND,76177,Europe,500.1509642,0.000249419,0,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-04-07,7,4,2020,25,3,Andorra,AD,AND,76177,Europe,515.9037505,0.000328183,2,6,Social Distancing and Wearing Masks Enforced,2
2020-04-06,6,4,2020,35,1,Andorra,AD,AND,76177,Europe,509.3400895,0.000459456,-2,10,Social Distancing and Wearing Masks Enforced,2.209061955
2020-04-05,5,4,2020,27,1,Andorra,AD,AND,76177,Europe,496.2127676,0.000354438,0,-8,Social Distancing and Wearing Masks Enforced,2.047818583
2020-04-04,4,4,2020,11,1,Andorra,AD,AND,76177,Europe,477.834517,0.000144401,0,-16,Social Distancing and Wearing Masks Enforced,1.489896102
2020-04-03,3,4,2020,38,1,Andorra,AD,AND,76177,Europe,463.3944629,0.000498838,0,27,Social Distancing and Wearing Masks Enforced,2.260159359
2020-04-02,2,4,2020,14,2,Andorra,AD,AND,76177,Europe,442.3907479,0.000183783,1,-24,Social Distancing and Wearing Masks Enforced,1.639738513
2020-04-01,1,4,2020,6,4,Andorra,AD,AND,76177,Europe,475.2090526,7.88E-05,2,-8,Social Distancing and Wearing Masks Enforced,1.113282753
2020-03-31,31,3,2020,36,2,Andorra,AD,AND,76177,Europe,467.3326595,0.000472584,-2,30,Social Distancing and Wearing Masks Enforced,2.226565505
2020-03-30,30,3,2020,26,2,Andorra,AD,AND,76177,Europe,431.8888904,0.00034131,0,-10,Social Distancing and Wearing Masks Enforced,2.024369199
2020-03-29,29,3,2020,41,1,Andorra,AD,AND,76177,Europe,401.69605,0.00053822,-1,15,Social Distancing and Wearing Masks Enforced,2.307372057
2020-03-28,28,3,2020,43,0,Andorra,AD,AND,76177,Europe,349.1867624,0.000564475,-1,2,Social Distancing and Wearing Masks Enforced,2.336965028
2020-03-27,27,3,2020,36,3,Andorra,AD,AND,76177,Europe,294.0520105,0.000472584,3,-7,Social Distancing and Wearing Masks Enforced,2.226565505
2020-03-26,26,3,2020,24,0,Andorra,AD,AND,76177,Europe,,0.000315056,-3,-12,Social Distancing and Wearing Masks Enforced,1.974635869
2020-03-25,25,3,2020,31,0,Andorra,AD,AND,76177,Europe,,0.000406947,0,7,Social Distancing and Wearing Masks Enforced,2.133656215
2020-03-24,24,3,2020,20,0,Andorra,AD,AND,76177,Europe,,0.000262546,0,-11,Social Distancing and Wearing Masks Enforced,1.861353116
2020-03-23,23,3,2020,25,0,Andorra,AD,AND,76177,Europe,,0.000328183,0,5,Social Distancing and Wearing Masks Enforced,2
2020-03-22,22,3,2020,13,0,Andorra,AD,AND,76177,Europe,,0.000170655,0,-12,Social Distancing and Wearing Masks Enforced,1.593692641
2020-03-21,21,3,2020,0,0,Andorra,AD,AND,76177,Europe,,0,0,-13,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-20,20,3,2020,22,0,Andorra,AD,AND,76177,Europe,,0.000288801,0,22,Social Distancing and Wearing Masks Enforced,1.92057266
2020-03-19,19,3,2020,39,0,Andorra,AD,AND,76177,Europe,,0.000511966,0,17,Social Distancing and Wearing Masks Enforced,2.276298836
2020-03-18,18,3,2020,0,0,Andorra,AD,AND,76177,Europe,,0,0,-39,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-17,17,3,2020,9,0,Andorra,AD,AND,76177,Europe,,0.000118146,0,9,Social Distancing and Wearing Masks Enforced,1.365212389
2020-03-16,16,3,2020,3,0,Andorra,AD,AND,76177,Europe,,3.94E-05,0,-6,Social Distancing and Wearing Masks Enforced,0.682606194
2020-03-14,14,3,2020,1,0,Andorra,AD,AND,76177,Europe,,1.31E-05,0,-2,Social Distancing and Wearing Masks Enforced,0
2020-03-03,3,3,2020,1,0,Andorra,AD,AND,76177,Europe,,1.31E-05,0,0,Social Distancing and Wearing Masks Enforced,0
2019-12-31,31,12,2019,0,0,Sweden,SE,SWE,10230185,Europe,,,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-01,1,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-02,2,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-03,3,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-04,4,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-05,5,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-06,6,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-07,7,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-08,8,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-09,9,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-10,10,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-11,11,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-12,12,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-13,13,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-14,14,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-15,15,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-16,16,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-17,17,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-18,18,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-19,19,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-20,20,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-21,21,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-22,22,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-23,23,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-24,24,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-25,25,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-26,26,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-27,27,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-28,28,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-29,29,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-30,30,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-31,31,1,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-01,1,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-02,2,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-03,3,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-04,4,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-05,5,2,2020,1,0,Sweden,SE,SWE,10230185,Europe,0,1,0,9.77E-08,Social Distancing and Wearing Masks Enforced,0
2020-02-06,6,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,-1,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-07,7,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-08,8,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-09,9,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-10,10,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-11,11,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-12,12,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-13,13,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-14,14,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-15,15,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-16,16,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-17,17,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-18,18,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-19,19,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-20,20,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-21,21,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-22,22,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-23,23,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-24,24,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-25,25,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-26,26,2,2020,0,0,Sweden,SE,SWE,10230185,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-27,27,2,2020,1,0,Sweden,SE,SWE,10230185,Europe,0,1,0,9.77E-08,Social Distancing and Wearing Masks Enforced,0
2020-02-28,28,2,2020,1,0,Sweden,SE,SWE,10230185,Europe,0.00977499,0,0,9.77E-08,Social Distancing and Wearing Masks Enforced,0
2020-02-29,29,2,2020,8,0,Sweden,SE,SWE,10230185,Europe,0.01954999,7,0,7.82E-07,Social Distancing and Wearing Masks Enforced,1.292029674
2020-03-01,1,3,2020,3,0,Sweden,SE,SWE,10230185,Europe,0.09774994,-5,0,2.93E-07,Social Distancing and Wearing Masks Enforced,0.682606194
2020-03-02,2,3,2020,0,0,Sweden,SE,SWE,10230185,Europe,0.01954999,-3,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-03,3,3,2020,5,0,Sweden,SE,SWE,10230185,Europe,0.12707493,5,0,4.89E-07,Social Distancing and Wearing Masks Enforced,1
2020-03-04,4,3,2020,13,0,Sweden,SE,SWE,10230185,Europe,0.1759499,8,0,1.27E-06,Social Distancing and Wearing Masks Enforced,1.593692641
2020-03-05,5,3,2020,30,0,Sweden,SE,SWE,10230185,Europe,0.30302482,17,0,2.93E-06,Social Distancing and Wearing Masks Enforced,2.113282753
2020-03-06,6,3,2020,25,0,Sweden,SE,SWE,10230185,Europe,0.59627465,-5,0,2.44E-06,Social Distancing and Wearing Masks Enforced,2
2020-03-07,7,3,2020,59,0,Sweden,SE,SWE,10230185,Europe,0.84064951,34,0,5.77E-06,Social Distancing and Wearing Masks Enforced,2.533516461
2020-03-08,8,3,2020,33,0,Sweden,SE,SWE,10230185,Europe,1.41737417,-26,0,3.23E-06,Social Distancing and Wearing Masks Enforced,2.172502297
2020-03-09,9,3,2020,46,0,Sweden,SE,SWE,10230185,Europe,1.73994898,13,0,4.50E-06,Social Distancing and Wearing Masks Enforced,2.378868652
2020-03-10,10,3,2020,101,0,Sweden,SE,SWE,10230185,Europe,2.18959872,55,0,9.87E-06,Social Distancing and Wearing Masks Enforced,2.867535604
2020-03-11,11,3,2020,98,0,Sweden,SE,SWE,10230185,Europe,3.17687315,-3,0,9.58E-06,Social Distancing and Wearing Masks Enforced,2.848800468
2020-03-12,12,3,2020,196,28,Sweden,SE,SWE,10230185,Europe,4.13482259,98,28,1.92E-05,Social Distancing and Wearing Masks Enforced,3.279477026
2020-03-13,13,3,2020,151,0,Sweden,SE,SWE,10230185,Europe,6.04094647,-45,-28,1.48E-05,Social Distancing and Wearing Masks Enforced,3.117411239
2020-03-14,14,3,2020,152,1,Sweden,SE,SWE,10230185,Europe,7.50719562,1,1,1.49E-05,Social Distancing and Wearing Masks Enforced,3.121512475
2020-03-15,15,3,2020,71,1,Sweden,SE,SWE,10230185,Europe,8.9147948,-81,0,6.94E-06,Social Distancing and Wearing Masks Enforced,2.648551922
2020-03-16,16,3,2020,69,2,Sweden,SE,SWE,10230185,Europe,9.57949441,-2,1,6.74E-06,Social Distancing and Wearing Masks Enforced,2.630798288
2020-03-17,17,3,2020,83,2,Sweden,SE,SWE,10230185,Europe,10.25396901,14,0,8.11E-06,Social Distancing and Wearing Masks Enforced,2.74558004
2020-03-18,18,3,2020,119,1,Sweden,SE,SWE,10230185,Europe,11.01641857,36,-1,1.16E-05,Social Distancing and Wearing Masks Enforced,2.969436383
2020-03-19,19,3,2020,145,6,Sweden,SE,SWE,10230185,Europe,12.05256796,26,5,1.42E-05,Social Distancing and Wearing Masks Enforced,3.092218534
2020-03-20,20,3,2020,143,7,Sweden,SE,SWE,10230185,Europe,13.17669231,-2,1,1.40E-05,Social Distancing and Wearing Masks Enforced,3.083588744
2020-03-21,21,3,2020,180,9,Sweden,SE,SWE,10230185,Europe,14.33014163,37,2,1.76E-05,Social Distancing and Wearing Masks Enforced,3.226565505
2020-03-22,22,3,2020,136,8,Sweden,SE,SWE,10230185,Europe,15.51291594,-44,-1,1.33E-05,Social Distancing and Wearing Masks Enforced,3.052404102
2020-03-23,23,3,2020,118,11,Sweden,SE,SWE,10230185,Europe,16.51974036,-18,3,1.15E-05,Social Distancing and Wearing Masks Enforced,2.964193019
2020-03-24,24,3,2020,182,11,Sweden,SE,SWE,10230185,Europe,17.22353995,64,0,1.78E-05,Social Distancing and Wearing Masks Enforced,3.233431154
2020-03-25,25,3,2020,230,21,Sweden,SE,SWE,10230185,Europe,18.01531448,48,10,2.25E-05,Social Distancing and Wearing Masks Enforced,3.378868652
2020-03-26,26,3,2020,314,22,Sweden,SE,SWE,10230185,Europe,19.30561373,84,1,3.07E-05,Social Distancing and Wearing Masks Enforced,3.572298715
2020-03-27,27,3,2020,286,31,Sweden,SE,SWE,10230185,Europe,20.45906306,-28,9,2.80E-05,Social Distancing and Wearing Masks Enforced,3.514265302
2020-03-28,28,3,2020,365,32,Sweden,SE,SWE,10230185,Europe,21.77868729,79,1,3.57E-05,Social Distancing and Wearing Masks Enforced,3.665812336
2020-03-29,29,3,2020,300,35,Sweden,SE,SWE,10230185,Europe,23.86076107,-65,3,2.93E-05,Social Distancing and Wearing Masks Enforced,3.543959311
2020-03-30,30,3,2020,280,38,Sweden,SE,SWE,10230185,Europe,26.09923476,-20,3,2.74E-05,Social Distancing and Wearing Masks Enforced,3.501091629
2020-03-31,31,3,2020,416,45,Sweden,SE,SWE,10230185,Europe,28.16175856,136,7,4.07E-05,Social Distancing and Wearing Masks Enforced,3.747075432
2020-04-01,1,4,2020,475,48,Sweden,SE,SWE,10230185,Europe,31.41683166,59,3,4.64E-05,Social Distancing and Wearing Masks Enforced,3.8294828
2020-04-02,2,4,2020,486,53,Sweden,SE,SWE,10230185,Europe,34.89672963,11,5,4.75E-05,Social Distancing and Wearing Masks Enforced,3.843707531
2020-04-03,3,4,2020,554,70,Sweden,SE,SWE,10230185,Europe,38.23000268,68,17,5.42E-05,Social Distancing and Wearing Masks Enforced,3.925075107
2020-04-04,4,4,2020,601,80,Sweden,SE,SWE,10230185,Europe,42.24752534,47,10,5.87E-05,Social Distancing and Wearing Masks Enforced,3.975670565
2020-04-05,5,4,2020,357,70,Sweden,SE,SWE,10230185,Europe,46.36279794,-244,-10,3.49E-05,Social Distancing and Wearing Masks Enforced,3.652042577
2020-04-06,6,4,2020,340,85,Sweden,SE,SWE,10230185,Europe,48.52307167,-17,15,3.32E-05,Social Distancing and Wearing Masks Enforced,3.621727544
2020-04-07,7,4,2020,389,90,Sweden,SE,SWE,10230185,Europe,50.69312041,49,5,3.80E-05,Social Distancing and Wearing Masks Enforced,3.705380181
2020-04-08,8,4,2020,738,84,Sweden,SE,SWE,10230185,Europe,52.71654423,349,-6,7.21E-05,Social Distancing and Wearing Masks Enforced,4.103261004
2020-04-09,9,4,2020,654,115,Sweden,SE,SWE,10230185,Europe,57.68224133,-84,31,6.39E-05,Social Distancing and Wearing Masks Enforced,4.028181082
2020-04-10,10,4,2020,645,86,Sweden,SE,SWE,10230185,Europe,61.00573939,-9,-29,6.30E-05,Social Distancing and Wearing Masks Enforced,4.019571222
2020-04-11,11,4,2020,454,90,Sweden,SE,SWE,10230185,Europe,64.51496234,-191,4,4.44E-05,Social Distancing and Wearing Masks Enforced,3.801387522
2020-04-12,12,4,2020,395,102,Sweden,SE,SWE,10230185,Europe,65.38493683,-59,12,3.86E-05,Social Distancing and Wearing Masks Enforced,3.714890595
2020-04-13,13,4,2020,464,97,Sweden,SE,SWE,10230185,Europe,66.31356129,69,-5,4.54E-05,Social Distancing and Wearing Masks Enforced,3.814924766
2020-04-14,14,4,2020,437,84,Sweden,SE,SWE,10230185,Europe,68.11216024,-27,-13,4.27E-05,Social Distancing and Wearing Masks Enforced,3.777674894
2020-04-15,15,4,2020,479,92,Sweden,SE,SWE,10230185,Europe,68.31743512,42,8,4.68E-05,Social Distancing and Wearing Masks Enforced,3.834693187
2020-04-16,16,4,2020,604,115,Sweden,SE,SWE,10230185,Europe,68.3565351,125,23,5.90E-05,Social Distancing and Wearing Masks Enforced,3.978764355
2020-04-17,17,4,2020,623,111,Sweden,SE,SWE,10230185,Europe,69.50998442,19,-4,6.09E-05,Social Distancing and Wearing Masks Enforced,3.99800854
2020-04-18,18,4,2020,688,83,Sweden,SE,SWE,10230185,Europe,70.18445903,65,-28,6.73E-05,Social Distancing and Wearing Masks Enforced,4.05967126
2020-04-19,19,4,2020,532,86,Sweden,SE,SWE,10230185,Europe,71.03488353,-156,3,5.20E-05,Social Distancing and Wearing Masks Enforced,3.899897872
2020-04-20,20,4,2020,388,87,Sweden,SE,SWE,10230185,Europe,72.74550753,-144,1,3.79E-05,Social Distancing and Wearing Masks Enforced,3.703780863
2020-04-21,21,4,2020,461,85,Sweden,SE,SWE,10230185,Europe,73.21470726,73,-2,4.51E-05,Social Distancing and Wearing Masks Enforced,3.810894472
2020-04-22,22,4,2020,707,62,Sweden,SE,SWE,10230185,Europe,73.91850685,246,-23,6.91E-05,Social Distancing and Wearing Masks Enforced,4.076597559
2020-04-23,23,4,2020,722,77,Sweden,SE,SWE,10230185,Europe,73.61548203,15,15,7.06E-05,Social Distancing and Wearing Masks Enforced,4.089642159
2020-04-24,24,4,2020,758,86,Sweden,SE,SWE,10230185,Europe,74.28018164,36,9,7.41E-05,Social Distancing and Wearing Masks Enforced,4.119875228
2020-04-25,25,4,2020,780,89,Sweden,SE,SWE,10230185,Europe,75.38475599,22,3,7.62E-05,Social Distancing and Wearing Masks Enforced,4.137651952
2020-04-26,26,4,2020,473,73,Sweden,SE,SWE,10230185,Europe,78.57140413,-307,-16,4.62E-05,Social Distancing and Wearing Masks Enforced,3.82686113
2020-04-27,27,4,2020,300,74,Sweden,SE,SWE,10230185,Europe,79.33385369,-173,1,2.93E-05,Social Distancing and Wearing Masks Enforced,3.543959311
2020-04-28,28,4,2020,563,74,Sweden,SE,SWE,10230185,Europe,77.73075462,263,0,5.50E-05,Social Distancing and Wearing Masks Enforced,3.935087883
2020-04-29,29,4,2020,742,83,Sweden,SE,SWE,10230185,Europe,78.96240391,179,9,7.25E-05,Social Distancing and Wearing Masks Enforced,4.106619579
2020-04-30,30,4,2020,798,83,Sweden,SE,SWE,10230185,Europe,81.5332274,56,0,7.80E-05,Social Distancing and Wearing Masks Enforced,4.151827508
2020-05-01,1,5,2020,636,78,Sweden,SE,SWE,10230185,Europe,83.4295763,-162,-5,6.22E-05,Social Distancing and Wearing Masks Enforced,4.010840377
2020-05-02,2,5,2020,532,78,Sweden,SE,SWE,10230185,Europe,83.55665122,-104,0,5.20E-05,Social Distancing and Wearing Masks Enforced,3.899897872
2020-05-03,3,5,2020,299,73,Sweden,SE,SWE,10230185,Europe,82.03175211,-233,-5,2.92E-05,Social Distancing and Wearing Masks Enforced,3.541884735
2020-05-04,4,5,2020,261,75,Sweden,SE,SWE,10230185,Europe,79.75417844,-38,2,2.55E-05,Social Distancing and Wearing Masks Enforced,3.457430923
2020-05-05,5,5,2020,477,84,Sweden,SE,SWE,10230185,Europe,78.51275417,216,9,4.66E-05,Social Distancing and Wearing Masks Enforced,3.832093455
2020-05-06,6,5,2020,657,72,Sweden,SE,SWE,10230185,Europe,78.66915408,180,-12,6.42E-05,Social Distancing and Wearing Masks Enforced,4.031024725
2020-05-07,7,5,2020,745,73,Sweden,SE,SWE,10230185,Europe,78.18040436,88,1,7.28E-05,Social Distancing and Wearing Masks Enforced,4.109126651
2020-05-08,8,5,2020,784,80,Sweden,SE,SWE,10230185,Europe,78.40522923,39,7,7.66E-05,Social Distancing and Wearing Masks Enforced,4.140830143
2020-05-09,9,5,2020,700,60,Sweden,SE,SWE,10230185,Europe,78.65937908,-84,-20,6.84E-05,Social Distancing and Wearing Masks Enforced,4.070415071
2020-05-10,10,5,2020,509,68,Sweden,SE,SWE,10230185,Europe,77.87737954,-191,8,4.98E-05,Social Distancing and Wearing Masks Enforced,3.872437681
2020-05-11,11,5,2020,279,73,Sweden,SE,SWE,10230185,Europe,78.22927933,-230,5,2.73E-05,Social Distancing and Wearing Masks Enforced,3.498868604
2020-05-12,12,5,2020,455,65,Sweden,SE,SWE,10230185,Europe,78.02400445,176,-8,4.45E-05,Social Distancing and Wearing Masks Enforced,3.802754596
2020-05-13,13,5,2020,754,61,Sweden,SE,SWE,10230185,Europe,76.96830507,299,-4,7.37E-05,Social Distancing and Wearing Masks Enforced,4.116587733
2020-05-14,14,5,2020,698,50,Sweden,SE,SWE,10230185,Europe,77.085605,-56,-11,6.82E-05,Social Distancing and Wearing Masks Enforced,4.068637288
2020-05-15,15,5,2020,657,46,Sweden,SE,SWE,10230185,Europe,76.10810557,-41,-4,6.42E-05,Social Distancing and Wearing Masks Enforced,4.031024725
2020-05-16,16,5,2020,688,58,Sweden,SE,SWE,10230185,Europe,76.31338045,31,12,6.73E-05,Social Distancing and Wearing Masks Enforced,4.05967126
2020-05-17,17,5,2020,358,48,Sweden,SE,SWE,10230185,Europe,77.83827956,-330,-10,3.50E-05,Social Distancing and Wearing Masks Enforced,3.653780578
2020-05-18,18,5,2020,259,53,Sweden,SE,SWE,10230185,Europe,78.41500423,-99,5,2.53E-05,Social Distancing and Wearing Masks Enforced,3.4526514
2020-05-19,19,5,2020,430,59,Sweden,SE,SWE,10230185,Europe,78.39545424,171,6,4.20E-05,Social Distancing and Wearing Masks Enforced,3.767641586
2020-05-20,20,5,2020,666,41,Sweden,SE,SWE,10230185,Europe,77.9360295,236,-18,6.51E-05,Social Distancing and Wearing Masks Enforced,4.039478392
2020-05-21,21,5,2020,808,52,Sweden,SE,SWE,10230185,Europe,78.02400445,142,11,7.90E-05,Social Distancing and Wearing Masks Enforced,4.159565279
2020-05-22,22,5,2020,610,53,Sweden,SE,SWE,10230185,Europe,78.63982909,-198,1,5.96E-05,Social Distancing and Wearing Masks Enforced,3.984906101
2020-05-23,23,5,2020,532,56,Sweden,SE,SWE,10230185,Europe,76.93898009,-78,3,5.20E-05,Social Distancing and Wearing Masks Enforced,3.899897872
2020-05-24,24,5,2020,403,55,Sweden,SE,SWE,10230185,Europe,75.29678105,-129,-1,3.94E-05,Social Distancing and Wearing Masks Enforced,3.727348856
2020-05-25,25,5,2020,210,44,Sweden,SE,SWE,10230185,Europe,74.26063165,-193,-11,2.05E-05,Social Distancing and Wearing Masks Enforced,3.322344708
2020-05-26,26,5,2020,491,42,Sweden,SE,SWE,10230185,Europe,73.58615704,281,-2,4.80E-05,Social Distancing and Wearing Masks Enforced,3.850067207
2020-05-27,27,5,2020,746,28,Sweden,SE,SWE,10230185,Europe,73.93805684,255,-14,7.29E-05,Social Distancing and Wearing Masks Enforced,4.109960098
2020-05-28,28,5,2020,800,38,Sweden,SE,SWE,10230185,Europe,73.85985688,54,10,7.82E-05,Social Distancing and Wearing Masks Enforced,4.15338279
2020-05-29,29,5,2020,774,40,Sweden,SE,SWE,10230185,Europe,74.8569063,-26,2,7.57E-05,Social Distancing and Wearing Masks Enforced,4.132853975
2020-05-30,30,5,2020,773,41,Sweden,SE,SWE,10230185,Europe,76.00058063,-1,1,7.56E-05,Social Distancing and Wearing Masks Enforced,4.132050697
2020-05-31,31,5,2020,432,39,Sweden,SE,SWE,10230185,Europe,76.83145515,-341,-2,4.22E-05,Social Distancing and Wearing Masks Enforced,3.770524816
2020-06-01,1,6,2020,265,46,Sweden,SE,SWE,10230185,Europe,77.55480473,-167,7,2.59E-05,Social Distancing and Wearing Masks Enforced,3.466881066
2020-06-02,2,6,2020,648,39,Sweden,SE,SWE,10230185,Europe,77.61345469,383,-7,6.33E-05,Social Distancing and Wearing Masks Enforced,4.022454452
2020-06-03,3,6,2020,900,36,Sweden,SE,SWE,10230185,Europe,79.74440345,252,-3,8.80E-05,Social Distancing and Wearing Masks Enforced,4.226565505
2020-06-04,4,6,2020,1046,28,Sweden,SE,SWE,10230185,Europe,82.03175211,146,-8,0.000102246,Social Distancing and Wearing Masks Enforced,4.319973197
2020-06-05,5,6,2020,1039,43,Sweden,SE,SWE,10230185,Europe,84.35820076,-7,15,0.000101562,Social Distancing and Wearing Masks Enforced,4.315801149
2020-06-06,6,6,2020,1146,37,Sweden,SE,SWE,10230185,Europe,88.55167331,107,-6,0.000112021,Social Distancing and Wearing Masks Enforced,4.376703719
2020-06-07,7,6,2020,780,29,Sweden,SE,SWE,10230185,Europe,94.5535198,-366,-8,7.62E-05,Social Distancing and Wearing Masks Enforced,4.137651952
2020-06-08,8,6,2020,462,33,Sweden,SE,SWE,10230185,Europe,98.23869265,-318,4,4.52E-05,Social Distancing and Wearing Masks Enforced,3.81224081
2020-06-09,9,6,2020,677,38,Sweden,SE,SWE,10230185,Europe,100.7019912,215,5,6.62E-05,Social Distancing and Wearing Masks Enforced,4.049656854
2020-06-10,10,6,2020,937,33,Sweden,SE,SWE,10230185,Europe,102.5201402,260,-5,9.16E-05,Social Distancing and Wearing Masks Enforced,4.251598169
2020-06-11,11,6,2020,1437,40,Sweden,SE,SWE,10230185,Europe,104.3871641,500,7,0.000140467,Social Distancing and Wearing Masks Enforced,4.517299381
2020-06-12,12,6,2020,1293,35,Sweden,SE,SWE,10230185,Europe,110.6138354,-144,-5,0.000126391,Social Distancing and Wearing Masks Enforced,4.451691068
2020-06-13,13,6,2020,1329,29,Sweden,SE,SWE,10230185,Europe,115.6870575,36,-6,0.00012991,Social Distancing and Wearing Masks Enforced,4.468753969
2020-06-14,14,6,2020,1032,33,Sweden,SE,SWE,10230185,Europe,121.1219543,-297,4,0.000100878,Social Distancing and Wearing Masks Enforced,4.311600896
2020-06-15,15,6,2020,418,27,Sweden,SE,SWE,10230185,Europe,126.9869509,-614,-6,4.09E-05,Social Distancing and Wearing Masks Enforced,3.750055461
2020-06-16,16,6,2020,685,30,Sweden,SE,SWE,10230185,Europe,128.482525,267,3,6.70E-05,Social Distancing and Wearing Masks Enforced,4.056956027
2020-06-17,17,6,2020,1209,28,Sweden,SE,SWE,10230185,Europe,128.8441998,524,-2,0.00011818,Social Distancing and Wearing Masks Enforced,4.409955051
2020-06-18,18,6,2020,1457,32,Sweden,SE,SWE,10230185,Europe,131.864673,248,4,0.000142422,Social Distancing and Wearing Masks Enforced,4.525887423
2020-06-19,19,6,2020,1494,29,Sweden,SE,SWE,10230185,Europe,135.8821957,37,-3,0.000146038,Social Distancing and Wearing Masks Enforced,4.541468987
2020-06-20,20,6,2020,1209,30,Sweden,SE,SWE,10230185,Europe,140.3298181,-285,1,0.00011818,Social Distancing and Wearing Masks Enforced,4.409955051
2020-06-21,21,6,2020,698,29,Sweden,SE,SWE,10230185,Europe,140.9456427,-511,-1,6.82E-05,Social Distancing and Wearing Masks Enforced,4.068637288
2020-06-22,22,6,2020,321,22,Sweden,SE,SWE,10230185,Europe,140.1440932,-377,-7,3.14E-05,Social Distancing and Wearing Masks Enforced,3.585997993
2020-06-23,23,6,2020,800,20,Sweden,SE,SWE,10230185,Europe,138.765819,479,-2,7.82E-05,Social Distancing and Wearing Masks Enforced,4.15338279
2020-06-24,24,6,2020,1309,25,Sweden,SE,SWE,10230185,Europe,139.9681433,509,5,0.000127955,Social Distancing and Wearing Masks Enforced,4.459332485
2020-06-25,25,6,2020,1698,22,Sweden,SE,SWE,10230185,Europe,143.6044412,389,-3,0.000165979,Social Distancing and Wearing Masks Enforced,4.620996131
2020-06-26,26,6,2020,1279,23,Sweden,SE,SWE,10230185,Europe,146.1557147,-419,1,0.000125022,Social Distancing and Wearing Masks Enforced,4.444926857
2020-06-27,27,6,2020,1204,11,Sweden,SE,SWE,10230185,Europe,146.0188648,-75,-12,0.000117691,Social Distancing and Wearing Masks Enforced,4.407380099
2020-06-28,28,6,2020,755,14,Sweden,SE,SWE,10230185,Europe,144.7969905,-449,3,7.38E-05,Social Distancing and Wearing Masks Enforced,4.117411239
2020-06-29,29,6,2020,415,23,Sweden,SE,SWE,10230185,Europe,142.0893171,-340,9,4.06E-05,Social Distancing and Wearing Masks Enforced,3.74558004
2020-06-30,30,6,2020,727,16,Sweden,SE,SWE,10230185,Europe,142.0599921,312,-7,7.11E-05,Social Distancing and Wearing Masks Enforced,4.093930202
2020-07-01,1,7,2020,804,20,Sweden,SE,SWE,10230185,Europe,142.4705418,77,4,7.86E-05,Social Distancing and Wearing Masks Enforced,4.156481724
2020-07-02,2,7,2020,684,15,Sweden,SE,SWE,10230185,Europe,138.5116691,-120,-5,6.69E-05,Social Distancing and Wearing Masks Enforced,4.056048306
2020-07-03,3,7,2020,687,15,Sweden,SE,SWE,10230185,Europe,130.9555986,3,0,6.72E-05,Social Distancing and Wearing Masks Enforced,4.0587675
2020-07-04,4,7,2020,694,8,Sweden,SE,SWE,10230185,Europe,123.0671782,7,-7,6.78E-05,Social Distancing and Wearing Masks Enforced,4.065066387
2020-07-05,5,7,2020,364,15,Sweden,SE,SWE,10230185,Europe,118.0330561,-330,7,3.56E-05,Social Distancing and Wearing Masks Enforced,3.664107712
2020-07-06,6,7,2020,315,9,Sweden,SE,SWE,10230185,Europe,114.768208,-49,-6,3.08E-05,Social Distancing and Wearing Masks Enforced,3.574274344
2020-07-07,7,7,2020,251,15,Sweden,SE,SWE,10230185,Europe,114.709558,-64,6,2.45E-05,Social Distancing and Wearing Masks Enforced,3.43315694
2020-07-08,8,7,2020,278,12,Sweden,SE,SWE,10230185,Europe,109.3430862,27,-3,2.72E-05,Social Distancing and Wearing Masks Enforced,3.496637596
2020-07-09,9,7,2020,533,11,Sweden,SE,SWE,10230185,Europe,99.26506705,255,-1,5.21E-05,Social Distancing and Wearing Masks Enforced,3.901064698
2020-07-10,10,7,2020,334,15,Sweden,SE,SWE,10230185,Europe,87.8771987,-199,4,3.26E-05,Social Distancing and Wearing Masks Enforced,3.610664909
2020-07-11,11,7,2020,369,14,Sweden,SE,SWE,10230185,Europe,78.63982909,35,-1,3.61E-05,Social Distancing and Wearing Masks Enforced,3.672584446
2020-07-12,12,7,2020,308,10,Sweden,SE,SWE,10230185,Europe,70.47770886,-61,-4,3.01E-05,Social Distancing and Wearing Masks Enforced,3.560311174
2020-07-13,13,7,2020,106,8,Sweden,SE,SWE,10230185,Europe,66.10828641,-202,-2,1.04E-05,Social Distancing and Wearing Masks Enforced,2.897557624
2020-07-14,14,7,2020,170,12,Sweden,SE,SWE,10230185,Europe,63.08781317,64,4,1.66E-05,Social Distancing and Wearing Masks Enforced,3.191050986
2020-07-15,15,7,2020,312,8,Sweden,SE,SWE,10230185,Europe,57.64314135,142,-4,3.05E-05,Social Distancing and Wearing Masks Enforced,3.56832851
2020-07-16,16,7,2020,287,6,Sweden,SE,SWE,10230185,Europe,52.83384416,-25,-2,2.81E-05,Social Distancing and Wearing Masks Enforced,3.516434012
2020-07-17,17,7,2020,268,6,Sweden,SE,SWE,10230185,Europe,48.95317142,-19,0,2.62E-05,Social Distancing and Wearing Masks Enforced,3.47387553
2020-07-18,18,7,2020,284,7,Sweden,SE,SWE,10230185,Europe,44.85744881,16,1,2.78E-05,Social Distancing and Wearing Masks Enforced,3.509905039
2020-07-19,19,7,2020,191,11,Sweden,SE,SWE,10230185,Europe,40.84970115,-93,4,1.87E-05,Social Distancing and Wearing Masks Enforced,3.263420967
2020-07-20,20,7,2020,110,7,Sweden,SE,SWE,10230185,Europe,39.15862714,-81,-4,1.08E-05,Social Distancing and Wearing Masks Enforced,2.92057266
2020-07-21,21,7,2020,131,6,Sweden,SE,SWE,10230185,Europe,37.15475331,21,-1,1.28E-05,Social Distancing and Wearing Masks Enforced,3.02913041
2020-07-22,22,7,2020,226,7,Sweden,SE,SWE,10230185,Europe,35.981754,95,1,2.21E-05,Social Distancing and Wearing Masks Enforced,3.367967759
2020-07-23,23,7,2020,297,6,Sweden,SE,SWE,10230185,Europe,35.47345429,71,-1,2.90E-05,Social Distancing and Wearing Masks Enforced,3.537714686
2020-07-24,24,7,2020,220,5,Sweden,SE,SWE,10230185,Europe,33.16655564,-77,-1,2.15E-05,Social Distancing and Wearing Masks Enforced,3.351249219
2020-07-25,25,7,2020,262,3,Sweden,SE,SWE,10230185,Europe,32.05220629,42,-2,2.56E-05,Social Distancing and Wearing Masks Enforced,3.459806968
2020-07-26,26,7,2020,138,1,Sweden,SE,SWE,10230185,Europe,31.0062819,-124,-2,1.35E-05,Social Distancing and Wearing Masks Enforced,3.061474846
2020-07-27,27,7,2020,42,2,Sweden,SE,SWE,10230185,Europe,29.34453287,-96,1,4.11E-06,Social Distancing and Wearing Masks Enforced,2.322344708
2020-07-28,28,7,2020,71,6,Sweden,SE,SWE,10230185,Europe,28.71893324,29,4,6.94E-06,Social Distancing and Wearing Masks Enforced,2.648551922
2020-07-29,29,7,2020,283,4,Sweden,SE,SWE,10230185,Europe,27.7512088,212,-2,2.77E-05,Social Distancing and Wearing Masks Enforced,3.507713379
2020-07-30,30,7,2020,301,1,Sweden,SE,SWE,10230185,Europe,27.46773397,18,-3,2.94E-05,Social Distancing and Wearing Masks Enforced,3.546026983
2020-07-31,31,7,2020,302,0,Sweden,SE,SWE,10230185,Europe,27.60458389,1,-1,2.95E-05,Social Distancing and Wearing Masks Enforced,3.548087797
2020-08-01,1,8,2020,258,2,Sweden,SE,SWE,10230185,Europe,27.93693369,-44,2,2.52E-05,Social Distancing and Wearing Masks Enforced,3.45024778
2020-08-02,2,8,2020,303,2,Sweden,SE,SWE,10230185,Europe,27.68278384,45,0,2.96E-05,Social Distancing and Wearing Masks Enforced,3.550141799
2020-08-03,3,8,2020,38,3,Sweden,SE,SWE,10230185,Europe,28.7775832,-265,1,3.71E-06,Social Distancing and Wearing Masks Enforced,2.260159359
2020-08-04,4,8,2020,165,4,Sweden,SE,SWE,10230185,Europe,28.07378361,127,1,1.61E-05,Social Distancing and Wearing Masks Enforced,3.172502297
2020-08-05,5,8,2020,333,2,Sweden,SE,SWE,10230185,Europe,28.40613342,168,-2,3.26E-05,Social Distancing and Wearing Masks Enforced,3.608801834
2020-08-06,6,8,2020,425,1,Sweden,SE,SWE,10230185,Europe,29.45205781,92,-1,4.15E-05,Social Distancing and Wearing Masks Enforced,3.760374428
2020-08-07,7,8,2020,378,4,Sweden,SE,SWE,10230185,Europe,30.70325708,-47,3,3.69E-05,Social Distancing and Wearing Masks Enforced,3.687557097
2020-08-08,8,8,2020,380,2,Sweden,SE,SWE,10230185,Europe,32.24770618,2,-2,3.71E-05,Social Distancing and Wearing Masks Enforced,3.690835917
2020-08-09,9,8,2020,260,1,Sweden,SE,SWE,10230185,Europe,33.4011555,-120,-1,2.54E-05,Social Distancing and Wearing Masks Enforced,3.455045757
2020-08-10,10,8,2020,73,4,Sweden,SE,SWE,10230185,Europe,34.59370481,-187,3,7.14E-06,Social Distancing and Wearing Masks Enforced,2.665812336
2020-08-11,11,8,2020,196,2,Sweden,SE,SWE,10230185,Europe,34.89672963,123,-2,1.92E-05,Social Distancing and Wearing Masks Enforced,3.279477026
2020-08-12,12,8,2020,417,4,Sweden,SE,SWE,10230185,Europe,36.11860392,221,2,4.08E-05,Social Distancing and Wearing Masks Enforced,3.748567233
2020-08-13,13,8,2020,443,3,Sweden,SE,SWE,10230185,Europe,37.42845315,26,-1,4.33E-05,Social Distancing and Wearing Masks Enforced,3.786147774
2020-08-14,14,8,2020,363,5,Sweden,SE,SWE,10230185,Europe,38.81650234,-80,2,3.55E-05,Social Distancing and Wearing Masks Enforced,3.662398399
2020-08-15,15,8,2020,344,1,Sweden,SE,SWE,10230185,Europe,39.41277699,-19,-4,3.36E-05,Social Distancing and Wearing Masks Enforced,3.628994702
2020-08-16,16,8,2020,226,1,Sweden,SE,SWE,10230185,Europe,40.2534265,-118,0,2.21E-05,Social Distancing and Wearing Masks Enforced,3.367967759
2020-08-17,17,8,2020,63,0,Sweden,SE,SWE,10230185,Europe,39.50075194,-163,-1,6.16E-06,Social Distancing and Wearing Masks Enforced,2.574274344
2020-08-18,18,8,2020,174,3,Sweden,SE,SWE,10230185,Europe,39.7451268,111,3,1.70E-05,Social Distancing and Wearing Masks Enforced,3.205501287
2020-08-19,19,8,2020,314,4,Sweden,SE,SWE,10230185,Europe,39.83310175,140,1,3.07E-05,Social Distancing and Wearing Masks Enforced,3.572298715
2020-08-20,20,8,2020,351,1,Sweden,SE,SWE,10230185,Europe,39.64737686,37,-3,3.43E-05,Social Distancing and Wearing Masks Enforced,3.641511225
2020-08-21,21,8,2020,333,2,Sweden,SE,SWE,10230185,Europe,38.92402728,-18,1,3.26E-05,Social Distancing and Wearing Masks Enforced,3.608801834
2020-08-22,22,8,2020,298,5,Sweden,SE,SWE,10230185,Europe,38.48415253,-35,3,2.91E-05,Social Distancing and Wearing Masks Enforced,3.539803209
2020-08-23,23,8,2020,160,1,Sweden,SE,SWE,10230185,Europe,37.682603,-138,-4,1.56E-05,Social Distancing and Wearing Masks Enforced,3.15338279
2020-08-24,24,8,2020,57,3,Sweden,SE,SWE,10230185,Europe,36.70510357,-103,2,5.57E-06,Social Distancing and Wearing Masks Enforced,2.512088995
2020-08-25,25,8,2020,174,1,Sweden,SE,SWE,10230185,Europe,36.54870366,117,-2,1.70E-05,Social Distancing and Wearing Masks Enforced,3.205501287
2020-08-26,26,8,2020,222,1,Sweden,SE,SWE,10230185,Europe,36.33365379,48,0,2.17E-05,Social Distancing and Wearing Masks Enforced,3.356872198
2020-08-27,27,8,2020,244,2,Sweden,SE,SWE,10230185,Europe,34.4275299,22,1,2.39E-05,Social Distancing and Wearing Masks Enforced,3.41558266
2020-08-28,28,8,2020,202,1,Sweden,SE,SWE,10230185,Europe,32.48230604,-42,-1,1.97E-05,Social Distancing and Wearing Masks Enforced,3.298212162
2020-08-29,29,8,2020,179,1,Sweden,SE,SWE,10230185,Europe,30.90853196,-23,0,1.75E-05,Social Distancing and Wearing Masks Enforced,3.22310402
2020-08-30,30,8,2020,131,1,Sweden,SE,SWE,10230185,Europe,29.2956579,-48,0,1.28E-05,Social Distancing and Wearing Masks Enforced,3.02913041
2020-08-31,31,8,2020,48,3,Sweden,SE,SWE,10230185,Europe,28.36703344,-83,2,4.69E-06,Social Distancing and Wearing Masks Enforced,2.405312427
2020-09-01,1,9,2020,162,2,Sweden,SE,SWE,10230185,Europe,28.22040853,114,-1,1.58E-05,Social Distancing and Wearing Masks Enforced,3.161101336
2020-09-02,2,9,2020,171,3,Sweden,SE,SWE,10230185,Europe,28.10310859,9,1,1.67E-05,Social Distancing and Wearing Masks Enforced,3.194695189
2020-09-03,3,9,2020,213,2,Sweden,SE,SWE,10230185,Europe,26.70528441,42,-1,2.08E-05,Social Distancing and Wearing Masks Enforced,3.331158117
2020-09-04,4,9,2020,286,2,Sweden,SE,SWE,10230185,Europe,25.3563352,73,0,2.80E-05,Social Distancing and Wearing Masks Enforced,3.514265302
2020-09-05,5,9,2020,262,0,Sweden,SE,SWE,10230185,Europe,24.89691047,-24,-2,2.56E-05,Social Distancing and Wearing Masks Enforced,3.459806968
2020-09-06,6,9,2020,171,0,Sweden,SE,SWE,10230185,Europe,24.54501067,-91,0,1.67E-05,Social Distancing and Wearing Masks Enforced,3.194695189
2020-09-07,7,9,2020,67,3,Sweden,SE,SWE,10230185,Europe,24.65253561,-104,3,6.55E-06,Social Distancing and Wearing Masks Enforced,2.612522414
2020-09-08,8,9,2020,185,1,Sweden,SE,SWE,10230185,Europe,24.75028555,118,-2,1.81E-05,Social Distancing and Wearing Masks Enforced,3.243589445
2020-09-09,9,9,2020,236,1,Sweden,SE,SWE,10230185,Europe,24.85781049,51,0,2.31E-05,Social Distancing and Wearing Masks Enforced,3.394869577
2020-09-10,10,9,2020,314,2,Sweden,SE,SWE,10230185,Europe,24.99466041,78,1,3.07E-05,Social Distancing and Wearing Masks Enforced,3.572298715
2020-09-11,11,9,2020,254,2,Sweden,SE,SWE,10230185,Europe,25.67891001,-60,0,2.48E-05,Social Distancing and Wearing Masks Enforced,3.440539224
2020-09-12,12,9,2020,291,4,Sweden,SE,SWE,10230185,Europe,26.18720971,37,2,2.84E-05,Social Distancing and Wearing Masks Enforced,3.525033941
2020-09-13,13,9,2020,206,1,Sweden,SE,SWE,10230185,Europe,27.28200907,-85,-3,2.01E-05,Social Distancing and Wearing Masks Enforced,3.310395591
2020-09-14,14,9,2020,106,2,Sweden,SE,SWE,10230185,Europe,28.01513365,-100,1,1.04E-05,Social Distancing and Wearing Masks Enforced,2.897557624
2020-09-15,15,9,2020,220,2,Sweden,SE,SWE,10230185,Europe,28.58208332,114,0,2.15E-05,Social Distancing and Wearing Masks Enforced,3.351249219
2020-09-16,16,9,2020,292,1,Sweden,SE,SWE,10230185,Europe,29.14903298,72,-1,2.85E-05,Social Distancing and Wearing Masks Enforced,3.527165452
2020-09-17,17,9,2020,330,2,Sweden,SE,SWE,10230185,Europe,30.33180729,38,1,3.23E-05,Social Distancing and Wearing Masks Enforced,3.603178855
2020-09-18,18,9,2020,389,1,Sweden,SE,SWE,10230185,Europe,31.47548163,59,-1,3.80E-05,Social Distancing and Wearing Masks Enforced,3.705380181
2020-09-19,19,9,2020,437,1,Sweden,SE,SWE,10230185,Europe,32.48230604,48,0,4.27E-05,Social Distancing and Wearing Masks Enforced,3.777674894
2020-09-20,20,9,2020,279,1,Sweden,SE,SWE,10230185,Europe,34.19293004,-158,0,2.73E-05,Social Distancing and Wearing Masks Enforced,3.498868604
2020-09-21,21,9,2020,133,4,Sweden,SE,SWE,10230185,Europe,35.24862942,-146,3,1.30E-05,Social Distancing and Wearing Masks Enforced,3.038544756
2020-09-22,22,9,2020,266,2,Sweden,SE,SWE,10230185,Europe,35.89377905,133,-2,2.60E-05,Social Distancing and Wearing Masks Enforced,3.469221314
2020-09-23,23,9,2020,438,1,Sweden,SE,SWE,10230185,Europe,36.68555358,172,-1,4.28E-05,Social Distancing and Wearing Masks Enforced,3.779095089
2020-09-24,24,9,2020,553,0,Sweden,SE,SWE,10230185,Europe,38.66010243,115,-1,5.41E-05,Social Distancing and Wearing Masks Enforced,3.923952551
2020-09-25,25,9,2020,540,1,Sweden,SE,SWE,10230185,Europe,40.99632607,-13,1,5.28E-05,Social Distancing and Wearing Masks Enforced,3.9091717
2020-09-26,26,9,2020,630,4,Sweden,SE,SWE,10230185,Europe,43.79197444,90,3,6.16E-05,Social Distancing and Wearing Masks Enforced,4.004950902
2020-09-27,27,9,2020,325,2,Sweden,SE,SWE,10230185,Europe,47.1056975,-305,-2,3.18E-05,Social Distancing and Wearing Masks Enforced,3.593692641
2020-09-28,28,9,2020,167,1,Sweden,SE,SWE,10230185,Europe,48.26892182,-158,-1,1.63E-05,Social Distancing and Wearing Masks Enforced,3.179988351
2020-09-29,29,9,2020,378,1,Sweden,SE,SWE,10230185,Europe,48.86519647,211,0,3.69E-05,Social Distancing and Wearing Masks Enforced,3.687557097
2020-09-30,30,9,2020,613,2,Sweden,SE,SWE,10230185,Europe,50.40964557,235,1,5.99E-05,Social Distancing and Wearing Masks Enforced,3.987954357
2020-10-01,1,10,2020,689,4,Sweden,SE,SWE,10230185,Europe,53.54741874,76,2,6.73E-05,Social Distancing and Wearing Masks Enforced,4.060573707
2020-10-02,2,10,2020,633,1,Sweden,SE,SWE,10230185,Europe,57.05664169,-56,-3,6.19E-05,Social Distancing and Wearing Masks Enforced,4.007902618
2020-10-03,3,10,2020,712,3,Sweden,SE,SWE,10230185,Europe,59.4417403,79,2,6.96E-05,Social Distancing and Wearing Masks Enforced,4.080976259
2020-10-04,4,10,2020,461,3,Sweden,SE,SWE,10230185,Europe,62.12986373,-251,0,4.51E-05,Social Distancing and Wearing Masks Enforced,3.810894472
2020-10-05,5,10,2020,156,3,Sweden,SE,SWE,10230185,Europe,63.90891269,-305,0,1.52E-05,Social Distancing and Wearing Masks Enforced,3.137651952
2020-10-06,6,10,2020,374,2,Sweden,SE,SWE,10230185,Europe,64.13373756,218,-1,3.66E-05,Social Distancing and Wearing Masks Enforced,3.680947088
2020-10-07,7,10,2020,786,4,Sweden,SE,SWE,10230185,Europe,65.18943695,412,2,7.68E-05,Social Distancing and Wearing Masks Enforced,4.142413162
2020-10-08,8,10,2020,831,3,Sweden,SE,SWE,10230185,Europe,68.59113496,45,-1,8.12E-05,Social Distancing and Wearing Masks Enforced,4.177004744
2020-10-09,9,10,2020,834,1,Sweden,SE,SWE,10230185,Europe,71.30858337,3,-2,8.15E-05,Social Distancing and Wearing Masks Enforced,4.179243791
2020-10-10,10,10,2020,783,5,Sweden,SE,SWE,10230185,Europe,74.1824317,-51,4,7.65E-05,Social Distancing and Wearing Masks Enforced,4.140037118
2020-10-11,11,10,2020,509,5,Sweden,SE,SWE,10230185,Europe,75.67800582,-274,0,4.98E-05,Social Distancing and Wearing Masks Enforced,3.872437681
2020-10-12,12,10,2020,161,2,Sweden,SE,SWE,10230185,Europe,77.47660477,-348,-3,1.57E-05,Social Distancing and Wearing Masks Enforced,3.157254049
2020-10-13,13,10,2020,637,3,Sweden,SE,SWE,10230185,Europe,77.41795481,476,1,6.23E-05,Social Distancing and Wearing Masks Enforced,4.011816551
2020-10-14,14,10,2020,916,1,Sweden,SE,SWE,10230185,Europe,79.94967833,279,-2,8.95E-05,Social Distancing and Wearing Masks Enforced,4.237514422
2020-10-15,15,10,2020,968,2,Sweden,SE,SWE,10230185,Europe,82.9115016,52,1,9.46E-05,Social Distancing and Wearing Masks Enforced,4.271821879
2020-10-16,16,10,2020,902,3,Sweden,SE,SWE,10230185,Europe,85.63872501,-66,1,8.82E-05,Social Distancing and Wearing Masks Enforced,4.227944718
2020-10-17,17,10,2020,1179,2,Sweden,SE,SWE,10230185,Europe,88.26819847,277,-1,0.000115247,Social Distancing and Wearing Masks Enforced,4.394342799
2020-10-18,18,10,2020,697,4,Sweden,SE,SWE,10230185,Europe,92.83312081,-482,2,6.81E-05,Social Distancing and Wearing Masks Enforced,4.067746485
2020-10-19,19,10,2020,321,1,Sweden,SE,SWE,10230185,Europe,95.14001946,-376,-3,3.14E-05,Social Distancing and Wearing Masks Enforced,3.585997993
2020-10-20,20,10,2020,771,4,Sweden,SE,SWE,10230185,Europe,96.75289352,450,3,7.54E-05,Social Distancing and Wearing Masks Enforced,4.130441021
2020-10-21,21,10,2020,1290,4,Sweden,SE,SWE,10230185,Europe,100.6335663,519,0,0.000126097,Social Distancing and Wearing Masks Enforced,4.45024778
2020-10-22,22,10,2020,1570,3,Sweden,SE,SWE,10230185,Europe,105.5601634,280,-1,0.000153467,Social Distancing and Wearing Masks Enforced,4.572298715
2020-10-23,23,10,2020,1666,9,Sweden,SE,SWE,10230185,Europe,112.7838842,96,6,0.000162851,Social Distancing and Wearing Masks Enforced,4.609174896
2020-10-24,24,10,2020,1868,7,Sweden,SE,SWE,10230185,Europe,120.9166794,202,-2,0.000182597,Social Distancing and Wearing Masks Enforced,4.680282203
2020-10-25,25,10,2020,1477,8,Sweden,SE,SWE,10230185,Europe,131.5225482,-391,1,0.000144377,Social Distancing and Wearing Masks Enforced,4.534358378
2020-10-26,26,10,2020,514,8,Sweden,SE,SWE,10230185,Europe,140.9847427,-963,0,5.02E-05,Social Distancing and Wearing Masks Enforced,3.878511384
2020-10-27,27,10,2020,1068,11,Sweden,SE,SWE,10230185,Europe,144.4353157,554,3,0.000104397,Social Distancing and Wearing Masks Enforced,4.332905896
2020-10-28,28,10,2020,2415,9,Sweden,SE,SWE,10230185,Europe,148.6483382,1347,-2,0.000236066,Social Distancing and Wearing Masks Enforced,4.839860243
2020-10-29,29,10,2020,3390,9,Sweden,SE,SWE,10230185,Europe,163.3010547,975,0,0.000331372,Social Distancing and Wearing Masks Enforced,5.050573954
2020-10-30,30,10,2020,3262,9,Sweden,SE,SWE,10230185,Europe,186.9760909,-128,0,0.00031886,Social Distancing and Wearing Masks Enforced,5.026659134
2020-10-31,31,10,2020,4055,9,Sweden,SE,SWE,10230185,Europe,210.0450774,793,0,0.000396376,Social Distancing and Wearing Masks Enforced,5.161867943
2020-11-01,1,11,2020,2987,13,Sweden,SE,SWE,10230185,Europe,238.157961,-1068,4,0.000291979,Social Distancing and Wearing Masks Enforced,4.971937567
2020-11-02,2,11,2020,1297,22,Sweden,SE,SWE,10230185,Europe,260.5426979,-1690,9,0.000126782,Social Distancing and Wearing Masks Enforced,4.45361025
2020-11-03,3,11,2020,1570,20,Sweden,SE,SWE,10230185,Europe,270.0830923,273,-2,0.000153467,Social Distancing and Wearing Masks Enforced,4.572298715
2020-11-04,4,11,2020,3608,19,Sweden,SE,SWE,10230185,Europe,277.8933128,2038,-1,0.000352682,Social Distancing and Wearing Masks Enforced,5.089297834
2020-11-05,5,11,2020,4483,21,Sweden,SE,SWE,10230185,Europe,300.5517496,875,2,0.000438213,Social Distancing and Wearing Masks Enforced,5.224213795
2020-11-06,6,11,2020,4744,22,Sweden,SE,SWE,10230185,Europe,329.0263079,261,1,0.000463726,Social Distancing and Wearing Masks Enforced,5.259374018
2020-11-07,7,11,2020,4453,25,Sweden,SE,SWE,10230185,Europe,359.1137404,-291,3,0.00043528,Social Distancing and Wearing Masks Enforced,5.220041879
2020-11-08,8,11,2020,4452,26,Sweden,SE,SWE,10230185,Europe,384.3821006,-1,1,0.000435183,Social Distancing and Wearing Masks Enforced,5.219902332
2020-11-09,9,11,2020,2097,22,Sweden,SE,SWE,10230185,Europe,413.4627086,-2355,-4,0.000204982,Social Distancing and Wearing Masks Enforced,4.75213301
2020-11-10,10,11,2020,3725,35,Sweden,SE,SWE,10230185,Europe,428.9365246,1628,13,0.000364119,Social Distancing and Wearing Masks Enforced,5.109126651
2020-11-11,11,11,2020,4498,35,Sweden,SE,SWE,10230185,Europe,454.9086845,773,0,0.000439679,Social Distancing and Wearing Masks Enforced,5.226289295
2020-11-12,12,11,2020,5709,27,Sweden,SE,SWE,10230185,Europe,475.2699976,1211,-8,0.000558054,Social Distancing and Wearing Masks Enforced,5.374422393
2020-11-13,13,11,2020,5565,28,Sweden,SE,SWE,10230185,Europe,497.9382093,-144,1,0.000543978,Social Distancing and Wearing Masks Enforced,5.358549216
2020-11-14,14,11,2020,6730,32,Sweden,SE,SWE,10230185,Europe,520.4500212,1165,4,0.000657857,Social Distancing and Wearing Masks Enforced,5.476651416
2020-11-15,15,11,2020,3513,37,Sweden,SE,SWE,10230185,Europe,546.5981309,-3217,5,0.000343396,Social Distancing and Wearing Masks Enforced,5.072718611
2020-11-16,16,11,2020,1582,39,Sweden,SE,SWE,10230185,Europe,551.7397779,-1931,2,0.00015464,Social Distancing and Wearing Masks Enforced,4.577029714
2020-11-17,17,11,2020,2544,36,Sweden,SE,SWE,10230185,Europe,554.5256513,962,-3,0.000248676,Social Distancing and Wearing Masks Enforced,4.872193493
2020-11-18,18,11,2020,4460,39,Sweden,SE,SWE,10230185,Europe,564.0464957,1916,3,0.000435965,Social Distancing and Wearing Masks Enforced,5.221017835
2020-11-19,19,11,2020,4961,50,Sweden,SE,SWE,10230185,Europe,572.3747909,501,11,0.000484937,Social Distancing and Wearing Masks Enforced,5.287164262
2020-11-20,20,11,2020,7622,44,Sweden,SE,SWE,10230185,Europe,577.0472382,2661,-6,0.00074505,Social Distancing and Wearing Masks Enforced,5.553985036
2020-11-21,21,11,2020,5459,42,Sweden,SE,SWE,10230185,Europe,605.1796717,-2163,-2,0.000533617,Social Distancing and Wearing Masks Enforced,5.346600099
2020-11-22,22,11,2020,4493,48,Sweden,SE,SWE,10230185,Europe,615.013316,-966,6,0.00043919,Social Distancing and Wearing Masks Enforced,5.225598232
2020-11-23,23,11,2020,2422,56,Sweden,SE,SWE,10230185,Europe,615.4140908,-2071,8,0.00023675,Social Distancing and Wearing Masks Enforced,4.841658609
2020-11-24,24,11,2020,3875,53,Sweden,SE,SWE,10230185,Europe,618.5909639,1453,-3,0.000378781,Social Distancing and Wearing Masks Enforced,5.133656215
2020-11-25,25,11,2020,5675,65,Sweden,SE,SWE,10230185,Europe,620.057213,1800,12,0.000554731,Social Distancing and Wearing Masks Enforced,5.370710964
2020-11-26,26,11,2020,6064,57,Sweden,SE,SWE,10230185,Europe,631.5623813,389,-8,0.000592756,Social Distancing and Wearing Masks Enforced,5.411904902
2020-11-27,27,11,2020,6900,42,Sweden,SE,SWE,10230185,Europe,635.0325043,836,-15,0.000674475,Social Distancing and Wearing Masks Enforced,5.492151404
2020-11-28,28,11,2020,6463,33,Sweden,SE,SWE,10230185,Europe,648.0821217,-437,-9,0.000631758,Social Distancing and Wearing Masks Enforced,5.451498823
2020-11-29,29,11,2020,3825,28,Sweden,SE,SWE,10230185,Europe,645.4721982,-2638,-5,0.000373894,Social Distancing and Wearing Masks Enforced,5.125586817
2020-11-30,30,11,2020,2754,28,Sweden,SE,SWE,10230185,Europe,648.5219964,-1071,0,0.000269203,Social Distancing and Wearing Masks Enforced,4.921475764
2020-12-01,1,12,2020,3487,37,Sweden,SE,SWE,10230185,Europe,659.9782897,733,9,0.000340854,Social Distancing and Wearing Masks Enforced,5.068102959
2020-12-02,2,12,2020,5812,27,Sweden,SE,SWE,10230185,Europe,669.1961094,2325,-10,0.000568123,Social Distancing and Wearing Masks Enforced,5.385532401
2020-12-03,3,12,2020,6548,20,Sweden,SE,SWE,10230185,Europe,682.4119016,736,-7,0.000640067,Social Distancing and Wearing Masks Enforced,5.459617218
2020-12-04,4,12,2020,6988,16,Sweden,SE,SWE,10230185,Europe,697.9248176,440,-4,0.000683077,Social Distancing and Wearing Masks Enforced,5.50002557
2020-12-05,5,12,2020,7343,12,Sweden,SE,SWE,10230185,Europe,691.7274712,355,-4,0.000717778,Social Distancing and Wearing Masks Enforced,5.530814633
2020-12-06,6,12,2020,4863,10,Sweden,SE,SWE,10230185,Europe,710.1435605,-2480,-2,0.000475358,Social Distancing and Wearing Masks Enforced,5.27476751
2020-12-07,7,12,2020,1800,16,Sweden,SE,SWE,10230185,Europe,713.7603083,-3063,6,0.00017595,Social Distancing and Wearing Masks Enforced,4.657242063
2020-12-08,8,12,2020,3319,2,Sweden,SE,SWE,10230185,Europe,707.6802619,1519,-14,0.000324432,Social Distancing and Wearing Masks Enforced,5.037422537
2020-12-09,9,12,2020,0,0,Sweden,SE,SWE,10230185,Europe,702.2453651,-3319,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-09,9,12,2020,12281,599,United_Kingdom,UK,GBR,66647112,Europe,317.2635598,0.000184269,#REF!,#REF!,Social Distancing and Wearing Masks Enforced,5.85037084
2020-12-08,8,12,2020,14718,189,United_Kingdom,UK,GBR,66647112,Europe,315.7901276,0.000220835,2437,-410,Social Distancing and Wearing Masks Enforced,5.962843574
2020-12-07,7,12,2020,17271,231,United_Kingdom,UK,GBR,66647112,Europe,316.8884497,0.000259141,2553,42,Social Distancing and Wearing Masks Enforced,6.062230794
2020-12-06,6,12,2020,15539,397,United_Kingdom,UK,GBR,66647112,Europe,318.9755619,0.000233153,-1732,166,Social Distancing and Wearing Masks Enforced,5.996570726
2020-12-05,5,12,2020,16298,504,United_Kingdom,UK,GBR,66647112,Europe,325.4814702,0.000244542,759,107,Social Distancing and Wearing Masks Enforced,6.026201822
2020-12-04,4,12,2020,14878,414,United_Kingdom,UK,GBR,66647112,Europe,331.4142104,0.000223235,-1420,-90,Social Distancing and Wearing Masks Enforced,5.969561681
2020-12-03,3,12,2020,16170,648,United_Kingdom,UK,GBR,66647112,Europe,343.4732476,0.000242621,1292,234,Social Distancing and Wearing Masks Enforced,6.021302765
2020-12-02,2,12,2020,13429,603,United_Kingdom,UK,GBR,66647112,Europe,348.6332611,0.000201494,-2741,-45,Lockdown,5.905895315
2020-12-01,1,12,2020,12330,203,United_Kingdom,UK,GBR,66647112,Europe,358.5691755,0.000185004,-1099,-400,Lockdown,5.852844974
2020-11-30,30,11,2020,12155,215,United_Kingdom,UK,GBR,66647112,Europe,372.122651,0.000182378,-175,12,Lockdown,5.843963171
2020-11-29,29,11,2020,15871,479,United_Kingdom,UK,GBR,66647112,Europe,391.3387875,0.000238135,3716,264,Lockdown,6.00970609
2020-11-28,28,11,2020,14739,520,United_Kingdom,UK,GBR,66647112,Europe,407.8271239,0.00022115,-1132,41,Lockdown,5.963729478
2020-11-27,27,11,2020,17555,498,United_Kingdom,UK,GBR,66647112,Europe,426.6756525,0.000263402,2816,-22,Lockdown,6.072364776
2020-11-26,26,11,2020,18213,695,United_Kingdom,UK,GBR,66647112,Europe,450.5551568,0.000273275,658,197,Lockdown,6.095227923
2020-11-25,25,11,2020,11299,608,United_Kingdom,UK,GBR,66647112,Europe,457.6627416,0.000169535,-6914,-87,Lockdown,5.798589329
2020-11-24,24,11,2020,15450,479,United_Kingdom,UK,GBR,66647112,Europe,471.3362524,0.000231818,4151,-129,Lockdown,5.993001785
2020-11-23,23,11,2020,18662,125,United_Kingdom,UK,GBR,66647112,Europe,480.188849,0.000280012,3212,-354,Lockdown,6.110359756
2020-11-22,22,11,2020,19875,340,United_Kingdom,UK,GBR,66647112,Europe,483.0546896,0.000298212,1213,215,Lockdown,6.149487261
2020-11-21,21,11,2020,20252,511,United_Kingdom,UK,GBR,66647112,Europe,490.6799262,0.000303869,377,171,Lockdown,6.161162699
2020-11-20,20,11,2020,22915,501,United_Kingdom,UK,GBR,66647112,Europe,495.233762,0.000343826,2663,-10,Lockdown,6.237921276
2020-11-19,19,11,2020,19609,529,United_Kingdom,UK,GBR,66647112,Europe,497.0688002,0.000294221,-3306,28,Lockdown,6.141115384
2020-11-18,18,11,2020,20051,598,United_Kingdom,UK,GBR,66647112,Europe,505.4232508,0.000300853,442,69,Lockdown,6.154965178
2020-11-17,17,11,2020,21363,213,United_Kingdom,UK,GBR,66647112,Europe,505.3737362,0.000320539,1312,-385,Lockdown,6.194346272
2020-11-16,16,11,2020,24962,168,United_Kingdom,UK,GBR,66647112,Europe,501.7531742,0.00037454,3599,-45,Lockdown,6.291084527
2020-11-15,15,11,2020,26860,462,United_Kingdom,UK,GBR,66647112,Europe,499.1904225,0.000403018,1898,294,Lockdown,6.336618139
2020-11-14,14,11,2020,27301,376,United_Kingdom,UK,GBR,66647112,Europe,491.7707462,0.000409635,441,-86,Lockdown,6.346736666
2020-11-13,13,11,2020,33470,563,United_Kingdom,UK,GBR,66647112,Europe,487.4254716,0.000502197,6169,187,Lockdown,6.473318861
2020-11-12,12,11,2020,22950,595,United_Kingdom,UK,GBR,66647112,Europe,471.8133923,0.000344351,-10520,32,Lockdown,6.238869569
2020-11-11,11,11,2020,20412,532,United_Kingdom,UK,GBR,66647112,Europe,474.4391625,0.00030627,-2538,-63,Lockdown,6.166052238
2020-11-10,10,11,2020,21350,194,United_Kingdom,UK,GBR,66647112,Europe,478.1497509,0.000320344,938,-338,Lockdown,6.193968057
2020-11-09,9,11,2020,20572,156,United_Kingdom,UK,GBR,66647112,Europe,477.4595484,0.000308671,-778,-38,Lockdown,6.170903599
2020-11-08,8,11,2020,24957,413,United_Kingdom,UK,GBR,66647112,Europe,476.2862043,0.000374465,4385,257,Lockdown,6.290960058
2020-11-07,7,11,2020,23287,355,United_Kingdom,UK,GBR,66647112,Europe,473.3678483,0.000349407,-1670,-58,Lockdown,6.247926973
2020-11-06,6,11,2020,24138,378,United_Kingdom,UK,GBR,66647112,Europe,469.2326353,0.000362176,851,23,Lockdown,6.270227987
2020-11-05,5,11,2020,25177,492,United_Kingdom,UK,GBR,66647112,Europe,464.881359,0.000377766,1039,114,Lockdown,6.296413226
2020-11-04,4,11,2020,20018,397,United_Kingdom,UK,GBR,66647112,Europe,467.1470236,0.000300358,-5159,-95,Social Distancing and Wearing Masks Enforced,6.15394174
2020-11-03,3,11,2020,18950,136,United_Kingdom,UK,GBR,66647112,Europe,469.115601,0.000284333,-1068,-261,Social Distancing and Wearing Masks Enforced,6.119875228
2020-11-02,2,11,2020,23254,162,United_Kingdom,UK,GBR,66647112,Europe,468.8950363,0.000348912,4304,26,Social Distancing and Wearing Masks Enforced,6.247045855
2020-11-01,1,11,2020,21915,326,United_Kingdom,UK,GBR,66647112,Europe,459.4827755,0.000328821,-1339,164,Social Distancing and Wearing Masks Enforced,6.210197073
2020-10-31,31,10,2020,24405,274,United_Kingdom,UK,GBR,66647112,Europe,450.8642475,0.000366182,2490,-52,Social Distancing and Wearing Masks Enforced,6.277063085
2020-10-30,30,10,2020,23065,280,United_Kingdom,UK,GBR,66647112,Europe,437.7053877,0.000346077,-1340,6,Social Distancing and Wearing Masks Enforced,6.241975238
2020-10-29,29,10,2020,24700,310,United_Kingdom,UK,GBR,66647112,Europe,431.573089,0.000370609,1635,30,Social Distancing and Wearing Masks Enforced,6.284528558
2020-10-28,28,10,2020,22885,367,United_Kingdom,UK,GBR,66647112,Europe,424.106899,0.000343376,-1815,57,Social Distancing and Wearing Masks Enforced,6.2371073
2020-10-27,27,10,2020,20890,102,United_Kingdom,UK,GBR,66647112,Europe,415.6249111,0.000313442,-1995,-265,Social Distancing and Wearing Masks Enforced,6.180434658
2020-10-26,26,10,2020,19790,151,United_Kingdom,UK,GBR,66647112,Europe,405.2448664,0.000296937,-1100,49,Social Distancing and Wearing Masks Enforced,6.146824281
2020-10-25,25,10,2020,23012,174,United_Kingdom,UK,GBR,66647112,Europe,394.8648218,0.000345281,3222,23,Social Distancing and Wearing Masks Enforced,6.240545858
2020-10-24,24,10,2020,20531,224,United_Kingdom,UK,GBR,66647112,Europe,383.0908682,0.000308055,-2481,50,Social Distancing and Wearing Masks Enforced,6.169664043
2020-10-23,23,10,2020,21238,189,United_Kingdom,UK,GBR,66647112,Europe,373.087434,0.000318663,707,-35,Social Distancing and Wearing Masks Enforced,6.190700015
2020-10-22,22,10,2020,26687,191,United_Kingdom,UK,GBR,66647112,Europe,367.5388065,0.000400422,5449,2,Social Distancing and Wearing Masks Enforced,6.332603299
2020-10-21,21,10,2020,21330,241,United_Kingdom,UK,GBR,66647112,Europe,348.7457941,0.000320044,-5357,50,Social Distancing and Wearing Masks Enforced,6.193385737
2020-10-20,20,10,2020,18803,80,United_Kingdom,UK,GBR,66647112,Europe,338.5608067,0.000282128,-2527,-161,Social Distancing and Wearing Masks Enforced,6.115036582
2020-10-19,19,10,2020,16981,67,United_Kingdom,UK,GBR,66647112,Europe,329.2430736,0.00025479,-1822,-13,Social Distancing and Wearing Masks Enforced,6.05170928
2020-10-18,18,10,2020,16171,150,United_Kingdom,UK,GBR,66647112,Europe,338.2157054,0.000242636,-810,83,Social Distancing and Wearing Masks Enforced,6.021341189
2020-10-17,17,10,2020,15635,136,United_Kingdom,UK,GBR,66647112,Europe,333.2642531,0.000234594,-536,-14,Social Distancing and Wearing Masks Enforced,6.000397527
2020-10-16,16,10,2020,18978,138,United_Kingdom,UK,GBR,66647112,Europe,320.2599387,0.000284754,3343,2,Social Distancing and Wearing Masks Enforced,6.120792617
2020-10-15,15,10,2020,19724,137,United_Kingdom,UK,GBR,66647112,Europe,302.1586292,0.000295947,746,-1,Social Distancing and Wearing Masks Enforced,6.144748655
2020-10-14,14,10,2020,17232,143,United_Kingdom,UK,GBR,66647112,Europe,283.2290768,0.000258556,-2492,6,Social Distancing and Wearing Masks Enforced,6.060826158
2020-10-13,13,10,2020,13972,50,United_Kingdom,UK,GBR,66647112,Europe,268.0911365,0.000209641,-3260,-93,Social Distancing and Wearing Masks Enforced,5.930524273
2020-10-12,12,10,2020,12872,65,United_Kingdom,UK,GBR,66647112,Europe,253.1947671,0.000193137,-1100,15,Social Distancing and Wearing Masks Enforced,5.879574239
2020-10-11,11,10,2020,15165,81,United_Kingdom,UK,GBR,66647112,Europe,242.4216071,0.000227542,2293,16,Social Distancing and Wearing Masks Enforced,5.981433236
2020-10-10,10,10,2020,13864,87,United_Kingdom,UK,GBR,66647112,Europe,228.7315916,0.000208021,-1301,6,Social Distancing and Wearing Masks Enforced,5.925702854
2020-10-09,9,10,2020,17540,77,United_Kingdom,UK,GBR,66647112,Europe,218.2420148,0.000263177,3676,-10,Social Distancing and Wearing Masks Enforced,6.071833645
2020-10-08,8,10,2020,14162,70,United_Kingdom,UK,GBR,66647112,Europe,201.8782149,0.000212492,-3378,-7,Social Distancing and Wearing Masks Enforced,5.938916641
2020-10-07,7,10,2020,14542,76,United_Kingdom,UK,GBR,66647112,Europe,189.8987011,0.000218194,380,6,Social Distancing and Wearing Masks Enforced,5.955368778
2020-10-06,6,10,2020,12593,19,United_Kingdom,UK,GBR,66647112,Europe,175.470469,0.00018895,-1949,-57,Social Distancing and Wearing Masks Enforced,5.865958736
2020-10-05,5,10,2020,22961,33,United_Kingdom,UK,GBR,66647112,Europe,163.1293491,0.000344516,10368,14,Social Distancing and Wearing Masks Enforced,6.239167306
2020-10-04,4,10,2020,12871,49,United_Kingdom,UK,GBR,66647112,Europe,134.5279597,0.000193122,-10090,16,Social Distancing and Wearing Masks Enforced,5.879525967
2020-10-03,3,10,2020,6968,66,United_Kingdom,UK,GBR,66647112,Europe,121.8507413,0.000104551,-5903,17,Social Distancing and Wearing Masks Enforced,5.498244729
2020-10-02,2,10,2020,6914,59,United_Kingdom,UK,GBR,66647112,Europe,117.8805767,0.00010374,-54,-7,Social Distancing and Wearing Masks Enforced,5.493410806
2020-10-01,1,10,2020,7108,71,United_Kingdom,UK,GBR,66647112,Europe,112.600528,0.000106651,194,12,Social Distancing and Wearing Masks Enforced,5.51060474
2020-09-30,30,9,2020,7143,71,United_Kingdom,UK,GBR,66647112,Europe,107.9236562,0.000107176,35,0,Social Distancing and Wearing Masks Enforced,5.513656704
2020-09-29,29,9,2020,4044,13,United_Kingdom,UK,GBR,66647112,Europe,101.8618781,6.07E-05,-3099,-58,Social Distancing and Wearing Masks Enforced,5.160180157
2020-09-28,28,9,2020,5692,17,United_Kingdom,UK,GBR,66647112,Europe,99.72675185,8.54E-05,1648,4,Social Distancing and Wearing Masks Enforced,5.372569449
2020-09-27,27,9,2020,6041,35,United_Kingdom,UK,GBR,66647112,Europe,96.18271231,9.06E-05,349,18,Social Distancing and Wearing Masks Enforced,5.409543775
2020-09-26,26,9,2020,6873,34,United_Kingdom,UK,GBR,66647112,Europe,92.36559268,0.000103125,832,-1,Social Distancing and Wearing Masks Enforced,5.489715324
2020-09-25,25,9,2020,6634,40,United_Kingdom,UK,GBR,66647112,Europe,87.36312535,9.95E-05,-239,6,Social Distancing and Wearing Masks Enforced,5.467724571
2020-09-24,24,9,2020,6178,37,United_Kingdom,UK,GBR,66647112,Europe,81.78899035,9.27E-05,-456,-3,Social Distancing and Wearing Masks Enforced,5.423477231
2020-09-23,23,9,2020,4926,37,United_Kingdom,UK,GBR,66647112,Europe,76.5089416,7.39E-05,-1252,0,Social Distancing and Wearing Masks Enforced,5.28276519
2020-09-22,22,9,2020,4368,11,United_Kingdom,UK,GBR,66647112,Europe,72.80885629,6.55E-05,-558,-26,Social Distancing and Wearing Masks Enforced,5.208067023
2020-09-21,21,9,2020,3899,18,United_Kingdom,UK,GBR,66647112,Europe,70.67823134,5.85E-05,-469,7,Social Distancing and Wearing Masks Enforced,5.137492615
2020-09-20,20,9,2020,4422,27,United_Kingdom,UK,GBR,66647112,Europe,69.3113304,6.63E-05,523,9,Social Distancing and Wearing Masks Enforced,5.215701268
2020-09-19,19,9,2020,4322,27,United_Kingdom,UK,GBR,66647112,Europe,65.39668215,6.48E-05,-100,0,Social Distancing and Wearing Masks Enforced,5.201488962
2020-09-18,18,9,2020,3395,21,United_Kingdom,UK,GBR,66647112,Europe,61.82263381,5.09E-05,-927,-6,Social Distancing and Wearing Masks Enforced,5.051489702
2020-09-17,17,9,2020,3991,20,United_Kingdom,UK,GBR,66647112,Europe,59.33190323,5.99E-05,596,-1,Social Distancing and Wearing Masks Enforced,5.151983212
2020-09-16,16,9,2020,3103,27,United_Kingdom,UK,GBR,66647112,Europe,55.60631044,4.66E-05,-888,7,Social Distancing and Wearing Masks Enforced,4.995610332
2020-09-15,15,9,2020,2621,9,United_Kingdom,UK,GBR,66647112,Europe,52.89351473,3.93E-05,-482,-18,Social Distancing and Wearing Masks Enforced,4.890720631
2020-09-14,14,9,2020,3330,5,United_Kingdom,UK,GBR,66647112,Europe,51.07047999,5.00E-05,709,-4,Social Distancing and Wearing Masks Enforced,5.039478392
2020-09-13,13,9,2020,3497,9,United_Kingdom,UK,GBR,66647112,Europe,48.64726922,5.25E-05,167,4,Social Distancing and Wearing Masks Enforced,5.06988227
2020-09-12,12,9,2020,3539,6,United_Kingdom,UK,GBR,66647112,Europe,45.0627178,5.31E-05,42,-3,Social Distancing and Wearing Masks Enforced,5.077300228
2020-09-11,11,9,2020,2919,14,United_Kingdom,UK,GBR,66647112,Europe,41.66722183,4.38E-05,-620,8,Social Distancing and Wearing Masks Enforced,4.957629188
2020-09-10,10,9,2020,2659,8,United_Kingdom,UK,GBR,66647112,Europe,39.571107,3.99E-05,-260,-6,Social Distancing and Wearing Masks Enforced,4.899664243
2020-09-09,9,9,2020,2460,32,United_Kingdom,UK,GBR,66647112,Europe,37.15389798,3.69E-05,-199,24,Social Distancing and Wearing Masks Enforced,4.851331368
2020-09-08,8,9,2020,2948,3,United_Kingdom,UK,GBR,66647112,Europe,35.2393364,4.42E-05,488,-29,Social Distancing and Wearing Masks Enforced,4.963771632
2020-09-07,7,9,2020,2988,2,United_Kingdom,UK,GBR,66647112,Europe,32.27446675,4.48E-05,40,-1,Social Distancing and Wearing Masks Enforced,4.972145545
2020-09-06,6,9,2020,1813,12,United_Kingdom,UK,GBR,66647112,Europe,29.35310985,2.72E-05,-1175,10,Social Distancing and Wearing Masks Enforced,4.661713355
2020-09-05,5,9,2020,1940,10,United_Kingdom,UK,GBR,66647112,Europe,28.5653788,2.91E-05,127,-2,Social Distancing and Wearing Masks Enforced,4.703780863
2020-09-04,4,9,2020,1735,13,United_Kingdom,UK,GBR,66647112,Europe,27.20447962,2.60E-05,-205,3,Social Distancing and Wearing Masks Enforced,4.634389829
2020-09-03,3,9,2020,1508,10,United_Kingdom,UK,GBR,66647112,Europe,26.37473624,2.26E-05,-227,-3,Social Distancing and Wearing Masks Enforced,4.547264291
2020-09-02,2,9,2020,1295,3,United_Kingdom,UK,GBR,66647112,Europe,25.33042992,1.94E-05,-213,-7,Social Distancing and Wearing Masks Enforced,4.4526514
2020-09-01,1,9,2020,1406,2,United_Kingdom,UK,GBR,66647112,Europe,25.02133926,2.11E-05,111,-1,Social Distancing and Wearing Masks Enforced,4.503748803
2020-08-31,31,8,2020,1715,1,United_Kingdom,UK,GBR,66647112,Europe,23.98153426,2.57E-05,309,-1,Social Distancing and Wearing Masks Enforced,4.627185865
2020-08-30,30,8,2020,1108,12,United_Kingdom,UK,GBR,66647112,Europe,22.96873719,1.66E-05,-607,11,Social Distancing and Wearing Masks Enforced,4.355751665
2020-08-29,29,8,2020,1276,9,United_Kingdom,UK,GBR,66647112,Europe,22.92222355,1.91E-05,168,-3,Social Distancing and Wearing Masks Enforced,4.443467753
2020-08-28,28,8,2020,1522,12,United_Kingdom,UK,GBR,66647112,Europe,23.16829572,2.28E-05,246,3,Social Distancing and Wearing Masks Enforced,4.553006041
2020-08-27,27,8,2020,1048,16,United_Kingdom,UK,GBR,66647112,Europe,22.57862276,1.57E-05,-474,4,Social Distancing and Wearing Masks Enforced,4.321160084
2020-08-26,26,8,2020,1184,16,United_Kingdom,UK,GBR,66647112,Europe,22.5201056,1.78E-05,136,0,Social Distancing and Wearing Masks Enforced,4.396972235
2020-08-25,25,8,2020,972,4,United_Kingdom,UK,GBR,66647112,Europe,22.46608975,1.46E-05,-212,-12,Social Distancing and Wearing Masks Enforced,4.274384089
2020-08-24,24,8,2020,1041,6,United_Kingdom,UK,GBR,66647112,Europe,22.2320211,1.56E-05,69,2,Social Distancing and Wearing Masks Enforced,4.316996024
2020-08-23,23,8,2020,1288,18,United_Kingdom,UK,GBR,66647112,Europe,22.26353034,1.93E-05,247,12,Social Distancing and Wearing Masks Enforced,4.449283723
2020-08-22,22,8,2020,1033,2,United_Kingdom,UK,GBR,66647112,Europe,21.46829708,1.55E-05,-255,-16,Social Distancing and Wearing Masks Enforced,4.312202674
2020-08-21,21,8,2020,1182,6,United_Kingdom,UK,GBR,66647112,Europe,21.22522578,1.77E-05,149,4,Social Distancing and Wearing Masks Enforced,4.395921796
2020-08-20,20,8,2020,812,16,United_Kingdom,UK,GBR,66647112,Europe,20.87712368,1.22E-05,-370,10,Social Distancing and Wearing Masks Enforced,4.162633605
2020-08-19,19,8,2020,1089,12,United_Kingdom,UK,GBR,66647112,Europe,20.99565845,1.63E-05,277,-4,Social Distancing and Wearing Masks Enforced,4.345004594
2020-08-18,18,8,2020,713,3,United_Kingdom,UK,GBR,66647112,Europe,20.36697404,1.07E-05,-376,-9,Social Distancing and Wearing Masks Enforced,4.081848308
2020-08-17,17,8,2020,1040,5,United_Kingdom,UK,GBR,66647112,Europe,20.68956866,1.56E-05,327,2,Social Distancing and Wearing Masks Enforced,4.316398873
2020-08-16,16,8,2020,1077,3,United_Kingdom,UK,GBR,66647112,Europe,20.24393795,1.62E-05,37,-2,Social Distancing and Wearing Masks Enforced,4.338119926
2020-08-15,15,8,2020,1440,11,United_Kingdom,UK,GBR,66647112,Europe,19.78480328,2.16E-05,363,8,Social Distancing and Wearing Masks Enforced,4.518595179
2020-08-14,14,8,2020,1129,18,United_Kingdom,UK,GBR,66647112,Europe,18.94455682,1.69E-05,-311,7,Social Distancing and Wearing Masks Enforced,4.367417662
2020-08-13,13,8,2020,1009,20,United_Kingdom,UK,GBR,66647112,Europe,18.51993227,1.51E-05,-120,2,Social Distancing and Wearing Masks Enforced,4.297596675
2020-08-12,12,8,2020,1148,13,United_Kingdom,UK,GBR,66647112,Europe,18.150824,1.72E-05,139,-7,Social Distancing and Wearing Masks Enforced,4.377787128
2020-08-11,11,8,2020,816,18,United_Kingdom,UK,GBR,66647112,Europe,16.53334956,1.22E-05,-332,5,Social Distancing and Wearing Masks Enforced,4.165686855
2020-08-10,10,8,2020,1062,5,United_Kingdom,UK,GBR,66647112,Europe,15.86565371,1.59E-05,246,-13,Social Distancing and Wearing Masks Enforced,4.329405408
2020-08-09,9,8,2020,758,3,United_Kingdom,UK,GBR,66647112,Europe,14.9038716,1.14E-05,-304,-2,Social Distancing and Wearing Masks Enforced,4.119875228
2020-08-08,8,8,2020,871,12,United_Kingdom,UK,GBR,66647112,Europe,14.76733155,1.31E-05,113,9,Social Distancing and Wearing Masks Enforced,4.206215055
2020-08-07,7,8,2020,950,18,United_Kingdom,UK,GBR,66647112,Europe,14.55726994,1.43E-05,79,6,Social Distancing and Wearing Masks Enforced,4.260159359
2020-08-06,6,8,2020,891,14,United_Kingdom,UK,GBR,66647112,Europe,14.29169204,1.34E-05,-59,-4,Social Distancing and Wearing Masks Enforced,4.22032088
2020-08-05,5,8,2020,670,18,United_Kingdom,UK,GBR,66647112,Europe,14.08163042,1.01E-05,-221,4,Social Distancing and Wearing Masks Enforced,4.043198972
2020-08-04,4,8,2020,928,1,United_Kingdom,UK,GBR,66647112,Europe,14.26618456,1.39E-05,258,-17,Social Distancing and Wearing Masks Enforced,4.245601325
2020-08-03,3,8,2020,743,5,United_Kingdom,UK,GBR,66647112,Europe,13.4934579,1.11E-05,-185,4,Social Distancing and Wearing Masks Enforced,4.107456394
2020-08-02,2,8,2020,771,13,United_Kingdom,UK,GBR,66647112,Europe,13.11834787,1.16E-05,28,8,Social Distancing and Wearing Masks Enforced,4.130441021
2020-08-01,1,8,2020,880,20,United_Kingdom,UK,GBR,66647112,Europe,12.81525897,1.32E-05,109,7,Social Distancing and Wearing Masks Enforced,4.212602335
2020-07-31,31,7,2020,846,0,United_Kingdom,UK,GBR,66647112,Europe,12.55118151,1.27E-05,-34,-20,Social Distancing and Wearing Masks Enforced,4.188120155
2020-07-30,30,7,2020,763,34,United_Kingdom,UK,GBR,66647112,Europe,12.44014894,1.14E-05,-83,34,Social Distancing and Wearing Masks Enforced,4.123960285
2020-07-29,29,7,2020,70,21,United_Kingdom,UK,GBR,66647112,Europe,12.32311462,1.05E-06,-693,-13,Social Distancing and Wearing Masks Enforced,2.639738513
2020-07-28,28,7,2020,371,3,United_Kingdom,UK,GBR,66647112,Europe,13.30740333,5.57E-06,301,-18,Social Distancing and Wearing Masks Enforced,3.675943021
2020-07-27,27,7,2020,421,8,United_Kingdom,UK,GBR,66647112,Europe,13.29239893,6.32E-06,50,5,Social Distancing and Wearing Masks Enforced,3.754498876
2020-07-26,26,7,2020,667,15,United_Kingdom,UK,GBR,66647112,Europe,13.32390817,1.00E-05,246,7,Social Distancing and Wearing Masks Enforced,4.040410628
2020-07-25,25,7,2020,731,32,United_Kingdom,UK,GBR,66647112,Europe,13.17086328,1.10E-05,64,17,Social Distancing and Wearing Masks Enforced,4.097339455
2020-07-24,24,7,2020,773,9,United_Kingdom,UK,GBR,66647112,Europe,13.14685624,1.16E-05,42,-23,Social Distancing and Wearing Masks Enforced,4.132050697
2020-07-23,23,7,2020,751,17,United_Kingdom,UK,GBR,66647112,Europe,13.02682103,1.13E-05,-22,8,Social Distancing and Wearing Masks Enforced,4.114110647
2020-07-22,22,7,2020,793,25,United_Kingdom,UK,GBR,66647112,Europe,12.79575325,1.19E-05,42,8,Social Distancing and Wearing Masks Enforced,4.147922185
2020-07-21,21,7,2020,413,10,United_Kingdom,UK,GBR,66647112,Europe,12.66221408,6.20E-06,-380,-15,Social Distancing and Wearing Masks Enforced,3.742578416
2020-07-20,20,7,2020,493,11,United_Kingdom,UK,GBR,66647112,Europe,12.87527658,7.40E-06,80,1,Social Distancing and Wearing Masks Enforced,3.852592962
2020-07-19,19,7,2020,569,9,United_Kingdom,UK,GBR,66647112,Europe,12.73723609,8.54E-06,76,-2,Social Distancing and Wearing Masks Enforced,3.941674534
2020-07-18,18,7,2020,704,26,United_Kingdom,UK,GBR,66647112,Europe,12.75224049,1.06E-05,135,17,Social Distancing and Wearing Masks Enforced,4.073955451
2020-07-17,17,7,2020,772,24,United_Kingdom,UK,GBR,66647112,Europe,12.5991956,1.16E-05,68,-2,Social Distancing and Wearing Masks Enforced,4.13124638
2020-07-16,16,7,2020,685,26,United_Kingdom,UK,GBR,66647112,Europe,12.41764234,1.03E-05,-87,2,Social Distancing and Wearing Masks Enforced,4.056956027
2020-07-15,15,7,2020,726,44,United_Kingdom,UK,GBR,66647112,Europe,12.31561242,1.09E-05,41,18,Social Distancing and Wearing Masks Enforced,4.093074957
2020-07-14,14,7,2020,361,10,United_Kingdom,UK,GBR,66647112,Europe,12.32161418,5.42E-06,-365,-34,Social Distancing and Wearing Masks Enforced,3.658965601
2020-07-13,13,7,2020,442,9,United_Kingdom,UK,GBR,66647112,Europe,12.44915159,6.63E-06,81,-1,Social Distancing and Wearing Masks Enforced,3.784743627
2020-07-12,12,7,2020,565,17,United_Kingdom,UK,GBR,66647112,Europe,12.75974269,8.48E-06,123,8,Social Distancing and Wearing Masks Enforced,3.937291201
2020-07-11,11,7,2020,715,34,United_Kingdom,UK,GBR,66647112,Europe,12.91878934,1.07E-05,150,17,Social Distancing and Wearing Masks Enforced,4.083588744
2020-07-10,10,7,2020,693,31,United_Kingdom,UK,GBR,66647112,Europe,12.92779198,1.04E-05,-22,-3,Social Distancing and Wearing Masks Enforced,4.064170446
2020-07-09,9,7,2020,597,57,United_Kingdom,UK,GBR,66647112,Europe,13.05532939,8.96E-06,-96,26,Social Distancing and Wearing Masks Enforced,3.971521401
2020-07-08,8,7,2020,704,54,United_Kingdom,UK,GBR,66647112,Europe,13.48895658,1.06E-05,107,-3,Social Distancing and Wearing Masks Enforced,4.073955451
2020-07-07,7,7,2020,555,11,United_Kingdom,UK,GBR,66647112,Europe,13.77704108,8.33E-06,-149,-43,Social Distancing and Wearing Masks Enforced,3.926195639
2020-07-06,6,7,2020,401,19,United_Kingdom,UK,GBR,66647112,Europe,13.90307805,6.02E-06,-154,8,Social Distancing and Wearing Masks Enforced,3.724257631
2020-07-05,5,7,2020,579,32,United_Kingdom,UK,GBR,66647112,Europe,14.33220392,8.69E-06,178,13,Social Distancing and Wearing Masks Enforced,3.952499459
2020-07-04,4,7,2020,602,49,United_Kingdom,UK,GBR,66647112,Europe,14.94288305,9.03E-06,23,17,Social Distancing and Wearing Masks Enforced,3.976703541
2020-07-03,3,7,2020,651,41,United_Kingdom,UK,GBR,66647112,Europe,15.58057009,9.77E-06,49,-8,Social Distancing and Wearing Masks Enforced,4.025324365
2020-07-02,2,7,2020,617,97,United_Kingdom,UK,GBR,66647112,Europe,16.12372941,9.26E-06,-34,56,Social Distancing and Wearing Masks Enforced,3.991995575
2020-07-01,1,7,2020,730,53,United_Kingdom,UK,GBR,66647112,Europe,16.85144287,1.10E-05,113,-44,Social Distancing and Wearing Masks Enforced,4.096488894
2020-06-30,30,6,2020,446,21,United_Kingdom,UK,GBR,66647112,Europe,17.32108062,6.69E-06,-284,-32,Social Distancing and Wearing Masks Enforced,3.790341277
2020-06-29,29,6,2020,649,31,United_Kingdom,UK,GBR,66647112,Europe,17.8852461,9.74E-06,203,10,Social Distancing and Wearing Masks Enforced,4.023412563
2020-06-28,28,6,2020,671,40,United_Kingdom,UK,GBR,66647112,Europe,18.24685217,1.01E-05,22,9,Social Distancing and Wearing Masks Enforced,4.044125646
2020-06-27,27,6,2020,721,77,United_Kingdom,UK,GBR,66647112,Europe,18.81851985,1.08E-05,50,37,Social Distancing and Wearing Masks Enforced,4.088780988
2020-06-26,26,6,2020,778,99,United_Kingdom,UK,GBR,66647112,Europe,19.26265012,1.17E-05,57,22,Social Distancing and Wearing Masks Enforced,4.136056739
2020-06-25,25,6,2020,886,87,United_Kingdom,UK,GBR,66647112,Europe,19.89433541,1.33E-05,108,-12,Social Distancing and Wearing Masks Enforced,4.216824332
2020-06-24,24,6,2020,896,94,United_Kingdom,UK,GBR,66647112,Europe,20.30245512,1.34E-05,10,7,Social Distancing and Wearing Masks Enforced,4.223797862
2020-06-23,23,6,2020,639,14,United_Kingdom,UK,GBR,66647112,Europe,20.60704446,9.59E-06,-257,-80,Social Distancing and Wearing Masks Enforced,4.013764311
2020-06-22,22,6,2020,687,31,United_Kingdom,UK,GBR,66647112,Europe,20.73008055,1.03E-05,48,17,Social Distancing and Wearing Masks Enforced,4.0587675
2020-06-21,21,6,2020,986,71,United_Kingdom,UK,GBR,66647112,Europe,20.90113072,1.48E-05,299,40,Social Distancing and Wearing Masks Enforced,4.28326952
2020-06-20,20,6,2020,1027,84,United_Kingdom,UK,GBR,66647112,Europe,21.10218969,1.54E-05,41,13,Social Distancing and Wearing Masks Enforced,4.308583237
2020-06-19,19,6,2020,1013,67,United_Kingdom,UK,GBR,66647112,Europe,21.42628476,1.52E-05,-14,-17,Social Distancing and Wearing Masks Enforced,4.300054976
2020-06-18,18,6,2020,1102,110,United_Kingdom,UK,GBR,66647112,Europe,21.94093572,1.65E-05,89,43,Social Distancing and Wearing Masks Enforced,4.352377893
2020-06-17,17,6,2020,1043,120,United_Kingdom,UK,GBR,66647112,Europe,22.51410384,1.56E-05,-59,10,Social Distancing and Wearing Masks Enforced,4.318188606
2020-06-16,16,6,2020,822,29,United_Kingdom,UK,GBR,66647112,Europe,23.111279,1.23E-05,-221,-91,Social Distancing and Wearing Masks Enforced,4.170238779
2020-06-15,15,6,2020,890,27,United_Kingdom,UK,GBR,66647112,Europe,23.49689211,1.34E-05,68,-2,Lockdown,4.219623143
2020-06-14,14,6,2020,1052,107,United_Kingdom,UK,GBR,66647112,Europe,23.84949553,1.58E-05,162,80,Lockdown,4.323527077
2020-06-13,13,6,2020,1017,131,United_Kingdom,UK,GBR,66647112,Europe,24.56220459,1.53E-05,-35,24,Lockdown,4.30250359
2020-06-12,12,6,2020,1199,76,United_Kingdom,UK,GBR,66647112,Europe,25.67703159,1.80E-05,182,-55,Lockdown,4.404794432
2020-06-11,11,6,2020,1158,164,United_Kingdom,UK,GBR,66647112,Europe,26.6313115,1.74E-05,-41,88,Lockdown,4.383176017
2020-06-10,10,6,2020,1099,195,United_Kingdom,UK,GBR,66647112,Europe,27.40253771,1.65E-05,-59,31,Lockdown,4.350684112
2020-06-09,9,6,2020,721,47,United_Kingdom,UK,GBR,66647112,Europe,28.19026877,1.08E-05,-378,-148,Lockdown,4.088780988
2020-06-08,8,6,2020,801,54,United_Kingdom,UK,GBR,66647112,Europe,29.15505176,1.20E-05,80,7,Lockdown,4.154158974
2020-06-07,7,6,2020,1120,143,United_Kingdom,UK,GBR,66647112,Europe,30.24437128,1.68E-05,319,89,Lockdown,4.362444745
2020-06-06,6,6,2020,1243,258,United_Kingdom,UK,GBR,66647112,Europe,31.65778586,1.87E-05,123,115,Lockdown,4.427187303
2020-06-05,5,6,2020,1356,130,United_Kingdom,UK,GBR,66647112,Europe,33.65487165,2.03E-05,113,-128,Lockdown,4.481250512
2020-06-04,4,6,2020,1484,254,United_Kingdom,UK,GBR,66647112,Europe,35.69847108,2.23E-05,128,124,Lockdown,4.537296138
2020-06-03,3,6,2020,1441,249,United_Kingdom,UK,GBR,66647112,Europe,38.05116117,2.16E-05,-43,-5,Lockdown,4.519026512
2020-06-02,2,6,2020,1079,86,United_Kingdom,UK,GBR,66647112,Europe,39.77366641,1.62E-05,-362,-163,Lockdown,4.339272681
2020-06-01,1,6,2020,1125,60,United_Kingdom,UK,GBR,66647112,Europe,40.91250045,1.69E-05,46,-26,Lockdown,4.365212389
2020-05-31,31,5,2020,1527,154,United_Kingdom,UK,GBR,66647112,Europe,42.34392032,2.29E-05,402,94,Lockdown,4.555043875
2020-05-30,30,5,2020,1760,274,United_Kingdom,UK,GBR,66647112,Europe,43.84285999,2.64E-05,233,120,Lockdown,4.643278893
2020-05-29,29,5,2020,1835,343,United_Kingdom,UK,GBR,66647112,Europe,45.145242,2.75E-05,75,69,Lockdown,4.669207617
2020-05-28,28,5,2020,1672,422,United_Kingdom,UK,GBR,66647112,Europe,47.35388984,2.51E-05,-163,79,Lockdown,4.611408577
2020-05-27,27,5,2020,1624,131,United_Kingdom,UK,GBR,66647112,Europe,49.94965123,2.44E-05,-48,-291,Lockdown,4.593310164
2020-05-26,26,5,2020,1364,104,United_Kingdom,UK,GBR,66647112,Europe,52.89351473,2.05E-05,-260,-27,Lockdown,4.484905434
2020-05-25,25,5,2020,1527,379,United_Kingdom,UK,GBR,66647112,Europe,54.34143943,2.29E-05,163,275,Lockdown,4.555043875
2020-05-24,24,5,2020,2062,220,United_Kingdom,UK,GBR,66647112,Europe,55.2867167,3.09E-05,535,-159,Lockdown,4.741675094
2020-05-23,23,5,2020,2574,291,United_Kingdom,UK,GBR,66647112,Europe,56.78865725,3.86E-05,512,71,Lockdown,4.879477691
2020-05-22,22,5,2020,2718,273,United_Kingdom,UK,GBR,66647112,Europe,58.5786823,4.08E-05,144,-18,Lockdown,4.913300186
2020-05-21,21,5,2020,3052,328,United_Kingdom,UK,GBR,66647112,Europe,60.24267038,4.58E-05,334,55,Lockdown,4.985313401
2020-05-20,20,5,2020,2589,500,United_Kingdom,UK,GBR,66647112,Europe,61.18794765,3.88E-05,-463,172,Lockdown,4.883088014
2020-05-19,19,5,2020,1838,146,United_Kingdom,UK,GBR,66647112,Europe,62.38829974,2.76E-05,-751,-354,Lockdown,4.670222594
2020-05-18,18,5,2020,2079,67,United_Kingdom,UK,GBR,66647112,Europe,64.10480322,3.12E-05,241,-79,Lockdown,4.746776641
2020-05-17,17,5,2020,2526,411,United_Kingdom,UK,GBR,66647112,Europe,65.83030935,3.79E-05,447,344,Lockdown,4.867781629
2020-05-16,16,5,2020,2628,350,United_Kingdom,UK,GBR,66647112,Europe,69.14778243,3.94E-05,102,-61,Lockdown,4.892377841
2020-05-15,15,5,2020,3307,352,United_Kingdom,UK,GBR,66647112,Europe,72.6558114,4.96E-05,679,2,Lockdown,5.035172
2020-05-14,14,5,2020,3402,447,United_Kingdom,UK,GBR,66647112,Europe,75.85925104,5.10E-05,95,95,Lockdown,5.052769486
2020-05-13,13,5,2020,3586,614,United_Kingdom,UK,GBR,66647112,Europe,77.85033506,5.38E-05,184,167,Lockdown,5.085497608
2020-05-12,12,5,2020,2329,187,United_Kingdom,UK,GBR,66647112,Europe,79.53082798,3.49E-05,-1257,-427,Lockdown,4.817330454
2020-05-11,11,5,2020,2157,217,United_Kingdom,UK,GBR,66647112,Europe,81.24733147,3.24E-05,-172,30,Lockdown,4.769661251
2020-05-10,10,5,2020,3063,275,United_Kingdom,UK,GBR,66647112,Europe,83.63453168,4.60E-05,906,58,Lockdown,4.987548786
2020-05-09,9,5,2020,3767,579,United_Kingdom,UK,GBR,66647112,Europe,86.49587097,5.65E-05,704,304,Lockdown,5.116093106
2020-05-08,8,5,2020,3827,458,United_Kingdom,UK,GBR,66647112,Europe,88.58298316,5.74E-05,60,-121,Lockdown,5.125911613
2020-05-07,7,5,2020,3682,647,United_Kingdom,UK,GBR,66647112,Europe,91.07371374,5.52E-05,-145,189,Lockdown,5.101912474
2020-05-06,6,5,2020,3389,726,United_Kingdom,UK,GBR,66647112,Europe,92.69118818,5.08E-05,-293,79,Lockdown,5.050390642
2020-05-05,5,5,2020,2982,272,United_Kingdom,UK,GBR,66647112,Europe,94.88933294,4.47E-05,-407,-454,Lockdown,4.97089663
2020-05-04,4,5,2020,3229,253,United_Kingdom,UK,GBR,66647112,Europe,96.19621627,4.84E-05,247,-19,Lockdown,5.020341393
2020-05-03,3,5,2020,4737,584,United_Kingdom,UK,GBR,66647112,Europe,98.43487292,7.11E-05,1508,331,Lockdown,5.258456532
2020-05-02,2,5,2020,4966,698,United_Kingdom,UK,GBR,66647112,Europe,98.7634693,7.45E-05,229,114,Lockdown,5.287790166
2020-05-01,1,5,2020,5442,634,United_Kingdom,UK,GBR,66647112,Europe,99.25261278,8.17E-05,476,-64,Lockdown,5.344662166
2020-04-30,30,4,2020,4729,769,United_Kingdom,UK,GBR,66647112,Europe,98.68694686,7.10E-05,-713,135,Lockdown,5.257406314
2020-04-29,29,4,2020,4706,969,United_Kingdom,UK,GBR,66647112,Europe,98.08226949,7.06E-05,-23,200,Lockdown,5.254377012
2020-04-28,28,4,2020,3473,320,United_Kingdom,UK,GBR,66647112,Europe,97.29003711,5.21E-05,-1233,-649,Lockdown,5.065603333
2020-04-27,27,4,2020,3748,364,United_Kingdom,UK,GBR,66647112,Europe,97.31404416,5.62E-05,275,44,Lockdown,5.112951286
2020-04-26,26,4,2020,4970,815,United_Kingdom,UK,GBR,66647112,Europe,97.06046978,7.46E-05,1222,451,Lockdown,5.288290436
2020-04-25,25,4,2020,5158,1010,United_Kingdom,UK,GBR,66647112,Europe,96.07468063,7.74E-05,188,195,Lockdown,5.311360022
2020-04-24,24,4,2020,5487,682,United_Kingdom,UK,GBR,66647112,Europe,95.62454859,8.23E-05,329,-328,Lockdown,5.34977887
2020-04-23,23,4,2020,4760,847,United_Kingdom,UK,GBR,66647112,Europe,95.09039191,7.14E-05,-727,165,Lockdown,5.261466057
2020-04-22,22,4,2020,4854,1224,United_Kingdom,UK,GBR,66647112,Europe,96.12569559,7.28E-05,94,377,Lockdown,5.273616535
2020-04-21,21,4,2020,3853,570,United_Kingdom,UK,GBR,66647112,Europe,96.76788396,5.78E-05,-1001,-654,Lockdown,5.130118584
2020-04-20,20,4,2020,4721,432,United_Kingdom,UK,GBR,66647112,Europe,96.37626909,7.08E-05,868,-138,Lockdown,5.256354318
2020-04-19,19,4,2020,4956,1105,United_Kingdom,UK,GBR,66647112,Europe,95.32446057,7.44E-05,235,673,Lockdown,5.286537727
2020-04-18,18,4,2020,5292,913,United_Kingdom,UK,GBR,66647112,Europe,95.25694077,7.94E-05,336,-192,Lockdown,5.32729561
2020-04-17,17,4,2020,5065,1036,United_Kingdom,UK,GBR,66647112,Europe,94.62075416,7.60E-05,-227,123,Lockdown,5.300054976
2020-04-16,16,4,2020,4326,880,United_Kingdom,UK,GBR,66647112,Europe,94.39268726,6.49E-05,-739,-156,Lockdown,5.20206374
2020-04-15,15,4,2020,4178,1076,United_Kingdom,UK,GBR,66647112,Europe,94.67477,6.27E-05,-148,196,Lockdown,5.180434658
2020-04-14,14,4,2020,3489,724,United_Kingdom,UK,GBR,66647112,Europe,94.81731181,5.24E-05,-689,-352,Lockdown,5.068459229
2020-04-13,13,4,2020,3579,657,United_Kingdom,UK,GBR,66647112,Europe,93.87053411,5.37E-05,90,-67,Lockdown,5.084283555
2020-04-12,12,4,2020,4313,843,United_Kingdom,UK,GBR,66647112,Europe,92.73470094,6.47E-05,734,186,Lockdown,5.200193765
2020-04-11,11,4,2020,4858,1122,United_Kingdom,UK,GBR,66647112,Europe,91.06020978,7.29E-05,545,279,Lockdown,5.274128343
2020-04-10,10,4,2020,5131,1116,United_Kingdom,UK,GBR,66647112,Europe,88.40293035,7.70E-05,273,-6,Lockdown,5.308099048
2020-04-09,9,4,2020,5450,1030,United_Kingdom,UK,GBR,66647112,Europe,84.74335692,8.18E-05,319,-86,Lockdown,5.345574887
2020-04-08,8,4,2020,5282,1105,United_Kingdom,UK,GBR,66647112,Europe,80.12950359,7.93E-05,-168,75,Lockdown,5.326120397
2020-04-07,7,4,2020,3592,567,United_Kingdom,UK,GBR,66647112,Europe,75.7122079,5.39E-05,-1690,-538,Lockdown,5.086536341
2020-04-06,6,4,2020,4020,599,United_Kingdom,UK,GBR,66647112,Europe,72.3902335,6.03E-05,428,32,Lockdown,5.156481724
2020-04-05,5,4,2020,4911,756,United_Kingdom,UK,GBR,66647112,Europe,68.15599152,7.37E-05,891,157,Lockdown,5.280870297
2020-04-04,4,4,2020,4868,736,United_Kingdom,UK,GBR,66647112,Europe,62.67038248,7.30E-05,-43,-20,Lockdown,5.275406021
2020-04-03,3,4,2020,4913,657,United_Kingdom,UK,GBR,66647112,Europe,56.94920434,7.37E-05,45,-79,Lockdown,5.281123283
2020-04-02,2,4,2020,4514,672,United_Kingdom,UK,GBR,66647112,Europe,51.07648175,6.77E-05,-399,15,Lockdown,5.228495546
2020-04-01,1,4,2020,4273,403,United_Kingdom,UK,GBR,66647112,Europe,45.45733355,6.41E-05,-241,-269,Lockdown,5.194404438
2020-03-31,31,3,2020,2858,374,United_Kingdom,UK,GBR,66647112,Europe,39.96272187,4.29E-05,-1415,-29,Lockdown,4.944507208
2020-03-30,30,3,2020,2822,212,United_Kingdom,UK,GBR,66647112,Europe,36.33765856,4.23E-05,-36,-162,Lockdown,4.936631026
2020-03-29,29,3,2020,3197,292,United_Kingdom,UK,GBR,66647112,Europe,32.64507545,4.80E-05,375,80,Lockdown,5.014153132
2020-03-28,28,3,2020,3087,288,United_Kingdom,UK,GBR,66647112,Europe,28.5653788,4.63E-05,-110,-4,Lockdown,4.992398254
2020-03-27,27,3,2020,2692,181,United_Kingdom,UK,GBR,66647112,Europe,24.65973319,4.04E-05,-395,-107,Lockdown,4.907327974
2020-03-26,26,3,2020,2375,191,United_Kingdom,UK,GBR,66647112,Europe,21.2297271,3.56E-05,-317,10,Lockdown,4.8294828
2020-03-25,25,3,2020,2338,148,United_Kingdom,UK,GBR,66647112,Europe,18.05479583,3.51E-05,-37,-43,Lockdown,4.819726864
2020-03-24,24,3,2020,1378,76,United_Kingdom,UK,GBR,66647112,Europe,14.76883199,2.07E-05,-960,-72,Lockdown,4.491250266
2020-03-23,23,3,2020,1198,36,United_Kingdom,UK,GBR,66647112,Europe,12.78675061,1.80E-05,-180,-40,Lockdown,4.404276005
2020-03-22,22,3,2020,1255,58,United_Kingdom,UK,GBR,66647112,Europe,11.07924977,1.88E-05,57,22,Social Distancing and Wearing Masks Enforced,4.43315694
2020-03-21,21,3,2020,1055,32,United_Kingdom,UK,GBR,66647112,Europe,9.31773308,1.58E-05,-200,-26,Social Distancing and Wearing Masks Enforced,4.325296423
2020-03-20,20,3,2020,999,46,United_Kingdom,UK,GBR,66647112,Europe,7.81129121,1.50E-05,-56,14,Social Distancing and Wearing Masks Enforced,4.291408028
2020-03-19,19,3,2020,769,34,United_Kingdom,UK,GBR,66647112,Europe,6.39637619,1.15E-05,-230,-12,Social Distancing and Wearing Masks Enforced,4.128827163
2020-03-18,18,3,2020,611,17,United_Kingdom,UK,GBR,66647112,Europe,5.32506195,9.17E-06,-158,-17,Social Distancing and Wearing Masks Enforced,3.985923849
2020-03-17,17,3,2020,442,22,United_Kingdom,UK,GBR,66647112,Europe,4.46831064,6.63E-06,-169,5,Social Distancing and Wearing Masks Enforced,3.784743627
2020-03-16,16,3,2020,361,14,United_Kingdom,UK,GBR,66647112,Europe,3.8381258,5.42E-06,-81,-8,Social Distancing and Wearing Masks Enforced,3.658965601
2020-03-15,15,3,2020,478,19,United_Kingdom,UK,GBR,66647112,Europe,3.30396912,7.17E-06,117,5,Social Distancing and Wearing Masks Enforced,3.833394681
2020-03-14,14,3,2020,484,1,United_Kingdom,UK,GBR,66647112,Europe,2.60476403,7.26E-06,6,-18,Social Distancing and Wearing Masks Enforced,3.841145321
2020-03-13,13,3,2020,406,2,United_Kingdom,UK,GBR,66647112,Europe,1.89055454,6.09E-06,-78,1,Social Distancing and Wearing Masks Enforced,3.731957047
2020-03-12,12,3,2020,259,0,United_Kingdom,UK,GBR,66647112,Europe,1.28737761,3.89E-06,-147,-2,Social Distancing and Wearing Masks Enforced,3.4526514
2020-03-11,11,3,2020,148,4,United_Kingdom,UK,GBR,66647112,Europe,0.90626583,2.22E-06,-111,4,Social Distancing and Wearing Masks Enforced,3.104942561
2020-03-10,10,3,2020,57,1,United_Kingdom,UK,GBR,66647112,Europe,0.68720157,8.55E-07,-91,-3,Social Distancing and Wearing Masks Enforced,2.512088995
2020-03-09,9,3,2020,60,0,United_Kingdom,UK,GBR,66647112,Europe,0.60167648,9.00E-07,3,-1,Social Distancing and Wearing Masks Enforced,2.543959311
2020-03-08,8,3,2020,81,1,United_Kingdom,UK,GBR,66647112,Europe,0.51165008,1.22E-06,21,1,Social Distancing and Wearing Masks Enforced,2.730424778
2020-03-07,7,3,2020,51,1,United_Kingdom,UK,GBR,66647112,Europe,0.39161487,7.65E-07,-30,0,Social Distancing and Wearing Masks Enforced,2.442980622
2020-03-06,6,3,2020,56,0,United_Kingdom,UK,GBR,66647112,Europe,0.31509242,8.40E-07,5,-1,Social Distancing and Wearing Masks Enforced,2.501091629
2020-03-05,5,3,2020,55,0,United_Kingdom,UK,GBR,66647112,Europe,0.23106778,8.25E-07,-1,0,Social Distancing and Wearing Masks Enforced,2.489896102
2020-03-04,4,3,2020,40,0,United_Kingdom,UK,GBR,66647112,Europe,0.14854357,6.00E-07,-15,0,Social Distancing and Wearing Masks Enforced,2.292029674
2020-03-03,3,3,2020,22,0,United_Kingdom,UK,GBR,66647112,Europe,0.08852597,3.30E-07,-18,0,Social Distancing and Wearing Masks Enforced,1.92057266
2020-03-02,2,3,2020,5,0,United_Kingdom,UK,GBR,66647112,Europe,0.05551628,7.50E-08,-17,0,Social Distancing and Wearing Masks Enforced,1
2020-03-01,1,3,2020,12,0,United_Kingdom,UK,GBR,66647112,Europe,0.04801408,1.80E-07,7,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-02-29,29,2,2020,8,0,United_Kingdom,UK,GBR,66647112,Europe,0.0300088,1.20E-07,-4,0,Social Distancing and Wearing Masks Enforced,1.292029674
2020-02-28,28,2,2020,4,0,United_Kingdom,UK,GBR,66647112,Europe,0.01800528,6.00E-08,-4,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-02-27,27,2,2020,5,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,7.50E-08,1,0,Social Distancing and Wearing Masks Enforced,1
2020-02-26,26,2,2020,2,0,United_Kingdom,UK,GBR,66647112,Europe,0.00600176,3.00E-08,-3,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-02-25,25,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-24,24,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00450132,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-23,23,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.01050308,1.50E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-22,22,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00900264,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-21,21,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00900264,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-20,20,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01050308,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-19,19,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01050308,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-18,18,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-17,17,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-16,16,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-15,15,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-14,14,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.0150044,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-13,13,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.0150044,1.50E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-12,12,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01350396,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-11,11,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.01350396,1.50E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-10,10,2,2020,4,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,6.00E-08,3,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-02-09,9,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00600176,0,-4,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-08,8,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00600176,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-07,7,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.00600176,1.50E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-06,6,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00450132,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-05,5,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.00450132,1.50E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-04,4,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-03,3,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-02,2,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-01,1,2,2020,2,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,3.00E-08,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-01-31,31,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-30,30,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-29,29,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-28,28,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-27,27,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-26,26,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-25,25,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-24,24,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-23,23,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-22,22,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-21,21,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-20,20,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-19,19,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-18,18,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-17,17,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-16,16,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-15,15,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-14,14,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-13,13,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-12,12,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-11,11,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-10,10,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-09,9,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-08,8,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-07,7,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-06,6,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-05,5,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-04,4,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-03,3,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-02,2,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-01,1,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2019-12-31,31,12,2019,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-09,9,12,2020,0,0,Laos,LA,LAO,7169456,Asia,0.04184418,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-08,8,12,2020,0,0,Laos,LA,LAO,7169456,Asia,0.04184418,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-07,7,12,2020,2,0,Laos,LA,LAO,7169456,Asia,0.23711701,2.79E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-12-06,6,12,2020,0,0,Laos,LA,LAO,7169456,Asia,0.20922089,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-05,5,12,2020,0,0,Laos,LA,LAO,7169456,Asia,0.20922089,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-04,4,12,2020,0,0,Laos,LA,LAO,7169456,Asia,0.20922089,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-03,3,12,2020,0,0,Laos,LA,LAO,7169456,Asia,0.20922089,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-02,2,12,2020,0,0,Laos,LA,LAO,7169456,Asia,0.20922089,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-01,1,12,2020,0,0,Laos,LA,LAO,7169456,Asia,0.20922089,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-30,30,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.20922089,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-29,29,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.20922089,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-28,28,11,2020,1,0,Laos,LA,LAO,7169456,Asia,0.20922089,1.39E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-11-27,27,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.19527284,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-26,26,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.19527284,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-25,25,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.19527284,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-24,24,11,2020,14,0,Laos,LA,LAO,7169456,Asia,0.19527284,1.95E-06,14,0,Social Distancing and Wearing Masks Enforced,1.639738513
2020-11-23,23,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,-14,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-22,22,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-21,21,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-20,20,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-19,19,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-18,18,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-17,17,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-16,16,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-15,15,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-14,14,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-13,13,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-12,12,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-11,11,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-10,10,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-09,9,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-08,8,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-07,7,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-06,6,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-05,5,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-04,4,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-03,3,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-02,2,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-01,1,11,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-31,31,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-30,30,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-29,29,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-28,28,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-27,27,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-26,26,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-25,25,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-24,24,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-23,23,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-22,22,10,2020,1,0,Laos,LA,LAO,7169456,Asia,0.01394806,1.39E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-10-21,21,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-20,20,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-19,19,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-18,18,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-17,17,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-16,16,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-15,15,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-14,14,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-13,13,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-12,12,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-11,11,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-10,10,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-09,9,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-08,8,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-07,7,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-06,6,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-05,5,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-04,4,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-03,3,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-02,2,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-01,1,10,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-30,30,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-29,29,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-28,28,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-27,27,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-26,26,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-25,25,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-24,24,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-23,23,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-22,22,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-21,21,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-20,20,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-19,19,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-18,18,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-17,17,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-16,16,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-15,15,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-14,14,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-13,13,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-12,12,9,2020,1,0,Laos,LA,LAO,7169456,Asia,0.01394806,1.39E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-09-11,11,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-10,10,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-09,9,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-08,8,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-07,7,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-06,6,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-05,5,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-04,4,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-03,3,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-02,2,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-01,1,9,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-31,31,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-30,30,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-29,29,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-28,28,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-27,27,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-26,26,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-25,25,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-24,24,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-23,23,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.02789612,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-22,22,8,2020,2,0,Laos,LA,LAO,7169456,Asia,0.02789612,2.79E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-08-21,21,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-20,20,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-19,19,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-18,18,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-17,17,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-16,16,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-15,15,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-14,14,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-13,13,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-12,12,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-11,11,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-10,10,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-09,9,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-08,8,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-07,7,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-06,6,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-05,5,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-04,4,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-03,3,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-02,2,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-01,1,8,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-31,31,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-30,30,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-29,29,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-28,28,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-27,27,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-26,26,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-25,25,7,2020,1,0,Laos,LA,LAO,7169456,Asia,0.01394806,1.39E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-07-24,24,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-23,23,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-22,22,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-21,21,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-20,20,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-19,19,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-18,18,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-17,17,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-16,16,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-15,15,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-14,14,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-13,13,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-12,12,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-11,11,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-10,10,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-09,9,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-08,8,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-07,7,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-06,6,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-05,5,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-04,4,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-03,3,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-02,2,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-01,1,7,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-30,30,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-29,29,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-28,28,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-27,27,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-26,26,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-25,25,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-24,24,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-23,23,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-22,22,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-21,21,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-20,20,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-19,19,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-18,18,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-17,17,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-16,16,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-15,15,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-14,14,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-13,13,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-12,12,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-11,11,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-10,10,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-09,9,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-08,8,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-07,7,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-06,6,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-05,5,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-04,4,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-03,3,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-02,2,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-01,1,6,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-31,31,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-30,30,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-29,29,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-28,28,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-27,27,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-26,26,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-25,25,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-24,24,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-23,23,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-22,22,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-21,21,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-20,20,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-19,19,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-18,18,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-17,17,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-16,16,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-15,15,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-14,14,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-13,13,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-12,12,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-11,11,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-10,10,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-09,9,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-08,8,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-07,7,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-06,6,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-05,5,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-04,4,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-03,3,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-02,2,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-05-01,1,5,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-04-30,30,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-04-29,29,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-04-28,28,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-04-27,27,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0,0,0,0,Lockdown,#NUM!
2020-04-26,26,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.01394806,0,0,0,Lockdown,#NUM!
2020-04-25,25,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.04184418,0,0,0,Lockdown,#NUM!
2020-04-24,24,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.04184418,0,0,0,Lockdown,#NUM!
2020-04-23,23,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.05579224,0,0,0,Lockdown,#NUM!
2020-04-22,22,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.09763642,0,0,0,Lockdown,#NUM!
2020-04-21,21,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.09763642,0,0,0,Lockdown,#NUM!
2020-04-20,20,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.11158448,0,0,0,Lockdown,#NUM!
2020-04-19,19,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.12553254,0,0,0,Lockdown,#NUM!
2020-04-18,18,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.12553254,0,0,0,Lockdown,#NUM!
2020-04-17,17,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.12553254,0,0,0,Lockdown,#NUM!
2020-04-16,16,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.12553254,0,0,0,Lockdown,#NUM!
2020-04-15,15,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.1394806,0,0,0,Lockdown,#NUM!
2020-04-14,14,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.1394806,0,0,0,Lockdown,#NUM!
2020-04-13,13,4,2020,1,0,Laos,LA,LAO,7169456,Asia,0.18132478,1.39E-07,1,0,Lockdown,0
2020-04-12,12,4,2020,2,0,Laos,LA,LAO,7169456,Asia,0.16737672,2.79E-07,1,0,Lockdown,0.430676558
2020-04-11,11,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.1394806,0,-2,0,Lockdown,#NUM!
2020-04-10,10,4,2020,1,0,Laos,LA,LAO,7169456,Asia,0.1394806,1.39E-07,1,0,Lockdown,0
2020-04-09,9,4,2020,3,0,Laos,LA,LAO,7169456,Asia,0.18132478,4.18E-07,2,0,Lockdown,0.682606194
2020-04-08,8,4,2020,0,0,Laos,LA,LAO,7169456,Asia,0.1394806,0,-3,0,Lockdown,#NUM!
2020-04-07,7,4,2020,1,0,Laos,LA,LAO,7169456,Asia,0.16737672,1.39E-07,1,0,Lockdown,0
2020-04-06,6,4,2020,1,0,Laos,LA,LAO,7169456,Asia,,1.39E-07,0,0,Lockdown,0
2020-04-05,5,4,2020,0,0,Laos,LA,LAO,7169456,Asia,,0,-1,0,Lockdown,#NUM!
2020-04-04,4,4,2020,0,0,Laos,LA,LAO,7169456,Asia,,0,0,0,Lockdown,#NUM!
2020-04-03,3,4,2020,0,0,Laos,LA,LAO,7169456,Asia,,0,0,0,Lockdown,#NUM!
2020-04-02,2,4,2020,1,0,Laos,LA,LAO,7169456,Asia,,1.39E-07,1,0,Lockdown,0
2020-04-01,1,4,2020,0,0,Laos,LA,LAO,7169456,Asia,,0,-1,0,Lockdown,#NUM!
2020-03-31,31,3,2020,3,0,Laos,LA,LAO,7169456,Asia,,4.18E-07,3,0,Lockdown,0.682606194
2020-03-30,30,3,2020,0,0,Laos,LA,LAO,7169456,Asia,,0,-3,0,Lockdown,#NUM!
2020-03-29,29,3,2020,0,0,Laos,LA,LAO,7169456,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-28,28,3,2020,0,0,Laos,LA,LAO,7169456,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-27,27,3,2020,4,0,Laos,LA,LAO,7169456,Asia,,5.58E-07,4,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-03-26,26,3,2020,0,0,Laos,LA,LAO,7169456,Asia,,0,-4,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-25,25,3,2020,2,0,Laos,LA,LAO,7169456,Asia,,2.79E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-12-09,9,12,2020,217344,2564,United_States_of_America,US,USA,329064917,America,784.1951137,0.00066049,217342,2564,Social Distancing and Wearing Masks Enforced,7.635732038
2020-12-08,8,12,2020,197334,1433,United_States_of_America,US,USA,329064917,America,769.8967192,0.000599681,-20010,-1131,Social Distancing and Wearing Masks Enforced,7.575721256
2020-12-07,7,12,2020,173432,1111,United_States_of_America,US,USA,329064917,America,762.7944732,0.000527045,-23902,-322,Social Distancing and Wearing Masks Enforced,7.495499377
2020-12-06,6,12,2020,211933,2203,United_States_of_America,US,USA,329064917,America,757.9440625,0.000644046,38501,1092,Social Distancing and Wearing Masks Enforced,7.62006746
2020-12-05,5,12,2020,231930,2680,United_States_of_America,US,USA,329064917,America,746.8705635,0.000704815,19997,477,Social Distancing and Wearing Masks Enforced,7.676090383
2020-12-04,4,12,2020,214747,2481,United_States_of_America,US,USA,329064917,America,735.9873007,0.000652598,-17183,-199,Social Distancing and Wearing Masks Enforced,7.628263119
2020-12-03,3,12,2020,203311,3190,United_States_of_America,US,USA,329064917,America,727.8651951,0.000617845,-11436,709,Social Distancing and Wearing Masks Enforced,7.594261332
2020-12-02,2,12,2020,180421,2600,United_States_of_America,US,USA,329064917,America,717.7437879,0.000548284,-22890,-590,Social Distancing and Wearing Masks Enforced,7.520046716
2020-12-01,1,12,2020,157903,1172,United_States_of_America,US,USA,329064917,America,709.8107028,0.000479854,-22518,-1428,Social Distancing and Wearing Masks Enforced,7.437215258
2020-11-30,30,11,2020,136670,810,United_States_of_America,US,USA,329064917,America,713.0082482,0.000415328,-21233,-362,Social Distancing and Wearing Masks Enforced,7.347487249
2020-11-29,29,11,2020,154893,1204,United_States_of_America,US,USA,329064917,America,711.6407368,0.000470707,18223,394,Social Distancing and Wearing Masks Enforced,7.42525682
2020-11-28,28,11,2020,207913,1404,United_States_of_America,US,USA,329064917,America,714.7963452,0.00063183,53020,200,Social Distancing and Wearing Masks Enforced,7.608168608
2020-11-27,27,11,2020,106091,1189,United_States_of_America,US,USA,329064917,America,707.7764537,0.000322401,-101822,-215,Social Distancing and Wearing Masks Enforced,7.19012048
2020-11-26,26,11,2020,186589,2341,United_States_of_America,US,USA,329064917,America,722.234999,0.000567028,80498,1152,Social Distancing and Wearing Masks Enforced,7.540933094
2020-11-25,25,11,2020,170293,2224,United_States_of_America,US,USA,329064917,America,709.0816673,0.000517506,-16296,-117,Social Distancing and Wearing Masks Enforced,7.484150627
2020-11-24,24,11,2020,173963,919,United_States_of_America,US,USA,329064917,America,702.0863911,0.000528659,3670,-1305,Social Distancing and Wearing Masks Enforced,7.497398824
2020-11-23,23,11,2020,157471,883,United_States_of_America,US,USA,329064917,America,691.4313506,0.000478541,-16492,-36,Social Distancing and Wearing Masks Enforced,7.435513045
2020-11-22,22,11,2020,175494,1486,United_States_of_America,US,USA,329064917,America,677.2159185,0.000533311,18023,603,Social Distancing and Wearing Masks Enforced,7.502843098
2020-11-21,21,11,2020,196117,1858,United_States_of_America,US,USA,329064917,America,660.7811674,0.000595983,20623,372,Social Distancing and Wearing Masks Enforced,7.571877489
2020-11-20,20,11,2020,188020,2018,United_States_of_America,US,USA,329064917,America,640.8781037,0.000571377,-8097,160,Social Distancing and Wearing Masks Enforced,7.545680094
2020-11-19,19,11,2020,170005,1850,United_States_of_America,US,USA,329064917,America,620.9476898,0.000516631,-18015,-168,Social Distancing and Wearing Masks Enforced,7.483098934
2020-11-18,18,11,2020,154316,1467,United_States_of_America,US,USA,329064917,America,600.4356277,0.000468953,-15689,-383,Social Distancing and Wearing Masks Enforced,7.422937931
2020-11-17,17,11,2020,168425,1006,United_States_of_America,US,USA,329064917,America,581.7213872,0.000511829,14109,-461,Social Distancing and Wearing Masks Enforced,7.477297343
2020-11-16,16,11,2020,132170,614,United_States_of_America,US,USA,329064917,America,556.0298,0.000401653,-36255,-392,Social Distancing and Wearing Masks Enforced,7.326684776
2020-11-15,15,11,2020,165277,1255,United_States_of_America,US,USA,329064917,America,540.4799807,0.000502263,33107,641,Social Distancing and Wearing Masks Enforced,7.465574186
2020-11-14,14,11,2020,184813,1915,United_States_of_America,US,USA,329064917,America,514.2410851,0.000561631,19536,660,Social Distancing and Wearing Masks Enforced,7.534990749
2020-11-13,13,11,2020,153669,630,United_States_of_America,US,USA,329064917,America,488.8539972,0.000466987,-31144,-1285,Social Distancing and Wearing Masks Enforced,7.420327386
2020-11-12,12,11,2020,143306,2117,United_States_of_America,US,USA,329064917,America,468.9372584,0.000435495,-10363,1487,Social Distancing and Wearing Masks Enforced,7.376946567
2020-11-11,11,11,2020,147274,1432,United_States_of_America,US,USA,329064917,America,449.20407,0.000447553,3968,-685,Social Distancing and Wearing Masks Enforced,7.393916835
2020-11-10,10,11,2020,138901,679,United_States_of_America,US,USA,329064917,America,427.2798246,0.000422108,-8373,-753,Social Distancing and Wearing Masks Enforced,7.357548021
2020-11-09,9,11,2020,110693,459,United_States_of_America,US,USA,329064917,America,405.8427171,0.000336387,-28208,-220,Social Distancing and Wearing Masks Enforced,7.216504466
2020-11-08,8,11,2020,121413,1014,United_States_of_America,US,USA,329064917,America,390.2673709,0.000368964,10720,555,Social Distancing and Wearing Masks Enforced,7.273939023
2020-11-07,7,11,2020,130623,1162,United_States_of_America,US,USA,329064917,America,378.6110082,0.000396952,9210,148,Social Distancing and Wearing Masks Enforced,7.31936939
2020-11-06,6,11,2020,122436,1208,United_States_of_America,US,USA,329064917,America,364.8465509,0.000372072,-8187,46,Social Distancing and Wearing Masks Enforced,7.279152326
2020-11-05,5,11,2020,102507,1102,United_States_of_America,US,USA,329064917,America,349.5371097,0.00031151,-19929,-106,Social Distancing and Wearing Masks Enforced,7.168767604
2020-11-04,4,11,2020,92734,1076,United_States_of_America,US,USA,329064917,America,337.5245864,0.000281811,-9773,-26,Social Distancing and Wearing Masks Enforced,7.106512386
2020-11-03,3,11,2020,83883,555,United_States_of_America,US,USA,329064917,America,327.1360587,0.000254913,-8851,-521,Social Distancing and Wearing Masks Enforced,7.044184906
2020-11-02,2,11,2020,81001,440,United_States_of_America,US,USA,329064917,America,319.9268429,0.000246155,-2882,-115,Social Distancing and Wearing Masks Enforced,7.022462123
2020-11-01,1,11,2020,78934,848,United_States_of_America,US,USA,329064917,America,309.8504117,0.000239874,-2067,408,Social Distancing and Wearing Masks Enforced,7.006400963
2020-10-31,31,10,2020,101273,1040,United_States_of_America,US,USA,329064917,America,303.0666438,0.00030776,22339,192,Social Distancing and Wearing Masks Enforced,7.161242463
2020-10-30,30,10,2020,88130,968,United_States_of_America,US,USA,329064917,America,293.6408441,0.000267819,-13143,-72,Social Distancing and Wearing Masks Enforced,7.074872655
2020-10-29,29,10,2020,78371,977,United_States_of_America,US,USA,329064917,America,286.2426079,0.000238163,-9759,9,Social Distancing and Wearing Masks Enforced,7.001953386
2020-10-28,28,10,2020,75129,988,United_States_of_America,US,USA,329064917,America,280.4732295,0.000228311,-3242,11,Social Distancing and Wearing Masks Enforced,6.975703647
2020-10-27,27,10,2020,68359,505,United_States_of_America,US,USA,329064917,America,273.6016371,0.000207737,-6770,-483,Social Distancing and Wearing Masks Enforced,6.917028872
2020-10-26,26,10,2020,59440,331,United_States_of_America,US,USA,329064917,America,265.4859132,0.000180633,-8919,-174,Social Distancing and Wearing Masks Enforced,6.830162627
2020-10-25,25,10,2020,83056,904,United_States_of_America,US,USA,329064917,America,260.6713617,0.0002524,23616,573,Social Distancing and Wearing Masks Enforced,7.038028787
2020-10-24,24,10,2020,85329,953,United_States_of_America,US,USA,329064917,America,251.9238476,0.000259307,2273,49,Social Distancing and Wearing Masks Enforced,7.054804391
2020-10-23,23,10,2020,72058,841,United_States_of_America,US,USA,329064917,America,243.6437185,0.000218978,-13271,-112,Social Distancing and Wearing Masks Enforced,6.949772056
2020-10-22,22,10,2020,62978,1135,United_States_of_America,US,USA,329064917,America,239.0069434,0.000191385,-9080,294,Social Distancing and Wearing Masks Enforced,6.866087006
2020-10-21,21,10,2020,58549,933,United_States_of_America,US,USA,329064917,America,234.5105662,0.000177925,-4429,-202,Social Distancing and Wearing Masks Enforced,6.820778363
2020-10-20,20,10,2020,60160,459,United_States_of_America,US,USA,329064917,America,229.8042,0.000182821,1611,-474,Social Distancing and Wearing Masks Enforced,6.837643673
2020-10-19,19,10,2020,47843,385,United_States_of_America,US,USA,329064917,America,223.8919927,0.000145391,-12317,-74,Social Distancing and Wearing Masks Enforced,6.695306487
2020-10-18,18,10,2020,56611,690,United_States_of_America,US,USA,329064917,America,219.9590302,0.000172036,8768,305,Social Distancing and Wearing Masks Enforced,6.799863795
2020-10-17,17,10,2020,70256,899,United_States_of_America,US,USA,329064917,America,218.1502685,0.000213502,13645,209,Social Distancing and Wearing Masks Enforced,6.934036353
2020-10-16,16,10,2020,63785,828,United_States_of_America,US,USA,329064917,America,213.3533427,0.000193837,-6471,-71,Social Distancing and Wearing Masks Enforced,6.873998212
2020-10-15,15,10,2020,59386,970,United_States_of_America,US,USA,329064917,America,207.5751515,0.000180469,-4399,142,Social Distancing and Wearing Masks Enforced,6.8295979
2020-10-14,14,10,2020,52517,817,United_States_of_America,US,USA,329064917,America,202.2862255,0.000159595,-6869,-153,Social Distancing and Wearing Masks Enforced,6.753222427
2020-10-13,13,10,2020,41653,314,United_States_of_America,US,USA,329064917,America,199.3992571,0.00012658,-10864,-503,Social Distancing and Wearing Masks Enforced,6.609219648
2020-10-12,12,10,2020,43597,394,United_States_of_America,US,USA,329064917,America,196.769077,0.000132488,1944,80,Social Distancing and Wearing Masks Enforced,6.637561808
2020-10-11,11,10,2020,54271,590,United_States_of_America,US,USA,329064917,America,194.5357791,0.000164925,10674,196,Social Distancing and Wearing Masks Enforced,6.773635198
2020-10-10,10,10,2020,58082,1014,United_States_of_America,US,USA,329064917,America,191.8302339,0.000176506,3811,424,Social Distancing and Wearing Masks Enforced,6.815802585
2020-10-09,9,10,2020,56800,972,United_States_of_America,US,USA,329064917,America,190.8975912,0.00017261,-1282,-42,Social Distancing and Wearing Masks Enforced,6.801934713
2020-10-08,8,10,2020,48182,892,United_States_of_America,US,USA,329064917,America,187.0725101,0.000146421,-8618,-80,Social Distancing and Wearing Masks Enforced,6.699693541
2020-10-07,7,10,2020,43062,717,United_States_of_America,US,USA,329064917,America,183.9570154,0.000130862,-5120,-175,Social Distancing and Wearing Masks Enforced,6.629889935
2020-10-06,6,10,2020,40705,398,United_States_of_America,US,USA,329064917,America,182.5120118,0.000123699,-2357,-319,Social Distancing and Wearing Masks Enforced,6.59491499
2020-10-05,5,10,2020,34901,400,United_States_of_America,US,USA,329064917,America,186.294852,0.000106061,-5804,2,Social Distancing and Wearing Masks Enforced,6.499331649
2020-10-04,4,10,2020,50659,678,United_States_of_America,US,USA,329064917,America,187.7994183,0.000153948,15758,278,Social Distancing and Wearing Masks Enforced,6.730841929
2020-10-03,3,10,2020,54471,908,United_States_of_America,US,USA,329064917,America,184.6498878,0.000165533,3812,230,Social Distancing and Wearing Masks Enforced,6.775920739
2020-10-02,2,10,2020,44771,880,United_States_of_America,US,USA,329064917,America,183.3547026,0.000136055,-9700,-28,Social Distancing and Wearing Masks Enforced,6.654072086
2020-10-01,1,10,2020,41982,930,United_States_of_America,US,USA,329064917,America,182.9888174,0.00012758,-2789,50,Social Distancing and Wearing Masks Enforced,6.614108038
2020-09-30,30,9,2020,43017,928,United_States_of_America,US,USA,329064917,America,177.7059692,0.000130725,1035,-2,Social Distancing and Wearing Masks Enforced,6.629240297
2020-09-29,29,9,2020,32998,314,United_States_of_America,US,USA,329064917,America,180.2756749,0.000100278,-10019,-614,Social Distancing and Wearing Masks Enforced,6.464494313
2020-09-28,28,9,2020,36248,259,United_States_of_America,US,USA,329064917,America,180.8357468,0.000110155,3250,-55,Social Distancing and Wearing Masks Enforced,6.522860811
2020-09-27,27,9,2020,45368,723,United_States_of_America,US,USA,329064917,America,180.1133969,0.000137869,9120,464,Social Distancing and Wearing Masks Enforced,6.662302539
2020-09-26,26,9,2020,55013,964,United_States_of_America,US,USA,329064917,America,178.7312988,0.00016718,9645,241,Social Distancing and Wearing Masks Enforced,6.78207262
2020-09-25,25,9,2020,44213,901,United_States_of_America,US,USA,329064917,America,176.6186457,0.00013436,-10800,-63,Social Distancing and Wearing Masks Enforced,6.646279462
2020-09-24,24,9,2020,37930,1102,United_States_of_America,US,USA,329064917,America,174.58075,0.000115266,-6283,201,Social Distancing and Wearing Masks Enforced,6.551043413
2020-09-23,23,9,2020,38307,926,United_States_of_America,US,USA,329064917,America,172.7564899,0.000116412,377,-176,Social Distancing and Wearing Masks Enforced,6.557188596
2020-09-22,22,9,2020,53153,372,United_States_of_America,US,USA,329064917,America,169.3574645,0.000161527,14846,-554,Social Distancing and Wearing Masks Enforced,6.760701822
2020-09-21,21,9,2020,39852,251,United_States_of_America,US,USA,329064917,America,160.5740912,0.000121107,-13301,-121,Social Distancing and Wearing Masks Enforced,6.581756146
2020-09-20,20,9,2020,40295,669,United_States_of_America,US,USA,329064917,America,157.7488128,0.000122453,443,418,Social Distancing and Wearing Masks Enforced,6.588624879
2020-09-19,19,9,2020,50209,956,United_States_of_America,US,USA,329064917,America,158.9172753,0.000152581,9914,287,Social Distancing and Wearing Masks Enforced,6.725297999
2020-09-18,18,9,2020,43567,831,United_States_of_America,US,USA,329064917,America,159.1792297,0.000132396,-6642,-125,Social Distancing and Wearing Masks Enforced,6.637134107
2020-09-17,17,9,2020,24598,865,United_States_of_America,US,USA,329064917,America,156.9553524,7.48E-05,-18969,34,Social Distancing and Wearing Masks Enforced,6.281957409
2020-09-16,16,9,2020,51473,1407,United_States_of_America,US,USA,329064917,America,161.2572391,0.000156422,26875,542,Social Distancing and Wearing Masks Enforced,6.740746315
2020-09-15,15,9,2020,34841,451,United_States_of_America,US,USA,329064917,America,159.1804452,0.000105879,-16632,-956,Social Distancing and Wearing Masks Enforced,6.498262563
2020-09-14,14,9,2020,33871,378,United_States_of_America,US,USA,329064917,America,158.8792889,0.000102931,-970,-73,Social Distancing and Wearing Masks Enforced,6.480718759
2020-09-13,13,9,2020,40820,685,United_States_of_America,US,USA,329064917,America,159.3989432,0.000124048,6949,307,Social Distancing and Wearing Masks Enforced,6.596667914
2020-09-12,12,9,2020,48061,1227,United_States_of_America,US,USA,329064917,America,160.4087743,0.000146053,7241,542,Social Distancing and Wearing Masks Enforced,6.698131213
2020-09-11,11,9,2020,37507,974,United_States_of_America,US,USA,329064917,America,160.8928733,0.000113981,-10554,-253,Social Distancing and Wearing Masks Enforced,6.544075282
2020-09-10,10,9,2020,31927,1136,United_States_of_America,US,USA,329064917,America,163.4461689,9.70E-05,-5580,162,Social Distancing and Wearing Masks Enforced,6.443993425
2020-09-09,9,9,2020,27122,471,United_States_of_America,US,USA,329064917,America,166.7649669,8.24E-05,-4805,-665,Social Distancing and Wearing Masks Enforced,6.342649447
2020-09-08,8,9,2020,24250,267,United_States_of_America,US,USA,329064917,America,170.1068607,7.37E-05,-2872,-204,Social Distancing and Wearing Masks Enforced,6.273104305
2020-09-07,7,9,2020,30555,403,United_States_of_America,US,USA,329064917,America,174.3759272,9.29E-05,6305,136,Social Distancing and Wearing Masks Enforced,6.416702091
2020-09-06,6,9,2020,44140,773,United_States_of_America,US,USA,329064917,America,175.5766021,0.000134138,13585,370,Social Distancing and Wearing Masks Enforced,6.645252729
2020-09-05,5,9,2020,51071,968,United_States_of_America,US,USA,329064917,America,175.6489283,0.0001552,6931,195,Social Distancing and Wearing Masks Enforced,6.735874691
2020-09-04,4,9,2020,36249,1053,United_States_of_America,US,USA,329064917,America,175.2869936,0.000110158,-14822,85,Social Distancing and Wearing Masks Enforced,6.522877952
2020-09-03,3,9,2020,38754,1055,United_States_of_America,US,USA,329064917,America,177.6439753,0.00011777,2505,2,Social Distancing and Wearing Masks Enforced,6.564396908
2020-09-02,2,9,2020,44639,1091,United_States_of_America,US,USA,329064917,America,180.2793216,0.000135654,5885,36,Social Distancing and Wearing Masks Enforced,6.652237475
2020-09-01,1,9,2020,33850,529,United_States_of_America,US,USA,329064917,America,180.1127891,0.000102867,-10789,-562,Social Distancing and Wearing Masks Enforced,6.480333412
2020-08-31,31,8,2020,35581,290,United_States_of_America,US,USA,329064917,America,180.4792822,0.000108128,1731,-239,Social Distancing and Wearing Masks Enforced,6.511321117
2020-08-30,30,8,2020,44143,1006,United_States_of_America,US,USA,329064917,America,182.4615658,0.000134147,8562,716,Social Distancing and Wearing Masks Enforced,6.645294957
2020-08-29,29,8,2020,49654,949,United_States_of_America,US,USA,329064917,America,183.6595057,0.000150894,5511,-57,Social Distancing and Wearing Masks Enforced,6.718391649
2020-08-28,28,8,2020,45909,1110,United_States_of_America,US,USA,329064917,America,188.2737928,0.000139514,-3745,161,Social Distancing and Wearing Masks Enforced,6.669667946
2020-08-27,27,8,2020,42848,1228,United_States_of_America,US,USA,329064917,America,189.8494697,0.000130211,-3061,118,Social Distancing and Wearing Masks Enforced,6.626794464
2020-08-26,26,8,2020,38119,1207,United_States_of_America,US,USA,329064917,America,193.8283199,0.00011584,-4729,-21,Social Distancing and Wearing Masks Enforced,6.554131752
2020-08-25,25,8,2020,38298,473,United_States_of_America,US,USA,329064917,America,196.4703518,0.000116384,179,-734,Social Distancing and Wearing Masks Enforced,6.5570426
2020-08-24,24,8,2020,34506,444,United_States_of_America,US,USA,329064917,America,199.88366,0.000104861,-3792,-29,Social Distancing and Wearing Masks Enforced,6.492259453
2020-08-23,23,8,2020,44378,956,United_States_of_America,US,USA,329064917,America,203.6339839,0.000134861,9872,512,Social Distancing and Wearing Masks Enforced,6.648593927
2020-08-22,22,8,2020,49880,1151,United_States_of_America,US,USA,329064917,America,207.2329698,0.000151581,5502,195,Social Distancing and Wearing Masks Enforced,6.721213236
2020-08-21,21,8,2020,44005,1078,United_States_of_America,US,USA,329064917,America,209.7461517,0.000133727,-5875,-73,Social Distancing and Wearing Masks Enforced,6.643349495
2020-08-20,20,8,2020,47426,1356,United_States_of_America,US,USA,329064917,America,214.5324413,0.000144124,3421,278,Social Distancing and Wearing Masks Enforced,6.689867187
2020-08-19,19,8,2020,44091,1324,United_States_of_America,US,USA,329064917,America,216.1667693,0.000133989,-3335,-32,Social Distancing and Wearing Masks Enforced,6.644562599
2020-08-18,18,8,2020,35056,445,United_States_of_America,US,USA,329064917,America,220.2492464,0.000106532,-9035,-879,Social Distancing and Wearing Masks Enforced,6.502084971
2020-08-17,17,8,2020,42104,571,United_States_of_America,US,USA,329064917,America,223.4556047,0.00012795,7048,126,Social Distancing and Wearing Masks Enforced,6.615911024
2020-08-16,16,8,2020,48085,1035,United_States_of_America,US,USA,329064917,America,225.0987455,0.000146126,5981,464,Social Distancing and Wearing Masks Enforced,6.698441409
2020-08-15,15,8,2020,64838,1336,United_States_of_America,US,USA,329064917,America,228.2355126,0.000197037,16753,301,Social Distancing and Wearing Masks Enforced,6.884171825
2020-08-14,14,8,2020,51094,1083,United_States_of_America,US,USA,329064917,America,228.8995153,0.00015527,-13744,-253,Social Distancing and Wearing Masks Enforced,6.736154448
2020-08-13,13,8,2020,55941,1490,United_States_of_America,US,USA,329064917,America,234.0468279,0.00017,4847,407,Social Distancing and Wearing Masks Enforced,6.792466338
2020-08-12,12,8,2020,46813,1076,United_States_of_America,US,USA,329064917,America,239.8341358,0.000142261,-9128,-414,Social Distancing and Wearing Masks Enforced,6.681783832
2020-08-11,11,8,2020,49530,523,United_States_of_America,US,USA,329064917,America,244.3684995,0.000150517,2717,-553,Social Distancing and Wearing Masks Enforced,6.71683806
2020-08-10,10,8,2020,46847,513,United_States_of_America,US,USA,329064917,America,246.4085225,0.000142364,-2683,-10,Social Distancing and Wearing Masks Enforced,6.68223494
2020-08-09,9,8,2020,56221,1069,United_States_of_America,US,USA,329064917,America,249.1879133,0.000170851,9374,556,Social Distancing and Wearing Masks Enforced,6.795568532
2020-08-08,8,8,2020,58150,1252,United_States_of_America,US,USA,329064917,America,252.0071138,0.000176713,1929,183,Social Distancing and Wearing Masks Enforced,6.816529593
2020-08-07,7,8,2020,59755,1848,United_States_of_America,US,USA,329064917,America,258.1691199,0.00018159,1605,596,Social Distancing and Wearing Masks Enforced,6.833446673
2020-08-06,6,8,2020,52804,1450,United_States_of_America,US,USA,329064917,America,259.2148102,0.000160467,-6951,-398,Social Distancing and Wearing Masks Enforced,6.756608714
2020-08-05,5,8,2020,57525,1403,United_States_of_America,US,USA,329064917,America,264.0904439,0.000174814,4721,-47,Social Distancing and Wearing Masks Enforced,6.809815297
2020-08-04,4,8,2020,45607,543,United_States_of_America,US,USA,329064917,America,268.5038588,0.000138596,-11918,-860,Social Distancing and Wearing Masks Enforced,6.665567158
2020-08-03,3,8,2020,47511,413,United_States_of_America,US,USA,329064917,America,271.8901207,0.000144382,1904,-130,Social Distancing and Wearing Masks Enforced,6.690979788
2020-08-02,2,8,2020,58407,1133,United_States_of_America,US,USA,329064917,America,276.2312094,0.000177494,10896,720,Social Distancing and Wearing Masks Enforced,6.819269597
2020-08-01,1,8,2020,67023,1244,United_States_of_America,US,USA,329064917,America,277.8545973,0.000203677,8616,111,Social Distancing and Wearing Masks Enforced,6.904765345
2020-07-31,31,7,2020,68032,1357,United_States_of_America,US,USA,329064917,America,279.2132958,0.000206743,1009,113,Social Distancing and Wearing Masks Enforced,6.914049542
2020-07-30,30,7,2020,74985,1457,United_States_of_America,US,USA,329064917,America,281.9173215,0.000227873,6953,100,Social Distancing and Wearing Masks Enforced,6.974511589
2020-07-29,29,7,2020,61734,1245,United_States_of_America,US,USA,329064917,America,279.7086388,0.000187604,-13251,-212,Social Distancing and Wearing Masks Enforced,6.853690985
2020-07-28,28,7,2020,56243,1076,United_States_of_America,US,USA,329064917,America,281.7702381,0.000170918,-5491,-169,Social Distancing and Wearing Masks Enforced,6.795811621
2020-07-27,27,7,2020,55993,475,United_States_of_America,US,USA,329064917,America,282.3388189,0.000170158,-250,-601,Social Distancing and Wearing Masks Enforced,6.793043632
2020-07-26,26,7,2020,65498,914,United_States_of_America,US,USA,329064917,America,282.7232415,0.000199043,9505,439,Social Distancing and Wearing Masks Enforced,6.890464554
2020-07-25,25,7,2020,78427,1304,United_States_of_America,US,USA,329064917,America,281.9796192,0.000238333,12929,390,Social Distancing and Wearing Masks Enforced,7.002397202
2020-07-24,24,7,2020,63196,1052,United_States_of_America,US,USA,329064917,America,278.3930929,0.000192047,-15231,-252,Social Distancing and Wearing Masks Enforced,6.86823406
2020-07-23,23,7,2020,68848,1124,United_States_of_America,US,USA,329064917,America,278.3347457,0.000209223,5652,72,Social Distancing and Wearing Masks Enforced,6.921457715
2020-07-22,22,7,2020,72048,1160,United_States_of_America,US,USA,329064917,America,275.3134574,0.000218948,3200,36,Social Distancing and Wearing Masks Enforced,6.949685823
2020-07-21,21,7,2020,56750,372,United_States_of_America,US,USA,329064917,America,270.8842402,0.000172458,-15298,-788,Social Distancing and Wearing Masks Enforced,6.801387522
2020-07-20,20,7,2020,61796,415,United_States_of_America,US,USA,329064917,America,268.8299343,0.000187793,5046,43,Social Distancing and Wearing Masks Enforced,6.854314684
2020-07-19,19,7,2020,63749,853,United_States_of_America,US,USA,329064917,America,264.9696017,0.000193728,1953,438,Social Distancing and Wearing Masks Enforced,6.873647434
2020-07-18,18,7,2020,71494,908,United_States_of_America,US,USA,329064917,America,259.3391018,0.000217264,7745,55,Social Distancing and Wearing Masks Enforced,6.944889718
2020-07-17,17,7,2020,76930,939,United_States_of_America,US,USA,329064917,America,254.1571455,0.000233784,5436,31,Social Distancing and Wearing Masks Enforced,6.990422625
2020-07-16,16,7,2020,67717,953,United_States_of_America,US,USA,329064917,America,247.0062769,0.000205786,-9213,14,Social Distancing and Wearing Masks Enforced,6.911165972
2020-07-15,15,7,2020,68518,861,United_States_of_America,US,USA,329064917,America,242.2446025,0.00020822,801,-92,Social Distancing and Wearing Masks Enforced,6.918472392
2020-07-14,14,7,2020,58114,400,United_States_of_America,US,USA,329064917,America,234.757326,0.000176603,-10404,-461,Social Distancing and Wearing Masks Enforced,6.816144812
2020-07-13,13,7,2020,57258,391,United_States_of_America,US,USA,329064917,America,229.7254921,0.000174002,-856,-9,Social Distancing and Wearing Masks Enforced,6.806924682
2020-07-12,12,7,2020,63051,717,United_States_of_America,US,USA,329064917,America,224.0776704,0.000191607,5793,326,Social Distancing and Wearing Masks Enforced,6.8668068
2020-07-11,11,7,2020,66625,806,United_States_of_America,US,USA,329064917,America,217.8281436,0.000202468,3574,89,Social Distancing and Wearing Masks Enforced,6.901064698
2020-07-10,10,7,2020,63004,982,United_States_of_America,US,USA,329064917,America,211.4166428,0.000191464,-3621,176,Social Distancing and Wearing Masks Enforced,6.866343467
2020-07-09,9,7,2020,58906,829,United_States_of_America,US,USA,329064917,America,204.7143178,0.00017901,-4098,-153,Social Distancing and Wearing Masks Enforced,6.824555422
2020-07-08,8,7,2020,57473,1174,United_States_of_America,US,USA,329064917,America,197.2486177,0.000174656,-1433,345,Social Distancing and Wearing Masks Enforced,6.809253384
2020-07-07,7,7,2020,49990,359,United_States_of_America,US,USA,329064917,America,190.3341765,0.000151915,-7483,-815,Social Distancing and Wearing Masks Enforced,6.722581953
2020-07-06,6,7,2020,49093,271,United_States_of_America,US,USA,329064917,America,184.6817964,0.000149189,-897,-88,Social Distancing and Wearing Masks Enforced,6.711331735
2020-07-05,5,7,2020,45221,242,United_States_of_America,US,USA,329064917,America,177.6011267,0.000137423,-3872,-29,Social Distancing and Wearing Masks Enforced,6.66028604
2020-07-04,4,7,2020,54442,694,United_States_of_America,US,USA,329064917,America,174.239176,0.000165445,9221,452,Social Distancing and Wearing Masks Enforced,6.775589856
2020-07-03,3,7,2020,53399,678,United_States_of_America,US,USA,329064917,America,166.7838082,0.000162275,-1043,-16,Social Distancing and Wearing Masks Enforced,6.763570818
2020-07-02,2,7,2020,52048,652,United_States_of_America,US,USA,329064917,America,158.9929442,0.000158169,-1351,-26,Social Distancing and Wearing Masks Enforced,6.747648707
2020-07-01,1,7,2020,43880,1270,United_States_of_America,US,USA,329064917,America,150.9431648,0.000133348,-8168,618,Social Distancing and Wearing Masks Enforced,6.641582028
2020-06-30,30,6,2020,41556,336,United_States_of_America,US,USA,329064917,America,144.8121557,0.000126285,-2324,-934,Social Distancing and Wearing Masks Enforced,6.607771019
2020-06-29,29,6,2020,38673,265,United_States_of_America,US,USA,329064917,America,138.2484053,0.000117524,-2883,-71,Social Distancing and Wearing Masks Enforced,6.563096892
2020-06-28,28,6,2020,42486,500,United_States_of_America,US,USA,329064917,America,132.4349627,0.000129111,3813,235,Social Distancing and Wearing Masks Enforced,6.621522835
2020-06-27,27,6,2020,45527,623,United_States_of_America,US,USA,329064917,America,127.2852189,0.000138353,3041,123,Social Distancing and Wearing Masks Enforced,6.664476307
2020-06-26,26,6,2020,40949,2437,United_States_of_America,US,USA,329064917,America,121.2414267,0.00012444,-4578,1814,Social Distancing and Wearing Masks Enforced,6.59862837
2020-06-25,25,6,2020,34339,751,United_States_of_America,US,USA,329064917,America,115.7513245,0.000104353,-6610,-1686,Social Distancing and Wearing Masks Enforced,6.489245054
2020-06-24,24,6,2020,34720,826,United_States_of_America,US,USA,329064917,America,111.580415,0.000105511,381,75,Social Distancing and Wearing Masks Enforced,6.49610096
2020-06-23,23,6,2020,31390,427,United_States_of_America,US,USA,329064917,America,106.7014385,9.54E-05,-3330,-399,Social Distancing and Wearing Masks Enforced,6.433453922
2020-06-22,22,6,2020,25793,256,United_States_of_America,US,USA,329064917,America,102.8821313,7.84E-05,-5597,-171,Social Distancing and Wearing Masks Enforced,6.311432294
2020-06-21,21,6,2020,34158,607,United_States_of_America,US,USA,329064917,America,101.8212464,0.000103803,8365,351,Social Distancing and Wearing Masks Enforced,6.485961352
2020-06-20,20,6,2020,29909,678,United_States_of_America,US,USA,329064917,America,98.19430249,9.09E-05,-4249,71,Social Distancing and Wearing Masks Enforced,6.403424847
2020-06-19,19,6,2020,27762,717,United_States_of_America,US,USA,329064917,America,96.75659226,8.44E-05,-2147,39,Social Distancing and Wearing Masks Enforced,6.357140825
2020-06-18,18,6,2020,25559,754,United_States_of_America,US,USA,329064917,America,94.74422337,7.77E-05,-2203,37,Social Distancing and Wearing Masks Enforced,6.305769676
2020-06-17,17,6,2020,23705,836,United_States_of_America,US,USA,329064917,America,92.96341974,7.20E-05,-1854,82,Social Distancing and Wearing Masks Enforced,6.258980976
2020-06-16,16,6,2020,19957,395,United_States_of_America,US,USA,329064917,America,92.00281901,6.06E-05,-3748,-441,Social Distancing and Wearing Masks Enforced,6.152045482
2020-06-15,15,6,2020,19543,296,United_States_of_America,US,USA,329064917,America,92.3459124,5.94E-05,-414,-99,Social Distancing and Wearing Masks Enforced,6.139020567
2020-06-14,14,6,2020,25540,767,United_States_of_America,US,USA,329064917,America,92.42613973,7.76E-05,5997,471,Social Distancing and Wearing Masks Enforced,6.305307618
2020-06-13,13,6,2020,25639,849,United_States_of_America,US,USA,329064917,America,91.74451131,7.79E-05,99,82,Social Distancing and Wearing Masks Enforced,6.307711425
2020-06-12,12,6,2020,22883,896,United_States_of_America,US,USA,329064917,America,91.65273611,6.95E-05,-2756,47,Social Distancing and Wearing Masks Enforced,6.237052997
2020-06-11,11,6,2020,20614,918,United_States_of_America,US,USA,329064917,America,91.32878787,6.26E-05,-2269,22,Social Distancing and Wearing Masks Enforced,6.17217083
2020-06-10,10,6,2020,18665,999,United_States_of_America,US,USA,329064917,America,90.75352144,5.67E-05,-1949,81,Social Distancing and Wearing Masks Enforced,6.11045963
2020-06-09,9,6,2020,18822,493,United_States_of_America,US,USA,329064917,America,90.82797483,5.72E-05,157,-506,Social Distancing and Wearing Masks Enforced,6.115664109
2020-06-08,8,6,2020,22302,712,United_States_of_America,US,USA,329064917,America,90.90151655,6.78E-05,3480,219,Social Distancing and Wearing Masks Enforced,6.221073558
2020-06-07,7,6,2020,22223,659,United_States_of_America,US,USA,329064917,America,90.37456886,6.75E-05,-79,-53,Social Distancing and Wearing Masks Enforced,6.218868706
2020-06-06,6,6,2020,25178,932,United_States_of_America,US,USA,329064917,America,90.07462804,7.65E-05,2955,273,Social Distancing and Wearing Masks Enforced,6.296437904
2020-06-05,5,6,2020,21140,1036,United_States_of_America,US,USA,329064917,America,89.761316,6.42E-05,-4038,104,Social Distancing and Wearing Masks Enforced,6.18782631
2020-06-04,4,6,2020,19699,994,United_States_of_America,US,USA,329064917,America,91.0662257,5.99E-05,-1441,-42,Social Distancing and Wearing Masks Enforced,6.143960619
2020-06-03,3,6,2020,20544,1034,United_States_of_America,US,USA,329064917,America,92.15598027,6.24E-05,845,40,Social Distancing and Wearing Masks Enforced,6.170057341
2020-06-02,2,6,2020,21086,764,United_States_of_America,US,USA,329064917,America,91.98154661,6.41E-05,542,-270,Social Distancing and Wearing Masks Enforced,6.186237142
2020-06-01,1,6,2020,19807,602,United_States_of_America,US,USA,329064917,America,92.21098462,6.02E-05,-1279,-162,Social Distancing and Wearing Masks Enforced,6.147357791
2020-05-31,31,5,2020,23297,945,United_States_of_America,US,USA,329064917,America,91.92715005,7.08E-05,3490,343,Social Distancing and Wearing Masks Enforced,6.248193732
2020-05-30,30,5,2020,25337,1219,United_States_of_America,US,USA,329064917,America,92.28878082,7.70E-05,2040,274,Social Distancing and Wearing Masks Enforced,6.30034932
2020-05-29,29,5,2020,21817,1175,United_States_of_America,US,USA,329064917,America,92.34074625,6.63E-05,-3520,-44,Social Distancing and Wearing Masks Enforced,6.207412342
2020-05-28,28,5,2020,18721,1526,United_States_of_America,US,USA,329064917,America,93.95927187,5.69E-05,-3096,351,Social Distancing and Wearing Masks Enforced,6.112321011
2020-05-27,27,5,2020,18910,696,United_States_of_America,US,USA,329064917,America,94.58559206,5.75E-05,189,-830,Social Distancing and Wearing Masks Enforced,6.118562316
2020-05-26,26,5,2020,19064,500,United_States_of_America,US,USA,329064917,America,95.53920329,5.79E-05,154,-196,Social Distancing and Wearing Masks Enforced,6.123601875
2020-05-25,25,5,2020,20568,633,United_States_of_America,US,USA,329064917,America,95.25141813,6.25E-05,1504,133,Lockdown,6.170782776
2020-05-24,24,5,2020,21236,1080,United_States_of_America,US,USA,329064917,America,95.15721179,6.45E-05,668,447,Lockdown,6.190641501
2020-05-23,23,5,2020,24147,1305,United_States_of_America,US,USA,329064917,America,96.48704058,7.34E-05,2911,225,Lockdown,6.270459612
2020-05-22,22,5,2020,25434,1263,United_States_of_America,US,USA,329064917,America,97.34097543,7.73E-05,1287,-42,Lockdown,6.302723493
2020-05-21,21,5,2020,23285,1518,United_States_of_America,US,USA,329064917,America,98.2328967,7.08E-05,-2149,255,Lockdown,6.247873607
2020-05-20,20,5,2020,19970,1568,United_States_of_America,US,USA,329064917,America,98.48907716,6.07E-05,-3315,50,Lockdown,6.152450088
2020-05-19,19,5,2020,21841,791,United_States_of_America,US,USA,329064917,America,99.66544079,6.64E-05,1871,-777,Lockdown,6.208095472
2020-05-18,18,5,2020,18873,808,United_States_of_America,US,USA,329064917,America,99.89396712,5.74E-05,-2968,17,Lockdown,6.117345399
2020-05-17,17,5,2020,24487,1186,United_States_of_America,US,USA,329064917,America,101.7474008,7.44E-05,5614,378,Lockdown,6.279147251
2020-05-16,16,5,2020,25508,1662,United_States_of_America,US,USA,329064917,America,103.2063834,7.75E-05,1021,476,Lockdown,6.304528636
2020-05-15,15,5,2020,27143,1773,United_States_of_America,US,USA,329064917,America,105.7733541,8.25E-05,1635,111,Lockdown,6.343130348
2020-05-14,14,5,2020,20782,1746,United_States_of_America,US,USA,329064917,America,106.6163489,6.32E-05,-6361,-27,Lockdown,6.177214063
2020-05-13,13,5,2020,22048,1703,United_States_of_America,US,USA,329064917,America,108.6050143,6.70E-05,1266,-43,Lockdown,6.213956498
2020-05-12,12,5,2020,18117,1156,United_States_of_America,US,USA,329064917,America,109.2383239,5.51E-05,-3931,-547,Lockdown,6.091944229
2020-05-11,11,5,2020,20258,734,United_States_of_America,US,USA,329064917,America,110.5827395,6.16E-05,2141,-422,Lockdown,6.161346753
2020-05-10,10,5,2020,25612,1614,United_States_of_America,US,USA,329064917,America,112.5881189,7.78E-05,5354,880,Lockdown,6.307056763
2020-05-09,9,5,2020,26957,1510,United_States_of_America,US,USA,329064917,America,119.5523982,8.19E-05,1345,-104,Lockdown,6.338857935
2020-05-08,8,5,2020,28369,2239,United_States_of_America,US,USA,329064917,America,117.8490869,8.62E-05,1412,729,Lockdown,6.370579567
2020-05-07,7,5,2020,24128,2353,United_States_of_America,US,USA,329064917,America,117.2941812,7.33E-05,-4241,114,Lockdown,6.269970524
2020-05-06,6,5,2020,23841,2144,United_States_of_America,US,USA,329064917,America,115.3067314,7.25E-05,-287,-209,Lockdown,6.262535503
2020-05-05,5,5,2020,22593,1252,United_States_of_America,US,USA,329064917,America,119.393463,6.87E-05,-1248,-892,Lockdown,6.229128397
2020-05-04,4,5,2020,24972,1297,United_States_of_America,US,USA,329064917,America,121.0563568,7.59E-05,2379,45,Lockdown,6.291333389
2020-05-03,3,5,2020,29288,1317,United_States_of_America,US,USA,329064917,America,120.9436131,8.90E-05,4316,20,Lockdown,6.390388269
2020-05-02,2,5,2020,33955,2062,United_States_of_America,US,USA,329064917,America,122.0479545,0.000103186,4667,745,Lockdown,6.48225776
2020-05-01,1,5,2020,29917,2040,United_States_of_America,US,USA,329064917,America,121.0992055,9.09E-05,-4038,-22,Lockdown,6.403591018
2020-04-30,30,4,2020,27326,2611,United_States_of_America,US,USA,329064917,America,121.6310154,8.30E-05,-2591,571,Lockdown,6.347305373
2020-04-29,29,4,2020,24132,2110,United_States_of_America,US,USA,329064917,America,122.488597,7.33E-05,-3194,-501,Lockdown,6.270073522
2020-04-28,28,4,2020,22541,1369,United_States_of_America,US,USA,329064917,America,123.336454,6.85E-05,-1591,-741,Lockdown,6.227696685
2020-04-27,27,4,2020,26857,1687,United_States_of_America,US,USA,329064917,America,124.0907125,8.16E-05,4316,318,Lockdown,6.336548738
2020-04-26,26,4,2020,48529,2172,United_States_of_America,US,USA,329064917,America,124.3225816,0.000147475,21672,485,Lockdown,6.704152271
2020-04-25,25,4,2020,21352,1054,United_States_of_America,US,USA,329064917,America,118.2028165,6.49E-05,-27177,-1118,Lockdown,6.194026259
2020-04-24,24,4,2020,26543,3179,United_States_of_America,US,USA,329064917,America,122.5104772,8.07E-05,5191,2125,Lockdown,6.329241569
2020-04-23,23,4,2020,17588,1721,United_States_of_America,US,USA,329064917,America,124.7465101,5.34E-05,-8955,-1458,Lockdown,6.073531669
2020-04-22,22,4,2020,37289,2524,United_States_of_America,US,USA,329064917,America,129.5282414,0.000113318,19701,803,Lockdown,6.540453393
2020-04-21,21,4,2020,28065,1857,United_States_of_America,US,USA,329064917,America,127.4994624,8.53E-05,-9224,-667,Lockdown,6.363885459
2020-04-20,20,4,2020,24601,1772,United_States_of_America,US,USA,329064917,America,128.2579753,7.48E-05,-3464,-85,Lockdown,6.282033183
2020-04-19,19,4,2020,32922,1856,United_States_of_America,US,USA,329064917,America,128.5001768,0.000100047,8321,84,Lockdown,6.463061623
2020-04-18,18,4,2020,30833,3770,United_States_of_America,US,USA,329064917,America,128.9104302,9.37E-05,-2089,1914,Lockdown,6.422329649
2020-04-17,17,4,2020,31667,2299,United_States_of_America,US,USA,329064917,America,129.3942253,9.62E-05,834,-1471,Lockdown,6.438912821
2020-04-16,16,4,2020,30148,4928,United_States_of_America,US,USA,329064917,America,128.5287426,9.16E-05,-1519,2629,Lockdown,6.408370143
2020-04-15,15,4,2020,26922,2408,United_States_of_America,US,USA,329064917,America,127.6033932,8.18E-05,-3226,-2520,Lockdown,6.338050692
2020-04-14,14,4,2020,25023,1541,United_States_of_America,US,USA,329064917,America,127.0187062,7.60E-05,-1899,-867,Lockdown,6.29260104
2020-04-13,13,4,2020,27620,1500,United_States_of_America,US,USA,329064917,America,125.9769664,8.39E-05,2597,-41,Lockdown,6.3539546
2020-04-12,12,4,2020,28391,1831,United_States_of_America,US,USA,329064917,America,123.162932,8.63E-05,771,331,Lockdown,6.371061222
2020-04-11,11,4,2020,35527,2087,United_States_of_America,US,USA,329064917,America,120.6065975,0.000107963,7136,256,Lockdown,6.510377424
2020-04-10,10,4,2020,33901,1873,United_States_of_America,US,USA,329064917,America,115.4914974,0.000103022,-1626,-214,Lockdown,6.48126884
2020-04-09,9,4,2020,33323,1922,United_States_of_America,US,USA,329064917,America,110.2937388,0.000101266,-578,49,Lockdown,6.470583952
2020-04-08,8,4,2020,30613,1906,United_States_of_America,US,USA,329064917,America,104.4104012,9.30E-05,-2710,-16,Lockdown,6.417880401
2020-04-07,7,4,2020,30561,1342,United_States_of_America,US,USA,329064917,America,97.77827516,9.29E-05,-52,-564,Lockdown,6.416824088
2020-04-06,6,4,2020,25398,1146,United_States_of_America,US,USA,329064917,America,91.90557376,7.72E-05,-5163,-196,Lockdown,6.301843415
2020-04-05,5,4,2020,34272,1344,United_States_of_America,US,USA,329064917,America,86.75795725,0.00010415,8874,198,Lockdown,6.488031562
2020-04-04,4,4,2020,32425,1104,United_States_of_America,US,USA,329064917,America,78.50760949,9.85E-05,-1847,-240,Lockdown,6.45361025
2020-04-03,3,4,2020,28819,915,United_States_of_America,US,USA,329064917,America,70.28704309,8.76E-05,-3606,-189,Lockdown,6.380358069
2020-04-02,2,4,2020,27103,1059,United_States_of_America,US,USA,329064917,America,62.99851163,8.24E-05,-1716,144,Lockdown,6.342214026
2020-04-01,1,4,2020,24998,909,United_States_of_America,US,USA,329064917,America,55.67017039,7.60E-05,-2105,-150,Lockdown,6.291979965
2020-03-31,31,3,2020,21595,661,United_States_of_America,US,USA,329064917,America,48.61016527,6.56E-05,-3403,-248,Lockdown,6.20105753
2020-03-30,30,3,2020,18360,318,United_States_of_America,US,USA,329064917,America,42.31718205,5.58E-05,-3235,-343,Lockdown,6.100222685
2020-03-29,29,3,2020,19979,484,United_States_of_America,US,USA,329064917,America,36.98783848,6.07E-05,1619,166,Lockdown,6.152730046
2020-03-28,28,3,2020,18695,411,United_States_of_America,US,USA,329064917,America,31.15251572,5.68E-05,-1284,-73,Lockdown,6.111457492
2020-03-27,27,3,2020,16797,246,United_States_of_America,US,USA,329064917,America,25.62655441,5.10E-05,-1898,-165,Lockdown,6.044939977
2020-03-26,26,3,2020,13963,249,United_States_of_America,US,USA,329064917,America,20.62875636,4.24E-05,-2834,3,Lockdown,5.930123914
2020-03-25,25,3,2020,8789,211,United_States_of_America,US,USA,329064917,America,16.47273751,2.67E-05,-5174,-38,Lockdown,5.642501738
2020-03-24,24,3,2020,11236,119,United_States_of_America,US,USA,329064917,America,13.88419052,3.41E-05,2447,-92,Lockdown,5.795115249
2020-03-23,23,3,2020,8459,131,United_States_of_America,US,USA,329064917,America,10.53044497,2.57E-05,-2777,12,Lockdown,5.618723265
2020-03-22,22,3,2020,7123,80,United_States_of_America,US,USA,329064917,America,7.99659843,2.16E-05,-1336,-51,Lockdown,5.511914561
2020-03-21,21,3,2020,5374,110,United_States_of_America,US,USA,329064917,America,5.86084964,1.63E-05,-1749,30,Lockdown,5.33684942
2020-03-20,20,3,2020,4835,0,United_States_of_America,US,USA,329064917,America,4.25964583,1.47E-05,-539,-110,Lockdown,5.271179672
2020-03-19,19,3,2020,2988,42,United_States_of_America,US,USA,329064917,America,2.81281885,9.08E-06,-1847,42,Lockdown,4.972145545
2020-03-18,18,3,2020,1766,23,United_States_of_America,US,USA,329064917,America,1.91512364,5.37E-06,-1222,-19,Social Distancing and Wearing Masks Enforced,4.645393478
2020-03-17,17,3,2020,887,16,United_States_of_America,US,USA,329064917,America,1.38513702,2.70E-06,-879,-7,Social Distancing and Wearing Masks Enforced,4.217525218
2020-03-16,16,3,2020,823,12,United_States_of_America,US,USA,329064917,America,1.11983983,2.50E-06,-64,-4,Social Distancing and Wearing Masks Enforced,4.170994202
2020-03-15,15,3,2020,777,10,United_States_of_America,US,USA,329064917,America,0.87581503,2.36E-06,-46,-2,Social Distancing and Wearing Masks Enforced,4.135257595
2020-03-14,14,3,2020,511,7,United_States_of_America,US,USA,329064917,America,0.64060308,1.55E-06,-266,-3,Social Distancing and Wearing Masks Enforced,3.874874291
2020-03-13,13,3,2020,351,10,United_States_of_America,US,USA,329064917,America,0.48713792,1.07E-06,-160,3,Social Distancing and Wearing Masks Enforced,3.641511225
2020-03-12,12,3,2020,287,2,United_States_of_America,US,USA,329064917,America,0.38077593,8.72E-07,-64,-8,Social Distancing and Wearing Masks Enforced,3.516434012
2020-03-11,11,3,2020,271,2,United_States_of_America,US,USA,329064917,America,0.29538245,8.24E-07,-16,0,Social Distancing and Wearing Masks Enforced,3.480792131
2020-03-10,10,3,2020,200,5,United_States_of_America,US,USA,329064917,America,0.21302787,6.08E-07,-71,3,Social Distancing and Wearing Masks Enforced,3.292029674
2020-03-09,9,3,2020,121,4,United_States_of_America,US,USA,329064917,America,0.15771964,3.68E-07,-79,-1,Social Distancing and Wearing Masks Enforced,2.979792205
2020-03-08,8,3,2020,95,3,United_States_of_America,US,USA,329064917,America,0.12094878,2.89E-07,-26,-1,Social Distancing and Wearing Masks Enforced,2.8294828
2020-03-07,7,3,2020,105,2,United_States_of_America,US,USA,329064917,America,0.0920791,3.19E-07,10,-1,Social Distancing and Wearing Masks Enforced,2.89166815
2020-03-06,6,3,2020,74,1,United_States_of_America,US,USA,329064917,America,0.06594443,2.25E-07,-31,-1,Social Distancing and Wearing Masks Enforced,2.674266003
2020-03-05,5,3,2020,34,2,United_States_of_America,US,USA,329064917,America,0.04376036,1.03E-07,-40,1,Social Distancing and Wearing Masks Enforced,2.191050986
2020-03-04,4,3,2020,22,3,United_States_of_America,US,USA,329064917,America,0.03342805,6.69E-08,-12,1,Social Distancing and Wearing Masks Enforced,1.92057266
2020-03-03,3,3,2020,14,4,United_States_of_America,US,USA,329064917,America,0.02674244,4.25E-08,-8,1,Social Distancing and Wearing Masks Enforced,1.639738513
2020-03-02,2,3,2020,20,1,United_States_of_America,US,USA,329064917,America,0.02248796,6.08E-08,6,-3,Social Distancing and Wearing Masks Enforced,1.861353116
2020-03-01,1,3,2020,3,1,United_States_of_America,US,USA,329064917,America,0.01641014,9.12E-09,-17,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-02-29,29,2,2020,6,0,United_States_of_America,US,USA,329064917,America,0.01549846,1.82E-08,3,-1,Social Distancing and Wearing Masks Enforced,1.113282753
2020-02-28,28,2,2020,1,0,United_States_of_America,US,USA,329064917,America,0.01367511,3.04E-09,-5,0,Social Distancing and Wearing Masks Enforced,0
2020-02-27,27,2,2020,6,0,United_States_of_America,US,USA,329064917,America,0.01367511,1.82E-08,5,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-02-26,26,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.01215566,0,-6,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-25,25,2,2020,18,0,United_States_of_America,US,USA,329064917,America,0.01215566,5.47E-08,18,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-02-24,24,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.0069895,0,-18,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-23,23,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.0069895,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-22,22,2,2020,19,0,United_States_of_America,US,USA,329064917,America,0.0069895,5.77E-08,19,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-02-21,21,2,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00121557,3.04E-09,-18,0,Social Distancing and Wearing Masks Enforced,0
2020-02-20,20,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00091167,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-19,19,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00121557,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-18,18,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00121557,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-17,17,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00121557,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-16,16,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00212724,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-15,15,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00243113,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-14,14,2,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00273502,3.04E-09,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-13,13,2,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00273502,3.04E-09,0,0,Social Distancing and Wearing Masks Enforced,0
2020-02-12,12,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00243113,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-11,11,2,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00243113,3.04E-09,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-10,10,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00212724,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-09,9,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00303891,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-08,8,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00303891,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-07,7,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00334281,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-06,6,2,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00334281,3.04E-09,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-05,5,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00303891,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-04,4,2,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00303891,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-03,3,2,2020,3,0,United_States_of_America,US,USA,329064917,America,0.00334281,9.12E-09,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-02-02,2,2,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00243113,3.04E-09,-2,0,Social Distancing and Wearing Masks Enforced,0
2020-02-01,1,2,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00212724,3.04E-09,0,0,Social Distancing and Wearing Masks Enforced,0
2020-01-31,31,1,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00182335,3.04E-09,0,0,Social Distancing and Wearing Masks Enforced,0
2020-01-30,30,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00151946,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-29,29,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00151946,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-28,28,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00151946,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-27,27,1,2020,3,0,United_States_of_America,US,USA,329064917,America,0.00151946,9.12E-09,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-01-26,26,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00060778,0,-3,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-25,25,1,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00060778,3.04E-09,1,0,Social Distancing and Wearing Masks Enforced,0
2020-01-24,24,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00030389,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-23,23,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00030389,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-22,22,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0.00030389,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-21,21,1,2020,1,0,United_States_of_America,US,USA,329064917,America,0.00030389,3.04E-09,1,0,Social Distancing and Wearing Masks Enforced,0
2020-01-20,20,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-19,19,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-18,18,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-17,17,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-16,16,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-15,15,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-14,14,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-13,13,1,2020,0,0,United_States_of_America,US,USA,329064917,America,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-12,12,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-11,11,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-10,10,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-09,9,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-08,8,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-07,7,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-06,6,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-05,5,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-04,4,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-03,3,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-02,2,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-01,1,1,2020,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2019-12-31,31,12,2019,0,0,United_States_of_America,US,USA,329064917,America,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-09,9,12,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,1.02444836,6.27E-07,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-12-08,8,12,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,1.1289839,1.25E-06,3,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-12-07,7,12,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.02444836,2.09E-07,-5,0,Social Distancing and Wearing Masks Enforced,0
2020-12-06,6,12,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,1.04535546,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-05,5,12,2020,9,0,New_Zealand,NZ,NZL,4783062,Oceania,1.23351945,1.88E-06,9,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-12-04,4,12,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,1.17079812,0,-9,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-03,3,12,2020,9,0,New_Zealand,NZ,NZL,4783062,Oceania,1.23351945,1.88E-06,9,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-12-02,2,12,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.08716968,2.09E-07,-8,0,Social Distancing and Wearing Masks Enforced,0
2020-12-01,1,12,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,1.1289839,6.27E-07,2,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-11-30,30,11,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,1.14989101,1.25E-06,3,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-11-29,29,11,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,1.02444836,0,-6,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-28,28,11,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,1.08716968,6.27E-07,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-11-27,27,11,2020,7,0,New_Zealand,NZ,NZL,4783062,Oceania,1.08716968,1.46E-06,4,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-11-26,26,11,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.02444836,2.09E-07,-6,0,Social Distancing and Wearing Masks Enforced,0
2020-11-25,25,11,2020,8,0,New_Zealand,NZ,NZL,4783062,Oceania,1.06626257,1.67E-06,7,0,Social Distancing and Wearing Masks Enforced,1.292029674
2020-11-24,24,11,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.91991281,2.09E-07,-7,0,Social Distancing and Wearing Masks Enforced,0
2020-11-23,23,11,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.91991281,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-11-22,22,11,2020,9,0,New_Zealand,NZ,NZL,4783062,Oceania,0.96172703,1.88E-06,7,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-11-21,21,11,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,0.8990057,1.25E-06,-3,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-11-20,20,11,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.81537726,6.27E-07,-3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-11-19,19,11,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.77356304,4.18E-07,-1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-11-18,18,11,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.77356304,6.27E-07,1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-11-17,17,11,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.77356304,8.36E-07,1,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-11-16,16,11,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.79447015,0,-4,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-15,15,11,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.87809859,6.27E-07,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-11-14,14,11,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.85719148,6.27E-07,0,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-11-13,13,11,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.94081992,8.36E-07,1,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-11-12,12,11,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.87809859,6.27E-07,-1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-11-11,11,11,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.94081992,2.09E-07,-2,0,Social Distancing and Wearing Masks Enforced,0
2020-11-10,10,11,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.96172703,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-11-09,9,11,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.96172703,8.36E-07,3,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-11-08,8,11,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,0.98263414,1.25E-06,2,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-11-07,7,11,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.87809859,4.18E-07,-4,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-11-06,6,11,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.06626257,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-11-05,5,11,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,1.23351945,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-11-04,4,11,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,1.23351945,6.27E-07,1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-11-03,3,11,2020,5,0,New_Zealand,NZ,NZL,4783062,Oceania,1.69347585,1.05E-06,2,0,Social Distancing and Wearing Masks Enforced,1
2020-11-02,2,11,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,1.60984742,8.36E-07,-1,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-11-01,1,11,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,1.52621898,4.18E-07,-2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-10-31,31,10,2020,7,0,New_Zealand,NZ,NZL,4783062,Oceania,1.54712609,1.46E-06,5,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-10-30,30,10,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.46349765,2.09E-07,-6,0,Social Distancing and Wearing Masks Enforced,0
2020-10-29,29,10,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,1.52621898,1.25E-06,5,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-10-28,28,10,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,1.44259054,4.18E-07,-4,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-10-27,27,10,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.44259054,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-10-26,26,10,2020,5,0,New_Zealand,NZ,NZL,4783062,Oceania,1.44259054,1.05E-06,4,0,Social Distancing and Wearing Masks Enforced,1
2020-10-25,25,10,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.33805499,2.09E-07,-4,0,Social Distancing and Wearing Masks Enforced,0
2020-10-24,24,10,2020,11,0,New_Zealand,NZ,NZL,4783062,Oceania,1.33805499,2.30E-06,10,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-10-23,23,10,2020,9,0,New_Zealand,NZ,NZL,4783062,Oceania,1.19170523,1.88E-06,-2,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-10-22,22,10,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,1.04535546,4.18E-07,-7,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-10-21,21,10,2020,25,0,New_Zealand,NZ,NZL,4783062,Oceania,1.06626257,5.23E-06,23,0,Social Distancing and Wearing Masks Enforced,2
2020-10-20,20,10,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.60630617,2.09E-07,-24,0,Social Distancing and Wearing Masks Enforced,0
2020-10-19,19,10,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.64812039,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-18,18,10,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.6690275,6.27E-07,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-10-17,17,10,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.71084172,6.27E-07,0,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-10-16,16,10,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.6690275,8.36E-07,1,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-10-15,15,10,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.83628437,4.18E-07,-2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-10-14,14,10,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.79447015,4.18E-07,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-10-13,13,10,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.77356304,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-10-12,12,10,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.79447015,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-10-11,11,10,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.79447015,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-10-10,10,10,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.81537726,8.36E-07,3,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-10-09,9,10,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.77356304,4.18E-07,-2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-10-08,8,10,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.77356304,6.27E-07,1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-10-07,7,10,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.77356304,6.27E-07,0,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-10-06,6,10,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.79447015,6.27E-07,0,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-10-05,5,10,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.73174883,2.09E-07,-2,0,Social Distancing and Wearing Masks Enforced,0
2020-10-04,4,10,2020,5,0,New_Zealand,NZ,NZL,4783062,Oceania,0.71084172,1.05E-06,4,0,Social Distancing and Wearing Masks Enforced,1
2020-10-03,3,10,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.68993461,2.09E-07,-4,0,Social Distancing and Wearing Masks Enforced,0
2020-10-02,2,10,2020,12,0,New_Zealand,NZ,NZL,4783062,Oceania,0.71084172,2.51E-06,11,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-10-01,1,10,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4599564,0,-12,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-30,30,9,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.60630617,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-09-29,29,9,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.60630617,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-09-28,28,9,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.62721328,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-27,27,9,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.64812039,4.18E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-09-26,26,9,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.64812039,4.18E-07,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-09-25,25,9,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.64812039,4.18E-07,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-09-24,24,9,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.62721328,6.27E-07,1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-09-23,23,9,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.64812039,8.36E-07,1,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-09-22,22,9,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.68993461,0,-4,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-21,21,9,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.81537726,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-20,20,9,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.8990057,8.36E-07,4,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-09-19,19,9,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.98263414,4.18E-07,-2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-09-18,18,9,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.94081992,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-17,17,9,2020,7,0,New_Zealand,NZ,NZL,4783062,Oceania,1.04535546,1.46E-06,7,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-09-16,16,9,2020,1,1,New_Zealand,NZ,NZL,4783062,Oceania,0.94081992,2.09E-07,-6,1,Social Distancing and Wearing Masks Enforced,0
2020-09-15,15,9,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,1.02444836,6.27E-07,2,-1,Social Distancing and Wearing Masks Enforced,0.682606194
2020-09-14,14,9,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.25442656,2.09E-07,-2,0,Social Distancing and Wearing Masks Enforced,0
2020-09-13,13,9,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,1.42168343,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-09-12,12,9,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,1.42168343,4.18E-07,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-09-11,11,9,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,1.65166163,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-09-10,10,9,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,1.88163984,8.36E-07,3,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-09-09,9,9,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,1.94436116,1.25E-06,2,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-09-08,8,9,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,1.92345406,1.25E-06,0,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-09-07,7,9,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,1.94436116,8.36E-07,-2,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-09-06,6,9,2020,8,2,New_Zealand,NZ,NZL,4783062,Oceania,2.0279896,1.67E-06,4,2,Social Distancing and Wearing Masks Enforced,1.292029674
2020-09-05,5,9,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,1.92345406,0,-8,-2,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-04,4,9,2020,5,0,New_Zealand,NZ,NZL,4783062,Oceania,2.04889671,1.05E-06,5,0,Social Distancing and Wearing Masks Enforced,1
2020-09-03,3,9,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,2.17433937,4.18E-07,-3,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-09-02,2,9,2020,5,0,New_Zealand,NZ,NZL,4783062,Oceania,2.23706069,1.05E-06,3,0,Social Distancing and Wearing Masks Enforced,1
2020-09-01,1,9,2020,14,0,New_Zealand,NZ,NZL,4783062,Oceania,2.2579678,2.93E-06,9,0,Social Distancing and Wearing Masks Enforced,1.639738513
2020-08-31,31,8,2020,9,0,New_Zealand,NZ,NZL,4783062,Oceania,2.23706069,1.88E-06,-5,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-08-30,30,8,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,2.23706069,4.18E-07,-7,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-08-29,29,8,2020,13,0,New_Zealand,NZ,NZL,4783062,Oceania,2.4670389,2.72E-06,11,0,Social Distancing and Wearing Masks Enforced,1.593692641
2020-08-28,28,8,2020,12,0,New_Zealand,NZ,NZL,4783062,Oceania,2.34159624,2.51E-06,-1,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-08-27,27,8,2020,7,0,New_Zealand,NZ,NZL,4783062,Oceania,2.36250335,1.46E-06,-5,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-08-26,26,8,2020,5,0,New_Zealand,NZ,NZL,4783062,Oceania,2.59248155,1.05E-06,-2,0,Social Distancing and Wearing Masks Enforced,1
2020-08-25,25,8,2020,7,0,New_Zealand,NZ,NZL,4783062,Oceania,2.48794601,1.46E-06,2,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-08-24,24,8,2020,8,0,New_Zealand,NZ,NZL,4783062,Oceania,2.36250335,1.67E-06,1,0,Social Distancing and Wearing Masks Enforced,1.292029674
2020-08-23,23,8,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,2.19524648,6.27E-07,-5,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-08-22,22,8,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,2.13252515,1.25E-06,3,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-08-21,21,8,2020,11,0,New_Zealand,NZ,NZL,4783062,Oceania,2.00708249,2.30E-06,5,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-08-20,20,8,2020,5,0,New_Zealand,NZ,NZL,4783062,Oceania,1.77710429,1.05E-06,-6,0,Social Distancing and Wearing Masks Enforced,1
2020-08-19,19,8,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,1.67256874,1.25E-06,1,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-08-18,18,8,2020,13,0,New_Zealand,NZ,NZL,4783062,Oceania,1.58894031,2.72E-06,7,0,Social Distancing and Wearing Masks Enforced,1.593692641
2020-08-17,17,8,2020,9,0,New_Zealand,NZ,NZL,4783062,Oceania,1.31714789,1.88E-06,-4,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-08-16,16,8,2020,13,0,New_Zealand,NZ,NZL,4783062,Oceania,1.17079812,2.72E-06,4,0,Social Distancing and Wearing Masks Enforced,1.593692641
2020-08-15,15,8,2020,7,0,New_Zealand,NZ,NZL,4783062,Oceania,0.96172703,1.46E-06,-6,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-08-14,14,8,2020,13,0,New_Zealand,NZ,NZL,4783062,Oceania,0.85719148,2.72E-06,6,0,Social Distancing and Wearing Masks Enforced,1.593692641
2020-08-13,13,8,2020,18,0,New_Zealand,NZ,NZL,4783062,Oceania,0.58539906,3.76E-06,5,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-08-12,12,8,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.2299782,0,-18,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-11,11,8,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-08-10,10,8,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-09,9,8,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-08,8,8,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-07,7,8,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-06,6,8,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.29269953,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-05,5,8,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.29269953,4.18E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-08-04,4,8,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-03,3,8,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,4.18E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-08-02,2,8,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,6.27E-07,1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-08-01,1,8,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,4.18E-07,-1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-07-31,31,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.2299782,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-30,30,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-07-29,29,7,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-07-28,28,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-07-27,27,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-26,26,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-25,25,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-24,24,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.29269953,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-07-23,23,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.31360664,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-22,22,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.37632797,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-21,21,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.39723508,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-07-20,20,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4390493,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-07-19,19,7,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.41814219,6.27E-07,2,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-07-18,18,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.41814219,2.09E-07,-2,0,Social Distancing and Wearing Masks Enforced,0
2020-07-17,17,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.39723508,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-07-16,16,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.37632797,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-07-15,15,7,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.39723508,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-07-14,14,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.35542086,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-07-13,13,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.33451375,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-12,12,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.37632797,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-07-11,11,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4390493,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-07-10,10,7,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4599564,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-07-09,9,7,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4390493,6.27E-07,1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-07-08,8,7,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4390493,2.09E-07,-2,0,Social Distancing and Wearing Masks Enforced,0
2020-07-07,7,7,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4390493,6.27E-07,2,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-07-06,6,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.41814219,0,-3,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-05,5,7,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4599564,6.27E-07,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-07-04,4,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4390493,0,-3,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-03,3,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.48086351,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-02,2,7,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.48086351,4.18E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-07-01,1,7,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4599564,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-30,30,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4599564,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-29,29,6,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.50177062,4.18E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-06-28,28,6,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4599564,8.36E-07,2,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-06-27,27,6,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.37632797,4.18E-07,-2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-06-26,26,6,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.33451375,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-06-25,25,6,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.31360664,6.27E-07,2,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-06-24,24,6,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,2.09E-07,-2,0,Social Distancing and Wearing Masks Enforced,0
2020-06-23,23,6,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.2299782,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-06-22,22,6,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.18816398,4.18E-07,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-06-21,21,6,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.14634977,4.18E-07,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-06-20,20,6,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.10453555,4.18E-07,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-06-19,19,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.06272133,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-18,18,6,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.06272133,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-06-17,17,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.04181422,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-16,16,6,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.04181422,4.18E-07,2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-06-15,15,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,-2,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-14,14,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-13,13,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-12,12,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-11,11,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-10,10,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-09,9,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-08,8,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-07,7,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-06,6,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-05,5,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-04,4,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.02090711,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-03,3,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.02090711,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-02,2,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.02090711,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-06-01,1,6,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.10453555,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-31,31,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.10453555,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-30,30,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.12544266,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-29,29,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.12544266,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-28,28,5,2020,0,1,New_Zealand,NZ,NZL,4783062,Oceania,0.14634977,0,0,1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-27,27,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.14634977,0,0,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-26,26,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.14634977,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-25,25,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.14634977,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-24,24,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.20907109,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-23,23,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-22,22,5,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-05-21,21,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.29269953,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-20,20,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.31360664,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-19,19,5,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,0.33451375,8.36E-07,4,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-05-18,18,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.25088531,0,-4,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-17,17,5,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.27179242,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-05-16,16,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.29269953,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-15,15,5,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.33451375,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-05-14,14,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.37632797,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-13,13,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.4390493,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-12,12,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.48086351,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-11,11,5,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.52267773,6.27E-07,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-05-10,10,5,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.48086351,4.18E-07,-1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-09,9,5,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.52267773,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-05-08,8,5,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.56449195,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-07,7,5,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.56449195,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-05-06,6,5,2020,1,1,New_Zealand,NZ,NZL,4783062,Oceania,0.54358484,2.09E-07,0,1,Social Distancing and Wearing Masks Enforced,0
2020-05-05,5,5,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.62721328,0,-1,-1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-04,4,5,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.6690275,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-05-03,3,5,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.79447015,4.18E-07,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-02,2,5,2020,2,1,New_Zealand,NZ,NZL,4783062,Oceania,0.83628437,4.18E-07,0,1,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-01,1,5,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.96172703,6.27E-07,1,-1,Social Distancing and Wearing Masks Enforced,0.682606194
2020-04-30,30,4,2020,3,0,New_Zealand,NZ,NZL,4783062,Oceania,0.94081992,6.27E-07,0,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-04-29,29,4,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,1.00354125,4.18E-07,-1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-04-28,28,4,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,1.08716968,4.18E-07,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-04-27,27,4,2020,1,1,New_Zealand,NZ,NZL,4783062,Oceania,1.21261234,2.09E-07,-1,1,Social Distancing and Wearing Masks Enforced,0
2020-04-26,26,4,2020,4,0,New_Zealand,NZ,NZL,4783062,Oceania,1.50531187,8.36E-07,3,-1,Social Distancing and Wearing Masks Enforced,0.861353116
2020-04-25,25,4,2020,3,1,New_Zealand,NZ,NZL,4783062,Oceania,1.71438296,6.27E-07,-1,1,Social Distancing and Wearing Masks Enforced,0.682606194
2020-04-24,24,4,2020,2,1,New_Zealand,NZ,NZL,4783062,Oceania,2.06980382,4.18E-07,-1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-04-23,23,4,2020,0,2,New_Zealand,NZ,NZL,4783062,Oceania,2.50885312,0,-2,1,Social Distancing and Wearing Masks Enforced,#NUM!
2020-04-22,22,4,2020,5,1,New_Zealand,NZ,NZL,4783062,Oceania,2.98971663,1.05E-06,5,-1,Social Distancing and Wearing Masks Enforced,1
2020-04-21,21,4,2020,2,1,New_Zealand,NZ,NZL,4783062,Oceania,3.42876592,4.18E-07,-3,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-04-20,20,4,2020,7,0,New_Zealand,NZ,NZL,4783062,Oceania,4.0559792,1.46E-06,5,-1,Social Distancing and Wearing Masks Enforced,1.209061955
2020-04-19,19,4,2020,4,1,New_Zealand,NZ,NZL,4783062,Oceania,4.7250067,8.36E-07,-3,1,Social Distancing and Wearing Masks Enforced,0.861353116
2020-04-18,18,4,2020,8,0,New_Zealand,NZ,NZL,4783062,Oceania,5.64491951,1.67E-06,4,-1,Social Distancing and Wearing Masks Enforced,1.292029674
2020-04-17,17,4,2020,2,2,New_Zealand,NZ,NZL,4783062,Oceania,6.56483232,4.18E-07,-6,2,Social Distancing and Wearing Masks Enforced,0.430676558
2020-04-16,16,4,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,7.54746646,1.25E-06,4,-2,Social Distancing and Wearing Masks Enforced,1.113282753
2020-04-15,15,4,2020,6,0,New_Zealand,NZ,NZL,4783062,Oceania,9.01096411,1.25E-06,0,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-04-14,14,4,2020,8,4,New_Zealand,NZ,NZL,4783062,Oceania,8.88552145,1.67E-06,2,4,Social Distancing and Wearing Masks Enforced,1.292029674
2020-04-13,13,4,2020,15,1,New_Zealand,NZ,NZL,4783062,Oceania,10.70443996,3.14E-06,7,-3,Social Distancing and Wearing Masks Enforced,1.682606194
2020-04-12,12,4,2020,14,0,New_Zealand,NZ,NZL,4783062,Oceania,11.97977363,2.93E-06,-1,-1,Social Distancing and Wearing Masks Enforced,1.639738513
2020-04-11,11,4,2020,20,2,New_Zealand,NZ,NZL,4783062,Oceania,12.94150065,4.18E-06,6,2,Social Distancing and Wearing Masks Enforced,1.861353116
2020-04-10,10,4,2020,23,1,New_Zealand,NZ,NZL,4783062,Oceania,14.15411299,4.81E-06,3,-1,Social Distancing and Wearing Masks Enforced,1.948192093
2020-04-09,9,4,2020,23,0,New_Zealand,NZ,NZL,4783062,Oceania,15.26218979,4.81E-06,0,-1,Social Distancing and Wearing Masks Enforced,1.948192093
2020-04-08,8,4,2020,26,0,New_Zealand,NZ,NZL,4783062,Oceania,16.30754525,5.44E-06,3,0,Social Distancing and Wearing Masks Enforced,2.024369199
2020-04-07,7,4,2020,32,0,New_Zealand,NZ,NZL,4783062,Oceania,16.74659455,6.69E-06,6,0,Social Distancing and Wearing Masks Enforced,2.15338279
2020-04-06,6,4,2020,39,0,New_Zealand,NZ,NZL,4783062,Oceania,16.91385142,8.15E-06,7,0,Social Distancing and Wearing Masks Enforced,2.276298836
2020-04-05,5,4,2020,48,0,New_Zealand,NZ,NZL,4783062,Oceania,16.85113009,1.00E-05,9,0,Social Distancing and Wearing Masks Enforced,2.405312427
2020-04-04,4,4,2020,52,0,New_Zealand,NZ,NZL,4783062,Oceania,16.11938127,1.09E-05,4,0,Social Distancing and Wearing Masks Enforced,2.455045757
2020-04-03,3,4,2020,49,0,New_Zealand,NZ,NZL,4783062,Oceania,15.32491111,1.02E-05,-3,0,Social Distancing and Wearing Masks Enforced,2.41812391
2020-04-02,2,4,2020,76,0,New_Zealand,NZ,NZL,4783062,Oceania,14.53044096,1.59E-05,27,0,Social Distancing and Wearing Masks Enforced,2.690835917
2020-04-01,1,4,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,13.10875753,0,-76,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-31,31,3,2020,95,0,New_Zealand,NZ,NZL,4783062,Oceania,13.35964284,1.99E-05,95,0,Social Distancing and Wearing Masks Enforced,2.8294828
2020-03-30,30,3,2020,76,0,New_Zealand,NZ,NZL,4783062,Oceania,11.41528168,1.59E-05,-19,0,Social Distancing and Wearing Masks Enforced,2.690835917
2020-03-29,29,3,2020,60,1,New_Zealand,NZ,NZL,4783062,Oceania,9.84724848,1.25E-05,-16,1,Social Distancing and Wearing Masks Enforced,2.543959311
2020-03-28,28,3,2020,78,0,New_Zealand,NZ,NZL,4783062,Oceania,8.61372903,1.63E-05,18,-1,Social Distancing and Wearing Masks Enforced,2.706975394
2020-03-27,27,3,2020,76,0,New_Zealand,NZ,NZL,4783062,Oceania,7.00388161,1.59E-05,-2,0,Social Distancing and Wearing Masks Enforced,2.690835917
2020-03-26,26,3,2020,73,0,New_Zealand,NZ,NZL,4783062,Oceania,5.43584842,1.53E-05,-3,0,Social Distancing and Wearing Masks Enforced,2.665812336
2020-03-25,25,3,2020,47,0,New_Zealand,NZ,NZL,4783062,Oceania,3.93053655,9.83E-06,-26,0,Social Distancing and Wearing Masks Enforced,2.392231208
2020-03-24,24,3,2020,40,0,New_Zealand,NZ,NZL,4783062,Oceania,2.94790241,8.36E-06,-7,0,Social Distancing and Wearing Masks Enforced,2.292029674
2020-03-23,23,3,2020,36,0,New_Zealand,NZ,NZL,4783062,Oceania,2.11161804,7.53E-06,-4,0,Social Distancing and Wearing Masks Enforced,2.226565505
2020-03-22,22,3,2020,13,0,New_Zealand,NZ,NZL,4783062,Oceania,1.3589621,2.72E-06,-23,0,Social Distancing and Wearing Masks Enforced,1.593692641
2020-03-21,21,3,2020,14,0,New_Zealand,NZ,NZL,4783062,Oceania,1.10807679,2.93E-06,1,0,Social Distancing and Wearing Masks Enforced,1.639738513
2020-03-20,20,3,2020,11,0,New_Zealand,NZ,NZL,4783062,Oceania,0.81537726,2.30E-06,-3,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-03-19,19,3,2020,8,0,New_Zealand,NZ,NZL,4783062,Oceania,0.58539906,1.67E-06,-3,0,Social Distancing and Wearing Masks Enforced,1.292029674
2020-03-18,18,3,2020,12,0,New_Zealand,NZ,NZL,4783062,Oceania,0.41814219,2.51E-06,4,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-03-15,15,3,2020,2,0,New_Zealand,NZ,NZL,4783062,Oceania,0.16725687,4.18E-07,-10,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-03-14,14,3,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.12544266,2.09E-07,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-03-07,7,3,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.10453555,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-03-06,6,3,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.08362844,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-03-05,5,3,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.06272133,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-03-04,4,3,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.04181422,2.09E-07,0,0,Social Distancing and Wearing Masks Enforced,0
2020-03-02,2,3,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.02090711,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-01,1,3,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.02090711,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-29,29,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0.02090711,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-28,28,2,2020,1,0,New_Zealand,NZ,NZL,4783062,Oceania,0.02090711,2.09E-07,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-27,27,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-26,26,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-25,25,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-24,24,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-23,23,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-22,22,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-21,21,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-20,20,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-19,19,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-18,18,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-17,17,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-16,16,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-15,15,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-14,14,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-13,13,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-12,12,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-11,11,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-10,10,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-09,9,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-08,8,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-07,7,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-06,6,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-05,5,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-04,4,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-03,3,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-02,2,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-01,1,2,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-31,31,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-30,30,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-29,29,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-28,28,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-27,27,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-26,26,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-25,25,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-24,24,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-23,23,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-22,22,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-21,21,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-20,20,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-19,19,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-18,18,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-17,17,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-16,16,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-15,15,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-14,14,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-13,13,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-12,12,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-11,11,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-10,10,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-09,9,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-08,8,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-07,7,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-06,6,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-05,5,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-04,4,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-03,3,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-02,2,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-01,1,1,2020,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2019-12-31,31,12,2019,0,0,New_Zealand,NZ,NZL,4783062,Oceania,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-09,9,12,2020,677,4,South_Korea,KR,KOR,51225321,Asia,15.02577212,1.32E-05,677,4,Social Distancing and Wearing Masks Enforced,4.049656854
2020-12-08,8,12,2020,594,3,South_Korea,KR,KOR,51225321,Asia,14.44988505,1.16E-05,-83,-1,Social Distancing and Wearing Masks Enforced,3.968391244
2020-12-07,7,12,2020,615,4,South_Korea,KR,KOR,51225321,Asia,13.97160596,1.20E-05,21,1,Social Distancing and Wearing Masks Enforced,3.989978252
2020-12-06,6,12,2020,631,5,South_Korea,KR,KOR,51225321,Asia,13.30006307,1.23E-05,16,1,Social Distancing and Wearing Masks Enforced,4.005936366
2020-12-05,5,12,2020,583,4,South_Korea,KR,KOR,51225321,Asia,12.71246304,1.14E-05,-48,-1,Social Distancing and Wearing Masks Enforced,3.956777169
2020-12-04,4,12,2020,629,7,South_Korea,KR,KOR,51225321,Asia,12.32788761,1.23E-05,46,3,Social Distancing and Wearing Masks Enforced,4.003963873
2020-12-03,3,12,2020,540,3,South_Korea,KR,KOR,51225321,Asia,11.80861317,1.05E-05,-89,-4,Social Distancing and Wearing Masks Enforced,3.9091717
2020-12-02,2,12,2020,511,0,South_Korea,KR,KOR,51225321,Asia,11.42403773,9.98E-06,-29,-3,Social Distancing and Wearing Masks Enforced,3.874874291
2020-12-01,1,12,2020,451,0,South_Korea,KR,KOR,51225321,Asia,11.03751014,8.80E-06,-60,0,Social Distancing and Wearing Masks Enforced,3.797268159
2020-11-30,30,11,2020,377,3,South_Korea,KR,KOR,51225321,Asia,10.60413072,7.36E-06,-74,3,Social Distancing and Wearing Masks Enforced,3.685911175
2020-11-29,29,11,2020,449,1,South_Korea,KR,KOR,51225321,Asia,10.30349815,8.77E-06,72,-2,Social Distancing and Wearing Masks Enforced,3.794506666
2020-11-28,28,11,2020,488,6,South_Korea,KR,KOR,51225321,Asia,9.83302769,9.53E-06,39,5,Social Distancing and Wearing Masks Enforced,3.846259218
2020-11-27,27,11,2020,569,1,South_Korea,KR,KOR,51225321,Asia,9.28056654,1.11E-05,81,-5,Social Distancing and Wearing Masks Enforced,3.941674534
2020-11-26,26,11,2020,583,2,South_Korea,KR,KOR,51225321,Asia,8.54265023,1.14E-05,14,1,Social Distancing and Wearing Masks Enforced,3.956777169
2020-11-25,25,11,2020,382,3,South_Korea,KR,KOR,51225321,Asia,7.68370002,7.46E-06,-201,1,Social Distancing and Wearing Masks Enforced,3.694097525
2020-11-24,24,11,2020,349,1,South_Korea,KR,KOR,51225321,Asia,7.22299036,6.81E-06,-33,-2,Social Distancing and Wearing Masks Enforced,3.63796073
2020-11-23,23,11,2020,271,4,South_Korea,KR,KOR,51225321,Asia,6.73690263,5.29E-06,-78,3,Social Distancing and Wearing Masks Enforced,3.480792131
2020-11-22,22,11,2020,330,2,South_Korea,KR,KOR,51225321,Asia,6.4538395,6.44E-06,59,-2,Social Distancing and Wearing Masks Enforced,3.603178855
2020-11-21,21,11,2020,386,2,South_Korea,KR,KOR,51225321,Asia,6.08878566,7.54E-06,56,0,Social Distancing and Wearing Masks Enforced,3.700569822
2020-11-20,20,11,2020,363,3,South_Korea,KR,KOR,51225321,Asia,5.50899427,7.09E-06,-23,1,Social Distancing and Wearing Masks Enforced,3.662398399
2020-11-19,19,11,2020,343,2,South_Korea,KR,KOR,51225321,Asia,5.08342349,6.70E-06,-20,-1,Social Distancing and Wearing Masks Enforced,3.627185865
2020-11-18,18,11,2020,313,2,South_Korea,KR,KOR,51225321,Asia,4.65785271,6.11E-06,-30,0,Social Distancing and Wearing Masks Enforced,3.570316783
2020-11-17,17,11,2020,229,0,South_Korea,KR,KOR,51225321,Asia,4.27718159,4.47E-06,-84,-2,Social Distancing and Wearing Masks Enforced,3.376161305
2020-11-16,16,11,2020,223,1,South_Korea,KR,KOR,51225321,Asia,3.97654902,4.35E-06,-6,1,Social Distancing and Wearing Masks Enforced,3.359664719
2020-11-15,15,11,2020,208,1,South_Korea,KR,KOR,51225321,Asia,3.73057692,4.06E-06,-15,0,Social Distancing and Wearing Masks Enforced,3.316398873
2020-11-14,14,11,2020,205,4,South_Korea,KR,KOR,51225321,Asia,3.56659551,4.00E-06,-3,3,Social Distancing and Wearing Masks Enforced,3.307372057
2020-11-13,13,11,2020,191,1,South_Korea,KR,KOR,51225321,Asia,3.41237491,3.73E-06,-14,-3,Social Distancing and Wearing Masks Enforced,3.263420967
2020-11-12,12,11,2020,143,0,South_Korea,KR,KOR,51225321,Asia,3.26205862,2.79E-06,-48,-1,Social Distancing and Wearing Masks Enforced,3.083588744
2020-11-11,11,11,2020,146,2,South_Korea,KR,KOR,51225321,Asia,3.22691975,2.85E-06,3,2,Social Distancing and Wearing Masks Enforced,3.096488894
2020-11-10,10,11,2020,100,5,South_Korea,KR,KOR,51225321,Asia,3.14297689,1.95E-06,-46,3,Social Distancing and Wearing Masks Enforced,2.861353116
2020-11-09,9,11,2020,126,2,South_Korea,KR,KOR,51225321,Asia,3.11955097,2.46E-06,26,-3,Social Distancing and Wearing Masks Enforced,3.004950902
2020-11-08,8,11,2020,143,1,South_Korea,KR,KOR,51225321,Asia,3.10588586,2.79E-06,17,-1,Social Distancing and Wearing Masks Enforced,3.083588744
2020-11-07,7,11,2020,89,1,South_Korea,KR,KOR,51225321,Asia,2.94580877,1.74E-06,-54,0,Social Distancing and Wearing Masks Enforced,2.788946585
2020-11-06,6,11,2020,145,1,South_Korea,KR,KOR,51225321,Asia,2.92238286,2.83E-06,56,0,Social Distancing and Wearing Masks Enforced,3.092218534
2020-11-05,5,11,2020,125,1,South_Korea,KR,KOR,51225321,Asia,2.94190445,2.44E-06,-20,0,Social Distancing and Wearing Masks Enforced,3
2020-11-04,4,11,2020,118,2,South_Korea,KR,KOR,51225321,Asia,2.9301915,2.30E-06,-7,1,Social Distancing and Wearing Masks Enforced,2.964193019
2020-11-03,3,11,2020,75,4,South_Korea,KR,KOR,51225321,Asia,2.87748319,1.46E-06,-43,2,Social Distancing and Wearing Masks Enforced,2.682606194
2020-11-02,2,11,2020,97,2,South_Korea,KR,KOR,51225321,Asia,2.84429648,1.89E-06,22,-2,Social Distancing and Wearing Masks Enforced,2.842427746
2020-11-01,1,11,2020,124,2,South_Korea,KR,KOR,51225321,Asia,2.80330113,2.42E-06,27,0,Social Distancing and Wearing Masks Enforced,2.995009331
2020-10-31,31,10,2020,126,0,South_Korea,KR,KOR,51225321,Asia,2.73887986,2.46E-06,2,-2,Social Distancing and Wearing Masks Enforced,3.004950902
2020-10-30,30,10,2020,114,2,South_Korea,KR,KOR,51225321,Asia,2.6354154,2.23E-06,-12,2,Social Distancing and Wearing Masks Enforced,2.942765553
2020-10-29,29,10,2020,125,1,South_Korea,KR,KOR,51225321,Asia,2.50462071,2.44E-06,11,-1,Social Distancing and Wearing Masks Enforced,3
2020-10-28,28,10,2020,103,1,South_Korea,KR,KOR,51225321,Asia,2.45386456,2.01E-06,-22,0,Social Distancing and Wearing Masks Enforced,2.879719033
2020-10-27,27,10,2020,88,3,South_Korea,KR,KOR,51225321,Asia,2.41677353,1.72E-06,-15,2,Social Distancing and Wearing Masks Enforced,2.781925777
2020-10-26,26,10,2020,119,0,South_Korea,KR,KOR,51225321,Asia,2.44410377,2.32E-06,31,-3,Social Distancing and Wearing Masks Enforced,2.969436383
2020-10-25,25,10,2020,61,0,South_Korea,KR,KOR,51225321,Asia,2.40115626,1.19E-06,-58,0,Social Distancing and Wearing Masks Enforced,2.554229543
2020-10-24,24,10,2020,77,2,South_Korea,KR,KOR,51225321,Asia,2.39529978,1.50E-06,16,2,Social Distancing and Wearing Masks Enforced,2.698958058
2020-10-23,23,10,2020,155,2,South_Korea,KR,KOR,51225321,Asia,2.38553898,3.03E-06,78,0,Social Distancing and Wearing Masks Enforced,3.133656215
2020-10-22,22,10,2020,119,3,South_Korea,KR,KOR,51225321,Asia,2.18837086,2.32E-06,-36,1,Social Distancing and Wearing Masks Enforced,2.969436383
2020-10-21,21,10,2020,91,3,South_Korea,KR,KOR,51225321,Asia,2.09076289,1.78E-06,-28,0,Social Distancing and Wearing Masks Enforced,2.802754596
2020-10-20,20,10,2020,58,3,South_Korea,KR,KOR,51225321,Asia,2.13566256,1.13E-06,-33,0,Social Distancing and Wearing Masks Enforced,2.522895092
2020-10-19,19,10,2020,76,0,South_Korea,KR,KOR,51225321,Asia,2.16884927,1.48E-06,18,-3,Social Distancing and Wearing Masks Enforced,2.690835917
2020-10-18,18,10,2020,91,1,South_Korea,KR,KOR,51225321,Asia,2.16299279,1.78E-06,15,1,Social Distancing and Wearing Masks Enforced,2.802754596
2020-10-17,17,10,2020,73,2,South_Korea,KR,KOR,51225321,Asia,2.11028448,1.43E-06,-18,1,Social Distancing and Wearing Masks Enforced,2.665812336
2020-10-16,16,10,2020,47,2,South_Korea,KR,KOR,51225321,Asia,2.1141888,9.18E-07,-26,0,Social Distancing and Wearing Masks Enforced,2.392231208
2020-10-15,15,10,2020,99,1,South_Korea,KR,KOR,51225321,Asia,2.29573964,1.93E-06,52,-1,Social Distancing and Wearing Masks Enforced,2.855108491
2020-10-14,14,10,2020,84,4,South_Korea,KR,KOR,51225321,Asia,2.10247584,1.64E-06,-15,3,Social Distancing and Wearing Masks Enforced,2.753021266
2020-10-13,13,10,2020,102,1,South_Korea,KR,KOR,51225321,Asia,2.15908847,1.99E-06,18,-3,Social Distancing and Wearing Masks Enforced,2.87365718
2020-10-12,12,10,2020,97,1,South_Korea,KR,KOR,51225321,Asia,2.03415026,1.89E-06,-5,0,Social Distancing and Wearing Masks Enforced,2.842427746
2020-10-11,11,10,2020,58,2,South_Korea,KR,KOR,51225321,Asia,1.94239876,1.13E-06,-39,1,Social Distancing and Wearing Masks Enforced,2.522895092
2020-10-10,10,10,2020,72,2,South_Korea,KR,KOR,51225321,Asia,2.01462866,1.41E-06,14,0,Social Distancing and Wearing Masks Enforced,2.657242063
2020-10-09,9,10,2020,54,1,South_Korea,KR,KOR,51225321,Asia,1.99315491,1.05E-06,-18,-1,Social Distancing and Wearing Masks Enforced,2.478495142
2020-10-08,8,10,2020,69,2,South_Korea,KR,KOR,51225321,Asia,2.11028448,1.35E-06,15,1,Social Distancing and Wearing Masks Enforced,2.630798288
2020-10-07,7,10,2020,114,3,South_Korea,KR,KOR,51225321,Asia,2.21960542,2.23E-06,45,1,Social Distancing and Wearing Masks Enforced,2.942765553
2020-10-06,6,10,2020,75,0,South_Korea,KR,KOR,51225321,Asia,2.21179678,1.46E-06,-39,-3,Social Distancing and Wearing Masks Enforced,2.682606194
2020-10-05,5,10,2020,73,1,South_Korea,KR,KOR,51225321,Asia,2.18446655,1.43E-06,-2,1,Social Distancing and Wearing Masks Enforced,2.665812336
2020-10-04,4,10,2020,64,1,South_Korea,KR,KOR,51225321,Asia,2.17861007,1.25E-06,-9,0,Social Distancing and Wearing Masks Enforced,2.584059348
2020-10-03,3,10,2020,75,4,South_Korea,KR,KOR,51225321,Asia,2.21374894,1.46E-06,11,3,Social Distancing and Wearing Masks Enforced,2.682606194
2020-10-02,2,10,2020,140,3,South_Korea,KR,KOR,51225321,Asia,2.28207452,2.73E-06,65,-1,Social Distancing and Wearing Masks Enforced,3.070415071
2020-10-01,1,10,2020,0,0,South_Korea,KR,KOR,51225321,Asia,2.25474429,0,-140,-3,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-30,30,9,2020,113,6,South_Korea,KR,KOR,51225321,Asia,2.5534247,2.21E-06,113,6,Social Distancing and Wearing Masks Enforced,2.937291201
2020-09-29,29,9,2020,38,1,South_Korea,KR,KOR,51225321,Asia,2.5534247,7.42E-07,-75,-5,Social Distancing and Wearing Masks Enforced,2.260159359
2020-09-28,28,9,2020,50,5,South_Korea,KR,KOR,51225321,Asia,2.68617155,9.76E-07,12,4,Social Distancing and Wearing Masks Enforced,2.430676558
2020-09-27,27,9,2020,95,2,South_Korea,KR,KOR,51225321,Asia,2.80134897,1.85E-06,45,-3,Social Distancing and Wearing Masks Enforced,2.8294828
2020-09-26,26,9,2020,61,4,South_Korea,KR,KOR,51225321,Asia,2.85210511,1.19E-06,-34,2,Social Distancing and Wearing Masks Enforced,2.554229543
2020-09-25,25,9,2020,114,2,South_Korea,KR,KOR,51225321,Asia,2.99851708,2.23E-06,53,-2,Social Distancing and Wearing Masks Enforced,2.942765553
2020-09-24,24,9,2020,125,5,South_Korea,KR,KOR,51225321,Asia,3.11955097,2.44E-06,11,3,Social Distancing and Wearing Masks Enforced,3
2020-09-23,23,9,2020,110,0,South_Korea,KR,KOR,51225321,Asia,3.17811576,2.15E-06,-15,-5,Social Distancing and Wearing Masks Enforced,2.92057266
2020-09-22,22,9,2020,61,3,South_Korea,KR,KOR,51225321,Asia,3.2679151,1.19E-06,-49,3,Social Distancing and Wearing Masks Enforced,2.554229543
2020-09-21,21,9,2020,70,2,South_Korea,KR,KOR,51225321,Asia,3.41432707,1.37E-06,9,-1,Social Distancing and Wearing Masks Enforced,2.639738513
2020-09-20,20,9,2020,82,5,South_Korea,KR,KOR,51225321,Asia,3.50998289,1.60E-06,12,3,Social Distancing and Wearing Masks Enforced,2.738048615
2020-09-19,19,9,2020,110,1,South_Korea,KR,KOR,51225321,Asia,4.00387925,2.15E-06,28,-4,Social Distancing and Wearing Masks Enforced,2.92057266
2020-09-18,18,9,2020,126,5,South_Korea,KR,KOR,51225321,Asia,3.7891417,2.46E-06,16,4,Social Distancing and Wearing Masks Enforced,3.004950902
2020-09-17,17,9,2020,153,5,South_Korea,KR,KOR,51225321,Asia,3.92969719,2.99E-06,27,0,Social Distancing and Wearing Masks Enforced,3.125586817
2020-09-16,16,9,2020,113,0,South_Korea,KR,KOR,51225321,Asia,4.01168789,2.21E-06,-40,-5,Social Distancing and Wearing Masks Enforced,2.937291201
2020-09-15,15,9,2020,106,4,South_Korea,KR,KOR,51225321,Asia,4.31232046,2.07E-06,-7,4,Social Distancing and Wearing Masks Enforced,2.897557624
2020-09-14,14,9,2020,109,5,South_Korea,KR,KOR,51225321,Asia,4.56414905,2.13E-06,3,1,Social Distancing and Wearing Masks Enforced,2.914898329
2020-09-13,13,9,2020,121,3,South_Korea,KR,KOR,51225321,Asia,4.83549923,2.36E-06,12,-2,Social Distancing and Wearing Masks Enforced,2.979792205
2020-09-12,12,9,2020,136,5,South_Korea,KR,KOR,51225321,Asia,5.18298363,2.65E-06,15,2,Social Distancing and Wearing Masks Enforced,3.052404102
2020-09-11,11,9,2020,176,4,South_Korea,KR,KOR,51225321,Asia,5.54803746,3.44E-06,40,-1,Social Distancing and Wearing Masks Enforced,3.212602335
2020-09-10,10,9,2020,155,2,South_Korea,KR,KOR,51225321,Asia,5.92870858,3.03E-06,-21,-2,Social Distancing and Wearing Masks Enforced,3.133656215
2020-09-09,9,9,2020,156,3,South_Korea,KR,KOR,51225321,Asia,6.48702621,3.05E-06,1,1,Social Distancing and Wearing Masks Enforced,3.137651952
2020-09-08,8,9,2020,136,5,South_Korea,KR,KOR,51225321,Asia,6.80718038,2.65E-06,-20,2,Social Distancing and Wearing Masks Enforced,3.052404102
2020-09-07,7,9,2020,119,2,South_Korea,KR,KOR,51225321,Asia,7.08829135,2.32E-06,-17,-3,Social Distancing and Wearing Masks Enforced,2.969436383
2020-09-06,6,9,2020,335,3,South_Korea,KR,KOR,51225321,Asia,7.37525881,6.54E-06,216,1,Social Distancing and Wearing Masks Enforced,3.612522414
2020-09-05,5,9,2020,0,0,South_Korea,KR,KOR,51225321,Asia,7.4962927,0,-335,-3,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-04,4,9,2020,198,2,South_Korea,KR,KOR,51225321,Asia,8.14440968,3.87E-06,198,2,Social Distancing and Wearing Masks Enforced,3.285785049
2020-09-03,3,9,2020,195,3,South_Korea,KR,KOR,51225321,Asia,8.39038178,3.81E-06,-3,1,Social Distancing and Wearing Masks Enforced,3.276298836
2020-09-02,2,9,2020,267,2,South_Korea,KR,KOR,51225321,Asia,8.57193262,5.21E-06,72,-1,Social Distancing and Wearing Masks Enforced,3.47155278
2020-09-01,1,9,2020,235,0,South_Korea,KR,KOR,51225321,Asia,8.63049741,4.59E-06,-32,-2,Social Distancing and Wearing Masks Enforced,3.392231208
2020-08-31,31,8,2020,248,1,South_Korea,KR,KOR,51225321,Asia,8.65197116,4.84E-06,13,1,Social Distancing and Wearing Masks Enforced,3.425685889
2020-08-30,30,8,2020,299,2,South_Korea,KR,KOR,51225321,Asia,8.55241102,5.84E-06,51,1,Social Distancing and Wearing Masks Enforced,3.541884735
2020-08-29,29,8,2020,323,5,South_Korea,KR,KOR,51225321,Asia,8.51336783,6.31E-06,24,3,Social Distancing and Wearing Masks Enforced,3.589857228
2020-08-28,28,8,2020,371,3,South_Korea,KR,KOR,51225321,Asia,8.20687878,7.24E-06,48,-2,Social Distancing and Wearing Masks Enforced,3.675943021
2020-08-27,27,8,2020,441,1,South_Korea,KR,KOR,51225321,Asia,7.68370002,8.61E-06,70,-2,Social Distancing and Wearing Masks Enforced,3.783336299
2020-08-26,26,8,2020,320,2,South_Korea,KR,KOR,51225321,Asia,6.93211859,6.25E-06,-121,1,Social Distancing and Wearing Masks Enforced,3.584059348
2020-08-25,25,8,2020,280,1,South_Korea,KR,KOR,51225321,Asia,6.41284415,5.47E-06,-40,-1,Social Distancing and Wearing Masks Enforced,3.501091629
2020-08-24,24,8,2020,266,0,South_Korea,KR,KOR,51225321,Asia,5.9326129,5.19E-06,-14,-1,Social Distancing and Wearing Masks Enforced,3.469221314
2020-08-23,23,8,2020,397,0,South_Korea,KR,KOR,51225321,Asia,5.46799892,7.75E-06,131,0,Social Distancing and Wearing Masks Enforced,3.718028657
2020-08-22,22,8,2020,332,0,South_Korea,KR,KOR,51225321,Asia,4.76326932,6.48E-06,-65,0,Social Distancing and Wearing Masks Enforced,3.606933156
2020-08-21,21,8,2020,324,2,South_Korea,KR,KOR,51225321,Asia,4.19909521,6.33E-06,-8,2,Social Distancing and Wearing Masks Enforced,3.591777894
2020-08-20,20,8,2020,288,1,South_Korea,KR,KOR,51225321,Asia,3.6056387,5.62E-06,-36,-1,Social Distancing and Wearing Masks Enforced,3.518595179
2020-08-19,19,8,2020,297,0,South_Korea,KR,KOR,51225321,Asia,3.12735961,5.80E-06,9,-1,Social Distancing and Wearing Masks Enforced,3.537714686
2020-08-18,18,8,2020,246,1,South_Korea,KR,KOR,51225321,Asia,2.61198949,4.80E-06,-51,1,Social Distancing and Wearing Masks Enforced,3.42065481
2020-08-17,17,8,2020,197,0,South_Korea,KR,KOR,51225321,Asia,2.19813166,3.85E-06,-49,-1,Social Distancing and Wearing Masks Enforced,3.282639043
2020-08-16,16,8,2020,279,0,South_Korea,KR,KOR,51225321,Asia,1.91702069,5.45E-06,82,0,Social Distancing and Wearing Masks Enforced,3.498868604
2020-08-15,15,8,2020,166,0,South_Korea,KR,KOR,51225321,Asia,1.37236817,3.24E-06,-113,0,Social Distancing and Wearing Masks Enforced,3.176256598
2020-08-14,14,8,2020,103,0,South_Korea,KR,KOR,51225321,Asia,1.10882663,2.01E-06,-63,0,Social Distancing and Wearing Masks Enforced,2.879719033
2020-08-13,13,8,2020,56,0,South_Korea,KR,KOR,51225321,Asia,0.97803194,1.09E-06,-47,0,Social Distancing and Wearing Masks Enforced,2.501091629
2020-08-12,12,8,2020,54,0,South_Korea,KR,KOR,51225321,Asia,0.90384988,1.05E-06,-2,0,Social Distancing and Wearing Masks Enforced,2.478495142
2020-08-11,11,8,2020,34,0,South_Korea,KR,KOR,51225321,Asia,0.89213692,6.64E-07,-20,0,Social Distancing and Wearing Masks Enforced,2.191050986
2020-08-10,10,8,2020,28,0,South_Korea,KR,KOR,51225321,Asia,0.88042396,5.47E-07,-6,0,Social Distancing and Wearing Masks Enforced,2.070415071
2020-08-09,9,8,2020,36,1,South_Korea,KR,KOR,51225321,Asia,0.87456748,7.03E-07,8,1,Social Distancing and Wearing Masks Enforced,2.226565505
2020-08-08,8,8,2020,43,1,South_Korea,KR,KOR,51225321,Asia,0.91751499,8.39E-07,7,0,Social Distancing and Wearing Masks Enforced,2.336965028
2020-08-07,7,8,2020,20,1,South_Korea,KR,KOR,51225321,Asia,1.05416616,3.90E-07,-23,0,Social Distancing and Wearing Masks Enforced,1.861353116
2020-08-06,6,8,2020,43,0,South_Korea,KR,KOR,51225321,Asia,1.09516151,8.39E-07,23,-1,Social Distancing and Wearing Masks Enforced,2.336965028
2020-08-05,5,8,2020,33,1,South_Korea,KR,KOR,51225321,Asia,1.12639606,6.44E-07,-10,1,Social Distancing and Wearing Masks Enforced,2.172502297
2020-08-04,4,8,2020,34,0,South_Korea,KR,KOR,51225321,Asia,1.18496085,6.64E-07,1,-1,Social Distancing and Wearing Masks Enforced,2.191050986
2020-08-03,3,8,2020,53,0,South_Korea,KR,KOR,51225321,Asia,1.20643461,1.03E-06,19,0,Social Distancing and Wearing Masks Enforced,2.466881066
2020-08-02,2,8,2020,0,0,South_Korea,KR,KOR,51225321,Asia,1.1537263,0,-53,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-08-01,1,8,2020,31,0,South_Korea,KR,KOR,51225321,Asia,1.22009972,6.05E-07,31,0,Social Distancing and Wearing Masks Enforced,2.133656215
2020-07-31,31,7,2020,36,1,South_Korea,KR,KOR,51225321,Asia,1.235717,7.03E-07,5,1,Social Distancing and Wearing Masks Enforced,2.226565505
2020-07-30,30,7,2020,18,0,South_Korea,KR,KOR,51225321,Asia,1.28256883,3.51E-07,-18,-1,Social Distancing and Wearing Masks Enforced,1.795888947
2020-07-29,29,7,2020,48,0,South_Korea,KR,KOR,51225321,Asia,1.36651169,9.37E-07,30,0,Social Distancing and Wearing Masks Enforced,2.405312427
2020-07-28,28,7,2020,28,1,South_Korea,KR,KOR,51225321,Asia,1.34894225,5.47E-07,-20,1,Social Distancing and Wearing Masks Enforced,2.070415071
2020-07-27,27,7,2020,25,1,South_Korea,KR,KOR,51225321,Asia,1.35870305,4.88E-07,-3,0,Social Distancing and Wearing Masks Enforced,2
2020-07-26,26,7,2020,58,0,South_Korea,KR,KOR,51225321,Asia,1.43093296,1.13E-06,33,-1,Social Distancing and Wearing Masks Enforced,2.522895092
2020-07-25,25,7,2020,113,0,South_Korea,KR,KOR,51225321,Asia,1.40360272,2.21E-06,55,0,Social Distancing and Wearing Masks Enforced,2.937291201
2020-07-24,24,7,2020,41,1,South_Korea,KR,KOR,51225321,Asia,1.25133428,8.00E-07,-72,1,Social Distancing and Wearing Masks Enforced,2.307372057
2020-07-23,23,7,2020,59,0,South_Korea,KR,KOR,51225321,Asia,1.25914291,1.15E-06,18,-1,Social Distancing and Wearing Masks Enforced,2.533516461
2020-07-22,22,7,2020,63,1,South_Korea,KR,KOR,51225321,Asia,1.23962132,1.23E-06,4,1,Social Distancing and Wearing Masks Enforced,2.574274344
2020-07-21,21,7,2020,45,0,South_Korea,KR,KOR,51225321,Asia,1.23962132,8.78E-07,-18,-1,Social Distancing and Wearing Masks Enforced,2.365212389
2020-07-20,20,7,2020,26,1,South_Korea,KR,KOR,51225321,Asia,1.3274685,5.08E-07,-19,1,Social Distancing and Wearing Masks Enforced,2.024369199
2020-07-19,19,7,2020,34,1,South_Korea,KR,KOR,51225321,Asia,1.27671235,6.64E-07,8,0,Social Distancing and Wearing Masks Enforced,2.191050986
2020-07-18,18,7,2020,39,1,South_Korea,KR,KOR,51225321,Asia,1.32942066,7.61E-07,5,0,Social Distancing and Wearing Masks Enforced,2.276298836
2020-07-17,17,7,2020,60,2,South_Korea,KR,KOR,51225321,Asia,1.37627249,1.17E-06,21,1,Social Distancing and Wearing Masks Enforced,2.543959311
2020-07-16,16,7,2020,61,2,South_Korea,KR,KOR,51225321,Asia,1.38212897,1.19E-06,1,0,Social Distancing and Wearing Masks Enforced,2.554229543
2020-07-15,15,7,2020,39,0,South_Korea,KR,KOR,51225321,Asia,1.36846385,7.61E-07,-22,-2,Social Distancing and Wearing Masks Enforced,2.276298836
2020-07-14,14,7,2020,33,0,South_Korea,KR,KOR,51225321,Asia,1.38993761,6.44E-07,-6,0,Social Distancing and Wearing Masks Enforced,2.172502297
2020-07-13,13,7,2020,62,0,South_Korea,KR,KOR,51225321,Asia,1.4094592,1.21E-06,29,0,Social Distancing and Wearing Masks Enforced,2.564332773
2020-07-12,12,7,2020,44,1,South_Korea,KR,KOR,51225321,Asia,1.37041601,8.59E-07,-18,1,Social Distancing and Wearing Masks Enforced,2.351249219
2020-07-11,11,7,2020,35,0,South_Korea,KR,KOR,51225321,Asia,1.40555488,6.83E-07,-9,-1,Social Distancing and Wearing Masks Enforced,2.209061955
2020-07-10,10,7,2020,45,1,South_Korea,KR,KOR,51225321,Asia,1.43678943,8.78E-07,10,1,Social Distancing and Wearing Masks Enforced,2.365212389
2020-07-09,9,7,2020,49,2,South_Korea,KR,KOR,51225321,Asia,1.42507648,9.57E-07,4,1,Social Distancing and Wearing Masks Enforced,2.41812391
2020-07-08,8,7,2020,63,0,South_Korea,KR,KOR,51225321,Asia,1.38408113,1.23E-06,14,-2,Social Distancing and Wearing Masks Enforced,2.574274344
2020-07-07,7,7,2020,90,2,South_Korea,KR,KOR,51225321,Asia,1.36065521,1.76E-06,27,2,Social Distancing and Wearing Masks Enforced,2.795888947
2020-07-06,6,7,2020,0,0,South_Korea,KR,KOR,51225321,Asia,1.27476019,0,-90,-2,Social Distancing and Wearing Masks Enforced,#NUM!
2020-07-05,5,7,2020,61,0,South_Korea,KR,KOR,51225321,Asia,1.3079469,1.19E-06,61,0,Social Distancing and Wearing Masks Enforced,2.554229543
2020-07-04,4,7,2020,63,1,South_Korea,KR,KOR,51225321,Asia,1.28256883,1.23E-06,2,1,Social Distancing and Wearing Masks Enforced,2.574274344
2020-07-03,3,7,2020,63,0,South_Korea,KR,KOR,51225321,Asia,1.29037747,1.23E-06,0,-1,Social Distancing and Wearing Masks Enforced,2.574274344
2020-07-02,2,7,2020,54,0,South_Korea,KR,KOR,51225321,Asia,1.26304723,1.05E-06,-9,0,Social Distancing and Wearing Masks Enforced,2.478495142
2020-07-01,1,7,2020,50,0,South_Korea,KR,KOR,51225321,Asia,1.27280803,9.76E-07,-4,0,Social Distancing and Wearing Masks Enforced,2.430676558
2020-06-30,30,6,2020,43,0,South_Korea,KR,KOR,51225321,Asia,1.25914291,8.39E-07,-7,0,Social Distancing and Wearing Masks Enforced,2.336965028
2020-06-29,29,6,2020,42,0,South_Korea,KR,KOR,51225321,Asia,1.24157348,8.20E-07,-1,0,Social Distancing and Wearing Masks Enforced,2.322344708
2020-06-28,28,6,2020,62,0,South_Korea,KR,KOR,51225321,Asia,1.23181268,1.21E-06,20,0,Social Distancing and Wearing Masks Enforced,2.564332773
2020-06-27,27,6,2020,51,0,South_Korea,KR,KOR,51225321,Asia,1.17520005,9.96E-07,-11,0,Social Distancing and Wearing Masks Enforced,2.442980622
2020-06-26,26,6,2020,39,0,South_Korea,KR,KOR,51225321,Asia,1.16934358,7.61E-07,-12,0,Social Distancing and Wearing Masks Enforced,2.276298836
2020-06-25,25,6,2020,28,1,South_Korea,KR,KOR,51225321,Asia,1.20253029,5.47E-07,-11,1,Social Distancing and Wearing Masks Enforced,2.070415071
2020-06-24,24,6,2020,51,0,South_Korea,KR,KOR,51225321,Asia,1.235717,9.96E-07,23,-1,Social Distancing and Wearing Masks Enforced,2.442980622
2020-06-23,23,6,2020,46,1,South_Korea,KR,KOR,51225321,Asia,1.23376484,8.98E-07,-5,1,Social Distancing and Wearing Masks Enforced,2.378868652
2020-06-22,22,6,2020,17,0,South_Korea,KR,KOR,51225321,Asia,1.21814756,3.32E-07,-29,-1,Social Distancing and Wearing Masks Enforced,1.760374428
2020-06-21,21,6,2020,48,0,South_Korea,KR,KOR,51225321,Asia,1.25914291,9.37E-07,31,0,Social Distancing and Wearing Masks Enforced,2.405312427
2020-06-20,20,6,2020,67,0,South_Korea,KR,KOR,51225321,Asia,1.27671235,1.31E-06,19,0,Social Distancing and Wearing Masks Enforced,2.612522414
2020-06-19,19,6,2020,49,0,South_Korea,KR,KOR,51225321,Asia,1.2454778,9.57E-07,-18,0,Social Distancing and Wearing Masks Enforced,2.41812391
2020-06-18,18,6,2020,59,1,South_Korea,KR,KOR,51225321,Asia,1.2259562,1.15E-06,10,1,Social Distancing and Wearing Masks Enforced,2.533516461
2020-06-17,17,6,2020,43,1,South_Korea,KR,KOR,51225321,Asia,1.18691301,8.39E-07,-16,0,Social Distancing and Wearing Masks Enforced,2.336965028
2020-06-16,16,6,2020,34,1,South_Korea,KR,KOR,51225321,Asia,1.19862597,6.64E-07,-9,0,Social Distancing and Wearing Masks Enforced,2.191050986
2020-06-15,15,6,2020,37,0,South_Korea,KR,KOR,51225321,Asia,1.20643461,7.22E-07,3,-1,Social Distancing and Wearing Masks Enforced,2.243589445
2020-06-14,14,6,2020,33,0,South_Korea,KR,KOR,51225321,Asia,1.20253029,6.44E-07,-4,0,Social Distancing and Wearing Masks Enforced,2.172502297
2020-06-13,13,6,2020,48,0,South_Korea,KR,KOR,51225321,Asia,1.19081733,9.37E-07,15,0,Social Distancing and Wearing Masks Enforced,2.405312427
2020-06-12,12,6,2020,56,1,South_Korea,KR,KOR,51225321,Asia,1.17324789,1.09E-06,8,1,Social Distancing and Wearing Masks Enforced,2.501091629
2020-06-11,11,6,2020,45,0,South_Korea,KR,KOR,51225321,Asia,1.17715221,8.78E-07,-11,-1,Social Distancing and Wearing Masks Enforced,2.365212389
2020-06-10,10,6,2020,50,2,South_Korea,KR,KOR,51225321,Asia,1.24352564,9.76E-07,5,2,Social Distancing and Wearing Masks Enforced,2.430676558
2020-06-09,9,6,2020,38,1,South_Korea,KR,KOR,51225321,Asia,1.22400404,7.42E-07,-12,-1,Social Distancing and Wearing Masks Enforced,2.260159359
2020-06-08,8,6,2020,38,0,South_Korea,KR,KOR,51225321,Asia,1.18691301,7.42E-07,0,-1,Social Distancing and Wearing Masks Enforced,2.260159359
2020-06-07,7,6,2020,57,0,South_Korea,KR,KOR,51225321,Asia,1.1439655,1.11E-06,19,0,Social Distancing and Wearing Masks Enforced,2.512088995
2020-06-06,6,6,2020,51,0,South_Korea,KR,KOR,51225321,Asia,1.0814964,9.96E-07,-6,0,Social Distancing and Wearing Masks Enforced,2.442980622
2020-06-05,5,6,2020,39,0,South_Korea,KR,KOR,51225321,Asia,1.02683593,7.61E-07,-12,0,Social Distancing and Wearing Masks Enforced,2.276298836
2020-06-04,4,6,2020,39,0,South_Korea,KR,KOR,51225321,Asia,0.9897449,7.61E-07,0,0,Social Distancing and Wearing Masks Enforced,2.276298836
2020-06-03,3,6,2020,49,1,South_Korea,KR,KOR,51225321,Asia,0.93703659,9.57E-07,10,1,Social Distancing and Wearing Masks Enforced,2.41812391
2020-06-02,2,6,2020,38,1,South_Korea,KR,KOR,51225321,Asia,0.90384988,7.42E-07,-11,0,Social Distancing and Wearing Masks Enforced,2.260159359
2020-06-01,1,6,2020,35,1,South_Korea,KR,KOR,51225321,Asia,0.85504589,6.83E-07,-3,0,Social Distancing and Wearing Masks Enforced,2.209061955
2020-05-31,31,5,2020,27,1,South_Korea,KR,KOR,51225321,Asia,0.8160027,5.27E-07,-8,0,Social Distancing and Wearing Masks Enforced,2.047818583
2020-05-30,30,5,2020,39,0,South_Korea,KR,KOR,51225321,Asia,0.78867246,7.61E-07,12,-1,Social Distancing and Wearing Masks Enforced,2.276298836
2020-05-29,29,5,2020,58,0,South_Korea,KR,KOR,51225321,Asia,0.74962927,1.13E-06,19,0,Social Distancing and Wearing Masks Enforced,2.522895092
2020-05-28,28,5,2020,79,0,South_Korea,KR,KOR,51225321,Asia,0.68911232,1.54E-06,21,0,Social Distancing and Wearing Masks Enforced,2.714890595
2020-05-27,27,5,2020,40,0,South_Korea,KR,KOR,51225321,Asia,0.59150435,7.81E-07,-39,0,Social Distancing and Wearing Masks Enforced,2.292029674
2020-05-26,26,5,2020,19,2,South_Korea,KR,KOR,51225321,Asia,0.56417411,3.71E-07,-21,2,Social Distancing and Wearing Masks Enforced,1.8294828
2020-05-25,25,5,2020,16,1,South_Korea,KR,KOR,51225321,Asia,0.57979139,3.12E-07,-3,-1,Social Distancing and Wearing Masks Enforced,1.722706232
2020-05-24,24,5,2020,25,0,South_Korea,KR,KOR,51225321,Asia,0.61688242,4.88E-07,9,-1,Social Distancing and Wearing Masks Enforced,2
2020-05-23,23,5,2020,23,2,South_Korea,KR,KOR,51225321,Asia,0.63445186,4.49E-07,-2,2,Social Distancing and Wearing Masks Enforced,1.948192093
2020-05-22,22,5,2020,20,0,South_Korea,KR,KOR,51225321,Asia,0.62469106,3.90E-07,-3,-2,Social Distancing and Wearing Masks Enforced,1.861353116
2020-05-21,21,5,2020,12,1,South_Korea,KR,KOR,51225321,Asia,0.60907378,2.34E-07,-8,1,Social Distancing and Wearing Masks Enforced,1.543959311
2020-05-20,20,5,2020,32,0,South_Korea,KR,KOR,51225321,Asia,0.59345651,6.25E-07,20,-1,Social Distancing and Wearing Masks Enforced,2.15338279
2020-05-19,19,5,2020,13,0,South_Korea,KR,KOR,51225321,Asia,0.53489172,2.54E-07,-19,0,Social Distancing and Wearing Masks Enforced,1.593692641
2020-05-18,18,5,2020,15,1,South_Korea,KR,KOR,51225321,Asia,0.51537012,2.93E-07,2,1,Social Distancing and Wearing Masks Enforced,1.682606194
2020-05-17,17,5,2020,13,0,South_Korea,KR,KOR,51225321,Asia,0.50170501,2.54E-07,-2,-1,Social Distancing and Wearing Masks Enforced,1.593692641
2020-05-16,16,5,2020,19,2,South_Korea,KR,KOR,51225321,Asia,0.50170501,3.71E-07,6,2,Social Distancing and Wearing Masks Enforced,1.8294828
2020-05-15,15,5,2020,27,0,South_Korea,KR,KOR,51225321,Asia,0.47632693,5.27E-07,8,-2,Social Distancing and Wearing Masks Enforced,2.047818583
2020-05-14,14,5,2020,29,1,South_Korea,KR,KOR,51225321,Asia,0.44118806,5.66E-07,2,1,Social Distancing and Wearing Masks Enforced,2.092218534
2020-05-13,13,5,2020,26,1,South_Korea,KR,KOR,51225321,Asia,0.39238407,5.08E-07,-3,0,Social Distancing and Wearing Masks Enforced,2.024369199
2020-05-12,12,5,2020,27,2,South_Korea,KR,KOR,51225321,Asia,0.35919736,5.27E-07,1,1,Social Distancing and Wearing Masks Enforced,2.047818583
2020-05-11,11,5,2020,35,0,South_Korea,KR,KOR,51225321,Asia,0.33381928,6.83E-07,8,-2,Social Distancing and Wearing Masks Enforced,2.209061955
2020-05-10,10,5,2020,34,0,South_Korea,KR,KOR,51225321,Asia,0.2850153,6.64E-07,-1,0,Social Distancing and Wearing Masks Enforced,2.191050986
2020-05-09,9,5,2020,18,0,South_Korea,KR,KOR,51225321,Asia,0.23816347,3.51E-07,-16,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-05-08,8,5,2020,12,0,South_Korea,KR,KOR,51225321,Asia,0.22254619,2.34E-07,-6,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-05-07,7,5,2020,4,1,South_Korea,KR,KOR,51225321,Asia,0.21083323,7.81E-08,-8,1,Social Distancing and Wearing Masks Enforced,0.861353116
2020-05-06,6,5,2020,2,1,South_Korea,KR,KOR,51225321,Asia,0.21864187,3.90E-08,-2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-05,5,5,2020,3,2,South_Korea,KR,KOR,51225321,Asia,0.23621131,5.86E-08,1,1,Social Distancing and Wearing Masks Enforced,0.682606194
2020-05-04,4,5,2020,8,2,South_Korea,KR,KOR,51225321,Asia,0.24792426,1.56E-07,5,0,Social Distancing and Wearing Masks Enforced,1.292029674
2020-05-03,3,5,2020,13,0,South_Korea,KR,KOR,51225321,Asia,0.25768506,2.54E-07,5,-2,Social Distancing and Wearing Masks Enforced,1.593692641
2020-05-02,2,5,2020,6,2,South_Korea,KR,KOR,51225321,Asia,0.24792426,1.17E-07,-7,2,Social Distancing and Wearing Masks Enforced,1.113282753
2020-05-01,1,5,2020,9,1,South_Korea,KR,KOR,51225321,Asia,0.27135018,1.76E-07,3,-1,Social Distancing and Wearing Masks Enforced,1.365212389
2020-04-30,30,4,2020,4,1,South_Korea,KR,KOR,51225321,Asia,0.29672825,7.81E-08,-5,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-04-29,29,4,2020,9,2,South_Korea,KR,KOR,51225321,Asia,0.33186712,1.76E-07,5,1,Social Distancing and Wearing Masks Enforced,1.365212389
2020-04-28,28,4,2020,14,1,South_Korea,KR,KOR,51225321,Asia,0.367006,2.73E-07,5,-1,Social Distancing and Wearing Masks Enforced,1.639738513
2020-04-27,27,4,2020,10,1,South_Korea,KR,KOR,51225321,Asia,0.39238407,1.95E-07,-4,0,Social Distancing and Wearing Masks Enforced,1.430676558
2020-04-26,26,4,2020,10,2,South_Korea,KR,KOR,51225321,Asia,0.42166646,1.95E-07,0,1,Social Distancing and Wearing Masks Enforced,1.430676558
2020-04-25,25,4,2020,10,0,South_Korea,KR,KOR,51225321,Asia,0.52317876,1.95E-07,0,-2,Social Distancing and Wearing Masks Enforced,1.430676558
2020-04-24,24,4,2020,6,0,South_Korea,KR,KOR,51225321,Asia,0.50365717,1.17E-07,-4,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-04-23,23,4,2020,8,2,South_Korea,KR,KOR,51225321,Asia,0.54465252,1.56E-07,2,2,Social Distancing and Wearing Masks Enforced,1.292029674
2020-04-22,22,4,2020,11,1,South_Korea,KR,KOR,51225321,Asia,0.60516946,2.15E-07,3,-1,Social Distancing and Wearing Masks Enforced,1.489896102
2020-04-21,21,4,2020,9,1,South_Korea,KR,KOR,51225321,Asia,0.68716016,1.76E-07,-2,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-04-20,20,4,2020,13,2,South_Korea,KR,KOR,51225321,Asia,0.76134223,2.54E-07,4,1,Social Distancing and Wearing Masks Enforced,1.593692641
2020-04-19,19,4,2020,8,2,South_Korea,KR,KOR,51225321,Asia,0.82771565,1.56E-07,-5,0,Social Distancing and Wearing Masks Enforced,1.292029674
2020-04-18,18,4,2020,18,2,South_Korea,KR,KOR,51225321,Asia,0.9702233,3.51E-07,10,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-04-17,17,4,2020,22,1,South_Korea,KR,KOR,51225321,Asia,1.11858743,4.29E-07,4,-1,Social Distancing and Wearing Masks Enforced,1.92057266
2020-04-16,16,4,2020,22,4,South_Korea,KR,KOR,51225321,Asia,1.24352564,4.29E-07,0,3,Social Distancing and Wearing Masks Enforced,1.92057266
2020-04-15,15,4,2020,27,3,South_Korea,KR,KOR,51225321,Asia,1.57148844,5.27E-07,5,-1,Social Distancing and Wearing Masks Enforced,2.047818583
2020-04-14,14,4,2020,27,5,South_Korea,KR,KOR,51225321,Asia,1.51878014,5.27E-07,0,2,Social Distancing and Wearing Masks Enforced,2.047818583
2020-04-13,13,4,2020,25,3,South_Korea,KR,KOR,51225321,Asia,1.71009177,4.88E-07,-2,-2,Social Distancing and Wearing Masks Enforced,2
2020-04-12,12,4,2020,62,6,South_Korea,KR,KOR,51225321,Asia,1.81355623,1.21E-06,37,3,Social Distancing and Wearing Masks Enforced,2.564332773
2020-04-11,11,4,2020,0,0,South_Korea,KR,KOR,51225321,Asia,1.89749909,0,-62,-6,Social Distancing and Wearing Masks Enforced,#NUM!
2020-04-10,10,4,2020,27,4,South_Korea,KR,KOR,51225321,Asia,2.18251439,5.27E-07,27,4,Social Distancing and Wearing Masks Enforced,2.047818583
2020-04-09,9,4,2020,39,4,South_Korea,KR,KOR,51225321,Asia,2.3074526,7.61E-07,12,0,Social Distancing and Wearing Masks Enforced,2.276298836
2020-04-08,8,4,2020,53,8,South_Korea,KR,KOR,51225321,Asia,2.43434297,1.03E-06,14,4,Social Distancing and Wearing Masks Enforced,2.466881066
2020-04-07,7,4,2020,47,6,South_Korea,KR,KOR,51225321,Asia,2.52609447,9.18E-07,-6,-2,Social Distancing and Wearing Masks Enforced,2.392231208
2020-04-06,6,4,2020,47,3,South_Korea,KR,KOR,51225321,Asia,2.5827071,9.18E-07,0,-3,Social Distancing and Wearing Masks Enforced,2.392231208
2020-04-05,5,4,2020,81,6,South_Korea,KR,KOR,51225321,Asia,2.61589381,1.58E-06,34,3,Social Distancing and Wearing Masks Enforced,2.730424778
2020-04-04,4,4,2020,94,3,South_Korea,KR,KOR,51225321,Asia,2.64908052,1.84E-06,13,-3,Social Distancing and Wearing Masks Enforced,2.822907766
2020-04-03,3,4,2020,86,5,South_Korea,KR,KOR,51225321,Asia,2.75254498,1.68E-06,-8,2,Social Distancing and Wearing Masks Enforced,2.767641586
2020-04-02,2,4,2020,190,6,South_Korea,KR,KOR,51225321,Asia,2.75449714,3.71E-06,104,1,Social Distancing and Wearing Masks Enforced,3.260159359
2020-04-01,1,4,2020,0,0,South_Korea,KR,KOR,51225321,Asia,2.68031507,0,-190,-6,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-31,31,3,2020,125,5,South_Korea,KR,KOR,51225321,Asia,2.86186591,2.44E-06,125,5,Social Distancing and Wearing Masks Enforced,3
2020-03-30,30,3,2020,78,6,South_Korea,KR,KOR,51225321,Asia,2.78182737,1.52E-06,-47,1,Social Distancing and Wearing Masks Enforced,2.706975394
2020-03-29,29,3,2020,105,8,South_Korea,KR,KOR,51225321,Asia,2.77401873,2.05E-06,27,2,Social Distancing and Wearing Masks Enforced,2.89166815
2020-03-28,28,3,2020,146,5,South_Korea,KR,KOR,51225321,Asia,2.7174061,2.85E-06,41,-3,Social Distancing and Wearing Masks Enforced,3.096488894
2020-03-27,27,3,2020,91,8,South_Korea,KR,KOR,51225321,Asia,2.64127188,1.78E-06,-55,3,Social Distancing and Wearing Masks Enforced,2.802754596
2020-03-26,26,3,2020,104,5,South_Korea,KR,KOR,51225321,Asia,2.67836291,2.03E-06,13,-3,Social Distancing and Wearing Masks Enforced,2.885722315
2020-03-25,25,3,2020,100,6,South_Korea,KR,KOR,51225321,Asia,2.69788451,1.95E-06,-4,1,Social Distancing and Wearing Masks Enforced,2.861353116
2020-03-24,24,3,2020,76,7,South_Korea,KR,KOR,51225321,Asia,2.97509117,1.48E-06,-24,1,Social Distancing and Wearing Masks Enforced,2.690835917
2020-03-23,23,3,2020,64,9,South_Korea,KR,KOR,51225321,Asia,3.08245994,1.25E-06,-12,2,Social Distancing and Wearing Masks Enforced,2.584059348
2020-03-22,22,3,2020,98,1,South_Korea,KR,KOR,51225321,Asia,3.4416573,1.91E-06,34,-8,Social Distancing and Wearing Masks Enforced,2.848800468
2020-03-21,21,3,2020,147,3,South_Korea,KR,KOR,51225321,Asia,3.96678822,2.87E-06,49,2,Social Distancing and Wearing Masks Enforced,3.100730105
2020-03-20,20,3,2020,87,9,South_Korea,KR,KOR,51225321,Asia,4.62271383,1.70E-06,-60,6,Social Distancing and Wearing Masks Enforced,2.774824729
2020-03-19,19,3,2020,152,5,South_Korea,KR,KOR,51225321,Asia,5.4640946,2.97E-06,65,-4,Social Distancing and Wearing Masks Enforced,3.121512475
2020-03-18,18,3,2020,93,5,South_Korea,KR,KOR,51225321,Asia,6.02241224,1.82E-06,-59,0,Social Distancing and Wearing Masks Enforced,2.816262409
2020-03-17,17,3,2020,84,6,South_Korea,KR,KOR,51225321,Asia,6.84817573,1.64E-06,-9,1,Social Distancing and Wearing Masks Enforced,2.753021266
2020-03-16,16,3,2020,74,0,South_Korea,KR,KOR,51225321,Asia,7.85549006,1.44E-06,-10,-6,Social Distancing and Wearing Masks Enforced,2.674266003
2020-03-15,15,3,2020,76,3,South_Korea,KR,KOR,51225321,Asia,9.05021171,1.48E-06,2,3,Social Distancing and Wearing Masks Enforced,2.690835917
2020-03-14,14,3,2020,107,5,South_Korea,KR,KOR,51225321,Asia,10.06338252,2.09E-06,31,2,Social Distancing and Wearing Masks Enforced,2.903391798
2020-03-13,13,3,2020,110,1,South_Korea,KR,KOR,51225321,Asia,11.62901449,2.15E-06,3,-4,Social Distancing and Wearing Masks Enforced,2.92057266
2020-03-12,12,3,2020,114,6,South_Korea,KR,KOR,51225321,Asia,12.24784907,2.23E-06,4,5,Social Distancing and Wearing Masks Enforced,2.942765553
2020-03-11,11,3,2020,242,6,South_Korea,KR,KOR,51225321,Asia,12.90182252,4.72E-06,128,0,Social Distancing and Wearing Masks Enforced,3.410468763
2020-03-10,10,3,2020,131,3,South_Korea,KR,KOR,51225321,Asia,12.92524843,2.56E-06,-111,-3,Social Distancing and Wearing Masks Enforced,3.02913041
2020-03-09,9,3,2020,248,1,South_Korea,KR,KOR,51225321,Asia,12.92329627,4.84E-06,117,-2,Social Distancing and Wearing Masks Enforced,3.425685889
2020-03-08,8,3,2020,367,6,South_Korea,KR,KOR,51225321,Asia,12.75345839,7.16E-06,119,5,Social Distancing and Wearing Masks Enforced,3.669207617
2020-03-07,7,3,2020,483,2,South_Korea,KR,KOR,51225321,Asia,12.53676868,9.43E-06,116,-4,Social Distancing and Wearing Masks Enforced,3.839860243
2020-03-06,6,3,2020,518,7,South_Korea,KR,KOR,51225321,Asia,11.96478593,1.01E-05,35,5,Social Distancing and Wearing Masks Enforced,3.883327958
2020-03-05,5,3,2020,438,3,South_Korea,KR,KOR,51225321,Asia,11.09997925,8.55E-06,-80,-4,Social Distancing and Wearing Masks Enforced,3.779095089
2020-03-04,4,3,2020,516,4,South_Korea,KR,KOR,51225321,Asia,10.31130679,1.01E-05,78,1,Social Distancing and Wearing Masks Enforced,3.880924338
2020-03-03,3,3,2020,600,6,South_Korea,KR,KOR,51225321,Asia,9.33327485,1.17E-05,84,2,Social Distancing and Wearing Masks Enforced,3.974635869
2020-03-02,2,3,2020,686,5,South_Korea,KR,KOR,51225321,Asia,8.16393127,1.34E-05,86,-1,Social Distancing and Wearing Masks Enforced,4.057862423
2020-03-01,1,3,2020,595,1,South_Korea,KR,KOR,51225321,Asia,6.82670197,1.16E-05,-91,-4,Social Distancing and Wearing Masks Enforced,3.969436383
2020-02-29,29,2,2020,909,3,South_Korea,KR,KOR,51225321,Asia,5.6671192,1.77E-05,314,2,Social Distancing and Wearing Masks Enforced,4.232747993
2020-02-28,28,2,2020,427,1,South_Korea,KR,KOR,51225321,Asia,3.89260616,8.34E-06,-482,-2,Social Distancing and Wearing Masks Enforced,3.763291499
2020-02-27,27,2,2020,449,1,South_Korea,KR,KOR,51225321,Asia,3.05903403,8.77E-06,22,0,Social Distancing and Wearing Masks Enforced,3.794506666
2020-02-26,26,2,2020,254,3,South_Korea,KR,KOR,51225321,Asia,2.18251439,4.96E-06,-195,2,Social Distancing and Wearing Masks Enforced,3.440539224
2020-02-25,25,2,2020,130,1,South_Korea,KR,KOR,51225321,Asia,1.68666586,2.54E-06,-124,-2,Social Distancing and Wearing Masks Enforced,3.024369199
2020-02-24,24,2,2020,161,2,South_Korea,KR,KOR,51225321,Asia,1.43483728,3.14E-06,31,1,Social Distancing and Wearing Masks Enforced,3.157254049
2020-02-23,23,2,2020,256,3,South_Korea,KR,KOR,51225321,Asia,1.12444391,5.00E-06,95,1,Social Distancing and Wearing Masks Enforced,3.445412465
2020-02-22,22,2,2020,190,1,South_Korea,KR,KOR,51225321,Asia,0.62664322,3.71E-06,-66,-2,Social Distancing and Wearing Masks Enforced,3.260159359
2020-02-21,21,2,2020,75,1,South_Korea,KR,KOR,51225321,Asia,0.2557329,1.46E-06,-115,0,Social Distancing and Wearing Masks Enforced,2.682606194
2020-02-20,20,2,2020,34,0,South_Korea,KR,KOR,51225321,Asia,0.11127309,6.64E-07,-41,-1,Social Distancing and Wearing Masks Enforced,2.191050986
2020-02-19,19,2,2020,15,0,South_Korea,KR,KOR,51225321,Asia,0.05466047,2.93E-07,-19,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-02-18,18,2,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.02928239,1.95E-08,-14,0,Social Distancing and Wearing Masks Enforced,0
2020-02-17,17,2,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.02928239,1.95E-08,0,0,Social Distancing and Wearing Masks Enforced,0
2020-02-16,16,2,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.02733023,1.95E-08,0,0,Social Distancing and Wearing Masks Enforced,0
2020-02-15,15,2,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.03123455,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-14,14,2,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.04099535,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-13,13,2,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.04685183,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-12,12,2,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.04685183,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-11,11,2,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.04685183,1.95E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-10,10,2,2020,2,0,South_Korea,KR,KOR,51225321,Asia,0.04489967,3.90E-08,1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-02-09,9,2,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.04294751,1.95E-08,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-08,8,2,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.04294751,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-07,7,2,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.04294751,1.95E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-06,6,2,2020,5,0,South_Korea,KR,KOR,51225321,Asia,0.04294751,9.76E-08,4,0,Social Distancing and Wearing Masks Enforced,1
2020-02-05,5,2,2020,2,0,South_Korea,KR,KOR,51225321,Asia,0.03318671,3.90E-08,-3,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-02-04,4,2,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.02928239,1.95E-08,-1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-03,3,2,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.02733023,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-02,2,2,2020,3,0,South_Korea,KR,KOR,51225321,Asia,0.02928239,5.86E-08,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-02-01,1,2,2020,5,0,South_Korea,KR,KOR,51225321,Asia,0.02342591,9.76E-08,2,0,Social Distancing and Wearing Masks Enforced,1
2020-01-31,31,1,2020,3,0,South_Korea,KR,KOR,51225321,Asia,0.01366512,5.86E-08,-2,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-01-30,30,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.00780864,0,-3,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-29,29,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.00780864,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-28,28,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.00780864,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-27,27,1,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.00780864,1.95E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-01-26,26,1,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.00585648,1.95E-08,0,0,Social Distancing and Wearing Masks Enforced,0
2020-01-25,25,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.00390432,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-24,24,1,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.00390432,1.95E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-01-23,23,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.00195216,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-22,22,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.00195216,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-21,21,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0.00195216,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-20,20,1,2020,1,0,South_Korea,KR,KOR,51225321,Asia,0.00195216,1.95E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-01-19,19,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-18,18,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-17,17,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-16,16,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-15,15,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-14,14,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-13,13,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-12,12,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-11,11,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-10,10,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-09,9,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-08,8,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-07,7,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-06,6,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-05,5,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-04,4,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-03,3,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-02,2,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-01,1,1,2020,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2019-12-31,31,12,2019,0,0,South_Korea,KR,KOR,51225321,Asia,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-09,9,12,2020,20815,590,Germany,DE,DEU,83019213,Europe,309.8126213,0.000250725,20815,590,Social Distancing and Wearing Masks Enforced,6.178199906
2020-12-08,8,12,2020,14055,423,Germany,DE,DEU,83019213,Europe,307.1843141,0.000169298,-6760,-167,Social Distancing and Wearing Masks Enforced,5.934204364
2020-12-07,7,12,2020,12332,147,Germany,DE,DEU,83019213,Europe,306.5808393,0.000148544,-1723,-276,Social Distancing and Wearing Masks Enforced,5.85294575
2020-12-06,6,12,2020,17767,255,Germany,DE,DEU,83019213,Europe,304.8125739,0.000214011,5435,108,Social Distancing and Wearing Masks Enforced,6.079823277
2020-12-05,5,12,2020,23318,483,Germany,DE,DEU,83019213,Europe,302.372175,0.000280875,5551,228,Social Distancing and Wearing Masks Enforced,6.248753553
2020-12-04,4,12,2020,23448,432,Germany,DE,DEU,83019213,Europe,301.9457677,0.000282441,130,-51,Social Distancing and Wearing Masks Enforced,6.252207932
2020-12-03,3,12,2020,22046,479,Germany,DE,DEU,83019213,Europe,302.1866758,0.000265553,-1402,47,Social Distancing and Wearing Masks Enforced,6.213900133
2020-12-02,2,12,2020,17270,487,Germany,DE,DEU,83019213,Europe,302.864832,0.000208024,-4776,8,Social Distancing and Wearing Masks Enforced,6.062194817
2020-12-01,1,12,2020,13604,388,Germany,DE,DEU,83019213,Europe,303.2153533,0.000163866,-3666,-99,Social Distancing and Wearing Masks Enforced,5.913939937
2020-11-30,30,11,2020,11169,125,Germany,DE,DEU,83019213,Europe,304.1970538,0.000134535,-2435,-263,Social Distancing and Wearing Masks Enforced,5.791399153
2020-11-29,29,11,2020,14611,158,Germany,DE,DEU,83019213,Europe,303.7814873,0.000175995,3442,33,Social Distancing and Wearing Masks Enforced,5.958309963
2020-11-28,28,11,2020,21695,379,Germany,DE,DEU,83019213,Europe,306.5952938,0.000261325,7084,221,Social Distancing and Wearing Masks Enforced,6.203928105
2020-11-27,27,11,2020,22806,426,Germany,DE,DEU,83019213,Europe,307.5179718,0.000274707,1111,47,Social Distancing and Wearing Masks Enforced,6.234958715
2020-11-26,26,11,2020,22268,389,Germany,DE,DEU,83019213,Europe,308.4045135,0.000268227,-538,-37,Social Distancing and Wearing Masks Enforced,6.220125593
2020-11-25,25,11,2020,18633,410,Germany,DE,DEU,83019213,Europe,307.9202883,0.000224442,-3635,21,Social Distancing and Wearing Masks Enforced,6.109393475
2020-11-24,24,11,2020,13554,249,Germany,DE,DEU,83019213,Europe,307.7444254,0.000163263,-5079,-161,Social Distancing and Wearing Masks Enforced,5.911652082
2020-11-23,23,11,2020,10864,90,Germany,DE,DEU,83019213,Europe,309.8860983,0.000130861,-2690,-159,Social Distancing and Wearing Masks Enforced,5.774195934
2020-11-22,22,11,2020,15741,138,Germany,DE,DEU,83019213,Europe,312.8962449,0.000189607,4877,48,Social Distancing and Wearing Masks Enforced,6.004595752
2020-11-21,21,11,2020,22964,254,Germany,DE,DEU,83019213,Europe,313.228698,0.000276611,7223,116,Social Distancing and Wearing Masks Enforced,6.239248482
2020-11-20,20,11,2020,23648,260,Germany,DE,DEU,83019213,Europe,313.7526731,0.00028485,684,6,Social Distancing and Wearing Masks Enforced,6.257485142
2020-11-19,19,11,2020,22609,251,Germany,DE,DEU,83019213,Europe,311.1725475,0.000272335,-1039,-9,Social Distancing and Wearing Masks Enforced,6.22956826
2020-11-18,18,11,2020,17561,305,Germany,DE,DEU,83019213,Europe,308.0178561,0.000211529,-5048,54,Social Distancing and Wearing Masks Enforced,6.072577101
2020-11-17,17,11,2020,14419,267,Germany,DE,DEU,83019213,Europe,307.5998805,0.000173683,-3142,-38,Social Distancing and Wearing Masks Enforced,5.950091014
2020-11-16,16,11,2020,10824,62,Germany,DE,DEU,83019213,Europe,308.7237168,0.000130379,-3595,-205,Social Distancing and Wearing Masks Enforced,5.771904028
2020-11-15,15,11,2020,16947,107,Germany,DE,DEU,83019213,Europe,310.2570968,0.000204133,6123,45,Social Distancing and Wearing Masks Enforced,6.050463973
2020-11-14,14,11,2020,22461,178,Germany,DE,DEU,83019213,Europe,306.9205197,0.000270552,5514,71,Social Distancing and Wearing Masks Enforced,6.22548759
2020-11-13,13,11,2020,23542,218,Germany,DE,DEU,83019213,Europe,302.8226731,0.000283573,1081,40,Social Distancing and Wearing Masks Enforced,6.254693804
2020-11-12,12,11,2020,21866,215,Germany,DE,DEU,83019213,Europe,296.967402,0.000263385,-1676,-3,Social Distancing and Wearing Masks Enforced,6.208806268
2020-11-11,11,11,2020,18487,261,Germany,DE,DEU,83019213,Europe,290.833882,0.000222683,-3379,46,Social Distancing and Wearing Masks Enforced,6.104505794
2020-11-10,10,11,2020,15332,154,Germany,DE,DEU,83019213,Europe,286.590286,0.00018468,-3155,-107,Social Distancing and Wearing Masks Enforced,5.9882381
2020-11-09,9,11,2020,13363,63,Germany,DE,DEU,83019213,Europe,281.8648739,0.000160963,-1969,-91,Social Distancing and Wearing Masks Enforced,5.902834088
2020-11-08,8,11,2020,16017,63,Germany,DE,DEU,83019213,Europe,276.2300336,0.000192931,2654,0,Social Distancing and Wearing Masks Enforced,6.015395724
2020-11-07,7,11,2020,23399,130,Germany,DE,DEU,83019213,Europe,270.3988533,0.00028185,7382,67,Social Distancing and Wearing Masks Enforced,6.250908151
2020-11-06,6,11,2020,21506,166,Germany,DE,DEU,83019213,Europe,259.9374196,0.000259048,-1893,36,Social Distancing and Wearing Masks Enforced,6.198491516
2020-11-05,5,11,2020,19990,118,Germany,DE,DEU,83019213,Europe,247.5740164,0.000240788,-1516,-48,Social Distancing and Wearing Masks Enforced,6.153072045
2020-11-04,4,11,2020,17214,151,Germany,DE,DEU,83019213,Europe,237.0909009,0.00020735,-2776,33,Social Distancing and Wearing Masks Enforced,6.060176792
2020-11-03,3,11,2020,15352,131,Germany,DE,DEU,83019213,Europe,225.5044263,0.000184921,-1862,-20,Social Distancing and Wearing Masks Enforced,5.989048079
2020-11-02,2,11,2020,12097,49,Germany,DE,DEU,83019213,Europe,215.2851052,0.000145713,-3255,-82,Social Distancing and Wearing Masks Enforced,5.840991252
2020-11-01,1,11,2020,14177,29,Germany,DE,DEU,83019213,Europe,205.9234168,0.000170768,2080,-20,Social Distancing and Wearing Masks Enforced,5.939574393
2020-10-31,31,10,2020,19059,103,Germany,DE,DEU,83019213,Europe,195.5764143,0.000229573,4882,74,Social Distancing and Wearing Masks Enforced,6.123438894
2020-10-30,30,10,2020,18681,77,Germany,DE,DEU,83019213,Europe,182.0506297,0.00022502,-378,-26,Social Distancing and Wearing Masks Enforced,6.110992022
2020-10-29,29,10,2020,16774,89,Germany,DE,DEU,83019213,Europe,168.3827092,0.00020205,-1907,12,Social Distancing and Wearing Masks Enforced,6.044088605
2020-10-28,28,10,2020,14964,85,Germany,DE,DEU,83019213,Europe,156.1734872,0.000180247,-1810,-4,Social Distancing and Wearing Masks Enforced,5.973142873
2020-10-27,27,10,2020,11409,42,Germany,DE,DEU,83019213,Europe,144.3304455,0.000137426,-3555,-43,Social Distancing and Wearing Masks Enforced,5.804609003
2020-10-26,26,10,2020,8685,24,Germany,DE,DEU,83019213,Europe,135.5529593,0.000104614,-2724,-18,Social Distancing and Wearing Masks Enforced,5.635105653
2020-10-25,25,10,2020,11176,29,Germany,DE,DEU,83019213,Europe,128.0631268,0.000134619,2491,5,Social Distancing and Wearing Masks Enforced,5.791788443
2020-10-24,24,10,2020,14714,49,Germany,DE,DEU,83019213,Europe,118.7965971,0.000177236,3538,20,Social Distancing and Wearing Masks Enforced,5.962674687
2020-10-23,23,10,2020,11242,49,Germany,DE,DEU,83019213,Europe,106.7596244,0.000135414,-3472,0,Social Distancing and Wearing Masks Enforced,5.795446952
2020-10-22,22,10,2020,11287,30,Germany,DE,DEU,83019213,Europe,98.65788537,0.000135956,45,-19,Social Distancing and Wearing Masks Enforced,5.797929096
2020-10-21,21,10,2020,7595,39,Germany,DE,DEU,83019213,Europe,89.95026248,9.15E-05,-3692,9,Social Distancing and Wearing Masks Enforced,5.551780125
2020-10-20,20,10,2020,6868,47,Germany,DE,DEU,83019213,Europe,84.20821816,8.27E-05,-727,8,Social Distancing and Wearing Masks Enforced,5.489263148
2020-10-19,19,10,2020,4325,12,Germany,DE,DEU,83019213,Europe,79.11421661,5.21E-05,-2543,-35,Social Distancing and Wearing Masks Enforced,5.201920096
2020-10-18,18,10,2020,5587,10,Germany,DE,DEU,83019213,Europe,75.56925407,6.73E-05,1262,-2,Social Distancing and Wearing Masks Enforced,5.361000684
2020-10-17,17,10,2020,7830,33,Germany,DE,DEU,83019213,Europe,71.58463427,9.43E-05,2243,23,Social Distancing and Wearing Masks Enforced,5.570713676
2020-10-16,16,10,2020,7334,24,Germany,DE,DEU,83019213,Europe,65.24031973,8.83E-05,-496,-9,Social Distancing and Wearing Masks Enforced,5.530052623
2020-10-15,15,10,2020,6638,33,Germany,DE,DEU,83019213,Europe,59.6259567,8.00E-05,-696,9,Social Distancing and Wearing Masks Enforced,5.468099095
2020-10-14,14,10,2020,5132,43,Germany,DE,DEU,83019213,Europe,54.64518195,6.18E-05,-1506,10,Social Distancing and Wearing Masks Enforced,5.308220131
2020-10-13,13,10,2020,4122,13,Germany,DE,DEU,83019213,Europe,50.6292441,4.97E-05,-1010,-30,Social Distancing and Wearing Masks Enforced,5.172050253
2020-10-12,12,10,2020,2467,6,Germany,DE,DEU,83019213,Europe,48.18041337,2.97E-05,-1655,-7,Social Distancing and Wearing Masks Enforced,4.853096883
2020-10-11,11,10,2020,3483,11,Germany,DE,DEU,83019213,Europe,46.6446243,4.20E-05,1016,5,Social Distancing and Wearing Masks Enforced,5.067389806
2020-10-10,10,10,2020,4721,15,Germany,DE,DEU,83019213,Europe,44.14761195,5.69E-05,1238,4,Social Distancing and Wearing Masks Enforced,5.256354318
2020-10-09,9,10,2020,4516,11,Germany,DE,DEU,83019213,Europe,41.4807594,5.44E-05,-205,-4,Social Distancing and Wearing Masks Enforced,5.228770778
2020-10-08,8,10,2020,4058,16,Germany,DE,DEU,83019213,Europe,38.63443032,4.89E-05,-458,5,Social Distancing and Wearing Masks Enforced,5.162327454
2020-10-07,7,10,2020,2828,16,Germany,DE,DEU,83019213,Europe,36.32773536,3.41E-05,-1230,0,Social Distancing and Wearing Masks Enforced,4.937950676
2020-10-06,6,10,2020,2639,12,Germany,DE,DEU,83019213,Europe,35.05212703,3.18E-05,-189,-4,Social Distancing and Wearing Masks Enforced,4.89497313
2020-10-05,5,10,2020,1382,5,Germany,DE,DEU,83019213,Europe,34.06681294,1.66E-05,-1257,-7,Social Distancing and Wearing Masks Enforced,4.493051238
2020-10-04,4,10,2020,2279,2,Germany,DE,DEU,83019213,Europe,33.51272434,2.75E-05,897,-3,Social Distancing and Wearing Masks Enforced,4.803846094
2020-10-03,3,10,2020,2563,19,Germany,DE,DEU,83019213,Europe,32.38768356,3.09E-05,284,17,Social Distancing and Wearing Masks Enforced,4.876816723
2020-10-02,2,10,2020,2673,8,Germany,DE,DEU,83019213,Europe,32.0672758,3.22E-05,110,-11,Social Distancing and Wearing Masks Enforced,4.902927075
2020-10-01,1,10,2020,2503,12,Germany,DE,DEU,83019213,Europe,31.15543868,3.01E-05,-170,4,Social Distancing and Wearing Masks Enforced,4.862098271
2020-09-30,30,9,2020,1798,17,Germany,DE,DEU,83019213,Europe,30.78323568,2.17E-05,-705,5,Social Distancing and Wearing Masks Enforced,4.656551307
2020-09-29,29,9,2020,2089,11,Germany,DE,DEU,83019213,Europe,30.90730335,2.52E-05,291,-6,Social Distancing and Wearing Masks Enforced,4.7497581
2020-09-28,28,9,2020,1192,3,Germany,DE,DEU,83019213,Europe,30.08580676,1.44E-05,-897,-8,Social Distancing and Wearing Masks Enforced,4.401156325
2020-09-27,27,9,2020,1410,5,Germany,DE,DEU,83019213,Europe,29.76660355,1.70E-05,218,2,Social Distancing and Wearing Masks Enforced,4.505513961
2020-09-26,26,9,2020,2507,9,Germany,DE,DEU,83019213,Europe,29.21010586,3.02E-05,1097,4,Social Distancing and Wearing Masks Enforced,4.863090423
2020-09-25,25,9,2020,2153,15,Germany,DE,DEU,83019213,Europe,28.15372389,2.59E-05,-354,6,Social Distancing and Wearing Masks Enforced,4.76850796
2020-09-24,24,9,2020,2143,19,Germany,DE,DEU,83019213,Europe,27.34788633,2.58E-05,-10,4,Social Distancing and Wearing Masks Enforced,4.765615335
2020-09-23,23,9,2020,1769,13,Germany,DE,DEU,83019213,Europe,27.04554667,2.13E-05,-374,-6,Social Distancing and Wearing Masks Enforced,4.646448078
2020-09-22,22,9,2020,1821,10,Germany,DE,DEU,83019213,Europe,26.33125419,2.19E-05,52,-3,Social Distancing and Wearing Masks Enforced,4.664449012
2020-09-21,21,9,2020,922,0,Germany,DE,DEU,83019213,Europe,25.94339216,1.11E-05,-899,-10,Social Distancing and Wearing Masks Enforced,4.24157103
2020-09-20,20,9,2020,1345,2,Germany,DE,DEU,83019213,Europe,25.8133018,1.62E-05,423,2,Social Distancing and Wearing Masks Enforced,4.476189629
2020-09-19,19,9,2020,2297,6,Germany,DE,DEU,83019213,Europe,25.38328086,2.77E-05,952,4,Social Distancing and Wearing Masks Enforced,4.808734244
2020-09-18,18,9,2020,1916,7,Germany,DE,DEU,83019213,Europe,24.27630818,2.31E-05,-381,1,Social Distancing and Wearing Masks Enforced,4.696046303
2020-09-17,17,9,2020,2194,3,Germany,DE,DEU,83019213,Europe,23.71860596,2.64E-05,278,-4,Social Distancing and Wearing Masks Enforced,4.780228912
2020-09-16,16,9,2020,1901,6,Germany,DE,DEU,83019213,Europe,22.65499674,2.29E-05,-293,3,Social Distancing and Wearing Masks Enforced,4.691162849
2020-09-15,15,9,2020,1407,12,Germany,DE,DEU,83019213,Europe,21.87806815,1.69E-05,-494,6,Social Distancing and Wearing Masks Enforced,4.504190563
2020-09-14,14,9,2020,927,1,Germany,DE,DEU,83019213,Europe,21.65041001,1.12E-05,-480,-11,Social Distancing and Wearing Masks Enforced,4.244931422
2020-09-13,13,9,2020,948,2,Germany,DE,DEU,83019213,Europe,21.26857069,1.14E-05,21,1,Social Distancing and Wearing Masks Enforced,4.258849906
2020-09-12,12,9,2020,1630,5,Germany,DE,DEU,83019213,Europe,21.07223059,1.96E-05,682,3,Social Distancing and Wearing Masks Enforced,4.595601506
2020-09-11,11,9,2020,1484,1,Germany,DE,DEU,83019213,Europe,20.89034499,1.79E-05,-146,-4,Social Distancing and Wearing Masks Enforced,4.537296138
2020-09-10,10,9,2020,1892,3,Germany,DE,DEU,83019213,Europe,20.99514,2.28E-05,408,2,Social Distancing and Wearing Masks Enforced,4.688214246
2020-09-09,9,9,2020,1176,9,Germany,DE,DEU,83019213,Europe,20.53139193,1.42E-05,-716,6,Social Distancing and Wearing Masks Enforced,4.392759779
2020-09-08,8,9,2020,1499,4,Germany,DE,DEU,83019213,Europe,21.01320811,1.81E-05,323,-5,Social Distancing and Wearing Masks Enforced,4.543544949
2020-09-07,7,9,2020,814,0,Germany,DE,DEU,83019213,Europe,20.74700467,9.80E-06,-685,-4,Social Distancing and Wearing Masks Enforced,4.164162105
2020-09-06,6,9,2020,988,1,Germany,DE,DEU,83019213,Europe,20.62293701,1.19E-05,174,1,Social Distancing and Wearing Masks Enforced,4.284528558
2020-09-05,5,9,2020,1378,2,Germany,DE,DEU,83019213,Europe,20.37480167,1.66E-05,390,1,Social Distancing and Wearing Masks Enforced,4.491250266
2020-09-04,4,9,2020,1453,1,Germany,DE,DEU,83019213,Europe,21.16498021,1.75E-05,75,-1,Social Distancing and Wearing Masks Enforced,4.524179285
2020-09-03,3,9,2020,1311,8,Germany,DE,DEU,83019213,Europe,21.13366216,1.58E-05,-142,7,Social Distancing and Wearing Masks Enforced,4.460281088
2020-09-02,2,9,2020,1256,11,Germany,DE,DEU,83019213,Europe,21.61066017,1.51E-05,-55,3,Social Distancing and Wearing Masks Enforced,4.433651831
2020-09-01,1,9,2020,1218,4,Germany,DE,DEU,83019213,Europe,21.91661345,1.47E-05,-38,-7,Social Distancing and Wearing Masks Enforced,4.414563242
2020-08-31,31,8,2020,610,3,Germany,DE,DEU,83019213,Europe,22.1237944,7.35E-06,-608,-1,Social Distancing and Wearing Masks Enforced,3.984906101
2020-08-30,30,8,2020,785,6,Germany,DE,DEU,83019213,Europe,22.06477192,9.46E-06,175,3,Social Distancing and Wearing Masks Enforced,4.141622157
2020-08-29,29,8,2020,1479,1,Germany,DE,DEU,83019213,Europe,21.87204545,1.78E-05,694,-5,Social Distancing and Wearing Masks Enforced,4.535199156
2020-08-28,28,8,2020,1571,3,Germany,DE,DEU,83019213,Europe,21.79495486,1.89E-05,92,2,Social Distancing and Wearing Masks Enforced,4.572694343
2020-08-27,27,8,2020,1507,5,Germany,DE,DEU,83019213,Europe,21.64800093,1.82E-05,-64,2,Social Distancing and Wearing Masks Enforced,4.546852129
2020-08-26,26,8,2020,1576,3,Germany,DE,DEU,83019213,Europe,21.57331942,1.90E-05,69,-2,Social Distancing and Wearing Masks Enforced,4.574668717
2020-08-25,25,8,2020,1278,5,Germany,DE,DEU,83019213,Europe,21.15173026,1.54E-05,-298,2,Social Distancing and Wearing Masks Enforced,4.444440869
2020-08-24,24,8,2020,711,3,Germany,DE,DEU,83019213,Europe,20.77591364,8.56E-06,-567,-2,Social Distancing and Wearing Masks Enforced,4.080102984
2020-08-23,23,8,2020,782,2,Germany,DE,DEU,83019213,Europe,20.44466502,9.42E-06,71,-1,Social Distancing and Wearing Masks Enforced,4.139243079
2020-08-22,22,8,2020,2034,7,Germany,DE,DEU,83019213,Europe,20.17123434,2.45E-05,1252,5,Social Distancing and Wearing Masks Enforced,4.733180148
2020-08-21,21,8,2020,1427,7,Germany,DE,DEU,83019213,Europe,19.07269345,1.72E-05,-607,0,Social Distancing and Wearing Masks Enforced,4.512960433
2020-08-20,20,8,2020,1707,10,Germany,DE,DEU,83019213,Europe,18.73542212,2.06E-05,280,3,Social Distancing and Wearing Masks Enforced,4.624280729
2020-08-19,19,8,2020,1510,7,Germany,DE,DEU,83019213,Europe,17.93801635,1.82E-05,-197,-3,Social Distancing and Wearing Masks Enforced,4.548087797
2020-08-18,18,8,2020,1390,4,Germany,DE,DEU,83019213,Europe,17.01172474,1.67E-05,-120,-3,Social Distancing and Wearing Masks Enforced,4.496637596
2020-08-17,17,8,2020,561,1,Germany,DE,DEU,83019213,Europe,16.39620457,6.76E-06,-829,-3,Social Distancing and Wearing Masks Enforced,3.932876725
2020-08-16,16,8,2020,625,0,Germany,DE,DEU,83019213,Europe,16.33356847,7.53E-06,64,-1,Social Distancing and Wearing Masks Enforced,4
2020-08-15,15,8,2020,1415,6,Germany,DE,DEU,83019213,Europe,15.8698204,1.70E-05,790,6,Social Distancing and Wearing Masks Enforced,4.507713379
2020-08-14,14,8,2020,1449,14,Germany,DE,DEU,83019213,Europe,15.31573179,1.75E-05,34,8,Social Distancing and Wearing Masks Enforced,4.522466438
2020-08-13,13,8,2020,1445,4,Germany,DE,DEU,83019213,Europe,14.61830287,1.74E-05,-4,-10,Social Distancing and Wearing Masks Enforced,4.520748855
2020-08-12,12,8,2020,1226,6,Germany,DE,DEU,83019213,Europe,13.96423741,1.48E-05,-219,2,Social Distancing and Wearing Masks Enforced,4.418630916
2020-08-11,11,8,2020,966,4,Germany,DE,DEU,83019213,Europe,13.31137649,1.16E-05,-260,-2,Social Distancing and Wearing Masks Enforced,4.270536801
2020-08-10,10,8,2020,436,1,Germany,DE,DEU,83019213,Europe,12.91026452,5.25E-06,-530,-3,Social Distancing and Wearing Masks Enforced,3.776251446
2020-08-09,9,8,2020,555,1,Germany,DE,DEU,83019213,Europe,12.79462864,6.69E-06,119,0,Social Distancing and Wearing Masks Enforced,3.926195639
2020-08-08,8,8,2020,1122,12,Germany,DE,DEU,83019213,Europe,12.49349352,1.35E-05,567,11,Social Distancing and Wearing Masks Enforced,4.363553283
2020-08-07,7,8,2020,1147,8,Germany,DE,DEU,83019213,Europe,12.08274523,1.38E-05,25,-4,Social Distancing and Wearing Masks Enforced,4.37724566
2020-08-06,6,8,2020,1045,7,Germany,DE,DEU,83019213,Europe,11.6828378,1.26E-05,-102,-1,Social Distancing and Wearing Masks Enforced,4.319378903
2020-08-05,5,8,2020,741,12,Germany,DE,DEU,83019213,Europe,11.10947655,8.93E-06,-304,5,Social Distancing and Wearing Masks Enforced,4.105781636
2020-08-04,4,8,2020,879,8,Germany,DE,DEU,83019213,Europe,10.76377344,1.06E-05,138,-4,Social Distancing and Wearing Masks Enforced,4.211895871
2020-08-03,3,8,2020,509,7,Germany,DE,DEU,83019213,Europe,10.3337525,6.13E-06,-370,-1,Social Distancing and Wearing Masks Enforced,3.872437681
2020-08-02,2,8,2020,240,0,Germany,DE,DEU,83019213,Europe,10.02057198,2.89E-06,-269,-7,Social Distancing and Wearing Masks Enforced,3.405312427
2020-08-01,1,8,2020,955,0,Germany,DE,DEU,83019213,Europe,9.97479945,1.15E-05,715,0,Social Distancing and Wearing Masks Enforced,4.263420967
2020-07-31,31,7,2020,870,7,Germany,DE,DEU,83019213,Europe,9.46166522,1.05E-05,-85,7,Social Distancing and Wearing Masks Enforced,4.205501287
2020-07-30,30,7,2020,902,6,Germany,DE,DEU,83019213,Europe,9.11596211,1.09E-05,32,-1,Social Distancing and Wearing Masks Enforced,4.227944718
2020-07-29,29,7,2020,684,6,Germany,DE,DEU,83019213,Europe,8.67269122,8.24E-06,-218,0,Social Distancing and Wearing Masks Enforced,4.056048306
2020-07-28,28,7,2020,633,4,Germany,DE,DEU,83019213,Europe,8.27157925,7.62E-06,-51,-2,Social Distancing and Wearing Masks Enforced,4.007902618
2020-07-27,27,7,2020,340,0,Germany,DE,DEU,83019213,Europe,8.00537582,4.10E-06,-293,-4,Social Distancing and Wearing Masks Enforced,3.621727544
2020-07-26,26,7,2020,305,0,Germany,DE,DEU,83019213,Europe,7.78735399,3.67E-06,-35,0,Social Distancing and Wearing Masks Enforced,3.554229543
2020-07-25,25,7,2020,781,7,Germany,DE,DEU,83019213,Europe,7.71869519,9.41E-06,476,7,Social Distancing and Wearing Masks Enforced,4.138448025
2020-07-24,24,7,2020,815,10,Germany,DE,DEU,83019213,Europe,7.23326539,9.82E-06,34,3,Social Distancing and Wearing Masks Enforced,4.164924948
2020-07-23,23,7,2020,569,6,Germany,DE,DEU,83019213,Europe,6.7273584,6.85E-06,-246,-4,Social Distancing and Wearing Masks Enforced,3.941674534
2020-07-22,22,7,2020,454,5,Germany,DE,DEU,83019213,Europe,6.57438176,5.47E-06,-115,-1,Social Distancing and Wearing Masks Enforced,3.801387522
2020-07-21,21,7,2020,522,4,Germany,DE,DEU,83019213,Europe,6.50572296,6.29E-06,68,-1,Social Distancing and Wearing Masks Enforced,3.888107481
2020-07-20,20,7,2020,249,2,Germany,DE,DEU,83019213,Europe,6.34672362,3.00E-06,-273,-2,Social Distancing and Wearing Masks Enforced,3.428186234
2020-07-19,19,7,2020,202,1,Germany,DE,DEU,83019213,Europe,6.31058741,2.43E-06,-47,-1,Social Distancing and Wearing Masks Enforced,3.298212162
2020-07-18,18,7,2020,529,1,Germany,DE,DEU,83019213,Europe,6.3551554,6.37E-06,327,0,Social Distancing and Wearing Masks Enforced,3.896384187
2020-07-17,17,7,2020,583,4,Germany,DE,DEU,83019213,Europe,6.22626957,7.02E-06,54,3,Social Distancing and Wearing Masks Enforced,3.956777169
2020-07-16,16,7,2020,534,7,Germany,DE,DEU,83019213,Europe,6.06124753,6.43E-06,-49,3,Social Distancing and Wearing Masks Enforced,3.902229338
2020-07-15,15,7,2020,351,3,Germany,DE,DEU,83019213,Europe,6.02390678,4.23E-06,-183,-4,Social Distancing and Wearing Masks Enforced,3.641511225
2020-07-14,14,7,2020,412,4,Germany,DE,DEU,83019213,Europe,6.16242893,4.96E-06,61,1,Social Distancing and Wearing Masks Enforced,3.741072149
2020-07-13,13,7,2020,159,1,Germany,DE,DEU,83019213,Europe,6.26601941,1.92E-06,-253,-3,Social Distancing and Wearing Masks Enforced,3.149487261
2020-07-12,12,7,2020,248,3,Germany,DE,DEU,83019213,Europe,6.39008708,2.99E-06,89,2,Social Distancing and Wearing Masks Enforced,3.425685889
2020-07-11,11,7,2020,378,6,Germany,DE,DEU,83019213,Europe,6.3997234,4.55E-06,130,3,Social Distancing and Wearing Masks Enforced,3.687557097
2020-07-10,10,7,2020,395,6,Germany,DE,DEU,83019213,Europe,6.7719264,4.76E-06,17,0,Social Distancing and Wearing Masks Enforced,3.714890595
2020-07-09,9,7,2020,442,12,Germany,DE,DEU,83019213,Europe,6.87069871,5.32E-06,47,6,Social Distancing and Wearing Masks Enforced,3.784743627
2020-07-08,8,7,2020,397,12,Germany,DE,DEU,83019213,Europe,7.09715232,4.78E-06,-45,0,Social Distancing and Wearing Masks Enforced,3.718028657
2020-07-07,7,7,2020,390,8,Germany,DE,DEU,83019213,Europe,7.326015,4.70E-06,-7,-4,Social Distancing and Wearing Masks Enforced,3.706975394
2020-07-06,6,7,2020,219,4,Germany,DE,DEU,83019213,Europe,7.46212807,2.64E-06,-171,-4,Social Distancing and Wearing Masks Enforced,3.348418531
2020-07-05,5,7,2020,239,2,Germany,DE,DEU,83019213,Europe,7.84517194,2.88E-06,20,-2,Social Distancing and Wearing Masks Enforced,3.402718123
2020-07-04,4,7,2020,422,7,Germany,DE,DEU,83019213,Europe,8.38480606,5.08E-06,183,5,Social Distancing and Wearing Masks Enforced,3.755972981
2020-07-03,3,7,2020,446,9,Germany,DE,DEU,83019213,Europe,8.6004188,5.37E-06,24,2,Social Distancing and Wearing Masks Enforced,3.790341277
2020-07-02,2,7,2020,503,9,Germany,DE,DEU,83019213,Europe,8.9906899,6.06E-06,57,0,Social Distancing and Wearing Masks Enforced,3.865069986
2020-07-01,1,7,2020,466,12,Germany,DE,DEU,83019213,Europe,9.08343952,5.61E-06,-37,3,Social Distancing and Wearing Masks Enforced,3.817597179
2020-06-30,30,6,2020,498,12,Germany,DE,DEU,83019213,Europe,8.93769012,6.00E-06,32,0,Social Distancing and Wearing Masks Enforced,3.858862792
2020-06-29,29,6,2020,262,4,Germany,DE,DEU,83019213,Europe,8.79314527,3.16E-06,-236,-8,Social Distancing and Wearing Masks Enforced,3.459806968
2020-06-28,28,6,2020,256,3,Germany,DE,DEU,83019213,Europe,8.70882744,3.08E-06,-6,-1,Social Distancing and Wearing Masks Enforced,3.445412465
2020-06-27,27,6,2020,687,6,Germany,DE,DEU,83019213,Europe,8.69798657,8.28E-06,431,3,Social Distancing and Wearing Masks Enforced,4.0587675
2020-06-26,26,6,2020,477,21,Germany,DE,DEU,83019213,Europe,8.28964736,5.75E-06,-210,15,Social Distancing and Wearing Masks Enforced,3.832093455
2020-06-25,25,6,2020,630,13,Germany,DE,DEU,83019213,Europe,8.025853,7.59E-06,153,-8,Social Distancing and Wearing Masks Enforced,4.004950902
2020-06-24,24,6,2020,587,19,Germany,DE,DEU,83019213,Europe,7.93551247,7.07E-06,-43,6,Social Distancing and Wearing Masks Enforced,3.961025629
2020-06-23,23,6,2020,503,10,Germany,DE,DEU,83019213,Europe,7.61149109,6.06E-06,-84,-9,Social Distancing and Wearing Masks Enforced,3.865069986
2020-06-22,22,6,2020,537,3,Germany,DE,DEU,83019213,Europe,7.4271964,6.47E-06,34,-7,Social Distancing and Wearing Masks Enforced,3.905710215
2020-06-21,21,6,2020,687,0,Germany,DE,DEU,83019213,Europe,7.03812984,8.28E-06,150,-3,Social Distancing and Wearing Masks Enforced,4.0587675
2020-06-20,20,6,2020,601,10,Germany,DE,DEU,83019213,Europe,6.57317722,7.24E-06,-86,10,Social Distancing and Wearing Masks Enforced,3.975670565
2020-06-19,19,6,2020,770,16,Germany,DE,DEU,83019213,Europe,6.33949638,9.27E-06,169,6,Social Distancing and Wearing Masks Enforced,4.129634616
2020-06-18,18,6,2020,580,26,Germany,DE,DEU,83019213,Europe,6.02270224,6.99E-06,-190,10,Social Distancing and Wearing Masks Enforced,3.95357165
2020-06-17,17,6,2020,345,30,Germany,DE,DEU,83019213,Europe,5.79865772,4.16E-06,-235,4,Social Distancing and Wearing Masks Enforced,3.630798288
2020-06-16,16,6,2020,378,9,Germany,DE,DEU,83019213,Europe,5.79504409,4.55E-06,33,-21,Social Distancing and Wearing Masks Enforced,3.687557097
2020-06-15,15,6,2020,192,4,Germany,DE,DEU,83019213,Europe,5.59629492,2.31E-06,-186,-5,Social Distancing and Wearing Masks Enforced,3.266665543
2020-06-14,14,6,2020,247,6,Germany,DE,DEU,83019213,Europe,5.76613512,2.98E-06,55,2,Social Distancing and Wearing Masks Enforced,3.423175442
2020-06-13,13,6,2020,348,18,Germany,DE,DEU,83019213,Europe,5.8131122,4.19E-06,101,12,Social Distancing and Wearing Masks Enforced,3.636177845
2020-06-12,12,6,2020,258,8,Germany,DE,DEU,83019213,Europe,6.28288298,3.11E-06,-90,-10,Social Distancing and Wearing Masks Enforced,3.45024778
2020-06-11,11,6,2020,555,26,Germany,DE,DEU,83019213,Europe,6.86467601,6.69E-06,297,18,Social Distancing and Wearing Masks Enforced,3.926195639
2020-06-10,10,6,2020,318,18,Germany,DE,DEU,83019213,Europe,6.62135884,3.83E-06,-237,-8,Social Distancing and Wearing Masks Enforced,3.580163819
2020-06-09,9,6,2020,350,37,Germany,DE,DEU,83019213,Europe,6.67435862,4.22E-06,32,19,Social Distancing and Wearing Masks Enforced,3.639738513
2020-06-08,8,6,2020,214,6,Germany,DE,DEU,83019213,Europe,6.77313094,2.58E-06,-136,-31,Social Distancing and Wearing Masks Enforced,3.334068356
2020-06-07,7,6,2020,301,22,Germany,DE,DEU,83019213,Europe,6.86347147,3.63E-06,87,16,Social Distancing and Wearing Masks Enforced,3.546026983
2020-06-06,6,6,2020,407,33,Germany,DE,DEU,83019213,Europe,7.02006173,4.90E-06,106,11,Social Distancing and Wearing Masks Enforced,3.733485547
2020-06-05,5,6,2020,507,32,Germany,DE,DEU,83019213,Europe,7.29831057,6.11E-06,100,-1,Social Distancing and Wearing Masks Enforced,3.869991477
2020-06-04,4,6,2020,394,30,Germany,DE,DEU,83019213,Europe,7.24169717,4.75E-06,-113,-2,Social Distancing and Wearing Masks Enforced,3.713315601
2020-06-03,3,6,2020,342,29,Germany,DE,DEU,83019213,Europe,7.66449087,4.12E-06,-52,-1,Social Distancing and Wearing Masks Enforced,3.625371747
2020-06-02,2,6,2020,213,11,Germany,DE,DEU,83019213,Europe,8.21255677,2.57E-06,-129,-18,Social Distancing and Wearing Masks Enforced,3.331158117
2020-06-01,1,6,2020,333,11,Germany,DE,DEU,83019213,Europe,8.57391891,4.01E-06,120,0,Social Distancing and Wearing Masks Enforced,3.608801834
2020-05-31,31,5,2020,286,11,Germany,DE,DEU,83019213,Europe,8.58475977,3.44E-06,-47,0,Social Distancing and Wearing Masks Enforced,3.514265302
2020-05-30,30,5,2020,738,39,Germany,DE,DEU,83019213,Europe,8.94250828,8.89E-06,452,28,Social Distancing and Wearing Masks Enforced,4.103261004
2020-05-29,29,5,2020,741,39,Germany,DE,DEU,83019213,Europe,8.80037251,8.93E-06,3,0,Social Distancing and Wearing Masks Enforced,4.105781636
2020-05-28,28,5,2020,353,62,Germany,DE,DEU,83019213,Europe,9.00755347,4.25E-06,-388,23,Social Distancing and Wearing Masks Enforced,3.645041546
2020-05-27,27,5,2020,362,47,Germany,DE,DEU,83019213,Europe,9.70618693,4.36E-06,9,-15,Social Distancing and Wearing Masks Enforced,3.660684371
2020-05-26,26,5,2020,432,45,Germany,DE,DEU,83019213,Europe,10.23136656,5.20E-06,70,-2,Social Distancing and Wearing Masks Enforced,3.770524816
2020-05-25,25,5,2020,289,10,Germany,DE,DEU,83019213,Europe,10.83484133,3.48E-06,-143,-35,Social Distancing and Wearing Masks Enforced,3.520748855
2020-05-24,24,5,2020,431,31,Germany,DE,DEU,83019213,Europe,10.91675008,5.19E-06,142,21,Social Distancing and Wearing Masks Enforced,3.769084873
2020-05-23,23,5,2020,638,42,Germany,DE,DEU,83019213,Europe,11.20102162,7.68E-06,207,11,Social Distancing and Wearing Masks Enforced,4.012791195
2020-05-22,22,5,2020,460,27,Germany,DE,DEU,83019213,Europe,11.93940492,5.54E-06,-178,-15,Social Distancing and Wearing Masks Enforced,3.80954521
2020-05-21,21,5,2020,745,57,Germany,DE,DEU,83019213,Europe,12.84160571,8.97E-06,285,30,Social Distancing and Wearing Masks Enforced,4.109126651
2020-05-20,20,5,2020,797,83,Germany,DE,DEU,83019213,Europe,13.49085301,9.60E-06,52,26,Social Distancing and Wearing Masks Enforced,4.151048405
2020-05-19,19,5,2020,513,72,Germany,DE,DEU,83019213,Europe,13.67153408,6.18E-06,-284,-11,Social Distancing and Wearing Masks Enforced,3.877301384
2020-05-18,18,5,2020,342,21,Germany,DE,DEU,83019213,Europe,13.87871504,4.12E-06,-171,-51,Social Distancing and Wearing Masks Enforced,3.625371747
2020-05-17,17,5,2020,583,33,Germany,DE,DEU,83019213,Europe,14.28464517,7.02E-06,241,12,Social Distancing and Wearing Masks Enforced,3.956777169
2020-05-16,16,5,2020,620,57,Germany,DE,DEU,83019213,Europe,14.53759866,7.47E-06,37,24,Social Distancing and Wearing Masks Enforced,3.995009331
2020-05-15,15,5,2020,913,101,Germany,DE,DEU,83019213,Europe,14.92907431,1.10E-05,293,44,Social Distancing and Wearing Masks Enforced,4.235476142
2020-05-14,14,5,2020,933,89,Germany,DE,DEU,83019213,Europe,15.80357067,1.12E-05,20,-12,Social Distancing and Wearing Masks Enforced,4.248940048
2020-05-13,13,5,2020,798,101,Germany,DE,DEU,83019213,Europe,16.46004522,9.61E-06,-135,12,Social Distancing and Wearing Masks Enforced,4.151827508
2020-05-12,12,5,2020,933,116,Germany,DE,DEU,83019213,Europe,17.06954269,1.12E-05,135,15,Social Distancing and Wearing Masks Enforced,4.248940048
2020-05-11,11,5,2020,357,22,Germany,DE,DEU,83019213,Europe,17.32370072,4.30E-06,-576,-94,Social Distancing and Wearing Masks Enforced,3.652042577
2020-05-10,10,5,2020,667,26,Germany,DE,DEU,83019213,Europe,18.11990196,8.03E-06,310,4,Social Distancing and Wearing Masks Enforced,4.040410628
2020-05-09,9,5,2020,1251,103,Germany,DE,DEU,83019213,Europe,19.40876023,1.51E-05,584,77,Social Distancing and Wearing Masks Enforced,4.431173427
2020-05-08,8,5,2020,1209,147,Germany,DE,DEU,83019213,Europe,20.37721075,1.46E-05,-42,44,Social Distancing and Wearing Masks Enforced,4.409955051
2020-05-07,7,5,2020,1284,123,Germany,DE,DEU,83019213,Europe,21.73593238,1.55E-05,75,-24,Social Distancing and Wearing Masks Enforced,4.447351109
2020-05-06,6,5,2020,947,165,Germany,DE,DEU,83019213,Europe,23.02238158,1.14E-05,-337,42,Social Distancing and Wearing Masks Enforced,4.258194144
2020-05-05,5,5,2020,685,139,Germany,DE,DEU,83019213,Europe,24.57623876,8.25E-06,-262,-26,Social Distancing and Wearing Masks Enforced,4.056956027
2020-05-04,4,5,2020,679,43,Germany,DE,DEU,83019213,Europe,25.90123325,8.18E-06,-6,-96,Social Distancing and Wearing Masks Enforced,4.051489702
2020-05-03,3,5,2020,793,74,Germany,DE,DEU,83019213,Europe,27.22140958,9.55E-06,114,31,Social Distancing and Wearing Masks Enforced,4.147922185
2020-05-02,2,5,2020,945,94,Germany,DE,DEU,83019213,Europe,29.22696942,1.14E-05,152,20,Social Distancing and Wearing Masks Enforced,4.256880539
2020-05-01,1,5,2020,1639,193,Germany,DE,DEU,83019213,Europe,32.43586518,1.97E-05,694,99,Social Distancing and Wearing Masks Enforced,4.599022753
2020-04-30,30,4,2020,1478,173,Germany,DE,DEU,83019213,Europe,34.5329701,1.78E-05,-161,-20,Social Distancing and Wearing Masks Enforced,4.53477891
2020-04-29,29,4,2020,1304,202,Germany,DE,DEU,83019213,Europe,36.20487224,1.57E-05,-174,29,Social Distancing and Wearing Masks Enforced,4.456954622
2020-04-28,28,4,2020,1144,163,Germany,DE,DEU,83019213,Europe,37.62863905,1.38E-05,-160,-39,Social Distancing and Wearing Masks Enforced,4.375618418
2020-04-27,27,4,2020,1018,110,Germany,DE,DEU,83019213,Europe,38.75849799,1.23E-05,-126,-53,Social Distancing and Wearing Masks Enforced,4.303114239
2020-04-26,26,4,2020,1737,140,Germany,DE,DEU,83019213,Europe,40.58819493,2.09E-05,719,30,Social Distancing and Wearing Masks Enforced,4.635105653
2020-04-25,25,4,2020,2055,179,Germany,DE,DEU,83019213,Europe,41.89391677,2.48E-05,318,39,Social Distancing and Wearing Masks Enforced,4.739562221
2020-04-24,24,4,2020,2337,227,Germany,DE,DEU,83019213,Europe,44.39695182,2.82E-05,282,48,Social Distancing and Wearing Masks Enforced,4.819461052
2020-04-23,23,4,2020,2352,215,Germany,DE,DEU,83019213,Europe,47.9937096,2.83E-05,15,-12,Social Distancing and Wearing Masks Enforced,4.823436337
2020-04-22,22,4,2020,2237,281,Germany,DE,DEU,83019213,Europe,51.15201465,2.69E-05,-115,66,Social Distancing and Wearing Masks Enforced,4.792288601
2020-04-21,21,4,2020,1785,194,Germany,DE,DEU,83019213,Europe,53.27923309,2.15E-05,-452,-87,Social Distancing and Wearing Masks Enforced,4.652042577
2020-04-20,20,4,2020,1775,110,Germany,DE,DEU,83019213,Europe,55.74733646,2.14E-05,-10,-84,Social Distancing and Wearing Masks Enforced,4.648551922
2020-04-19,19,4,2020,2458,184,Germany,DE,DEU,83019213,Europe,58.03837239,2.96E-05,683,74,Social Distancing and Wearing Masks Enforced,4.850826012
2020-04-18,18,4,2020,3609,242,Germany,DE,DEU,83019213,Europe,62.22776407,4.35E-05,1151,58,Social Distancing and Wearing Masks Enforced,5.08947002
2020-04-17,17,4,2020,3380,299,Germany,DE,DEU,83019213,Europe,65.2065926,4.07E-05,-229,57,Social Distancing and Wearing Masks Enforced,5.048738398
2020-04-16,16,4,2020,2866,315,Germany,DE,DEU,83019213,Europe,68.57207861,3.45E-05,-514,16,Social Distancing and Wearing Masks Enforced,4.946243994
2020-04-15,15,4,2020,2486,285,Germany,DE,DEU,83019213,Europe,72.53501668,2.99E-05,-380,-30,Social Distancing and Wearing Masks Enforced,4.857863861
2020-04-14,14,4,2020,2082,170,Germany,DE,DEU,83019213,Europe,76.10888819,2.51E-05,-404,-115,Social Distancing and Wearing Masks Enforced,4.747672582
2020-04-13,13,4,2020,2537,126,Germany,DE,DEU,83019213,Europe,79.15998915,3.06E-05,455,-44,Social Distancing and Wearing Masks Enforced,4.870481489
2020-04-12,12,4,2020,2821,129,Germany,DE,DEU,83019213,Europe,81.8268417,3.40E-05,284,3,Social Distancing and Wearing Masks Enforced,4.936410811
2020-04-11,11,4,2020,4133,171,Germany,DE,DEU,83019213,Europe,83.20483597,4.98E-05,1312,42,Social Distancing and Wearing Masks Enforced,5.173706143
2020-04-10,10,4,2020,5323,266,Germany,DE,DEU,83019213,Europe,85.80784788,6.41E-05,1190,95,Social Distancing and Wearing Masks Enforced,5.330924708
2020-04-09,9,4,2020,4974,246,Germany,DE,DEU,83019213,Europe,86.35832286,5.99E-05,-349,-20,Social Distancing and Wearing Masks Enforced,5.288790303
2020-04-08,8,4,2020,4003,254,Germany,DE,DEU,83019213,Europe,86.33423205,4.82E-05,-971,8,Social Distancing and Wearing Masks Enforced,5.153848617
2020-04-07,7,4,2020,3834,173,Germany,DE,DEU,83019213,Europe,84.33349037,4.62E-05,-169,-81,Social Distancing and Wearing Masks Enforced,5.127047064
2020-04-06,6,4,2020,3677,92,Germany,DE,DEU,83019213,Europe,85.0610328,4.43E-05,-157,-81,Social Distancing and Wearing Masks Enforced,5.101068154
2020-04-05,5,4,2020,5936,184,Germany,DE,DEU,83019213,Europe,84.620171,7.15E-05,2259,92,Social Distancing and Wearing Masks Enforced,5.398649254
2020-04-04,4,4,2020,6082,141,Germany,DE,DEU,83019213,Europe,81.4160934,7.33E-05,146,-43,Social Distancing and Wearing Masks Enforced,5.413746502
2020-04-03,3,4,2020,6174,145,Germany,DE,DEU,83019213,Europe,78.96726267,7.44E-05,92,4,Social Distancing and Wearing Masks Enforced,5.423074812
2020-04-02,2,4,2020,6156,140,Germany,DE,DEU,83019213,Europe,78.68540021,7.42E-05,-18,-5,Social Distancing and Wearing Masks Enforced,5.421260695
2020-04-01,1,4,2020,5453,149,Germany,DE,DEU,83019213,Europe,72.52538036,6.57E-05,-703,9,Social Distancing and Wearing Masks Enforced,5.345916813
2020-03-31,31,3,2020,4615,128,Germany,DE,DEU,83019213,Europe,67.33501557,5.56E-05,-838,-21,Social Distancing and Wearing Masks Enforced,5.242244564
2020-03-30,30,3,2020,4751,66,Germany,DE,DEU,83019213,Europe,63.19019189,5.72E-05,136,-62,Social Distancing and Wearing Masks Enforced,5.260290152
2020-03-29,29,3,2020,3965,64,Germany,DE,DEU,83019213,Europe,58.72375591,4.78E-05,-786,-2,Social Distancing and Wearing Masks Enforced,5.147922185
2020-03-28,28,3,2020,6294,72,Germany,DE,DEU,83019213,Europe,54.83068118,7.58E-05,2329,8,Social Distancing and Wearing Masks Enforced,5.435035431
2020-03-27,27,3,2020,5780,55,Germany,DE,DEU,83019213,Europe,48.08405013,6.96E-05,-514,-17,Social Distancing and Wearing Masks Enforced,5.382101972
2020-03-26,26,3,2020,4954,49,Germany,DE,DEU,83019213,Europe,42.08784779,5.97E-05,-826,-6,Social Distancing and Wearing Masks Enforced,5.286286936
2020-03-25,25,3,2020,2342,23,Germany,DE,DEU,83019213,Europe,36.44698487,2.82E-05,-2612,-26,Social Distancing and Wearing Masks Enforced,4.820788975
2020-03-24,24,3,2020,4438,32,Germany,DE,DEU,83019213,Europe,33.81506399,5.35E-05,2096,9,Social Distancing and Wearing Masks Enforced,5.21794537
2020-03-23,23,3,2020,3311,27,Germany,DE,DEU,83019213,Europe,28.75478957,3.99E-05,-1127,-5,Social Distancing and Wearing Masks Enforced,5.035923085
2020-03-22,22,3,2020,3276,22,Germany,DE,DEU,83019213,Europe,24.83280587,3.95E-05,-35,-5,Social Distancing and Wearing Masks Enforced,5.029320101
2020-03-21,21,3,2020,4049,2,Germany,DE,DEU,83019213,Europe,21.08307146,4.88E-05,773,-20,Social Distancing and Wearing Masks Enforced,5.160947901
2020-03-20,20,3,2020,5940,30,Germany,DE,DEU,83019213,Europe,16.54797667,7.15E-05,1891,28,Social Distancing and Wearing Masks Enforced,5.399067802
2020-03-19,19,3,2020,1042,0,Germany,DE,DEU,83019213,Europe,9.55923299,1.26E-05,-4898,-30,Social Distancing and Wearing Masks Enforced,4.317592601
2020-03-18,18,3,2020,1144,0,Germany,DE,DEU,83019213,Europe,8.38360152,1.38E-05,102,0,Social Distancing and Wearing Masks Enforced,4.375618418
2020-03-17,17,3,2020,1174,1,Germany,DE,DEU,83019213,Europe,7.05258432,1.41E-05,30,1,Social Distancing and Wearing Masks Enforced,4.391702187
2020-03-16,16,3,2020,1043,4,Germany,DE,DEU,83019213,Europe,5.67218097,1.26E-05,-131,3,Social Distancing and Wearing Masks Enforced,4.318188606
2020-03-15,15,3,2020,733,3,Germany,DE,DEU,83019213,Europe,4.43752701,8.83E-06,-310,-1,Social Distancing and Wearing Masks Enforced,4.099037093
2020-03-14,14,3,2020,693,0,Germany,DE,DEU,83019213,Europe,3.61964405,8.35E-06,-40,-3,Social Distancing and Wearing Masks Enforced,4.064170446
2020-03-13,13,3,2020,802,2,Germany,DE,DEU,83019213,Europe,2.79694292,9.66E-06,109,2,Social Distancing and Wearing Masks Enforced,4.154934189
2020-03-12,12,3,2020,271,1,Germany,DE,DEU,83019213,Europe,1.86221953,3.26E-06,-531,-1,Social Distancing and Wearing Masks Enforced,3.480792131
2020-03-11,11,3,2020,157,0,Germany,DE,DEU,83019213,Europe,1.54060723,1.89E-06,-114,-1,Social Distancing and Wearing Masks Enforced,3.141622157
2020-03-10,10,3,2020,237,2,Germany,DE,DEU,83019213,Europe,1.35390346,2.85E-06,80,2,Social Distancing and Wearing Masks Enforced,3.39749679
2020-03-09,9,3,2020,55,0,Germany,DE,DEU,83019213,Europe,1.06842738,6.62E-07,-182,-2,Social Distancing and Wearing Masks Enforced,2.489896102
2020-03-08,8,3,2020,163,0,Germany,DE,DEU,83019213,Europe,1.00217765,1.96E-06,108,0,Lockdown,3.164924948
2020-03-07,7,3,2020,284,0,Germany,DE,DEU,83019213,Europe,0.80583756,3.42E-06,121,0,Lockdown,3.509905039
2020-03-06,6,3,2020,138,0,Germany,DE,DEU,83019213,Europe,0.46374807,1.66E-06,-146,0,Lockdown,3.061474846
2020-03-05,5,3,2020,66,0,Germany,DE,DEU,83019213,Europe,0.29752149,7.95E-07,-72,0,Lockdown,2.603178855
2020-03-04,4,3,2020,39,0,Germany,DE,DEU,83019213,Europe,0.21802182,4.70E-07,-27,0,Lockdown,2.276298836
2020-03-03,3,3,2020,28,0,Germany,DE,DEU,83019213,Europe,0.17104474,3.37E-07,-11,0,Lockdown,2.070415071
2020-03-02,2,3,2020,18,0,Germany,DE,DEU,83019213,Europe,0.13731761,2.17E-07,-10,0,Lockdown,1.795888947
2020-03-01,1,3,2020,54,0,Germany,DE,DEU,83019213,Europe,0.11563588,6.50E-07,36,0,Lockdown,2.478495142
2020-02-29,29,2,2020,10,0,Germany,DE,DEU,83019213,Europe,0.0505907,1.20E-07,-44,0,Lockdown,1.430676558
2020-02-28,28,2,2020,26,0,Germany,DE,DEU,83019213,Europe,0.03854529,3.13E-07,16,0,Lockdown,2.024369199
2020-02-27,27,2,2020,4,0,Germany,DE,DEU,83019213,Europe,0.00722724,4.82E-08,-22,0,Lockdown,0.861353116
2020-02-26,26,2,2020,2,0,Germany,DE,DEU,83019213,Europe,0.00240908,2.41E-08,-2,0,Lockdown,0.430676558
2020-02-25,25,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00240908,0,-2,0,Lockdown,#NUM!
2020-02-24,24,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00240908,0,0,0,Lockdown,#NUM!
2020-02-23,23,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00240908,0,0,0,Lockdown,#NUM!
2020-02-22,22,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00240908,0,0,0,Lockdown,#NUM!
2020-02-21,21,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00361362,0,0,0,Lockdown,#NUM!
2020-02-20,20,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00481816,0,0,0,Lockdown,#NUM!
2020-02-19,19,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00481816,0,0,0,Lockdown,#NUM!
2020-02-18,18,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00481816,0,0,0,Lockdown,#NUM!
2020-02-17,17,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00722724,0,0,0,Lockdown,#NUM!
2020-02-16,16,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00843178,0,0,0,Lockdown,#NUM!
2020-02-15,15,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00963632,0,0,0,Lockdown,#NUM!
2020-02-14,14,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.0120454,0,0,0,Lockdown,#NUM!
2020-02-13,13,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.01324994,0,0,0,Lockdown,#NUM!
2020-02-12,12,2,2020,2,0,Germany,DE,DEU,83019213,Europe,0.01324994,2.41E-08,2,0,Lockdown,0.430676558
2020-02-11,11,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.01445449,0,-2,0,Lockdown,#NUM!
2020-02-10,10,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.01565903,0,0,0,Lockdown,#NUM!
2020-02-09,9,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.01565903,0,0,0,Lockdown,#NUM!
2020-02-08,8,2,2020,1,0,Germany,DE,DEU,83019213,Europe,0.01565903,1.20E-08,1,0,Lockdown,0
2020-02-07,7,2,2020,1,0,Germany,DE,DEU,83019213,Europe,0.01445449,1.20E-08,0,0,Lockdown,0
2020-02-06,6,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.01324994,0,-1,0,Lockdown,#NUM!
2020-02-05,5,2,2020,0,0,Germany,DE,DEU,83019213,Europe,0.01324994,0,0,0,Lockdown,#NUM!
2020-02-04,4,2,2020,2,0,Germany,DE,DEU,83019213,Europe,0.01324994,2.41E-08,2,0,Lockdown,0.430676558
2020-02-03,3,2,2020,1,0,Germany,DE,DEU,83019213,Europe,0.01084086,1.20E-08,-1,0,Lockdown,0
2020-02-02,2,2,2020,1,0,Germany,DE,DEU,83019213,Europe,0.00963632,1.20E-08,0,0,Lockdown,0
2020-02-01,1,2,2020,2,0,Germany,DE,DEU,83019213,Europe,0.00843178,2.41E-08,1,0,Lockdown,0.430676558
2020-01-31,31,1,2020,1,0,Germany,DE,DEU,83019213,Europe,0.0060227,1.20E-08,-1,0,Lockdown,0
2020-01-30,30,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0.00481816,0,-1,0,Lockdown,#NUM!
2020-01-29,29,1,2020,3,0,Germany,DE,DEU,83019213,Europe,0.00481816,3.61E-08,3,0,Lockdown,0.682606194
2020-01-28,28,1,2020,1,0,Germany,DE,DEU,83019213,Europe,0.00120454,1.20E-08,-2,0,Lockdown,0
2020-01-27,27,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,-1,0,Lockdown,#NUM!
2020-01-26,26,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-25,25,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-24,24,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-23,23,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-22,22,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-21,21,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-20,20,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-19,19,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-18,18,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-17,17,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-16,16,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-15,15,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-14,14,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-13,13,1,2020,0,0,Germany,DE,DEU,83019213,Europe,0,0,0,0,Lockdown,#NUM!
2020-01-12,12,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-11,11,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-10,10,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-09,9,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-08,8,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-07,7,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-06,6,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-05,5,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-04,4,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-03,3,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-02,2,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-01-01,1,1,2020,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2019-12-31,31,12,2019,0,0,Germany,DE,DEU,83019213,Europe,,0,0,0,Lockdown,#NUM!
2020-12-09,9,12,2020,3,10,Belgium,BE,BEL,11455519,Europe,251.6079804,2.62E-07,3,10,Social Distancing and Wearing Masks Enforced,0.682606194
2020-12-08,8,12,2020,1530,73,Belgium,BE,BEL,11455519,Europe,272.7593573,0.00013356,1527,63,Social Distancing and Wearing Masks Enforced,4.556263375
2020-12-07,7,12,2020,577,77,Belgium,BE,BEL,11455519,Europe,272.8641103,5.04E-05,-953,4,Social Distancing and Wearing Masks Enforced,3.950349509
2020-12-06,6,12,2020,1084,81,Belgium,BE,BEL,11455519,Europe,274.4266759,9.46E-05,507,4,Social Distancing and Wearing Masks Enforced,4.342145247
2020-12-05,5,12,2020,2516,100,Belgium,BE,BEL,11455519,Europe,279.3587964,0.000219632,1432,19,Social Distancing and Wearing Masks Enforced,4.865316989
2020-12-04,4,12,2020,2353,92,Belgium,BE,BEL,11455519,Europe,285.172588,0.000205403,-163,-8,Social Distancing and Wearing Masks Enforced,4.823700454
2020-12-03,3,12,2020,2602,117,Belgium,BE,BEL,11455519,Europe,294.7574876,0.000227139,249,25,Social Distancing and Wearing Masks Enforced,4.886200082
2020-12-02,2,12,2020,2672,108,Belgium,BE,BEL,11455519,Europe,313.5781103,0.00023325,70,-9,Social Distancing and Wearing Masks Enforced,4.902694583
2020-12-01,1,12,2020,3291,98,Belgium,BE,BEL,11455519,Europe,335.6635348,0.000287285,619,-10,Social Distancing and Wearing Masks Enforced,5.032158548
2020-11-30,30,11,2020,560,118,Belgium,BE,BEL,11455519,Europe,340.0020549,4.89E-05,-2731,20,Social Distancing and Wearing Masks Enforced,3.931768187
2020-11-29,29,11,2020,1004,114,Belgium,BE,BEL,11455519,Europe,351.9351677,8.76E-05,444,-4,Social Distancing and Wearing Masks Enforced,4.294510056
2020-11-28,28,11,2020,2696,124,Belgium,BE,BEL,11455519,Europe,378.2369005,0.000235345,1692,10,Social Distancing and Wearing Masks Enforced,4.908250521
2020-11-27,27,11,2020,2404,118,Belgium,BE,BEL,11455519,Europe,413.8354622,0.000209855,-292,-6,Social Distancing and Wearing Masks Enforced,4.837023681
2020-11-26,26,11,2020,2670,137,Belgium,BE,BEL,11455519,Europe,408.0216706,0.000233075,266,19,Social Distancing and Wearing Masks Enforced,4.902229338
2020-11-25,25,11,2020,2864,119,Belgium,BE,BEL,11455519,Europe,450.2458597,0.00025001,194,-18,Social Distancing and Wearing Masks Enforced,4.945810253
2020-11-24,24,11,2020,3953,139,Belgium,BE,BEL,11455519,Europe,491.1257185,0.000345074,1089,20,Social Distancing and Wearing Masks Enforced,5.146038874
2020-11-23,23,11,2020,589,135,Belgium,BE,BEL,11455519,Europe,498.6242876,5.14E-05,-3364,-4,Social Distancing and Wearing Masks Enforced,3.963139015
2020-11-22,22,11,2020,1263,137,Belgium,BE,BEL,11455519,Europe,514.1888377,0.000110253,674,2,Social Distancing and Wearing Masks Enforced,4.437105071
2020-11-21,21,11,2020,3081,165,Belgium,BE,BEL,11455519,Europe,545.3266674,0.000268953,1818,28,Social Distancing and Wearing Masks Enforced,4.991189431
2020-11-20,20,11,2020,3019,172,Belgium,BE,BEL,11455519,Europe,585.8311614,0.000263541,-62,7,Social Distancing and Wearing Masks Enforced,4.978558581
2020-11-19,19,11,2020,3700,158,Belgium,BE,BEL,11455519,Europe,634.1048363,0.000322988,681,-14,Social Distancing and Wearing Masks Enforced,5.104942561
2020-11-18,18,11,2020,4828,153,Belgium,BE,BEL,11455519,Europe,697.6026141,0.000421456,1128,-5,Social Distancing and Wearing Masks Enforced,5.270279466
2020-11-17,17,11,2020,5821,195,Belgium,BE,BEL,11455519,Europe,767.7609369,0.000508139,993,42,Social Distancing and Wearing Masks Enforced,5.386493806
2020-11-16,16,11,2020,1057,192,Belgium,BE,BEL,11455519,Europe,781.8065685,9.23E-05,-4764,-3,Social Distancing and Wearing Masks Enforced,4.326473194
2020-11-15,15,11,2020,2371,175,Belgium,BE,BEL,11455519,Europe,816.1742825,0.000206974,1314,-17,Social Distancing and Wearing Masks Enforced,4.828435459
2020-11-14,14,11,2020,5709,183,Belgium,BE,BEL,11455519,Europe,900.7797901,0.000498362,3338,8,Social Distancing and Wearing Masks Enforced,5.374422393
2020-11-13,13,11,2020,6482,173,Belgium,BE,BEL,11455519,Europe,975.9226099,0.000565841,773,-10,Social Distancing and Wearing Masks Enforced,5.453322751
2020-11-12,12,11,2020,2004,196,Belgium,BE,BEL,11455519,Europe,1115.540902,0.000174938,-4478,23,Social Distancing and Wearing Masks Enforced,4.723947661
2020-11-11,11,11,2020,7701,217,Belgium,BE,BEL,11455519,Europe,1242.196011,0.000672252,5697,21,Social Distancing and Wearing Masks Enforced,5.560391861
2020-11-10,10,11,2020,8636,194,Belgium,BE,BEL,11455519,Europe,1340.24482,0.000753872,935,-23,Social Distancing and Wearing Masks Enforced,5.63159021
2020-11-09,9,11,2020,1448,210,Belgium,BE,BEL,11455519,Europe,1370.33512,0.000126402,-7188,16,Social Distancing and Wearing Masks Enforced,4.522037487
2020-11-08,8,11,2020,3046,208,Belgium,BE,BEL,11455519,Europe,1444.631186,0.000265898,1598,-2,Social Distancing and Wearing Masks Enforced,4.984090701
2020-11-07,7,11,2020,6648,214,Belgium,BE,BEL,11455519,Europe,1551.374495,0.000580332,3602,6,Social Distancing and Wearing Masks Enforced,5.469034418
2020-11-06,6,11,2020,7659,206,Belgium,BE,BEL,11455519,Europe,1638.913086,0.000668586,1011,-8,Social Distancing and Wearing Masks Enforced,5.556993927
2020-11-05,5,11,2020,9230,198,Belgium,BE,BEL,11455519,Europe,1710.974422,0.000805725,1571,-8,Social Distancing and Wearing Masks Enforced,5.672921122
2020-11-04,4,11,2020,12102,173,Belgium,BE,BEL,11455519,Europe,1773.503235,0.001056434,2872,-25,Social Distancing and Wearing Masks Enforced,5.841248012
2020-11-03,3,11,2020,13858,208,Belgium,BE,BEL,11455519,Europe,1788.360702,0.001209723,1756,35,Social Distancing and Wearing Masks Enforced,5.925433897
2020-11-02,2,11,2020,2666,164,Belgium,BE,BEL,11455519,Europe,1802.528545,0.000232726,-11192,-44,Social Distancing and Wearing Masks Enforced,4.901297801
2020-11-01,1,11,2020,6308,177,Belgium,BE,BEL,11455519,Europe,1817.255072,0.000550652,3642,13,Social Distancing and Wearing Masks Enforced,5.436415956
2020-10-31,31,10,2020,15401,185,Belgium,BE,BEL,11455519,Europe,1800.459674,0.001344417,9093,8,Social Distancing and Wearing Masks Enforced,5.991028077
2020-10-30,30,10,2020,15090,139,Belgium,BE,BEL,11455519,Europe,1771.897022,0.001317269,-311,-46,Social Distancing and Wearing Masks Enforced,5.978352739
2020-10-29,29,10,2020,17998,142,Belgium,BE,BEL,11455519,Europe,1722.095699,0.00157112,2908,3,Social Distancing and Wearing Masks Enforced,6.08784958
2020-10-28,28,10,2020,22210,132,Belgium,BE,BEL,11455519,Europe,1638.005227,0.001938803,4212,-10,Social Distancing and Wearing Masks Enforced,6.218505131
2020-10-27,27,10,2020,19868,121,Belgium,BE,BEL,11455519,Europe,1549.550047,0.001734361,-2342,-11,Social Distancing and Wearing Masks Enforced,6.149268387
2020-10-26,26,10,2020,4895,94,Belgium,BE,BEL,11455519,Europe,1527.79634,0.000427305,-14973,-27,Social Distancing and Wearing Masks Enforced,5.278842687
2020-10-25,25,10,2020,11557,93,Belgium,BE,BEL,11455519,Europe,1464.534256,0.001008859,6662,-1,Social Distancing and Wearing Masks Enforced,5.812617263
2020-10-24,24,10,2020,18876,94,Belgium,BE,BEL,11455519,Europe,1367.751212,0.001647765,7319,1,Social Distancing and Wearing Masks Enforced,6.117444157
2020-10-23,23,10,2020,17687,55,Belgium,BE,BEL,11455519,Europe,1270.863415,0.001543972,-1189,-39,Social Distancing and Wearing Masks Enforced,6.077019256
2020-10-22,22,10,2020,17485,62,Belgium,BE,BEL,11455519,Europe,1177.615785,0.001526339,-202,7,Social Distancing and Wearing Masks Enforced,6.06988227
2020-10-21,21,10,2020,19265,52,Belgium,BE,BEL,11455519,Europe,1059.087764,0.001681722,1780,-10,Social Distancing and Wearing Masks Enforced,6.130118584
2020-10-20,20,10,2020,15560,52,Belgium,BE,BEL,11455519,Europe,969.0787471,0.001358297,-3705,0,Social Distancing and Wearing Masks Enforced,5.997409855
2020-10-19,19,10,2020,4289,31,Belgium,BE,BEL,11455519,Europe,940.6732248,0.000374405,-11271,-21,Social Distancing and Wearing Masks Enforced,5.196726646
2020-10-18,18,10,2020,7995,23,Belgium,BE,BEL,11455519,Europe,885.8001109,0.000697917,3706,-8,Social Distancing and Wearing Masks Enforced,5.583670893
2020-10-17,17,10,2020,13477,36,Belgium,BE,BEL,11455519,Europe,800.6359206,0.001176464,5482,13,Social Distancing and Wearing Masks Enforced,5.908112226
2020-10-16,16,10,2020,11818,35,Belgium,BE,BEL,11455519,Europe,727.2389841,0.001031642,-1659,-1,Social Distancing and Wearing Masks Enforced,5.826493212
2020-10-15,15,10,2020,12293,41,Belgium,BE,BEL,11455519,Europe,648.2377621,0.001073107,475,6,Social Distancing and Wearing Masks Enforced,5.850977662
2020-10-14,14,10,2020,12577,34,Belgium,BE,BEL,11455519,Europe,564.4964667,0.001097899,284,-7,Social Distancing and Wearing Masks Enforced,5.865168799
2020-10-13,13,10,2020,9735,36,Belgium,BE,BEL,11455519,Europe,503.8008317,0.000849809,-2842,2,Social Distancing and Wearing Masks Enforced,5.706018758
2020-10-12,12,10,2020,2403,26,Belgium,BE,BEL,11455519,Europe,487.5379282,0.000209768,-7332,-10,Social Distancing and Wearing Masks Enforced,4.836765169
2020-10-11,11,10,2020,4310,22,Belgium,BE,BEL,11455519,Europe,458.1547113,0.000376238,1907,-4,Social Distancing and Wearing Masks Enforced,5.199761431
2020-10-10,10,10,2020,7789,19,Belgium,BE,BEL,11455519,Europe,404.3291273,0.000679934,3479,-3,Social Distancing and Wearing Masks Enforced,5.56745165
2020-10-09,9,10,2020,6588,20,Belgium,BE,BEL,11455519,Europe,362.497762,0.000575094,-1201,1,Social Distancing and Wearing Masks Enforced,5.463401243
2020-10-08,8,10,2020,6803,20,Belgium,BE,BEL,11455519,Europe,321.4171265,0.000593862,215,0,Social Distancing and Wearing Masks Enforced,5.483354718
2020-10-07,7,10,2020,5687,18,Belgium,BE,BEL,11455519,Europe,289.8777436,0.000496442,-1116,-2,Social Distancing and Wearing Masks Enforced,5.372023413
2020-10-06,6,10,2020,5249,14,Belgium,BE,BEL,11455519,Europe,263.2966695,0.000458207,-438,-4,Social Distancing and Wearing Masks Enforced,5.322226347
2020-10-05,5,10,2020,1035,14,Belgium,BE,BEL,11455519,Europe,258.2859843,9.03E-05,-4214,0,Social Distancing and Wearing Masks Enforced,4.313404482
2020-10-04,4,10,2020,1709,15,Belgium,BE,BEL,11455519,Europe,251.1715096,0.000149186,674,1,Social Distancing and Wearing Masks Enforced,4.625008287
2020-10-03,3,10,2020,3721,11,Belgium,BE,BEL,11455519,Europe,233.607923,0.000324822,2012,-4,Social Distancing and Wearing Masks Enforced,5.108459087
2020-10-02,2,10,2020,3410,15,Belgium,BE,BEL,11455519,Europe,219.1345499,0.000297673,-311,4,Social Distancing and Wearing Masks Enforced,5.054228875
2020-10-01,1,10,2020,3243,6,Belgium,BE,BEL,11455519,Europe,207.7775787,0.000283095,-167,-9,Social Distancing and Wearing Masks Enforced,5.023029496
2020-09-30,30,9,2020,2984,10,Belgium,BE,BEL,11455519,Europe,195.9404895,0.000260486,-259,4,Social Distancing and Wearing Masks Enforced,4.971313214
2020-09-29,29,9,2020,2782,13,Belgium,BE,BEL,11455519,Europe,186.7309548,0.000242852,-202,3,Social Distancing and Wearing Masks Enforced,4.927760997
2020-09-28,28,9,2020,540,12,Belgium,BE,BEL,11455519,Europe,184.6446241,4.71E-05,-2242,-1,Social Distancing and Wearing Masks Enforced,3.9091717
2020-09-27,27,9,2020,944,6,Belgium,BE,BEL,11455519,Europe,181.7901048,8.24E-05,404,-6,Social Distancing and Wearing Masks Enforced,4.256222693
2020-09-26,26,9,2020,1623,5,Belgium,BE,BEL,11455519,Europe,178.8308325,0.000141678,679,-1,Social Distancing and Wearing Masks Enforced,4.59292745
2020-09-25,25,9,2020,1796,4,Belgium,BE,BEL,11455519,Europe,173.1305234,0.00015678,173,-1,Social Distancing and Wearing Masks Enforced,4.655859782
2020-09-24,24,9,2020,2097,8,Belgium,BE,BEL,11455519,Europe,163.7638592,0.000183056,301,4,Social Distancing and Wearing Masks Enforced,4.75213301
2020-09-23,23,9,2020,2074,1,Belgium,BE,BEL,11455519,Europe,153.2623707,0.000181048,-23,-7,Social Distancing and Wearing Masks Enforced,4.745280529
2020-09-22,22,9,2020,2204,3,Belgium,BE,BEL,11455519,Europe,142.0363407,0.000192396,130,2,Social Distancing and Wearing Masks Enforced,4.783054451
2020-09-21,21,9,2020,461,3,Belgium,BE,BEL,11455519,Europe,139.3651392,4.02E-05,-1743,0,Social Distancing and Wearing Masks Enforced,3.810894472
2020-09-20,20,9,2020,894,8,Belgium,BE,BEL,11455519,Europe,134.3719128,7.80E-05,433,5,Social Distancing and Wearing Masks Enforced,4.222409403
2020-09-19,19,9,2020,1709,6,Belgium,BE,BEL,11455519,Europe,125.8083549,0.000149186,815,-2,Social Distancing and Wearing Masks Enforced,4.625008287
2020-09-18,18,9,2020,1752,1,Belgium,BE,BEL,11455519,Europe,116.4242319,0.000152939,43,-5,Social Distancing and Wearing Masks Enforced,4.640448205
2020-09-17,17,9,2020,1942,2,Belgium,BE,BEL,11455519,Europe,104.4823897,0.000169525,190,1,Social Distancing and Wearing Masks Enforced,4.704421084
2020-09-16,16,9,2020,1628,3,Belgium,BE,BEL,11455519,Europe,95.20301961,0.000142115,-314,1,Social Distancing and Wearing Masks Enforced,4.594838664
2020-09-15,15,9,2020,1727,4,Belgium,BE,BEL,11455519,Europe,85.66176705,0.000150757,99,1,Social Distancing and Wearing Masks Enforced,4.631518259
2020-09-14,14,9,2020,301,1,Belgium,BE,BEL,11455519,Europe,84.05555436,2.63E-05,-1426,-3,Social Distancing and Wearing Masks Enforced,3.546026983
2020-09-13,13,9,2020,617,1,Belgium,BE,BEL,11455519,Europe,80.37174047,5.39E-05,316,0,Social Distancing and Wearing Masks Enforced,3.991995575
2020-09-12,12,9,2020,1284,5,Belgium,BE,BEL,11455519,Europe,74.52303121,0.000112086,667,4,Social Distancing and Wearing Masks Enforced,4.447351109
2020-09-11,11,9,2020,1143,3,Belgium,BE,BEL,11455519,Europe,69.2155458,9.98E-05,-141,-2,Social Distancing and Wearing Masks Enforced,4.375075055
2020-09-10,10,9,2020,1024,2,Belgium,BE,BEL,11455519,Europe,64.86829623,8.94E-05,-119,-1,Social Distancing and Wearing Masks Enforced,4.306765581
2020-09-09,9,9,2020,871,3,Belgium,BE,BEL,11455519,Europe,61.86537685,7.60E-05,-153,1,Social Distancing and Wearing Masks Enforced,4.206215055
2020-09-08,8,9,2020,918,4,Belgium,BE,BEL,11455519,Europe,59.15052823,8.01E-05,47,1,Social Distancing and Wearing Masks Enforced,4.238869569
2020-09-07,7,9,2020,155,2,Belgium,BE,BEL,11455519,Europe,58.80135156,1.35E-05,-763,-2,Social Distancing and Wearing Masks Enforced,3.133656215
2020-09-06,6,9,2020,322,1,Belgium,BE,BEL,11455519,Europe,57.76255096,2.81E-05,167,-1,Social Distancing and Wearing Masks Enforced,3.587930607
2020-09-05,5,9,2020,728,2,Belgium,BE,BEL,11455519,Europe,55.8595381,6.36E-05,406,1,Social Distancing and Wearing Masks Enforced,4.094784271
2020-09-04,4,9,2020,677,4,Belgium,BE,BEL,11455519,Europe,55.02151408,5.91E-05,-51,2,Social Distancing and Wearing Masks Enforced,4.049656854
2020-09-03,3,9,2020,574,2,Belgium,BE,BEL,11455519,Europe,55.35323192,5.01E-05,-103,-2,Social Distancing and Wearing Masks Enforced,3.94711057
2020-09-02,2,9,2020,565,3,Belgium,BE,BEL,11455519,Europe,56.74993861,4.93E-05,-9,1,Social Distancing and Wearing Masks Enforced,3.937291201
2020-09-01,1,9,2020,634,3,Belgium,BE,BEL,11455519,Europe,57.38718604,5.53E-05,69,0,Social Distancing and Wearing Masks Enforced,4.008883415
2020-08-31,31,8,2020,117,1,Belgium,BE,BEL,11455519,Europe,57.51812729,1.02E-05,-517,-2,Social Distancing and Wearing Masks Enforced,2.95890503
2020-08-30,30,8,2020,195,6,Belgium,BE,BEL,11455519,Europe,57.23878595,1.70E-05,78,5,Social Distancing and Wearing Masks Enforced,3.276298836
2020-08-29,29,8,2020,614,4,Belgium,BE,BEL,11455519,Europe,57.0030917,5.36E-05,419,-2,Social Distancing and Wearing Masks Enforced,3.988967129
2020-08-28,28,8,2020,535,3,Belgium,BE,BEL,11455519,Europe,58.17283355,4.67E-05,-79,-1,Social Distancing and Wearing Masks Enforced,3.903391798
2020-08-27,27,8,2020,526,4,Belgium,BE,BEL,11455519,Europe,58.89737514,4.59E-05,-9,1,Social Distancing and Wearing Masks Enforced,3.892850519
2020-08-26,26,8,2020,527,5,Belgium,BE,BEL,11455519,Europe,60.56469375,4.60E-05,1,1,Social Distancing and Wearing Masks Enforced,3.894030643
2020-08-25,25,8,2020,607,5,Belgium,BE,BEL,11455519,Europe,62.88671862,5.30E-05,80,0,Social Distancing and Wearing Masks Enforced,3.981842817
2020-08-24,24,8,2020,115,3,Belgium,BE,BEL,11455519,Europe,62.94782454,1.00E-05,-492,-2,Social Distancing and Wearing Masks Enforced,2.948192093
2020-08-23,23,8,2020,203,5,Belgium,BE,BEL,11455519,Europe,63.82949563,1.77E-05,88,2,Social Distancing and Wearing Masks Enforced,3.301280489
2020-08-22,22,8,2020,510,3,Belgium,BE,BEL,11455519,Europe,66.10787342,4.45E-05,307,-2,Social Distancing and Wearing Masks Enforced,3.87365718
2020-08-21,21,8,2020,581,4,Belgium,BE,BEL,11455519,Europe,67.74900378,5.07E-05,71,1,Social Distancing and Wearing Masks Enforced,3.954641995
2020-08-20,20,8,2020,612,9,Belgium,BE,BEL,11455519,Europe,69.18062813,5.34E-05,31,5,Social Distancing and Wearing Masks Enforced,3.986939933
2020-08-19,19,8,2020,725,11,Belgium,BE,BEL,11455519,Europe,69.95754623,6.33E-05,113,2,Social Distancing and Wearing Masks Enforced,4.092218534
2020-08-18,18,8,2020,707,7,Belgium,BE,BEL,11455519,Europe,70.71700549,6.17E-05,-18,-4,Social Distancing and Wearing Masks Enforced,4.076597559
2020-08-17,17,8,2020,132,7,Belgium,BE,BEL,11455519,Europe,70.85667616,1.15E-05,-575,0,Social Distancing and Wearing Masks Enforced,3.033855413
2020-08-16,16,8,2020,163,9,Belgium,BE,BEL,11455519,Europe,72.13117101,1.42E-05,31,2,Social Distancing and Wearing Masks Enforced,3.164924948
2020-08-15,15,8,2020,587,12,Belgium,BE,BEL,11455519,Europe,72.97792444,5.12E-05,424,3,Social Distancing and Wearing Masks Enforced,3.961025629
2020-08-14,14,8,2020,669,12,Belgium,BE,BEL,11455519,Europe,72.68112427,5.84E-05,82,0,Social Distancing and Wearing Masks Enforced,4.042270913
2020-08-13,13,8,2020,609,11,Belgium,BE,BEL,11455519,Europe,73.50168945,5.32E-05,-60,-1,Social Distancing and Wearing Masks Enforced,3.983886684
2020-08-12,12,8,2020,718,13,Belgium,BE,BEL,11455519,Europe,73.21361869,6.27E-05,109,2,Social Distancing and Wearing Masks Enforced,4.086190289
2020-08-11,11,8,2020,873,11,Belgium,BE,BEL,11455519,Europe,70.78684082,7.62E-05,155,-2,Social Distancing and Wearing Masks Enforced,4.207640135
2020-08-10,10,8,2020,122,5,Belgium,BE,BEL,11455519,Europe,71.32806466,1.06E-05,-751,-6,Social Distancing and Wearing Masks Enforced,2.984906101
2020-08-09,9,8,2020,304,2,Belgium,BE,BEL,11455519,Europe,70.6733584,2.65E-05,182,-3,Social Distancing and Wearing Masks Enforced,3.552189033
2020-08-08,8,8,2020,771,6,Belgium,BE,BEL,11455519,Europe,68.27276879,6.73E-05,467,4,Social Distancing and Wearing Masks Enforced,4.130441021
2020-08-07,7,8,2020,769,4,Belgium,BE,BEL,11455519,Europe,65.39206124,6.71E-05,-2,-2,Social Distancing and Wearing Masks Enforced,4.128827163
2020-08-06,6,8,2020,776,5,Belgium,BE,BEL,11455519,Europe,63.4454013,6.77E-05,7,1,Social Distancing and Wearing Masks Enforced,4.134457421
2020-08-05,5,8,2020,814,5,Belgium,BE,BEL,11455519,Europe,57.60542146,7.11E-05,38,0,Social Distancing and Wearing Masks Enforced,4.164162105
2020-08-04,4,8,2020,794,3,Belgium,BE,BEL,11455519,Europe,54.54139616,6.93E-05,-20,-2,Social Distancing and Wearing Masks Enforced,4.148705215
2020-08-03,3,8,2020,148,5,Belgium,BE,BEL,11455519,Europe,53.80812515,1.29E-05,-646,2,Social Distancing and Wearing Masks Enforced,3.104942561
2020-08-02,2,8,2020,309,2,Belgium,BE,BEL,11455519,Europe,52.24555954,2.70E-05,161,-3,Social Distancing and Wearing Masks Enforced,3.562325227
2020-08-01,1,8,2020,684,3,Belgium,BE,BEL,11455519,Europe,48.66649865,5.97E-05,375,1,Social Distancing and Wearing Masks Enforced,4.056048306
2020-07-31,31,7,2020,635,2,Belgium,BE,BEL,11455519,Europe,45.09616718,5.54E-05,-49,-1,Social Distancing and Wearing Masks Enforced,4.009862666
2020-07-30,30,7,2020,703,3,Belgium,BE,BEL,11455519,Europe,41.22903554,6.14E-05,68,1,Social Distancing and Wearing Masks Enforced,4.073072245
2020-07-29,29,7,2020,685,1,Belgium,BE,BEL,11455519,Europe,37.05637431,5.98E-05,-18,-2,Social Distancing and Wearing Masks Enforced,4.056956027
2020-07-28,28,7,2020,595,4,Belgium,BE,BEL,11455519,Europe,33.81776068,5.19E-05,-90,3,Social Distancing and Wearing Masks Enforced,3.969436383
2020-07-27,27,7,2020,184,2,Belgium,BE,BEL,11455519,Europe,32.58691291,1.61E-05,-411,-2,Social Distancing and Wearing Masks Enforced,3.240221768
2020-07-26,26,7,2020,229,1,Belgium,BE,BEL,11455519,Europe,31.12910031,2.00E-05,45,-1,Social Distancing and Wearing Masks Enforced,3.376161305
2020-07-25,25,7,2020,496,5,Belgium,BE,BEL,11455519,Europe,27.90794551,4.33E-05,267,4,Social Distancing and Wearing Masks Enforced,3.856362447
2020-07-24,24,7,2020,439,2,Belgium,BE,BEL,11455519,Europe,25.15817921,3.83E-05,-57,-3,Social Distancing and Wearing Masks Enforced,3.780512045
2020-07-23,23,7,2020,553,2,Belgium,BE,BEL,11455519,Europe,21.52674183,4.83E-05,114,0,Social Distancing and Wearing Masks Enforced,3.923952551
2020-07-22,22,7,2020,145,1,Belgium,BE,BEL,11455519,Europe,21.12518865,1.27E-05,-408,-1,Social Distancing and Wearing Masks Enforced,3.092218534
2020-07-21,21,7,2020,443,2,Belgium,BE,BEL,11455519,Europe,18.23575169,3.87E-05,298,1,Social Distancing and Wearing Masks Enforced,3.786147774
2020-07-20,20,7,2020,64,1,Belgium,BE,BEL,11455519,Europe,17.88657502,5.59E-06,-379,-1,Social Distancing and Wearing Masks Enforced,2.584059348
2020-07-19,19,7,2020,130,3,Belgium,BE,BEL,11455519,Europe,17.31043351,1.13E-05,66,2,Social Distancing and Wearing Masks Enforced,3.024369199
2020-07-18,18,7,2020,274,2,Belgium,BE,BEL,11455519,Europe,15.73913849,2.39E-05,144,-1,Social Distancing and Wearing Masks Enforced,3.487632585
2020-07-17,17,7,2020,226,5,Belgium,BE,BEL,11455519,Europe,14.57812605,1.97E-05,-48,3,Social Distancing and Wearing Masks Enforced,3.367967759
2020-07-16,16,7,2020,260,5,Belgium,BE,BEL,11455519,Europe,13.48694895,2.27E-05,34,0,Social Distancing and Wearing Masks Enforced,3.455045757
2020-07-15,15,7,2020,207,3,Belgium,BE,BEL,11455519,Europe,12.55290136,1.81E-05,-53,-2,Social Distancing and Wearing Masks Enforced,3.313404482
2020-07-14,14,7,2020,224,0,Belgium,BE,BEL,11455519,Europe,11.70614793,1.96E-05,17,-3,Social Distancing and Wearing Masks Enforced,3.362444745
2020-07-13,13,7,2020,43,4,Belgium,BE,BEL,11455519,Europe,11.54028901,3.75E-06,-181,4,Social Distancing and Wearing Masks Enforced,2.336965028
2020-07-12,12,7,2020,62,2,Belgium,BE,BEL,11455519,Europe,11.35697126,5.41E-06,19,-2,Social Distancing and Wearing Masks Enforced,2.564332773
2020-07-11,11,7,2020,127,0,Belgium,BE,BEL,11455519,Europe,11.23475942,1.11E-05,65,-2,Social Distancing and Wearing Masks Enforced,3.009862666
2020-07-10,10,7,2020,124,2,Belgium,BE,BEL,11455519,Europe,10.81574741,1.08E-05,-3,2,Social Distancing and Wearing Masks Enforced,2.995009331
2020-07-09,9,7,2020,137,1,Belgium,BE,BEL,11455519,Europe,10.49275899,1.20E-05,13,-1,Social Distancing and Wearing Masks Enforced,3.056956027
2020-07-08,8,7,2020,99,3,Belgium,BE,BEL,11455519,Europe,10.58878258,8.64E-06,-38,2,Social Distancing and Wearing Masks Enforced,2.855108491
2020-07-07,7,7,2020,112,1,Belgium,BE,BEL,11455519,Europe,10.8593945,9.78E-06,13,-2,Social Distancing and Wearing Masks Enforced,2.931768187
2020-07-06,6,7,2020,24,2,Belgium,BE,BEL,11455519,Europe,10.82447683,2.10E-06,-88,1,Social Distancing and Wearing Masks Enforced,1.974635869
2020-07-05,5,7,2020,64,3,Belgium,BE,BEL,11455519,Europe,10.702265,5.59E-06,40,1,Social Distancing and Wearing Masks Enforced,2.584059348
2020-07-04,4,7,2020,94,2,Belgium,BE,BEL,11455519,Europe,10.93795925,8.21E-06,30,-1,Social Distancing and Wearing Masks Enforced,2.822907766
2020-07-03,3,7,2020,93,5,Belgium,BE,BEL,11455519,Europe,11.0689005,8.12E-06,-1,3,Social Distancing and Wearing Masks Enforced,2.816262409
2020-07-02,2,7,2020,135,2,Belgium,BE,BEL,11455519,Europe,10.9641475,1.18E-05,42,-3,Social Distancing and Wearing Masks Enforced,3.047818583
2020-07-01,1,7,2020,100,8,Belgium,BE,BEL,11455519,Europe,10.95541808,8.73E-06,-35,6,Social Distancing and Wearing Masks Enforced,2.861353116
2020-06-30,30,6,2020,127,3,Belgium,BE,BEL,11455519,Europe,11.13000642,1.11E-05,27,-5,Social Distancing and Wearing Masks Enforced,3.009862666
2020-06-29,29,6,2020,24,5,Belgium,BE,BEL,11455519,Europe,11.11254759,2.10E-06,-103,2,Social Distancing and Wearing Masks Enforced,1.974635869
2020-06-28,28,6,2020,41,8,Belgium,BE,BEL,11455519,Europe,11.18238292,3.58E-06,17,3,Social Distancing and Wearing Masks Enforced,2.307372057
2020-06-27,27,6,2020,113,2,Belgium,BE,BEL,11455519,Europe,10.97287692,9.86E-06,72,-6,Social Distancing and Wearing Masks Enforced,2.937291201
2020-06-26,26,6,2020,76,5,Belgium,BE,BEL,11455519,Europe,11.13873584,6.63E-06,-37,3,Social Distancing and Wearing Masks Enforced,2.690835917
2020-06-25,25,6,2020,100,3,Belgium,BE,BEL,11455519,Europe,11.30459475,8.73E-06,24,-2,Social Distancing and Wearing Masks Enforced,2.861353116
2020-06-24,24,6,2020,110,4,Belgium,BE,BEL,11455519,Europe,11.61012434,9.60E-06,10,1,Social Distancing and Wearing Masks Enforced,2.92057266
2020-06-23,23,6,2020,143,12,Belgium,BE,BEL,11455519,Europe,11.69741851,1.25E-05,33,8,Social Distancing and Wearing Masks Enforced,3.083588744
2020-06-22,22,6,2020,20,9,Belgium,BE,BEL,11455519,Europe,11.98548927,1.75E-06,-123,-3,Social Distancing and Wearing Masks Enforced,1.861353116
2020-06-21,21,6,2020,50,3,Belgium,BE,BEL,11455519,Europe,12.15134818,4.36E-06,30,-6,Social Distancing and Wearing Masks Enforced,2.430676558
2020-06-20,20,6,2020,121,4,Belgium,BE,BEL,11455519,Europe,12.43941894,1.06E-05,71,1,Social Distancing and Wearing Masks Enforced,2.979792205
2020-06-19,19,6,2020,108,5,Belgium,BE,BEL,11455519,Europe,12.99810161,9.43E-06,-13,1,Social Distancing and Wearing Masks Enforced,2.9091717
2020-06-18,18,6,2020,123,7,Belgium,BE,BEL,11455519,Europe,13.31236062,1.07E-05,15,2,Social Distancing and Wearing Masks Enforced,2.989978252
2020-06-17,17,6,2020,99,7,Belgium,BE,BEL,11455519,Europe,14.04563163,8.64E-06,-24,0,Social Distancing and Wearing Masks Enforced,2.855108491
2020-06-16,16,6,2020,147,8,Belgium,BE,BEL,11455519,Europe,13.27744295,1.28E-05,48,1,Social Distancing and Wearing Masks Enforced,3.100730105
2020-06-15,15,6,2020,22,3,Belgium,BE,BEL,11455519,Europe,13.5131372,1.92E-06,-125,-5,Social Distancing and Wearing Masks Enforced,1.92057266
2020-06-14,14,6,2020,49,5,Belgium,BE,BEL,11455519,Europe,13.61789021,4.28E-06,27,2,Social Distancing and Wearing Masks Enforced,2.41812391
2020-06-13,13,6,2020,89,10,Belgium,BE,BEL,11455519,Europe,14.28132588,7.77E-06,40,5,Social Distancing and Wearing Masks Enforced,2.788946585
2020-06-12,12,6,2020,95,7,Belgium,BE,BEL,11455519,Europe,14.94476156,8.29E-06,6,-3,Social Distancing and Wearing Masks Enforced,2.8294828
2020-06-11,11,6,2020,119,12,Belgium,BE,BEL,11455519,Europe,15.49471482,1.04E-05,24,5,Social Distancing and Wearing Masks Enforced,2.969436383
2020-06-10,10,6,2020,145,12,Belgium,BE,BEL,11455519,Europe,15.99229158,1.27E-05,26,0,Social Distancing and Wearing Masks Enforced,3.092218534
2020-06-09,9,6,2020,153,9,Belgium,BE,BEL,11455519,Europe,17.39772768,1.34E-05,8,-3,Social Distancing and Wearing Masks Enforced,3.125586817
2020-06-08,8,6,2020,53,12,Belgium,BE,BEL,11455519,Europe,17.58977485,4.63E-06,-100,3,Lockdown,2.466881066
2020-06-07,7,6,2020,69,11,Belgium,BE,BEL,11455519,Europe,18.06116336,6.02E-06,16,-1,Lockdown,2.630798288
2020-06-06,6,6,2020,154,12,Belgium,BE,BEL,11455519,Europe,18.88172854,1.34E-05,85,1,Lockdown,3.129634616
2020-06-05,5,6,2020,172,14,Belgium,BE,BEL,11455519,Europe,17.99132802,1.50E-05,18,2,Lockdown,3.198318144
2020-06-04,4,6,2020,159,20,Belgium,BE,BEL,11455519,Europe,19.96417622,1.39E-05,-13,6,Lockdown,3.149487261
2020-06-03,3,6,2020,183,23,Belgium,BE,BEL,11455519,Europe,20.91568265,1.60E-05,24,3,Lockdown,3.236835738
2020-06-02,2,6,2020,59,21,Belgium,BE,BEL,11455519,Europe,23.16787218,5.15E-06,-124,-2,Lockdown,2.533516461
2020-06-01,1,6,2020,49,22,Belgium,BE,BEL,11455519,Europe,23.44721352,4.28E-06,-10,1,Lockdown,2.41812391
2020-05-31,31,5,2020,61,23,Belgium,BE,BEL,11455519,Europe,24.19794337,5.32E-06,12,1,Lockdown,2.554229543
2020-05-30,30,5,2020,165,16,Belgium,BE,BEL,11455519,Europe,25.78669722,1.44E-05,104,-7,Lockdown,3.172502297
2020-05-29,29,5,2020,171,26,Belgium,BE,BEL,11455519,Europe,26.95643908,1.49E-05,6,10,Lockdown,3.194695189
2020-05-28,28,5,2020,182,24,Belgium,BE,BEL,11455519,Europe,28.16982801,1.59E-05,11,-2,Lockdown,3.233431154
2020-05-27,27,5,2020,202,24,Belgium,BE,BEL,11455519,Europe,29.85460545,1.76E-05,20,0,Lockdown,3.298212162
2020-05-26,26,5,2020,314,26,Belgium,BE,BEL,11455519,Europe,31.26877097,2.74E-05,112,2,Lockdown,3.572298715
2020-05-25,25,5,2020,75,33,Belgium,BE,BEL,11455519,Europe,31.6441359,6.55E-06,-239,7,Lockdown,2.682606194
2020-05-24,24,5,2020,123,25,Belgium,BE,BEL,11455519,Europe,32.66547766,1.07E-05,48,-8,Lockdown,2.989978252
2020-05-23,23,5,2020,248,41,Belgium,BE,BEL,11455519,Europe,34.71689061,2.16E-05,125,16,Lockdown,3.425685889
2020-05-22,22,5,2020,70,34,Belgium,BE,BEL,11455519,Europe,37.96423366,6.11E-06,-178,-7,Lockdown,2.639738513
2020-05-21,21,5,2020,385,30,Belgium,BE,BEL,11455519,Europe,39.42204626,3.36E-05,315,-4,Lockdown,3.698958058
2020-05-20,20,5,2020,292,33,Belgium,BE,BEL,11455519,Europe,41.64804755,2.55E-05,-93,3,Lockdown,3.527165452
2020-05-19,19,5,2020,317,37,Belgium,BE,BEL,11455519,Europe,44.72953168,2.77E-05,25,4,Lockdown,3.578206857
2020-05-18,18,5,2020,81,31,Belgium,BE,BEL,11455519,Europe,45.24456727,7.07E-06,-236,-6,Lockdown,2.730424778
2020-05-17,17,5,2020,147,30,Belgium,BE,BEL,11455519,Europe,46.4579562,1.28E-05,66,-1,Lockdown,3.100730105
2020-05-16,16,5,2020,347,45,Belgium,BE,BEL,11455519,Europe,45.49772036,3.03E-05,200,15,Lockdown,3.634389829
2020-05-15,15,5,2020,305,43,Belgium,BE,BEL,11455519,Europe,47.95068648,2.66E-05,-42,-2,Lockdown,3.554229543
2020-05-14,14,5,2020,321,56,Belgium,BE,BEL,11455519,Europe,49.70529925,2.80E-05,16,13,Lockdown,3.585997993
2020-05-13,13,5,2020,395,45,Belgium,BE,BEL,11455519,Europe,51.22421778,3.45E-05,74,-11,Lockdown,3.714890595
2020-05-12,12,5,2020,476,65,Belgium,BE,BEL,11455519,Europe,53.65972506,4.16E-05,81,20,Lockdown,3.830789499
2020-05-11,11,5,2020,118,72,Belgium,BE,BEL,11455519,Europe,54.41918433,1.03E-05,-358,7,Lockdown,2.964193019
2020-05-10,10,5,2020,240,71,Belgium,BE,BEL,11455519,Europe,55.71113801,2.10E-05,122,-1,Lockdown,3.405312427
2020-05-09,9,5,2020,483,74,Belgium,BE,BEL,11455519,Europe,58.57438672,4.22E-05,243,3,Lockdown,3.839860243
2020-05-08,8,5,2020,442,71,Belgium,BE,BEL,11455519,Europe,63.23589529,3.86E-05,-41,-3,Lockdown,3.784743627
2020-05-07,7,5,2020,552,76,Belgium,BE,BEL,11455519,Europe,65.20874349,4.82E-05,110,5,Lockdown,3.922827962
2020-05-06,6,5,2020,547,81,Belgium,BE,BEL,11455519,Europe,71.52011183,4.77E-05,-5,5,Lockdown,3.917174284
2020-05-05,5,5,2020,670,95,Belgium,BE,BEL,11455519,Europe,76.82759725,5.85E-05,123,14,Lockdown,4.043198972
2020-05-04,4,5,2020,140,94,Belgium,BE,BEL,11455519,Europe,79.48133996,1.22E-05,-530,-1,Lockdown,3.070415071
2020-05-03,3,5,2020,286,75,Belgium,BE,BEL,11455519,Europe,83.28736568,2.50E-05,146,-19,Lockdown,3.514265302
2020-05-02,2,5,2020,237,93,Belgium,BE,BEL,11455519,Europe,93.39603033,2.07E-05,-49,18,Lockdown,3.39749679
2020-05-01,1,5,2020,586,87,Belgium,BE,BEL,11455519,Europe,102.9023652,5.12E-05,349,-6,Lockdown,3.959966234
2020-04-30,30,4,2020,522,107,Belgium,BE,BEL,11455519,Europe,112.6007473,4.56E-05,-64,20,Lockdown,3.888107481
2020-04-29,29,4,2020,569,110,Belgium,BE,BEL,11455519,Europe,121.2603288,4.97E-05,47,3,Lockdown,3.941674534
2020-04-28,28,4,2020,755,135,Belgium,BE,BEL,11455519,Europe,119.3660453,6.59E-05,186,25,Lockdown,4.117411239
2020-04-27,27,4,2020,205,154,Belgium,BE,BEL,11455519,Europe,122.1507293,1.79E-05,-550,19,Lockdown,3.307372057
2020-04-26,26,4,2020,388,142,Belgium,BE,BEL,11455519,Europe,127.7724737,3.39E-05,183,-12,Lockdown,3.703780863
2020-04-25,25,4,2020,811,155,Belgium,BE,BEL,11455519,Europe,141.0848343,7.08E-05,423,13,Lockdown,4.161867943
2020-04-24,24,4,2020,976,156,Belgium,BE,BEL,11455519,Europe,152.1188171,8.52E-05,165,1,Lockdown,4.276935776
2020-04-23,23,4,2020,778,181,Belgium,BE,BEL,11455519,Europe,159.2856683,6.79E-05,-198,25,Lockdown,4.136056739
2020-04-22,22,4,2020,1270,203,Belgium,BE,BEL,11455519,Europe,161.4243755,0.000110864,492,22,Lockdown,4.440539224
2020-04-21,21,4,2020,1278,206,Belgium,BE,BEL,11455519,Europe,167.1683317,0.000111562,8,3,Lockdown,4.444440869
2020-04-20,20,4,2020,444,190,Belgium,BE,BEL,11455519,Europe,169.1149917,3.88E-05,-834,-16,Lockdown,3.787548756
2020-04-19,19,4,2020,722,208,Belgium,BE,BEL,11455519,Europe,170.8696044,6.30E-05,278,18,Lockdown,4.089642159
2020-04-18,18,4,2020,1395,205,Belgium,BE,BEL,11455519,Europe,173.4797001,0.000121775,673,-3,Lockdown,4.498868604
2020-04-17,17,4,2020,1675,246,Belgium,BE,BEL,11455519,Europe,171.7600049,0.000146218,280,41,Lockdown,4.612522414
2020-04-16,16,4,2020,1633,280,Belgium,BE,BEL,11455519,Europe,170.7473926,0.000142551,-42,34,Lockdown,4.596744016
2020-04-15,15,4,2020,1561,261,Belgium,BE,BEL,11455519,Europe,171.803652,0.000136266,-72,-19,Lockdown,4.568726674
2020-04-14,14,4,2020,538,277,Belgium,BE,BEL,11455519,Europe,182.2876816,4.70E-05,-1023,16,Lockdown,3.906866187
2020-04-13,13,4,2020,524,265,Belgium,BE,BEL,11455519,Europe,183.6931177,4.57E-05,-14,-12,Lockdown,3.890483526
2020-04-12,12,4,2020,1032,284,Belgium,BE,BEL,11455519,Europe,182.0607168,9.01E-05,508,19,Lockdown,4.311600896
2020-04-11,11,4,2020,2336,302,Belgium,BE,BEL,11455519,Europe,174.9375127,0.000203919,1304,18,Lockdown,4.819195126
2020-04-10,10,4,2020,2240,272,Belgium,BE,BEL,11455519,Europe,167.2818141,0.000195539,-96,-30,Lockdown,4.793121304
2020-04-09,9,4,2020,1599,322,Belgium,BE,BEL,11455519,Europe,163.7900474,0.000139583,-641,50,Lockdown,4.583670893
2020-04-08,8,4,2020,1515,277,Belgium,BE,BEL,11455519,Europe,160.996634,0.000132251,-84,-45,Lockdown,4.550141799
2020-04-07,7,4,2020,1936,257,Belgium,BE,BEL,11455519,Europe,155.6891486,0.000169002,421,-20,Lockdown,4.702498437
2020-04-06,6,4,2020,667,247,Belgium,BE,BEL,11455519,Europe,154.1091242,5.82E-05,-1269,-10,Lockdown,4.040410628
2020-04-05,5,4,2020,923,271,Belgium,BE,BEL,11455519,Europe,150.1459689,8.06E-05,256,24,Lockdown,4.242244564
2020-04-04,4,4,2020,1694,236,Belgium,BE,BEL,11455519,Europe,141.1372108,0.000147876,771,-35,Lockdown,4.619530718
2020-04-03,3,4,2020,1478,219,Belgium,BE,BEL,11455519,Europe,134.459207,0.000129021,-216,-17,Lockdown,4.53477891
2020-04-02,2,4,2020,1517,233,Belgium,BE,BEL,11455519,Europe,125.8869197,0.000132425,39,14,Lockdown,4.550961502
2020-04-01,1,4,2020,1682,208,Belgium,BE,BEL,11455519,Europe,114.8878545,0.000146829,165,-25,Lockdown,4.615113626
2020-03-31,31,3,2020,1739,170,Belgium,BE,BEL,11455519,Europe,103.085683,0.000151805,57,-38,Lockdown,4.635820653
2020-03-30,30,3,2020,685,149,Belgium,BE,BEL,11455519,Europe,98.97412767,5.98E-05,-1054,-21,Lockdown,4.056956027
2020-03-29,29,3,2020,845,141,Belgium,BE,BEL,11455519,Europe,93.16033608,7.38E-05,160,-8,Lockdown,4.187385282
2020-03-28,28,3,2020,1520,128,Belgium,BE,BEL,11455519,Europe,82.84216542,0.000132687,675,-13,Lockdown,4.552189033
2020-03-27,27,3,2020,1363,102,Belgium,BE,BEL,11455519,Europe,73.12632453,0.000118982,-157,-26,Lockdown,4.484449742
2020-03-26,26,3,2020,1199,107,Belgium,BE,BEL,11455519,Europe,64.17867231,0.000104666,-164,5,Lockdown,4.404794432
2020-03-25,25,3,2020,1195,77,Belgium,BE,BEL,11455519,Europe,54.61123149,0.000104317,-4,-30,Lockdown,4.402718123
2020-03-24,24,3,2020,1328,78,Belgium,BE,BEL,11455519,Europe,43.83913116,0.000115927,133,1,Lockdown,4.468286272
2020-03-23,23,3,2020,486,47,Belgium,BE,BEL,11455519,Europe,40.15531728,4.24E-05,-842,-31,Lockdown,3.843707531
2020-03-22,22,3,2020,469,40,Belgium,BE,BEL,11455519,Europe,36.29691505,4.09E-05,-17,-7,Lockdown,3.821584369
2020-03-21,21,3,2020,662,35,Belgium,BE,BEL,11455519,Europe,31.47827698,5.78E-05,193,-5,Lockdown,4.035735399
2020-03-20,20,3,2020,713,33,Belgium,BE,BEL,11455519,Europe,25.96128556,6.22E-05,51,-2,Lockdown,4.081848308
2020-03-19,19,3,2020,535,22,Belgium,BE,BEL,11455519,Europe,21.75370666,4.67E-05,-178,-11,Lockdown,3.903391798
2020-03-18,18,3,2020,422,10,Belgium,BE,BEL,11455519,Europe,18.36669295,3.68E-05,-113,-12,Lockdown,3.755972981
2020-03-17,17,3,2020,387,12,Belgium,BE,BEL,11455519,Europe,15.15426756,3.38E-05,-35,2,Social Distancing and Wearing Masks Enforced,3.702177417
2020-03-16,16,3,2020,214,6,Belgium,BE,BEL,11455519,Europe,13.28617237,1.87E-05,-173,-6,Social Distancing and Wearing Masks Enforced,3.334068356
2020-03-15,15,3,2020,179,5,Belgium,BE,BEL,11455519,Europe,11.88073626,1.56E-05,-35,-1,Social Distancing and Wearing Masks Enforced,3.22310402
2020-03-14,14,3,2020,338,3,Belgium,BE,BEL,11455519,Europe,8.93019339,2.95E-05,159,-2,Social Distancing and Wearing Masks Enforced,3.61806184
2020-03-13,13,3,2020,250,1,Belgium,BE,BEL,11455519,Europe,6.74783919,2.18E-05,-88,-2,Social Distancing and Wearing Masks Enforced,3.430676558
2020-03-12,12,3,2020,174,3,Belgium,BE,BEL,11455519,Europe,5.22892066,1.52E-05,-76,2,Social Distancing and Wearing Masks Enforced,3.205501287
2020-03-11,11,3,2020,99,0,Belgium,BE,BEL,11455519,Europe,4.3647084,8.64E-06,-75,-3,Social Distancing and Wearing Masks Enforced,2.855108491
2020-03-10,10,3,2020,94,1,Belgium,BE,BEL,11455519,Europe,3.54414322,8.21E-06,-5,1,Social Distancing and Wearing Masks Enforced,2.822907766
2020-03-09,9,3,2020,64,0,Belgium,BE,BEL,11455519,Europe,2.98546055,5.59E-06,-30,-1,Social Distancing and Wearing Masks Enforced,2.584059348
2020-03-08,8,3,2020,27,0,Belgium,BE,BEL,11455519,Europe,2.74976629,2.36E-06,-37,0,Social Distancing and Wearing Masks Enforced,2.047818583
2020-03-07,7,3,2020,110,0,Belgium,BE,BEL,11455519,Europe,1.78953044,9.60E-06,83,0,Social Distancing and Wearing Masks Enforced,2.92057266
2020-03-06,6,3,2020,81,0,Belgium,BE,BEL,11455519,Europe,1.08244768,7.07E-06,-29,0,Social Distancing and Wearing Masks Enforced,2.730424778
2020-03-05,5,3,2020,53,0,Belgium,BE,BEL,11455519,Europe,0.61978859,4.63E-06,-28,0,Social Distancing and Wearing Masks Enforced,2.466881066
2020-03-04,4,3,2020,34,0,Belgium,BE,BEL,11455519,Europe,0.32298842,2.97E-06,-19,0,Social Distancing and Wearing Masks Enforced,2.191050986
2020-03-03,3,3,2020,19,0,Belgium,BE,BEL,11455519,Europe,0.1571295,1.66E-06,-15,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-03-02,2,3,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.1571295,0,-19,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-03-01,1,3,2020,18,0,Belgium,BE,BEL,11455519,Europe,0,1.57E-06,18,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-02-29,29,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,-18,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-28,28,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-27,27,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-26,26,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-25,25,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-24,24,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-23,23,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-22,22,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-21,21,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-20,20,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-19,19,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-18,18,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-17,17,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-16,16,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-15,15,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-14,14,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-13,13,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-12,12,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-11,11,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-10,10,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-09,9,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-08,8,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-07,7,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-06,6,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-05,5,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.00872942,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-04,4,2,2020,1,0,Belgium,BE,BEL,11455519,Europe,0,8.73E-08,1,0,Social Distancing and Wearing Masks Enforced,0
2020-02-03,3,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,-1,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-02,2,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-02-01,1,2,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-31,31,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-30,30,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-29,29,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-28,28,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-27,27,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-26,26,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-25,25,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-24,24,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-23,23,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-22,22,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-21,21,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-20,20,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-19,19,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-18,18,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-17,17,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-16,16,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-15,15,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-14,14,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-13,13,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,0.52376501,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-12,12,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-11,11,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-10,10,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-09,9,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-08,8,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-07,7,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-06,6,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-05,5,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-04,4,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-03,3,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-02,2,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-01-01,1,1,2020,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2019-12-31,31,12,2019,0,0,Belgium,BE,BEL,11455519,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-12-09,9,12,2020,15,0,China,CN,CHN,1433783692,Asia,0.01304241,1.05E-08,15,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-12-08,8,12,2020,12,0,China,CN,CHN,1433783692,Asia,0.01234496,8.37E-09,-3,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-12-07,7,12,2020,15,0,China,CN,CHN,1433783692,Asia,0.01304241,1.05E-08,3,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-12-06,6,12,2020,18,0,China,CN,CHN,1433783692,Asia,0.01276343,1.26E-08,3,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-12-05,5,12,2020,17,0,China,CN,CHN,1433783692,Asia,0.01262394,1.19E-08,-1,0,Social Distancing and Wearing Masks Enforced,1.760374428
2020-12-04,4,12,2020,17,0,China,CN,CHN,1433783692,Asia,0.01255419,1.19E-08,0,0,Social Distancing and Wearing Masks Enforced,1.760374428
2020-12-03,3,12,2020,16,0,China,CN,CHN,1433783692,Asia,0.01255419,1.12E-08,-1,0,Social Distancing and Wearing Masks Enforced,1.722706232
2020-12-02,2,12,2020,9,0,China,CN,CHN,1433783692,Asia,0.01227521,6.28E-09,-7,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-12-01,1,12,2020,12,0,China,CN,CHN,1433783692,Asia,0.01220547,8.37E-09,3,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-11-30,30,11,2020,18,0,China,CN,CHN,1433783692,Asia,0.0124147,1.26E-08,6,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-11-29,29,11,2020,6,0,China,CN,CHN,1433783692,Asia,0.0116475,4.18E-09,-12,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-11-28,28,11,2020,6,0,China,CN,CHN,1433783692,Asia,0.01199623,4.18E-09,0,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-11-27,27,11,2020,5,0,China,CN,CHN,1433783692,Asia,0.01262394,3.49E-09,-1,0,Social Distancing and Wearing Masks Enforced,1
2020-11-26,26,11,2020,21,0,China,CN,CHN,1433783692,Asia,0.01227521,1.46E-08,16,0,Social Distancing and Wearing Masks Enforced,1.89166815
2020-11-25,25,11,2020,5,0,China,CN,CHN,1433783692,Asia,0.01150801,3.49E-09,-16,0,Social Distancing and Wearing Masks Enforced,1
2020-11-24,24,11,2020,22,0,China,CN,CHN,1433783692,Asia,0.01206598,1.53E-08,17,0,Social Distancing and Wearing Masks Enforced,1.92057266
2020-11-23,23,11,2020,11,0,China,CN,CHN,1433783692,Asia,0.01192649,7.67E-09,-11,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-11-22,22,11,2020,16,0,China,CN,CHN,1433783692,Asia,0.01339114,1.12E-08,5,0,Social Distancing and Wearing Masks Enforced,1.722706232
2020-11-21,21,11,2020,16,0,China,CN,CHN,1433783692,Asia,0.01394911,1.12E-08,0,0,Social Distancing and Wearing Masks Enforced,1.722706232
2020-11-20,20,11,2020,17,0,China,CN,CHN,1433783692,Asia,0.01513478,1.19E-08,1,0,Social Distancing and Wearing Masks Enforced,1.760374428
2020-11-19,19,11,2020,12,0,China,CN,CHN,1433783692,Asia,0.01618096,8.37E-09,-5,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-11-18,18,11,2020,8,0,China,CN,CHN,1433783692,Asia,0.01722715,5.58E-09,-4,0,Social Distancing and Wearing Masks Enforced,1.292029674
2020-11-17,17,11,2020,15,0,China,CN,CHN,1433783692,Asia,0.01778511,1.05E-08,7,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-11-16,16,11,2020,7,0,China,CN,CHN,1433783692,Asia,0.02015646,4.88E-09,-8,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-11-15,15,11,2020,11,0,China,CN,CHN,1433783692,Asia,0.02134213,7.67E-09,4,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-11-14,14,11,2020,15,0,China,CN,CHN,1433783692,Asia,0.02224882,1.05E-08,4,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-11-13,13,11,2020,0,0,China,CN,CHN,1433783692,Asia,0.02350424,0,-15,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-11-12,12,11,2020,10,0,China,CN,CHN,1433783692,Asia,0.02524788,6.97E-09,10,0,Social Distancing and Wearing Masks Enforced,1.430676558
2020-11-11,11,11,2020,13,0,China,CN,CHN,1433783692,Asia,0.02622432,9.07E-09,3,0,Social Distancing and Wearing Masks Enforced,1.593692641
2020-11-10,10,11,2020,20,0,China,CN,CHN,1433783692,Asia,0.02824694,1.39E-08,7,0,Social Distancing and Wearing Masks Enforced,1.861353116
2020-11-09,9,11,2020,32,0,China,CN,CHN,1433783692,Asia,0.02852592,2.23E-08,12,0,Social Distancing and Wearing Masks Enforced,2.15338279
2020-11-08,8,11,2020,24,0,China,CN,CHN,1433783692,Asia,0.02810745,1.67E-08,-8,0,Social Distancing and Wearing Masks Enforced,1.974635869
2020-11-07,7,11,2020,33,0,China,CN,CHN,1433783692,Asia,0.02775872,2.30E-08,9,0,Social Distancing and Wearing Masks Enforced,2.172502297
2020-11-06,6,11,2020,32,0,China,CN,CHN,1433783692,Asia,0.02775872,2.23E-08,-1,0,Social Distancing and Wearing Masks Enforced,2.15338279
2020-11-05,5,11,2020,27,0,China,CN,CHN,1433783692,Asia,0.02754948,1.88E-08,-5,0,Social Distancing and Wearing Masks Enforced,2.047818583
2020-11-04,4,11,2020,16,0,China,CN,CHN,1433783692,Asia,0.02720076,1.12E-08,-11,0,Social Distancing and Wearing Masks Enforced,1.722706232
2020-11-03,3,11,2020,49,0,China,CN,CHN,1433783692,Asia,0.02720076,3.42E-08,33,0,Social Distancing and Wearing Masks Enforced,2.41812391
2020-11-02,2,11,2020,24,0,China,CN,CHN,1433783692,Asia,0.02615457,1.67E-08,-25,0,Social Distancing and Wearing Masks Enforced,1.974635869
2020-11-01,1,11,2020,24,0,China,CN,CHN,1433783692,Asia,0.02566635,1.67E-08,0,0,Social Distancing and Wearing Masks Enforced,1.974635869
2020-10-31,31,10,2020,33,0,China,CN,CHN,1433783692,Asia,0.02608483,2.30E-08,9,0,Social Distancing and Wearing Masks Enforced,2.172502297
2020-10-30,30,10,2020,25,0,China,CN,CHN,1433783692,Asia,0.02517814,1.74E-08,-8,0,Social Distancing and Wearing Masks Enforced,2
2020-10-29,29,10,2020,24,0,China,CN,CHN,1433783692,Asia,0.02594534,1.67E-08,-1,0,Social Distancing and Wearing Masks Enforced,1.974635869
2020-10-28,28,10,2020,42,0,China,CN,CHN,1433783692,Asia,0.02503864,2.93E-08,18,0,Social Distancing and Wearing Masks Enforced,2.322344708
2020-10-27,27,10,2020,24,0,China,CN,CHN,1433783692,Asia,0.02406221,1.67E-08,-18,0,Social Distancing and Wearing Masks Enforced,1.974635869
2020-10-26,26,10,2020,26,0,China,CN,CHN,1433783692,Asia,0.02364373,1.81E-08,2,0,Social Distancing and Wearing Masks Enforced,2.024369199
2020-10-25,25,10,2020,19,0,China,CN,CHN,1433783692,Asia,0.0242017,1.33E-08,-7,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-10-24,24,10,2020,33,0,China,CN,CHN,1433783692,Asia,0.02434119,2.30E-08,14,0,Social Distancing and Wearing Masks Enforced,2.172502297
2020-10-23,23,10,2020,29,0,China,CN,CHN,1433783692,Asia,0.02406221,2.02E-08,-4,0,Social Distancing and Wearing Masks Enforced,2.092218534
2020-10-22,22,10,2020,22,0,China,CN,CHN,1433783692,Asia,0.02475966,1.53E-08,-7,0,Social Distancing and Wearing Masks Enforced,1.92057266
2020-10-21,21,10,2020,16,0,China,CN,CHN,1433783692,Asia,0.02475966,1.12E-08,-6,0,Social Distancing and Wearing Masks Enforced,1.722706232
2020-10-20,20,10,2020,34,0,China,CN,CHN,1433783692,Asia,0.02468992,2.37E-08,18,0,Social Distancing and Wearing Masks Enforced,2.191050986
2020-10-19,19,10,2020,17,0,China,CN,CHN,1433783692,Asia,0.02392272,1.19E-08,-17,0,Social Distancing and Wearing Masks Enforced,1.760374428
2020-10-18,18,10,2020,30,0,China,CN,CHN,1433783692,Asia,0.02448068,2.09E-08,13,0,Social Distancing and Wearing Masks Enforced,2.113282753
2020-10-17,17,10,2020,20,0,China,CN,CHN,1433783692,Asia,0.02378322,1.39E-08,-10,0,Social Distancing and Wearing Masks Enforced,1.861353116
2020-10-16,16,10,2020,36,0,China,CN,CHN,1433783692,Asia,0.02357399,2.51E-08,16,0,Social Distancing and Wearing Masks Enforced,2.226565505
2020-10-15,15,10,2020,11,0,China,CN,CHN,1433783692,Asia,0.02378322,7.67E-09,-25,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-10-14,14,10,2020,28,0,China,CN,CHN,1433783692,Asia,0.02301602,1.95E-08,17,0,Social Distancing and Wearing Masks Enforced,2.070415071
2020-10-13,13,10,2020,18,0,China,CN,CHN,1433783692,Asia,0.0226673,1.26E-08,-10,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-10-12,12,10,2020,34,0,China,CN,CHN,1433783692,Asia,0.02294628,2.37E-08,16,0,Social Distancing and Wearing Masks Enforced,2.191050986
2020-10-11,11,10,2020,21,0,China,CN,CHN,1433783692,Asia,0.02245806,1.46E-08,-13,0,Social Distancing and Wearing Masks Enforced,1.89166815
2020-10-10,10,10,2020,29,0,China,CN,CHN,1433783692,Asia,0.02203959,2.02E-08,8,0,Social Distancing and Wearing Masks Enforced,2.092218534
2020-10-09,9,10,2020,39,0,China,CN,CHN,1433783692,Asia,0.02120264,2.72E-08,10,0,Social Distancing and Wearing Masks Enforced,2.276298836
2020-10-08,8,10,2020,22,0,China,CN,CHN,1433783692,Asia,0.01952875,1.53E-08,-17,0,Social Distancing and Wearing Masks Enforced,1.92057266
2020-10-07,7,10,2020,15,0,China,CN,CHN,1433783692,Asia,0.0186918,1.05E-08,-7,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-10-06,6,10,2020,23,0,China,CN,CHN,1433783692,Asia,0.01890104,1.60E-08,8,0,Social Distancing and Wearing Masks Enforced,1.948192093
2020-10-05,5,10,2020,25,0,China,CN,CHN,1433783692,Asia,0.01813384,1.74E-08,2,0,Social Distancing and Wearing Masks Enforced,2
2020-10-04,4,10,2020,20,0,China,CN,CHN,1433783692,Asia,0.01890104,1.39E-08,-5,0,Social Distancing and Wearing Masks Enforced,1.861353116
2020-10-03,3,10,2020,17,0,China,CN,CHN,1433783692,Asia,0.01924977,1.19E-08,-3,0,Social Distancing and Wearing Masks Enforced,1.760374428
2020-10-02,2,10,2020,39,0,China,CN,CHN,1433783692,Asia,0.01904053,2.72E-08,22,0,Social Distancing and Wearing Masks Enforced,2.276298836
2020-10-01,1,10,2020,0,0,China,CN,CHN,1433783692,Asia,0.01938926,0,-39,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-09-30,30,9,2020,23,0,China,CN,CHN,1433783692,Asia,0.01987748,1.60E-08,23,0,Social Distancing and Wearing Masks Enforced,1.948192093
2020-09-29,29,9,2020,22,0,China,CN,CHN,1433783692,Asia,0.01994722,1.53E-08,-1,0,Social Distancing and Wearing Masks Enforced,1.92057266
2020-09-28,28,9,2020,27,0,China,CN,CHN,1433783692,Asia,0.01994722,1.88E-08,5,0,Social Distancing and Wearing Masks Enforced,2.047818583
2020-09-27,27,9,2020,15,0,China,CN,CHN,1433783692,Asia,0.02008671,1.05E-08,-12,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-09-26,26,9,2020,17,1,China,CN,CHN,1433783692,Asia,0.02064468,1.19E-08,2,1,Social Distancing and Wearing Masks Enforced,1.760374428
2020-09-25,25,9,2020,15,0,China,CN,CHN,1433783692,Asia,0.02071442,1.05E-08,-2,-1,Social Distancing and Wearing Masks Enforced,1.682606194
2020-09-24,24,9,2020,10,1,China,CN,CHN,1433783692,Asia,0.02155137,6.97E-09,-5,1,Social Distancing and Wearing Masks Enforced,1.430676558
2020-09-23,23,9,2020,18,0,China,CN,CHN,1433783692,Asia,0.0217606,1.26E-08,8,-1,Social Distancing and Wearing Masks Enforced,1.795888947
2020-09-22,22,9,2020,12,0,China,CN,CHN,1433783692,Asia,0.02106315,8.37E-09,-6,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-09-21,21,9,2020,36,0,China,CN,CHN,1433783692,Asia,0.02169086,2.51E-08,24,0,Social Distancing and Wearing Masks Enforced,2.226565505
2020-09-20,20,9,2020,25,0,China,CN,CHN,1433783692,Asia,0.02148162,1.74E-08,-11,0,Social Distancing and Wearing Masks Enforced,2
2020-09-19,19,9,2020,14,1,China,CN,CHN,1433783692,Asia,0.02092366,9.76E-09,-11,1,Social Distancing and Wearing Masks Enforced,1.639738513
2020-09-18,18,9,2020,44,0,China,CN,CHN,1433783692,Asia,0.02148162,3.07E-08,30,-1,Social Distancing and Wearing Masks Enforced,2.351249219
2020-09-17,17,9,2020,7,0,China,CN,CHN,1433783692,Asia,0.02071442,4.88E-09,-37,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-09-16,16,9,2020,24,1,China,CN,CHN,1433783692,Asia,0.02155137,1.67E-08,17,1,Social Distancing and Wearing Masks Enforced,1.974635869
2020-09-15,15,9,2020,22,1,China,CN,CHN,1433783692,Asia,0.02127239,1.53E-08,-2,0,Social Distancing and Wearing Masks Enforced,1.92057266
2020-09-14,14,9,2020,29,0,China,CN,CHN,1433783692,Asia,0.02106315,2.02E-08,7,-1,Social Distancing and Wearing Masks Enforced,2.092218534
2020-09-13,13,9,2020,23,1,China,CN,CHN,1433783692,Asia,0.02127239,1.60E-08,-6,1,Social Distancing and Wearing Masks Enforced,1.948192093
2020-09-12,12,9,2020,18,0,China,CN,CHN,1433783692,Asia,0.02155137,1.26E-08,-5,-1,Social Distancing and Wearing Masks Enforced,1.795888947
2020-09-11,11,9,2020,27,0,China,CN,CHN,1433783692,Asia,0.02183035,1.88E-08,9,0,Social Distancing and Wearing Masks Enforced,2.047818583
2020-09-10,10,9,2020,13,0,China,CN,CHN,1433783692,Asia,0.02203959,9.07E-09,-14,0,Social Distancing and Wearing Masks Enforced,1.593692641
2020-09-09,9,9,2020,8,1,China,CN,CHN,1433783692,Asia,0.02336475,5.58E-09,-5,1,Social Distancing and Wearing Masks Enforced,1.292029674
2020-09-08,8,9,2020,21,2,China,CN,CHN,1433783692,Asia,0.02517814,1.46E-08,13,1,Social Distancing and Wearing Masks Enforced,1.89166815
2020-09-07,7,9,2020,33,2,China,CN,CHN,1433783692,Asia,0.02531763,2.30E-08,12,0,Social Distancing and Wearing Masks Enforced,2.172502297
2020-09-06,6,9,2020,17,0,China,CN,CHN,1433783692,Asia,0.02587559,1.19E-08,-16,-2,Social Distancing and Wearing Masks Enforced,1.760374428
2020-09-05,5,9,2020,22,0,China,CN,CHN,1433783692,Asia,0.02734025,1.53E-08,5,0,Social Distancing and Wearing Masks Enforced,1.92057266
2020-09-04,4,9,2020,33,1,China,CN,CHN,1433783692,Asia,0.02922338,2.30E-08,11,1,Social Distancing and Wearing Masks Enforced,2.172502297
2020-09-03,3,9,2020,19,3,China,CN,CHN,1433783692,Asia,0.02971159,1.33E-08,-14,2,Social Distancing and Wearing Masks Enforced,1.8294828
2020-09-02,2,9,2020,20,1,China,CN,CHN,1433783692,Asia,0.03068803,1.39E-08,1,-2,Social Distancing and Wearing Masks Enforced,1.861353116
2020-09-01,1,9,2020,19,1,China,CN,CHN,1433783692,Asia,0.03298963,1.33E-08,-1,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-08-31,31,8,2020,32,1,China,CN,CHN,1433783692,Asia,0.03626767,2.23E-08,13,0,Social Distancing and Wearing Masks Enforced,2.15338279
2020-08-30,30,8,2020,27,3,China,CN,CHN,1433783692,Asia,0.04073139,1.88E-08,-5,2,Social Distancing and Wearing Masks Enforced,2.047818583
2020-08-29,29,8,2020,22,3,China,CN,CHN,1433783692,Asia,0.04338172,1.53E-08,-5,0,Social Distancing and Wearing Masks Enforced,1.92057266
2020-08-28,28,8,2020,30,2,China,CN,CHN,1433783692,Asia,0.0467295,2.09E-08,8,-1,Social Distancing and Wearing Masks Enforced,2.113282753
2020-08-27,27,8,2020,32,1,China,CN,CHN,1433783692,Asia,0.05154194,2.23E-08,2,-1,Social Distancing and Wearing Masks Enforced,2.15338279
2020-08-26,26,8,2020,34,1,China,CN,CHN,1433783692,Asia,0.05495948,2.37E-08,2,0,Social Distancing and Wearing Masks Enforced,2.191050986
2020-08-25,25,8,2020,23,0,China,CN,CHN,1433783692,Asia,0.05663337,1.60E-08,-11,-1,Social Distancing and Wearing Masks Enforced,1.948192093
2020-08-24,24,8,2020,41,0,China,CN,CHN,1433783692,Asia,0.06291047,2.86E-08,18,0,Social Distancing and Wearing Masks Enforced,2.307372057
2020-08-23,23,8,2020,38,0,China,CN,CHN,1433783692,Asia,0.06849011,2.65E-08,-3,0,Social Distancing and Wearing Masks Enforced,2.260159359
2020-08-22,22,8,2020,49,2,China,CN,CHN,1433783692,Asia,0.07225637,3.42E-08,11,2,Social Distancing and Wearing Masks Enforced,2.41812391
2020-08-21,21,8,2020,40,3,China,CN,CHN,1433783692,Asia,0.0772083,2.79E-08,-9,1,Social Distancing and Wearing Masks Enforced,2.292029674
2020-08-20,20,8,2020,33,1,China,CN,CHN,1433783692,Asia,0.08362489,2.30E-08,-7,-2,Social Distancing and Wearing Masks Enforced,2.172502297
2020-08-19,19,8,2020,53,2,China,CN,CHN,1433783692,Asia,0.08983224,3.70E-08,20,1,Social Distancing and Wearing Masks Enforced,2.466881066
2020-08-18,18,8,2020,66,0,China,CN,CHN,1433783692,Asia,0.0935985,4.60E-08,13,-2,Social Distancing and Wearing Masks Enforced,2.603178855
2020-08-17,17,8,2020,96,0,China,CN,CHN,1433783692,Asia,0.09694628,6.70E-08,30,0,Social Distancing and Wearing Masks Enforced,2.835988985
2020-08-16,16,8,2020,65,2,China,CN,CHN,1433783692,Asia,0.10127051,4.53E-08,-31,2,Social Distancing and Wearing Masks Enforced,2.593692641
2020-08-15,15,8,2020,70,1,China,CN,CHN,1433783692,Asia,0.10873328,4.88E-08,5,-1,Social Distancing and Wearing Masks Enforced,2.639738513
2020-08-14,14,8,2020,99,3,China,CN,CHN,1433783692,Asia,0.11542885,6.90E-08,29,2,Social Distancing and Wearing Masks Enforced,2.855108491
2020-08-13,13,8,2020,81,4,China,CN,CHN,1433783692,Asia,0.12777381,5.65E-08,-18,1,Social Distancing and Wearing Masks Enforced,2.730424778
2020-08-12,12,8,2020,58,3,China,CN,CHN,1433783692,Asia,0.13767767,4.05E-08,-23,-1,Social Distancing and Wearing Masks Enforced,2.522895092
2020-08-11,11,8,2020,113,4,China,CN,CHN,1433783692,Asia,0.14806976,7.88E-08,55,1,Social Distancing and Wearing Masks Enforced,2.937291201
2020-08-10,10,8,2020,121,5,China,CN,CHN,1433783692,Asia,0.15504431,8.44E-08,8,1,Social Distancing and Wearing Masks Enforced,2.979792205
2020-08-09,9,8,2020,92,0,China,CN,CHN,1433783692,Asia,0.159787,6.42E-08,-29,-5,Social Distancing and Wearing Masks Enforced,2.80954521
2020-08-08,8,8,2020,120,1,China,CN,CHN,1433783692,Asia,0.16585486,8.37E-08,28,1,Social Distancing and Wearing Masks Enforced,2.974635869
2020-08-07,7,8,2020,132,3,China,CN,CHN,1433783692,Asia,0.16843545,9.21E-08,12,2,Social Distancing and Wearing Masks Enforced,3.033855413
2020-08-06,6,8,2020,122,1,China,CN,CHN,1433783692,Asia,0.16892367,8.51E-08,-10,-2,Social Distancing and Wearing Masks Enforced,2.984906101
2020-08-05,5,8,2020,107,4,China,CN,CHN,1433783692,Asia,0.16983036,7.46E-08,-15,3,Social Distancing and Wearing Masks Enforced,2.903391798
2020-08-04,4,8,2020,114,3,China,CN,CHN,1433783692,Asia,0.16752876,7.95E-08,7,-1,Social Distancing and Wearing Masks Enforced,2.942765553
2020-08-03,3,8,2020,158,2,China,CN,CHN,1433783692,Asia,0.16543639,1.10E-07,44,-1,Social Distancing and Wearing Masks Enforced,3.145567154
2020-08-02,2,8,2020,172,6,China,CN,CHN,1433783692,Asia,0.16348352,1.20E-07,14,4,Social Distancing and Wearing Masks Enforced,3.198318144
2020-08-01,1,8,2020,166,2,China,CN,CHN,1433783692,Asia,0.15706693,1.16E-07,-6,-4,Social Distancing and Wearing Masks Enforced,3.176256598
2020-07-31,31,7,2020,276,0,China,CN,CHN,1433783692,Asia,0.15106881,1.92E-07,110,-2,Social Distancing and Wearing Masks Enforced,3.492151404
2020-07-30,30,7,2020,223,2,China,CN,CHN,1433783692,Asia,0.13718945,1.56E-07,-53,2,Social Distancing and Wearing Masks Enforced,3.359664719
2020-07-29,29,7,2020,207,1,China,CN,CHN,1433783692,Asia,0.12303111,1.44E-07,-16,-1,Social Distancing and Wearing Masks Enforced,3.313404482
2020-07-28,28,7,2020,213,4,China,CN,CHN,1433783692,Asia,0.11236004,1.49E-07,6,3,Social Distancing and Wearing Masks Enforced,3.331158117
2020-07-27,27,7,2020,189,0,China,CN,CHN,1433783692,Asia,0.10134025,1.32E-07,-24,-4,Social Distancing and Wearing Masks Enforced,3.256880539
2020-07-26,26,7,2020,179,2,China,CN,CHN,1433783692,Asia,0.09136664,1.25E-07,-10,2,Social Distancing and Wearing Masks Enforced,3.22310402
2020-07-25,25,7,2020,157,1,China,CN,CHN,1433783692,Asia,0.08132329,1.10E-07,-22,-1,Social Distancing and Wearing Masks Enforced,3.141622157
2020-07-24,24,7,2020,139,1,China,CN,CHN,1433783692,Asia,0.07316306,9.69E-08,-18,0,Social Distancing and Wearing Masks Enforced,3.065961038
2020-07-23,23,7,2020,135,0,China,CN,CHN,1433783692,Asia,0.06667672,9.42E-08,-4,-1,Social Distancing and Wearing Masks Enforced,3.047818583
2020-07-22,22,7,2020,74,2,China,CN,CHN,1433783692,Asia,0.05956268,5.16E-08,-61,2,Social Distancing and Wearing Masks Enforced,2.674266003
2020-07-21,21,7,2020,84,0,China,CN,CHN,1433783692,Asia,0.05586617,5.86E-08,10,-2,Social Distancing and Wearing Masks Enforced,2.753021266
2020-07-20,20,7,2020,130,0,China,CN,CHN,1433783692,Asia,0.05175118,9.07E-08,46,0,Social Distancing and Wearing Masks Enforced,3.024369199
2020-07-19,19,7,2020,80,1,China,CN,CHN,1433783692,Asia,0.0436607,5.58E-08,-50,1,Social Distancing and Wearing Masks Enforced,2.722706232
2020-07-18,18,7,2020,80,1,China,CN,CHN,1433783692,Asia,0.03933648,5.58E-08,0,0,Social Distancing and Wearing Masks Enforced,2.722706232
2020-07-17,17,7,2020,77,0,China,CN,CHN,1433783692,Asia,0.03438455,5.37E-08,-3,-1,Social Distancing and Wearing Masks Enforced,2.698958058
2020-07-16,16,7,2020,20,2,China,CN,CHN,1433783692,Asia,0.02999058,1.39E-08,-57,2,Social Distancing and Wearing Masks Enforced,1.861353116
2020-07-15,15,7,2020,54,0,China,CN,CHN,1433783692,Asia,0.03075778,3.77E-08,34,-2,Social Distancing and Wearing Masks Enforced,2.478495142
2020-07-14,14,7,2020,55,1,China,CN,CHN,1433783692,Asia,0.02734025,3.84E-08,1,1,Social Distancing and Wearing Masks Enforced,2.489896102
2020-07-13,13,7,2020,46,0,China,CN,CHN,1433783692,Asia,0.02510839,3.21E-08,-9,-1,Social Distancing and Wearing Masks Enforced,2.378868652
2020-07-12,12,7,2020,35,0,China,CN,CHN,1433783692,Asia,0.02287653,2.44E-08,-11,0,Social Distancing and Wearing Masks Enforced,2.209061955
2020-07-11,11,7,2020,40,0,China,CN,CHN,1433783692,Asia,0.02169086,2.79E-08,5,0,Social Distancing and Wearing Masks Enforced,2.292029674
2020-07-10,10,7,2020,46,0,China,CN,CHN,1433783692,Asia,0.02057493,3.21E-08,6,0,Social Distancing and Wearing Masks Enforced,2.378868652
2020-07-09,9,7,2020,33,0,China,CN,CHN,1433783692,Asia,0.01931951,2.30E-08,-13,0,Social Distancing and Wearing Masks Enforced,2.172502297
2020-07-08,8,7,2020,21,0,China,CN,CHN,1433783692,Asia,0.01841282,1.46E-08,-12,0,Social Distancing and Wearing Masks Enforced,1.89166815
2020-07-07,7,7,2020,25,0,China,CN,CHN,1433783692,Asia,0.01897078,1.74E-08,4,0,Social Distancing and Wearing Masks Enforced,2
2020-07-06,6,7,2020,14,0,China,CN,CHN,1433783692,Asia,0.02085391,9.76E-09,-11,0,Social Distancing and Wearing Masks Enforced,1.639738513
2020-07-05,5,7,2020,18,0,China,CN,CHN,1433783692,Asia,0.02120264,1.26E-08,4,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-07-04,4,7,2020,9,0,China,CN,CHN,1433783692,Asia,0.02196984,6.28E-09,-9,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-07-03,3,7,2020,14,0,China,CN,CHN,1433783692,Asia,0.0234345,9.76E-09,5,0,Social Distancing and Wearing Masks Enforced,1.639738513
2020-07-02,2,7,2020,31,0,China,CN,CHN,1433783692,Asia,0.0249689,2.16E-08,17,0,Social Distancing and Wearing Masks Enforced,2.133656215
2020-07-01,1,7,2020,5,0,China,CN,CHN,1433783692,Asia,0.02531763,3.49E-09,-26,0,Social Distancing and Wearing Masks Enforced,1
2020-06-30,30,6,2020,23,0,China,CN,CHN,1433783692,Asia,0.0280377,1.60E-08,18,0,Social Distancing and Wearing Masks Enforced,1.948192093
2020-06-29,29,6,2020,14,0,China,CN,CHN,1433783692,Asia,0.02943261,9.76E-09,-9,0,Social Distancing and Wearing Masks Enforced,1.639738513
2020-06-28,28,6,2020,18,0,China,CN,CHN,1433783692,Asia,0.03173422,1.26E-08,4,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-06-27,27,6,2020,24,0,China,CN,CHN,1433783692,Asia,0.03466353,1.67E-08,6,0,Social Distancing and Wearing Masks Enforced,1.974635869
2020-06-26,26,6,2020,28,1,China,CN,CHN,1433783692,Asia,0.03382658,1.95E-08,4,1,Social Distancing and Wearing Masks Enforced,2.070415071
2020-06-25,25,6,2020,20,0,China,CN,CHN,1433783692,Asia,0.03236192,1.39E-08,-8,-1,Social Distancing and Wearing Masks Enforced,1.861353116
2020-06-24,24,6,2020,29,1,China,CN,CHN,1433783692,Asia,0.03173422,2.02E-08,9,1,Social Distancing and Wearing Masks Enforced,2.092218534
2020-06-23,23,6,2020,52,0,China,CN,CHN,1433783692,Asia,0.02999058,3.63E-08,23,-1,Social Distancing and Wearing Masks Enforced,2.455045757
2020-06-22,22,6,2020,19,0,China,CN,CHN,1433783692,Asia,0.02657305,1.33E-08,-33,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-06-21,21,6,2020,29,1,China,CN,CHN,1433783692,Asia,0.02559661,2.02E-08,10,1,Social Distancing and Wearing Masks Enforced,2.092218534
2020-06-20,20,6,2020,30,0,China,CN,CHN,1433783692,Asia,0.0242017,2.09E-08,1,-1,Social Distancing and Wearing Masks Enforced,2.113282753
2020-06-19,19,6,2020,36,0,China,CN,CHN,1433783692,Asia,0.02252781,2.51E-08,6,0,Social Distancing and Wearing Masks Enforced,2.226565505
2020-06-18,18,6,2020,36,0,China,CN,CHN,1433783692,Asia,0.02078417,2.51E-08,0,0,Social Distancing and Wearing Masks Enforced,2.226565505
2020-06-17,17,6,2020,44,0,China,CN,CHN,1433783692,Asia,0.01834307,3.07E-08,8,0,Social Distancing and Wearing Masks Enforced,2.351249219
2020-06-16,16,6,2020,43,0,China,CN,CHN,1433783692,Asia,0.015623,3.00E-08,-1,0,Social Distancing and Wearing Masks Enforced,2.336965028
2020-06-15,15,6,2020,47,0,China,CN,CHN,1433783692,Asia,0.01311216,3.28E-08,4,0,Social Distancing and Wearing Masks Enforced,2.392231208
2020-06-14,14,6,2020,60,0,China,CN,CHN,1433783692,Asia,0.01115928,4.18E-08,13,0,Social Distancing and Wearing Masks Enforced,2.543959311
2020-06-13,13,6,2020,12,0,China,CN,CHN,1433783692,Asia,0.00732328,8.37E-09,-48,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-06-12,12,6,2020,7,0,China,CN,CHN,1433783692,Asia,0.00767201,4.88E-09,-5,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-06-11,11,6,2020,11,0,China,CN,CHN,1433783692,Asia,0.00718379,7.67E-09,4,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-06-10,10,6,2020,4,0,China,CN,CHN,1433783692,Asia,0.00662583,2.79E-09,-7,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-06-09,9,6,2020,3,0,China,CN,CHN,1433783692,Asia,0.00641659,2.09E-09,-1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-06-08,8,6,2020,5,0,China,CN,CHN,1433783692,Asia,0.00669557,3.49E-09,2,0,Social Distancing and Wearing Masks Enforced,1
2020-06-07,7,6,2020,9,0,China,CN,CHN,1433783692,Asia,0.00711404,6.28E-09,4,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-06-06,6,6,2020,6,0,China,CN,CHN,1433783692,Asia,0.00669557,4.18E-09,-3,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-06-05,5,6,2020,11,0,China,CN,CHN,1433783692,Asia,0.00641659,7.67E-09,5,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-06-04,4,6,2020,1,0,China,CN,CHN,1433783692,Asia,0.00648633,6.97E-10,-10,0,Social Distancing and Wearing Masks Enforced,0
2020-06-03,3,6,2020,5,0,China,CN,CHN,1433783692,Asia,0.00655608,3.49E-09,4,0,Social Distancing and Wearing Masks Enforced,1
2020-06-02,2,6,2020,7,0,China,CN,CHN,1433783692,Asia,0.00634684,4.88E-09,2,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-06-01,1,6,2020,19,0,China,CN,CHN,1433783692,Asia,0.00648633,1.33E-08,12,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-05-31,31,5,2020,5,0,China,CN,CHN,1433783692,Asia,0.00585862,3.49E-09,-14,0,Social Distancing and Wearing Masks Enforced,1
2020-05-30,30,5,2020,17,0,China,CN,CHN,1433783692,Asia,0.00592837,1.19E-08,12,0,Social Distancing and Wearing Masks Enforced,1.760374428
2020-05-29,29,5,2020,0,0,China,CN,CHN,1433783692,Asia,0.00537041,0,-17,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-28,28,5,2020,3,0,China,CN,CHN,1433783692,Asia,0.00571913,2.09E-09,3,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-05-27,27,5,2020,1,0,China,CN,CHN,1433783692,Asia,0.00592837,6.97E-10,-2,0,Social Distancing and Wearing Masks Enforced,0
2020-05-26,26,5,2020,7,0,China,CN,CHN,1433783692,Asia,0.00634684,4.88E-09,6,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-05-25,25,5,2020,11,0,China,CN,CHN,1433783692,Asia,0.00592837,7.67E-09,4,0,Social Distancing and Wearing Masks Enforced,1.489896102
2020-05-24,24,5,2020,3,0,China,CN,CHN,1433783692,Asia,0.00648633,2.09E-09,-8,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-05-23,23,5,2020,2,0,China,CN,CHN,1433783692,Asia,0.00732328,1.39E-09,-1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-22,22,5,2020,12,0,China,CN,CHN,1433783692,Asia,0.00718379,8.37E-09,10,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-05-21,21,5,2020,2,0,China,CN,CHN,1433783692,Asia,0.00676532,1.39E-09,-10,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-20,20,5,2020,2,0,China,CN,CHN,1433783692,Asia,0.00676532,1.39E-09,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-19,19,5,2020,9,0,China,CN,CHN,1433783692,Asia,0.00676532,6.28E-09,7,0,Social Distancing and Wearing Masks Enforced,1.365212389
2020-05-18,18,5,2020,10,0,China,CN,CHN,1433783692,Asia,0.0062771,6.97E-09,1,0,Social Distancing and Wearing Masks Enforced,1.430676558
2020-05-17,17,5,2020,6,1,China,CN,CHN,1433783692,Asia,0.00578888,4.18E-09,-4,1,Social Distancing and Wearing Masks Enforced,1.113282753
2020-05-16,16,5,2020,9,0,China,CN,CHN,1433783692,Asia,0.0055099,6.28E-09,3,-1,Social Distancing and Wearing Masks Enforced,1.365212389
2020-05-15,15,5,2020,5,0,China,CN,CHN,1433783692,Asia,0.00509142,3.49E-09,-4,0,Social Distancing and Wearing Masks Enforced,1
2020-05-14,14,5,2020,6,0,China,CN,CHN,1433783692,Asia,0.00557964,4.18E-09,1,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-05-13,13,5,2020,7,0,China,CN,CHN,1433783692,Asia,0.00544015,4.88E-09,1,0,Social Distancing and Wearing Masks Enforced,1.209061955
2020-05-12,12,5,2020,1,0,China,CN,CHN,1433783692,Asia,0.00509142,6.97E-10,-6,0,Social Distancing and Wearing Masks Enforced,0
2020-05-11,11,5,2020,19,0,China,CN,CHN,1433783692,Asia,0.00683506,1.33E-08,18,0,Social Distancing and Wearing Masks Enforced,1.8294828
2020-05-10,10,5,2020,15,0,China,CN,CHN,1433783692,Asia,0.00571913,1.05E-08,-4,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-05-09,9,5,2020,0,0,China,CN,CHN,1433783692,Asia,0.00537041,0,-15,0,Social Distancing and Wearing Masks Enforced,#NUM!
2020-05-08,8,5,2020,6,0,China,CN,CHN,1433783692,Asia,0.00641659,4.18E-09,6,0,Social Distancing and Wearing Masks Enforced,1.113282753
2020-05-07,7,5,2020,2,0,China,CN,CHN,1433783692,Asia,0.00655608,1.39E-09,-4,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-06,6,5,2020,2,0,China,CN,CHN,1433783692,Asia,0.00725353,1.39E-09,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-05,5,5,2020,2,0,China,CN,CHN,1433783692,Asia,0.00816023,1.39E-09,0,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-04,4,5,2020,3,0,China,CN,CHN,1433783692,Asia,0.01025259,2.09E-09,1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-05-03,3,5,2020,2,0,China,CN,CHN,1433783692,Asia,0.01101979,1.39E-09,-1,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-05-02,2,5,2020,3,0,China,CN,CHN,1433783692,Asia,0.01213572,2.09E-09,1,0,Social Distancing and Wearing Masks Enforced,0.682606194
2020-05-01,1,5,2020,12,0,China,CN,CHN,1433783692,Asia,0.0140886,8.37E-09,9,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-04-30,30,4,2020,4,0,China,CN,CHN,1433783692,Asia,0.03780208,2.79E-09,-8,0,Social Distancing and Wearing Masks Enforced,0.861353116
2020-04-29,29,4,2020,2,0,China,CN,CHN,1433783692,Asia,0.04101037,1.39E-09,-2,0,Social Distancing and Wearing Masks Enforced,0.430676558
2020-04-28,28,4,2020,26,0,China,CN,CHN,1433783692,Asia,0.04428841,1.81E-08,24,0,Social Distancing and Wearing Masks Enforced,2.024369199
2020-04-27,27,4,2020,3,1,China,CN,CHN,1433783692,Asia,0.04903111,2.09E-09,-23,1,Social Distancing and Wearing Masks Enforced,0.682606194
2020-04-26,26,4,2020,10,0,China,CN,CHN,1433783692,Asia,0.05663337,6.97E-09,7,-1,Social Distancing and Wearing Masks Enforced,1.430676558
2020-04-25,25,4,2020,15,0,China,CN,CHN,1433783692,Asia,0.06242225,1.05E-08,5,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-04-24,24,4,2020,8,0,China,CN,CHN,1433783692,Asia,0.06688596,5.58E-09,-7,0,Social Distancing and Wearing Masks Enforced,1.292029674
2020-04-23,23,4,2020,12,0,China,CN,CHN,1433783692,Asia,0.070164,8.37E-09,4,0,Social Distancing and Wearing Masks Enforced,1.543959311
2020-04-22,22,4,2020,15,0,China,CN,CHN,1433783692,Asia,0.07532517,1.05E-08,3,0,Social Distancing and Wearing Masks Enforced,1.682606194
2020-04-21,21,4,2020,32,0,China,CN,CHN,1433783692,Asia,0.0802771,2.23E-08,17,0,Social Distancing and Wearing Masks Enforced,2.15338279
2020-04-20,20,4,2020,14,0,China,CN,CHN,1433783692,Asia,0.08195099,9.76E-09,-18,0,Social Distancing and Wearing Masks Enforced,1.639738513
2020-04-19,19,4,2020,18,0,China,CN,CHN,1433783692,Asia,0.08564751,1.26E-08,4,0,Social Distancing and Wearing Masks Enforced,1.795888947
2020-04-18,18,4,2020,31,0,China,CN,CHN,1433783692,Asia,0.08773987,2.16E-08,13,0,Social Distancing and Wearing Masks Enforced,2.133656215
2020-04-17,17,4,2020,352,1290,China,CN,CHN,1433783692,Asia,0.08990199,2.46E-07,321,1290,Social Distancing and Wearing Masks Enforced,3.643278893
2020-04-16,16,4,2020,50,0,China,CN,CHN,1433783692,Asia,0.07023375,3.49E-08,-302,-1290,Social Distancing and Wearing Masks Enforced,2.430676558
2020-04-15,15,4,2020,49,1,China,CN,CHN,1433783692,Asia,0.07372102,3.42E-08,-1,1,Social Distancing and Wearing Masks Enforced,2.41812391
2020-04-14,14,4,2020,94,0,China,CN,CHN,1433783692,Asia,0.07406975,6.56E-08,45,-1,Social Distancing and Wearing Masks Enforced,2.822907766
2020-04-13,13,4,2020,112,2,China,CN,CHN,1433783692,Asia,0.07337229,7.81E-08,18,2,Social Distancing and Wearing Masks Enforced,2.931768187
2020-04-12,12,4,2020,93,0,China,CN,CHN,1433783692,Asia,0.07239586,6.49E-08,-19,-2,Social Distancing and Wearing Masks Enforced,2.816262409
2020-04-11,11,4,2020,79,3,China,CN,CHN,1433783692,Asia,0.07379077,5.51E-08,-14,3,Social Distancing and Wearing Masks Enforced,2.714890595
2020-04-10,10,4,2020,55,1,China,CN,CHN,1433783692,Asia,0.07658059,3.84E-08,-24,-2,Social Distancing and Wearing Masks Enforced,2.489896102
2020-04-09,9,4,2020,86,2,China,CN,CHN,1433783692,Asia,0.07930066,6.00E-08,31,1,Social Distancing and Wearing Masks Enforced,2.767641586
2020-04-08,8,4,2020,86,2,China,CN,CHN,1433783692,Asia,0.08041659,6.00E-08,0,0,Lockdown,2.767641586
2020-04-07,7,4,2020,56,0,China,CN,CHN,1433783692,Asia,0.07985863,3.91E-08,-30,-2,Lockdown,2.501091629
2020-04-06,6,4,2020,67,2,China,CN,CHN,1433783692,Asia,0.08076532,4.67E-08,11,2,Lockdown,2.612522414
2020-04-05,5,4,2020,48,3,China,CN,CHN,1433783692,Asia,0.08571725,3.35E-08,-19,1,Lockdown,2.405312427
2020-04-04,4,4,2020,62,4,China,CN,CHN,1433783692,Asia,0.08690293,4.32E-08,14,1,Lockdown,2.564332773
2020-04-03,3,4,2020,70,10,China,CN,CHN,1433783692,Asia,0.08620547,4.88E-08,8,6,Lockdown,2.639738513
2020-04-02,2,4,2020,100,6,China,CN,CHN,1433783692,Asia,0.08822809,6.97E-08,30,-4,Lockdown,2.861353116
2020-04-01,1,4,2020,54,1,China,CN,CHN,1433783692,Asia,0.08432234,3.77E-08,-46,-5,Lockdown,2.478495142
2020-03-31,31,3,2020,84,3,China,CN,CHN,1433783692,Asia,0.08216023,5.86E-08,30,2,Lockdown,2.753021266
2020-03-30,30,3,2020,98,2,China,CN,CHN,1433783692,Asia,0.07930066,6.84E-08,14,-1,Lockdown,2.848800468
2020-03-29,29,3,2020,113,5,China,CN,CHN,1433783692,Asia,0.07420924,7.88E-08,15,3,Lockdown,2.937291201
2020-03-28,28,3,2020,119,3,China,CN,CHN,1433783692,Asia,0.0678624,8.30E-08,6,-2,Lockdown,2.969436383
2020-03-27,27,3,2020,94,5,China,CN,CHN,1433783692,Asia,0.06088785,6.56E-08,-25,2,Lockdown,2.822907766
2020-03-26,26,3,2020,102,6,China,CN,CHN,1433783692,Asia,0.05586617,7.11E-08,8,1,Lockdown,2.87365718
2020-03-25,25,3,2020,78,4,China,CN,CHN,1433783692,Asia,0.05042602,5.44E-08,-24,-2,Lockdown,2.706975394
2020-03-24,24,3,2020,69,7,China,CN,CHN,1433783692,Asia,0.04700849,4.81E-08,-9,3,Lockdown,2.630798288
2020-03-23,23,3,2020,138,9,China,CN,CHN,1433783692,Asia,0.04359095,9.62E-08,69,2,Lockdown,3.061474846
2020-03-22,22,3,2020,65,6,China,CN,CHN,1433783692,Asia,0.03710462,4.53E-08,-73,-3,Lockdown,2.593692641
2020-03-21,21,3,2020,52,6,China,CN,CHN,1433783692,Asia,0.03577946,3.63E-08,-13,0,Lockdown,2.455045757
2020-03-20,20,3,2020,99,4,China,CN,CHN,1433783692,Asia,0.03919699,6.90E-08,47,-2,Lockdown,2.855108491
2020-03-19,19,3,2020,44,8,China,CN,CHN,1433783692,Asia,0.04414892,3.07E-08,-55,4,Lockdown,2.351249219
2020-03-18,18,3,2020,23,16,China,CN,CHN,1433783692,Asia,0.04924034,1.60E-08,-21,8,Lockdown,1.948192093
2020-03-17,17,3,2020,43,9,China,CN,CHN,1433783692,Asia,0.05593591,3.00E-08,20,-7,Lockdown,2.336965028
2020-03-16,16,3,2020,25,13,China,CN,CHN,1433783692,Asia,0.06179454,1.74E-08,-18,4,Lockdown,2
2020-03-15,15,3,2020,22,9,China,CN,CHN,1433783692,Asia,0.07434873,1.53E-08,-3,-4,Lockdown,1.92057266
2020-03-14,14,3,2020,19,15,China,CN,CHN,1433783692,Asia,0.11284826,1.33E-08,-3,6,Lockdown,1.8294828
2020-03-13,13,3,2020,22,7,China,CN,CHN,1433783692,Asia,0.14137418,1.53E-08,3,-8,Lockdown,1.92057266
2020-03-12,12,3,2020,24,11,China,CN,CHN,1433783692,Asia,0.16278606,1.67E-08,2,4,Lockdown,1.974635869
2020-03-11,11,3,2020,29,22,China,CN,CHN,1433783692,Asia,0.19173046,2.02E-08,5,11,Lockdown,2.092218534
2020-03-10,10,3,2020,20,17,China,CN,CHN,1433783692,Asia,0.2183035,1.39E-08,-9,-5,Lockdown,1.861353116
2020-03-09,9,3,2020,45,23,China,CN,CHN,1433783692,Asia,0.25282754,3.14E-08,25,6,Lockdown,2.365212389
2020-03-08,8,3,2020,46,27,China,CN,CHN,1433783692,Asia,0.26489351,3.21E-08,1,4,Lockdown,2.378868652
2020-03-07,7,3,2020,101,28,China,CN,CHN,1433783692,Asia,0.30681058,7.04E-08,55,1,Lockdown,2.867535604
2020-03-06,6,3,2020,170,30,China,CN,CHN,1433783692,Asia,0.35737608,1.19E-07,69,2,Lockdown,3.191050986
2020-03-05,5,3,2020,117,31,China,CN,CHN,1433783692,Asia,0.40766261,8.16E-08,-53,1,Lockdown,2.95890503
2020-03-04,4,3,2020,119,37,China,CN,CHN,1433783692,Asia,0.42698212,8.30E-08,2,6,Lockdown,2.969436383
2020-03-03,3,3,2020,127,32,China,CN,CHN,1433783692,Asia,0.54073708,8.86E-08,8,-5,Lockdown,3.009862666
2020-03-02,2,3,2020,205,42,China,CN,CHN,1433783692,Asia,0.66369844,1.43E-07,78,10,Lockdown,3.307372057
2020-03-01,1,3,2020,574,35,China,CN,CHN,1433783692,Asia,0.79251843,4.00E-07,369,-7,Lockdown,3.94711057
2020-02-29,29,2,2020,428,47,China,CN,CHN,1433783692,Asia,0.89246377,2.99E-07,-146,12,Lockdown,3.764744914
2020-02-28,28,2,2020,329,44,China,CN,CHN,1433783692,Asia,1.03962683,2.29E-07,-99,-3,Lockdown,3.601293163
2020-02-27,27,2,2020,439,29,China,CN,CHN,1433783692,Asia,1.30654297,3.06E-07,110,-15,Lockdown,3.780512045
2020-02-26,26,2,2020,410,52,China,CN,CHN,1433783692,Asia,2.33194171,2.86E-07,-29,23,Lockdown,3.738048615
2020-02-25,25,2,2020,515,70,China,CN,CHN,1433783692,Asia,2.44478998,3.59E-07,105,18,Lockdown,3.879719033
2020-02-24,24,2,2020,218,150,China,CN,CHN,1433783692,Asia,2.58253739,1.52E-07,-297,80,Lockdown,3.345574887
2020-02-23,23,2,2020,647,98,China,CN,CHN,1433783692,Asia,2.77475607,4.51E-07,429,-52,Lockdown,4.021494861
2020-02-22,22,2,2020,826,109,China,CN,CHN,1433783692,Asia,2.9114573,5.76E-07,179,11,Lockdown,4.173254974
2020-02-21,21,2,2020,891,118,China,CN,CHN,1433783692,Asia,3.09223771,6.21E-07,65,9,Lockdown,4.22032088
2020-02-20,20,2,2020,394,112,China,CN,CHN,1433783692,Asia,3.25049031,2.75E-07,-497,-6,Lockdown,3.713315601
2020-02-19,19,2,2020,1750,139,China,CN,CHN,1433783692,Asia,3.48295216,1.22E-06,1356,27,Lockdown,4.639738513
2020-02-18,18,2,2020,1890,98,China,CN,CHN,1433783692,Asia,3.63095216,1.32E-06,140,-41,Lockdown,4.687557097
2020-02-17,17,2,2020,2052,105,China,CN,CHN,1433783692,Asia,3.72489939,1.43E-06,162,7,Lockdown,4.7386545
2020-02-16,16,2,2020,2007,142,China,CN,CHN,1433783692,Asia,3.77790599,1.40E-06,-45,37,Lockdown,4.724877108
2020-02-15,15,2,2020,2538,143,China,CN,CHN,1433783692,Asia,3.81856763,1.77E-06,531,1,Lockdown,4.87072635
2020-02-14,14,2,2020,4156,13,China,CN,CHN,1433783692,Asia,3.78767036,2.90E-06,1618,-130,Lockdown,5.177154265
2020-02-13,13,2,2020,15141,254,China,CN,CHN,1433783692,Asia,3.6359041,1.06E-05,10985,241,Lockdown,5.980449137
2020-02-12,12,2,2020,2028,97,China,CN,CHN,1433783692,Asia,2.70124428,1.41E-06,-13113,-157,Lockdown,4.731344593
2020-02-11,11,2,2020,2490,108,China,CN,CHN,1433783692,Asia,2.6620473,1.74E-06,462,11,Lockdown,4.858862792
2020-02-10,10,2,2020,2974,97,China,CN,CHN,1433783692,Asia,2.61064484,2.07E-06,484,-11,Lockdown,4.969227496
2020-02-09,9,2,2020,2607,89,China,CN,CHN,1433783692,Asia,2.45811137,1.82E-06,-367,-8,Lockdown,4.887392892
2020-02-08,8,2,2020,3418,86,China,CN,CHN,1433783692,Asia,2.32266556,2.38E-06,811,-3,Lockdown,5.055684846
2020-02-07,7,2,2020,3160,73,China,CN,CHN,1433783692,Asia,2.11503312,2.20E-06,-258,-13,Lockdown,5.00692027
2020-02-06,6,2,2020,3727,72,China,CN,CHN,1433783692,Asia,1.91270135,2.60E-06,567,-1,Lockdown,5.109460164
2020-02-05,5,2,2020,3872,66,China,CN,CHN,1433783692,Asia,1.65952508,2.70E-06,145,-6,Lockdown,5.133174995
2020-02-04,4,2,2020,3237,65,China,CN,CHN,1433783692,Asia,1.39923477,2.26E-06,-635,-1,Lockdown,5.021878876
2020-02-03,3,2,2020,2812,57,China,CN,CHN,1433783692,Asia,1.18400008,1.96E-06,-425,-8,Lockdown,4.934425362
2020-02-02,2,2,2020,2590,45,China,CN,CHN,1433783692,Asia,0.98920082,1.81E-06,-222,-12,Lockdown,4.883327958
2020-02-01,1,2,2020,2095,46,China,CN,CHN,1433783692,Asia,0.81804529,1.46E-06,-495,1,Lockdown,4.751540133
2020-01-31,31,1,2020,1980,43,China,CN,CHN,1433783692,Asia,0.67311409,1.38E-06,-115,-3,Lockdown,4.716461608
2020-01-30,30,1,2020,1740,38,China,CN,CHN,1433783692,Asia,0.53529692,1.21E-06,-240,-5,Lockdown,4.636177845
2020-01-29,29,1,2020,1466,26,China,CN,CHN,1433783692,Asia,0.41393971,1.02E-06,-274,-12,Lockdown,4.529713651
2020-01-28,28,1,2020,1753,25,China,CN,CHN,1433783692,Asia,0.31169276,1.22E-06,287,-1,Lockdown,4.640802747
2020-01-27,27,1,2020,787,25,China,CN,CHN,1433783692,Asia,0.18942885,5.49E-07,-966,0,Lockdown,4.143203162
2020-01-26,26,1,2020,665,15,China,CN,CHN,1433783692,Asia,0.13453912,4.64E-07,-122,-10,Lockdown,4.038544756
2020-01-25,25,1,2020,441,15,China,CN,CHN,1433783692,Asia,0.08815835,3.08E-07,-224,0,Lockdown,3.783336299
2020-01-24,24,1,2020,259,9,China,CN,CHN,1433783692,Asia,0.05740057,1.81E-07,-182,-6,Lockdown,3.4526514
2020-01-23,23,1,2020,97,0,China,CN,CHN,1433783692,Asia,0.03933648,6.77E-08,-162,-9,Lockdown,2.842427746
2020-01-22,22,1,2020,140,11,China,CN,CHN,1433783692,Asia,0.03257116,9.76E-08,43,11,Lockdown,3.070415071
2020-01-21,21,1,2020,151,3,China,CN,CHN,1433783692,Asia,0.02280679,1.05E-07,11,-8,Lockdown,3.117411239
2020-01-20,20,1,2020,19,0,China,CN,CHN,1433783692,Asia,0.01227521,1.33E-08,-132,-3,Lockdown,1.8294828
2020-01-19,19,1,2020,136,1,China,CN,CHN,1433783692,Asia,0.01095005,9.49E-08,117,1,Lockdown,3.052404102
2020-01-18,18,1,2020,17,0,China,CN,CHN,1433783692,Asia,0.00251084,1.19E-08,-119,-1,Lockdown,1.760374428
2020-01-17,17,1,2020,4,0,China,CN,CHN,1433783692,Asia,0.00132517,2.79E-09,-13,0,Lockdown,0.861353116
2020-01-16,16,1,2020,0,0,China,CN,CHN,1433783692,Asia,0.00223186,0,-4,0,Lockdown,#NUM!
2020-01-15,15,1,2020,0,1,China,CN,CHN,1433783692,Asia,0.00223186,0,0,1,Lockdown,#NUM!
2020-01-14,14,1,2020,0,0,China,CN,CHN,1433783692,Asia,0.00223186,0,0,-1,Lockdown,#NUM!
2020-01-13,13,1,2020,0,0,China,CN,CHN,1433783692,Asia,0.00411499,0,0,0,Lockdown,#NUM!
2020-01-12,12,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,0,0,Lockdown,#NUM!
2020-01-11,11,1,2020,0,1,China,CN,CHN,1433783692,Asia,,0,0,1,Lockdown,#NUM!
2020-01-10,10,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,0,-1,Lockdown,#NUM!
2020-01-09,9,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,0,0,Lockdown,#NUM!
2020-01-08,8,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,0,0,Lockdown,#NUM!
2020-01-07,7,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,0,0,Lockdown,#NUM!
2020-01-06,6,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,0,0,Lockdown,#NUM!
2020-01-05,5,1,2020,15,0,China,CN,CHN,1433783692,Asia,,1.05E-08,15,0,Lockdown,1.682606194
2020-01-04,4,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,-15,0,Lockdown,#NUM!
2020-01-03,3,1,2020,17,0,China,CN,CHN,1433783692,Asia,,1.19E-08,17,0,Lockdown,1.760374428
2020-01-02,2,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,-17,0,Lockdown,#NUM!
2020-01-01,1,1,2020,0,0,China,CN,CHN,1433783692,Asia,,0,0,0,Lockdown,#NUM!
2019-12-31,31,12,2019,27,0,China,CN,CHN,1433783692,Asia,,1.88E-08,27,0,Lockdown,2.047818583
"""
        |> fromCSV
```

```elm {l=hidden}
unitedKingdomTable: Table
unitedKingdomTable =
    """dateRep UK,day,month,year,cases UK,deaths,countriesAndTerritories,geoId,countryterritoryCode,popData2019,continentExp,Cumulative_number_for_14_days_of_COVID-19_cases_per_100000,As of Population,Change in Cases,Change in Deaths,Measures UK,sweden Cases Change,Projected Population,sweden cases 
2020-12-09,9,12,2020,12281,599,United_Kingdom,UK,GBR,66647112,Europe,317.2635598,0.000184269,#VALUE!,#VALUE!,Social Distancing and Wearing Masks Enforced,0,12281,0
2020-12-08,8,12,2020,14718,189,United_Kingdom,UK,GBR,66647112,Europe,315.7901276,0.000220835,2437,-410,Social Distancing and Wearing Masks Enforced,69,14787,0
2020-12-07,7,12,2020,17271,231,United_Kingdom,UK,GBR,66647112,Europe,316.8884497,0.000259141,2553,42,Social Distancing and Wearing Masks Enforced,59,17330,0
2020-12-06,6,12,2020,15539,397,United_Kingdom,UK,GBR,66647112,Europe,318.9755619,0.000233153,-1732,166,Social Distancing and Wearing Masks Enforced,-5,15534,0
2020-12-05,5,12,2020,16298,504,United_Kingdom,UK,GBR,66647112,Europe,325.4814702,0.000244542,759,107,Social Distancing and Wearing Masks Enforced,0,16298,0
2020-12-04,4,12,2020,14878,414,United_Kingdom,UK,GBR,66647112,Europe,331.4142104,0.000223235,-1420,-90,Social Distancing and Wearing Masks Enforced,0,14878,0
2020-12-03,3,12,2020,16170,648,United_Kingdom,UK,GBR,66647112,Europe,343.4732476,0.000242621,1292,234,Social Distancing and Wearing Masks Enforced,0,16170,0
2020-12-02,2,12,2020,13429,603,United_Kingdom,UK,GBR,66647112,Europe,348.6332611,0.000201494,-2741,-45,Lockdown,0,13429,0
2020-12-01,1,12,2020,12330,203,United_Kingdom,UK,GBR,66647112,Europe,358.5691755,0.000185004,-1099,-400,Lockdown,349,12679,0
2020-11-30,30,11,2020,12155,215,United_Kingdom,UK,GBR,66647112,Europe,372.122651,0.000182378,-175,12,Lockdown,-244,11911,0
2020-11-29,29,11,2020,15871,479,United_Kingdom,UK,GBR,66647112,Europe,391.3387875,0.000238135,3716,264,Lockdown,0,15871,0
2020-11-28,28,11,2020,14739,520,United_Kingdom,UK,GBR,66647112,Europe,407.8271239,0.00022115,-1132,41,Lockdown,0,14739,0
2020-11-27,27,11,2020,17555,498,United_Kingdom,UK,GBR,66647112,Europe,426.6756525,0.000263402,2816,-22,Lockdown,0,17555,0
2020-11-26,26,11,2020,18213,695,United_Kingdom,UK,GBR,66647112,Europe,450.5551568,0.000273275,658,197,Lockdown,0,18213,0
2020-11-25,25,11,2020,11299,608,United_Kingdom,UK,GBR,66647112,Europe,457.6627416,0.000169535,-6914,-87,Lockdown,0,11299,0
2020-11-24,24,11,2020,15450,479,United_Kingdom,UK,GBR,66647112,Europe,471.3362524,0.000231818,4151,-129,Lockdown,0,15450,0
2020-11-23,23,11,2020,18662,125,United_Kingdom,UK,GBR,66647112,Europe,480.188849,0.000280012,3212,-354,Lockdown,180,18842,0
2020-11-22,22,11,2020,19875,340,United_Kingdom,UK,GBR,66647112,Europe,483.0546896,0.000298212,1213,215,Lockdown,-45,19830,0
2020-11-21,21,11,2020,20252,511,United_Kingdom,UK,GBR,66647112,Europe,490.6799262,0.000303869,377,171,Lockdown,0,20252,0
2020-11-20,20,11,2020,22915,501,United_Kingdom,UK,GBR,66647112,Europe,495.233762,0.000343826,2663,-10,Lockdown,0,22915,0
2020-11-19,19,11,2020,19609,529,United_Kingdom,UK,GBR,66647112,Europe,497.0688002,0.000294221,-3306,28,Lockdown,0,19609,0
2020-11-18,18,11,2020,20051,598,United_Kingdom,UK,GBR,66647112,Europe,505.4232508,0.000300853,442,69,Lockdown,0,20051,0
2020-11-17,17,11,2020,21363,213,United_Kingdom,UK,GBR,66647112,Europe,505.3737362,0.000320539,1312,-385,Lockdown,-17,21346,0
2020-11-16,16,11,2020,24962,168,United_Kingdom,UK,GBR,66647112,Europe,501.7531742,0.00037454,3599,-45,Lockdown,65,25027,0
2020-11-15,15,11,2020,26860,462,United_Kingdom,UK,GBR,66647112,Europe,499.1904225,0.000403018,1898,294,Lockdown,0,26860,0
2020-11-14,14,11,2020,27301,376,United_Kingdom,UK,GBR,66647112,Europe,491.7707462,0.000409635,441,-86,Lockdown,17,27318,0
2020-11-13,13,11,2020,33470,563,United_Kingdom,UK,GBR,66647112,Europe,487.4254716,0.000502197,6169,187,Lockdown,0,33470,0
2020-11-12,12,11,2020,22950,595,United_Kingdom,UK,GBR,66647112,Europe,471.8133923,0.000344351,-10520,32,Lockdown,0,22950,0
2020-11-11,11,11,2020,20412,532,United_Kingdom,UK,GBR,66647112,Europe,474.4391625,0.00030627,-2538,-63,Lockdown,0,20412,0
2020-11-10,10,11,2020,21350,194,United_Kingdom,UK,GBR,66647112,Europe,478.1497509,0.000320344,938,-338,Lockdown,-9,21341,0
2020-11-09,9,11,2020,20572,156,United_Kingdom,UK,GBR,66647112,Europe,477.4595484,0.000308671,-778,-38,Lockdown,73,20645,0
2020-11-08,8,11,2020,24957,413,United_Kingdom,UK,GBR,66647112,Europe,476.2862043,0.000374465,4385,257,Lockdown,1,24958,0
2020-11-07,7,11,2020,23287,355,United_Kingdom,UK,GBR,66647112,Europe,473.3678483,0.000349407,-1670,-58,Lockdown,13,23300,0
2020-11-06,6,11,2020,24138,378,United_Kingdom,UK,GBR,66647112,Europe,469.2326353,0.000362176,851,23,Lockdown,8,24146,0
2020-11-05,5,11,2020,25177,492,United_Kingdom,UK,GBR,66647112,Europe,464.881359,0.000377766,1039,114,Lockdown,0,25177,0
2020-11-04,4,11,2020,20018,397,United_Kingdom,UK,GBR,66647112,Europe,467.1470236,0.000300358,-5159,-95,Social Distancing and Wearing Masks Enforced,-3,20015,0
2020-11-03,3,11,2020,18950,136,United_Kingdom,UK,GBR,66647112,Europe,469.115601,0.000284333,-1068,-261,Social Distancing and Wearing Masks Enforced,-162,18788,1
2020-11-02,2,11,2020,23254,162,United_Kingdom,UK,GBR,66647112,Europe,468.8950363,0.000348912,4304,26,Social Distancing and Wearing Masks Enforced,-144,23110,0
2020-11-01,1,11,2020,21915,326,United_Kingdom,UK,GBR,66647112,Europe,459.4827755,0.000328821,-1339,164,Social Distancing and Wearing Masks Enforced,-81,21834,0
2020-10-31,31,10,2020,24405,274,United_Kingdom,UK,GBR,66647112,Europe,450.8642475,0.000366182,2490,-52,Social Distancing and Wearing Masks Enforced,-18,24387,0
2020-10-30,30,10,2020,23065,280,United_Kingdom,UK,GBR,66647112,Europe,437.7053877,0.000346077,-1340,6,Social Distancing and Wearing Masks Enforced,37,23102,0
2020-10-29,29,10,2020,24700,310,United_Kingdom,UK,GBR,66647112,Europe,431.573089,0.000370609,1635,30,Social Distancing and Wearing Masks Enforced,14,24714,0
2020-10-28,28,10,2020,22885,367,United_Kingdom,UK,GBR,66647112,Europe,424.106899,0.000343376,-1815,57,Social Distancing and Wearing Masks Enforced,34,22919,0
2020-10-27,27,10,2020,20890,102,United_Kingdom,UK,GBR,66647112,Europe,415.6249111,0.000313442,-1995,-265,Social Distancing and Wearing Masks Enforced,-230,20660,0
2020-10-26,26,10,2020,19790,151,United_Kingdom,UK,GBR,66647112,Europe,405.2448664,0.000296937,-1100,49,Social Distancing and Wearing Masks Enforced,15,19805,0
2020-10-25,25,10,2020,23012,174,United_Kingdom,UK,GBR,66647112,Europe,394.8648218,0.000345281,3222,23,Social Distancing and Wearing Masks Enforced,19,23031,0
2020-10-24,24,10,2020,20531,224,United_Kingdom,UK,GBR,66647112,Europe,383.0908682,0.000308055,-2481,50,Social Distancing and Wearing Masks Enforced,11,20542,0
2020-10-23,23,10,2020,21238,189,United_Kingdom,UK,GBR,66647112,Europe,373.087434,0.000318663,707,-35,Social Distancing and Wearing Masks Enforced,-27,21211,0
2020-10-22,22,10,2020,26687,191,United_Kingdom,UK,GBR,66647112,Europe,367.5388065,0.000400422,5449,2,Social Distancing and Wearing Masks Enforced,-191,26496,0
2020-10-21,21,10,2020,21330,241,United_Kingdom,UK,GBR,66647112,Europe,348.7457941,0.000320044,-5357,50,Social Distancing and Wearing Masks Enforced,136,21466,0
2020-10-20,20,10,2020,18803,80,United_Kingdom,UK,GBR,66647112,Europe,338.5608067,0.000282128,-2527,-161,Social Distancing and Wearing Masks Enforced,236,19039,0
2020-10-19,19,10,2020,16981,67,United_Kingdom,UK,GBR,66647112,Europe,329.2430736,0.00025479,-1822,-13,Social Distancing and Wearing Masks Enforced,-1,16980,0
2020-10-18,18,10,2020,16171,150,United_Kingdom,UK,GBR,66647112,Europe,338.2157054,0.000242636,-810,83,Social Distancing and Wearing Masks Enforced,36,16207,0
2020-10-17,17,10,2020,15635,136,United_Kingdom,UK,GBR,66647112,Europe,333.2642531,0.000234594,-536,-14,Social Distancing and Wearing Masks Enforced,-104,15531,0
2020-10-16,16,10,2020,18978,138,United_Kingdom,UK,GBR,66647112,Europe,320.2599387,0.000284754,3343,2,Social Distancing and Wearing Masks Enforced,179,19157,0
2020-10-15,15,10,2020,19724,137,United_Kingdom,UK,GBR,66647112,Europe,302.1586292,0.000295947,746,-1,Social Distancing and Wearing Masks Enforced,56,19780,0
2020-10-14,14,10,2020,17232,143,United_Kingdom,UK,GBR,66647112,Europe,283.2290768,0.000258556,-2492,6,Social Distancing and Wearing Masks Enforced,-173,17059,0
2020-10-13,13,10,2020,13972,50,United_Kingdom,UK,GBR,66647112,Europe,268.0911365,0.000209641,-3260,-93,Social Distancing and Wearing Masks Enforced,500,14472,0
2020-10-12,12,10,2020,12872,65,United_Kingdom,UK,GBR,66647112,Europe,253.1947671,0.000193137,-1100,15,Social Distancing and Wearing Masks Enforced,252,13124,1
2020-10-11,11,10,2020,15165,81,United_Kingdom,UK,GBR,66647112,Europe,242.4216071,0.000227542,2293,16,Social Distancing and Wearing Masks Enforced,171,15336,1
2020-10-10,10,10,2020,13864,87,United_Kingdom,UK,GBR,66647112,Europe,228.7315916,0.000208021,-1301,6,Social Distancing and Wearing Masks Enforced,-41,13823,8
2020-10-09,9,10,2020,17540,77,United_Kingdom,UK,GBR,66647112,Europe,218.2420148,0.000263177,3676,-10,Social Distancing and Wearing Masks Enforced,142,17682,3
2020-10-08,8,10,2020,14162,70,United_Kingdom,UK,GBR,66647112,Europe,201.8782149,0.000212492,-3378,-7,Social Distancing and Wearing Masks Enforced,-26,14136,0
2020-10-07,7,10,2020,14542,76,United_Kingdom,UK,GBR,66647112,Europe,189.8987011,0.000218194,380,6,Social Distancing and Wearing Masks Enforced,-78,14464,5
2020-10-06,6,10,2020,12593,19,United_Kingdom,UK,GBR,66647112,Europe,175.470469,0.00018895,-1949,-57,Social Distancing and Wearing Masks Enforced,95,12688,13
2020-10-05,5,10,2020,22961,33,United_Kingdom,UK,GBR,66647112,Europe,163.1293491,0.000344516,10368,14,Social Distancing and Wearing Masks Enforced,-449,22512,30
2020-10-04,4,10,2020,12871,49,United_Kingdom,UK,GBR,66647112,Europe,134.5279597,0.000193122,-10090,16,Social Distancing and Wearing Masks Enforced,-144,12727,25
2020-10-03,3,10,2020,6968,66,United_Kingdom,UK,GBR,66647112,Europe,121.8507413,0.000104551,-5903,17,Social Distancing and Wearing Masks Enforced,383,7351,59
2020-10-02,2,10,2020,6914,59,United_Kingdom,UK,GBR,66647112,Europe,117.8805767,0.00010374,-54,-7,Social Distancing and Wearing Masks Enforced,-7,6907,33
2020-10-01,1,10,2020,7108,71,United_Kingdom,UK,GBR,66647112,Europe,112.600528,0.000106651,194,12,Social Distancing and Wearing Masks Enforced,281,7389,46
2020-09-30,30,9,2020,7143,71,United_Kingdom,UK,GBR,66647112,Europe,107.9236562,0.000107176,35,0,Social Distancing and Wearing Masks Enforced,255,7398,101
2020-09-29,29,9,2020,4044,13,United_Kingdom,UK,GBR,66647112,Europe,101.8618781,6.06778E-05,-3099,-58,Social Distancing and Wearing Masks Enforced,221,4265,98
2020-09-28,28,9,2020,5692,17,United_Kingdom,UK,GBR,66647112,Europe,99.72675185,8.54051E-05,1648,4,Social Distancing and Wearing Masks Enforced,1,5693,196
2020-09-27,27,9,2020,6041,35,United_Kingdom,UK,GBR,66647112,Europe,96.18271231,9.06416E-05,349,18,Social Distancing and Wearing Masks Enforced,479,6520,151
2020-09-26,26,9,2020,6873,34,United_Kingdom,UK,GBR,66647112,Europe,92.36559268,0.000103125,832,-1,Social Distancing and Wearing Masks Enforced,509,7382,152
2020-09-25,25,9,2020,6634,40,United_Kingdom,UK,GBR,66647112,Europe,87.36312535,9.95392E-05,-239,6,Social Distancing and Wearing Masks Enforced,248,6882,71
2020-09-24,24,9,2020,6178,37,United_Kingdom,UK,GBR,66647112,Europe,81.78899035,9.26972E-05,-456,-3,Social Distancing and Wearing Masks Enforced,-285,5893,69
2020-09-23,23,9,2020,4926,37,United_Kingdom,UK,GBR,66647112,Europe,76.5089416,7.39117E-05,-1252,0,Social Distancing and Wearing Masks Enforced,-511,4415,83
2020-09-22,22,9,2020,4368,11,United_Kingdom,UK,GBR,66647112,Europe,72.80885629,6.55392E-05,-558,-26,Social Distancing and Wearing Masks Enforced,-18,4350,119
2020-09-21,21,9,2020,3899,18,United_Kingdom,UK,GBR,66647112,Europe,70.67823134,5.85022E-05,-469,7,Social Distancing and Wearing Masks Enforced,42,3941,145
2020-09-20,20,9,2020,4422,27,United_Kingdom,UK,GBR,66647112,Europe,69.3113304,6.63495E-05,523,9,Social Distancing and Wearing Masks Enforced,-64,4358,143
2020-09-19,19,9,2020,4322,27,United_Kingdom,UK,GBR,66647112,Europe,65.39668215,6.4849E-05,-100,0,Social Distancing and Wearing Masks Enforced,27,4349,180
2020-09-18,18,9,2020,3395,21,United_Kingdom,UK,GBR,66647112,Europe,61.82263381,5.09399E-05,-927,-6,Social Distancing and Wearing Masks Enforced,-25,3370,136
2020-09-17,17,9,2020,3991,20,United_Kingdom,UK,GBR,66647112,Europe,59.33190323,5.98826E-05,596,-1,Social Distancing and Wearing Masks Enforced,-93,3898,118
2020-09-16,16,9,2020,3103,27,United_Kingdom,UK,GBR,66647112,Europe,55.60631044,4.65587E-05,-888,7,Social Distancing and Wearing Masks Enforced,255,3358,182
2020-09-15,15,9,2020,2621,9,United_Kingdom,UK,GBR,66647112,Europe,52.89351473,3.93265E-05,-482,-18,Social Distancing and Wearing Masks Enforced,-23,2598,230
2020-09-14,14,9,2020,3330,5,United_Kingdom,UK,GBR,66647112,Europe,51.07047999,4.99647E-05,709,-4,Social Distancing and Wearing Masks Enforced,51,3381,314
2020-09-13,13,9,2020,3497,9,United_Kingdom,UK,GBR,66647112,Europe,48.64726922,5.24704E-05,167,4,Social Distancing and Wearing Masks Enforced,-48,3449,286
2020-09-12,12,9,2020,3539,6,United_Kingdom,UK,GBR,66647112,Europe,45.0627178,5.31006E-05,42,-3,Social Distancing and Wearing Masks Enforced,-91,3448,365
2020-09-11,11,9,2020,2919,14,United_Kingdom,UK,GBR,66647112,Europe,41.66722183,4.37978E-05,-620,8,Social Distancing and Wearing Masks Enforced,2,2921,300
2020-09-10,10,9,2020,2659,8,United_Kingdom,UK,GBR,66647112,Europe,39.571107,3.98967E-05,-260,-6,Social Distancing and Wearing Masks Enforced,73,2732,280
2020-09-09,9,9,2020,2460,32,United_Kingdom,UK,GBR,66647112,Europe,37.15389798,3.69108E-05,-199,24,Social Distancing and Wearing Masks Enforced,-340,2120,416
2020-09-08,8,9,2020,2948,3,United_Kingdom,UK,GBR,66647112,Europe,35.2393364,4.4233E-05,488,-29,Social Distancing and Wearing Masks Enforced,114,3062,475
2020-09-07,7,9,2020,2988,2,United_Kingdom,UK,GBR,66647112,Europe,32.27446675,4.48332E-05,40,-1,Social Distancing and Wearing Masks Enforced,-146,2842,486
2020-09-06,6,9,2020,1813,12,United_Kingdom,UK,GBR,66647112,Europe,29.35310985,2.7203E-05,-1175,10,Social Distancing and Wearing Masks Enforced,-118,1695,554
2020-09-05,5,9,2020,1940,10,United_Kingdom,UK,GBR,66647112,Europe,28.5653788,2.91085E-05,127,-2,Social Distancing and Wearing Masks Enforced,117,2057,601
2020-09-04,4,9,2020,1735,13,United_Kingdom,UK,GBR,66647112,Europe,27.20447962,2.60326E-05,-205,3,Social Distancing and Wearing Masks Enforced,26,1761,357
2020-09-03,3,9,2020,1508,10,United_Kingdom,UK,GBR,66647112,Europe,26.37473624,2.26266E-05,-227,-3,Social Distancing and Wearing Masks Enforced,48,1556,340
2020-09-02,2,9,2020,1295,3,United_Kingdom,UK,GBR,66647112,Europe,25.33042992,1.94307E-05,-213,-7,Social Distancing and Wearing Masks Enforced,72,1367,389
2020-09-01,1,9,2020,1406,2,United_Kingdom,UK,GBR,66647112,Europe,25.02133926,2.10962E-05,111,-1,Social Distancing and Wearing Masks Enforced,133,1539,738
2020-08-31,31,8,2020,1715,1,United_Kingdom,UK,GBR,66647112,Europe,23.98153426,2.57325E-05,309,-1,Social Distancing and Wearing Masks Enforced,-13,1702,654
2020-08-30,30,8,2020,1108,12,United_Kingdom,UK,GBR,66647112,Europe,22.96873719,1.66249E-05,-607,11,Social Distancing and Wearing Masks Enforced,-163,945,645
2020-08-29,29,8,2020,1276,9,United_Kingdom,UK,GBR,66647112,Europe,22.92222355,1.91456E-05,168,-3,Social Distancing and Wearing Masks Enforced,-83,1193,454
2020-08-28,28,8,2020,1522,12,United_Kingdom,UK,GBR,66647112,Europe,23.16829572,2.28367E-05,246,3,Social Distancing and Wearing Masks Enforced,111,1633,395
2020-08-27,27,8,2020,1048,16,United_Kingdom,UK,GBR,66647112,Europe,22.57862276,1.57246E-05,-474,4,Social Distancing and Wearing Masks Enforced,127,1175,464
2020-08-26,26,8,2020,1184,16,United_Kingdom,UK,GBR,66647112,Europe,22.5201056,1.77652E-05,136,0,Social Distancing and Wearing Masks Enforced,168,1352,437
2020-08-25,25,8,2020,972,4,United_Kingdom,UK,GBR,66647112,Europe,22.46608975,1.45843E-05,-212,-12,Social Distancing and Wearing Masks Enforced,-85,887,479
2020-08-24,24,8,2020,1041,6,United_Kingdom,UK,GBR,66647112,Europe,22.2320211,1.56196E-05,69,2,Social Distancing and Wearing Masks Enforced,-104,937,604
2020-08-23,23,8,2020,1288,18,United_Kingdom,UK,GBR,66647112,Europe,22.26353034,1.93257E-05,247,12,Social Distancing and Wearing Masks Enforced,-124,1164,623
2020-08-22,22,8,2020,1033,2,United_Kingdom,UK,GBR,66647112,Europe,21.46829708,1.54995E-05,-255,-16,Social Distancing and Wearing Masks Enforced,172,1205,688
2020-08-21,21,8,2020,1182,6,United_Kingdom,UK,GBR,66647112,Europe,21.22522578,1.77352E-05,149,4,Social Distancing and Wearing Masks Enforced,118,1300,532
2020-08-20,20,8,2020,812,16,United_Kingdom,UK,GBR,66647112,Europe,20.87712368,1.21836E-05,-370,10,Social Distancing and Wearing Masks Enforced,92,904,388
2020-08-19,19,8,2020,1089,12,United_Kingdom,UK,GBR,66647112,Europe,20.99565845,1.63398E-05,277,-4,Social Distancing and Wearing Masks Enforced,140,1229,461
2020-08-18,18,8,2020,713,3,United_Kingdom,UK,GBR,66647112,Europe,20.36697404,1.06981E-05,-376,-9,Social Distancing and Wearing Masks Enforced,38,751,707
2020-08-17,17,8,2020,1040,5,United_Kingdom,UK,GBR,66647112,Europe,20.68956866,1.56046E-05,327,2,Social Distancing and Wearing Masks Enforced,78,1118,722
2020-08-16,16,8,2020,1077,3,United_Kingdom,UK,GBR,66647112,Europe,20.24393795,1.61597E-05,37,-2,Social Distancing and Wearing Masks Enforced,59,1136,758
2020-08-15,15,8,2020,1440,11,United_Kingdom,UK,GBR,66647112,Europe,19.78480328,2.16063E-05,363,8,Social Distancing and Wearing Masks Enforced,-35,1405,780
2020-08-14,14,8,2020,1129,18,United_Kingdom,UK,GBR,66647112,Europe,18.94455682,1.694E-05,-311,7,Social Distancing and Wearing Masks Enforced,-96,1033,473
2020-08-13,13,8,2020,1009,20,United_Kingdom,UK,GBR,66647112,Europe,18.51993227,1.51394E-05,-120,2,Social Distancing and Wearing Masks Enforced,-81,928,300
2020-08-12,12,8,2020,1148,13,United_Kingdom,UK,GBR,66647112,Europe,18.150824,1.72251E-05,139,-7,Social Distancing and Wearing Masks Enforced,-80,1068,563
2020-08-11,11,8,2020,816,18,United_Kingdom,UK,GBR,66647112,Europe,16.53334956,1.22436E-05,-332,5,Social Distancing and Wearing Masks Enforced,29,845,742
2020-08-10,10,8,2020,1062,5,United_Kingdom,UK,GBR,66647112,Europe,15.86565371,1.59347E-05,246,-13,Social Distancing and Wearing Masks Enforced,-60,1002,798
2020-08-09,9,8,2020,758,3,United_Kingdom,UK,GBR,66647112,Europe,14.9038716,1.13733E-05,-304,-2,Social Distancing and Wearing Masks Enforced,48,806,636
2020-08-08,8,8,2020,871,12,United_Kingdom,UK,GBR,66647112,Europe,14.76733155,1.30688E-05,113,9,Social Distancing and Wearing Masks Enforced,37,908,532
2020-08-07,7,8,2020,950,18,United_Kingdom,UK,GBR,66647112,Europe,14.55726994,1.42542E-05,79,6,Social Distancing and Wearing Masks Enforced,212,1162,299
2020-08-06,6,8,2020,891,14,United_Kingdom,UK,GBR,66647112,Europe,14.29169204,1.33689E-05,-59,-4,Social Distancing and Wearing Masks Enforced,-120,771,261
2020-08-05,5,8,2020,670,18,United_Kingdom,UK,GBR,66647112,Europe,14.08163042,1.00529E-05,-221,4,Social Distancing and Wearing Masks Enforced,18,688,477
2020-08-04,4,8,2020,928,1,United_Kingdom,UK,GBR,66647112,Europe,14.26618456,1.39241E-05,258,-17,Social Distancing and Wearing Masks Enforced,90,1018,657
2020-08-03,3,8,2020,743,5,United_Kingdom,UK,GBR,66647112,Europe,13.4934579,1.11483E-05,-185,4,Social Distancing and Wearing Masks Enforced,37,780,745
2020-08-02,2,8,2020,771,13,United_Kingdom,UK,GBR,66647112,Europe,13.11834787,1.15684E-05,28,8,Social Distancing and Wearing Masks Enforced,-19,752,784
2020-08-01,1,8,2020,880,20,United_Kingdom,UK,GBR,66647112,Europe,12.81525897,1.32039E-05,109,7,Social Distancing and Wearing Masks Enforced,21,901,700
2020-07-31,31,7,2020,846,0,United_Kingdom,UK,GBR,66647112,Europe,12.55118151,1.26937E-05,-34,-20,Social Distancing and Wearing Masks Enforced,76,922,509
2020-07-30,30,7,2020,763,34,United_Kingdom,UK,GBR,66647112,Europe,12.44014894,1.14484E-05,-83,34,Social Distancing and Wearing Masks Enforced,389,1152,279
2020-07-29,29,7,2020,70,21,United_Kingdom,UK,GBR,66647112,Europe,12.32311462,1.05031E-06,-693,-13,Social Distancing and Wearing Masks Enforced,-19,51,455
2020-07-28,28,7,2020,371,3,United_Kingdom,UK,GBR,66647112,Europe,13.30740333,5.56663E-06,301,-18,Social Distancing and Wearing Masks Enforced,-158,213,754
2020-07-27,27,7,2020,421,8,United_Kingdom,UK,GBR,66647112,Europe,13.29239893,6.31685E-06,50,5,Social Distancing and Wearing Masks Enforced,-24,397,698
2020-07-26,26,7,2020,667,15,United_Kingdom,UK,GBR,66647112,Europe,13.32390817,1.00079E-05,246,7,Social Distancing and Wearing Masks Enforced,-47,620,657
2020-07-25,25,7,2020,731,32,United_Kingdom,UK,GBR,66647112,Europe,13.17086328,1.09682E-05,64,17,Social Distancing and Wearing Masks Enforced,312,1043,688
2020-07-24,24,7,2020,773,9,United_Kingdom,UK,GBR,66647112,Europe,13.14685624,1.15984E-05,42,-23,Social Distancing and Wearing Masks Enforced,114,887,358
2020-07-23,23,7,2020,751,17,United_Kingdom,UK,GBR,66647112,Europe,13.02682103,1.12683E-05,-22,8,Social Distancing and Wearing Masks Enforced,-44,707,259
2020-07-22,22,7,2020,793,25,United_Kingdom,UK,GBR,66647112,Europe,12.79575325,1.18985E-05,42,8,Social Distancing and Wearing Masks Enforced,-202,591,430
2020-07-21,21,7,2020,413,10,United_Kingdom,UK,GBR,66647112,Europe,12.66221408,6.19682E-06,-380,-15,Social Distancing and Wearing Masks Enforced,22,435,666
2020-07-20,20,7,2020,493,11,United_Kingdom,UK,GBR,66647112,Europe,12.87527658,7.39717E-06,80,1,Social Distancing and Wearing Masks Enforced,-138,355,808
2020-07-19,19,7,2020,569,9,United_Kingdom,UK,GBR,66647112,Europe,12.73723609,8.5375E-06,76,-2,Social Distancing and Wearing Masks Enforced,9,578,610
2020-07-18,18,7,2020,704,26,United_Kingdom,UK,GBR,66647112,Europe,12.75224049,1.05631E-05,135,17,Social Distancing and Wearing Masks Enforced,35,739,532
2020-07-17,17,7,2020,772,24,United_Kingdom,UK,GBR,66647112,Europe,12.5991956,1.15834E-05,68,-2,Social Distancing and Wearing Masks Enforced,64,836,403
2020-07-16,16,7,2020,685,26,United_Kingdom,UK,GBR,66647112,Europe,12.41764234,1.0278E-05,-87,2,Social Distancing and Wearing Masks Enforced,-61,624,210
2020-07-15,15,7,2020,726,44,United_Kingdom,UK,GBR,66647112,Europe,12.31561242,1.08932E-05,41,18,Social Distancing and Wearing Masks Enforced,267,993,491
2020-07-14,14,7,2020,361,10,United_Kingdom,UK,GBR,66647112,Europe,12.32161418,5.41659E-06,-365,-34,Social Distancing and Wearing Masks Enforced,-42,319,746
2020-07-13,13,7,2020,442,9,United_Kingdom,UK,GBR,66647112,Europe,12.44915159,6.63195E-06,81,-1,Social Distancing and Wearing Masks Enforced,42,484,800
2020-07-12,12,7,2020,565,17,United_Kingdom,UK,GBR,66647112,Europe,12.75974269,8.47749E-06,123,8,Social Distancing and Wearing Masks Enforced,45,610,774
2020-07-11,11,7,2020,715,34,United_Kingdom,UK,GBR,66647112,Europe,12.91878934,1.07281E-05,150,17,Social Distancing and Wearing Masks Enforced,-419,296,773
2020-07-10,10,7,2020,693,31,United_Kingdom,UK,GBR,66647112,Europe,12.92779198,1.0398E-05,-22,-3,Social Distancing and Wearing Masks Enforced,3,696,432
2020-07-09,9,7,2020,597,57,United_Kingdom,UK,GBR,66647112,Europe,13.05532939,8.95763E-06,-96,26,Social Distancing and Wearing Masks Enforced,-366,231,265
2020-07-08,8,7,2020,704,54,United_Kingdom,UK,GBR,66647112,Europe,13.48895658,1.05631E-05,107,-3,Social Distancing and Wearing Masks Enforced,-318,386,648
2020-07-07,7,7,2020,555,11,United_Kingdom,UK,GBR,66647112,Europe,13.77704108,8.32744E-06,-149,-43,Social Distancing and Wearing Masks Enforced,-103,452,900
2020-07-06,6,7,2020,401,19,United_Kingdom,UK,GBR,66647112,Europe,13.90307805,6.01676E-06,-154,8,Social Distancing and Wearing Masks Enforced,71,472,1046
2020-07-05,5,7,2020,579,32,United_Kingdom,UK,GBR,66647112,Europe,14.33220392,8.68755E-06,178,13,Social Distancing and Wearing Masks Enforced,77,656,1039
2020-07-04,4,7,2020,602,49,United_Kingdom,UK,GBR,66647112,Europe,14.94288305,9.03265E-06,23,17,Social Distancing and Wearing Masks Enforced,36,638,1146
2020-07-03,3,7,2020,651,41,United_Kingdom,UK,GBR,66647112,Europe,15.58057009,9.76787E-06,49,-8,Social Distancing and Wearing Masks Enforced,524,1175,780
2020-07-02,2,7,2020,617,97,United_Kingdom,UK,GBR,66647112,Europe,16.12372941,9.25772E-06,-34,56,Social Distancing and Wearing Masks Enforced,299,916,462
2020-07-01,1,7,2020,730,53,United_Kingdom,UK,GBR,66647112,Europe,16.85144287,1.09532E-05,113,-44,Social Distancing and Wearing Masks Enforced,260,990,677
2020-06-30,30,6,2020,446,21,United_Kingdom,UK,GBR,66647112,Europe,17.32108062,6.69196E-06,-284,-32,Social Distancing and Wearing Masks Enforced,16,462,937
2020-06-29,29,6,2020,649,31,United_Kingdom,UK,GBR,66647112,Europe,17.8852461,9.73786E-06,203,10,Social Distancing and Wearing Masks Enforced,7,656,1437
2020-06-28,28,6,2020,671,40,United_Kingdom,UK,GBR,66647112,Europe,18.24685217,1.0068E-05,22,9,Social Distancing and Wearing Masks Enforced,37,708,1293
2020-06-27,27,6,2020,721,77,United_Kingdom,UK,GBR,66647112,Europe,18.81851985,1.08182E-05,50,37,Social Distancing and Wearing Masks Enforced,-198,523,1329
2020-06-26,26,6,2020,778,99,United_Kingdom,UK,GBR,66647112,Europe,19.26265012,1.16734E-05,57,22,Social Distancing and Wearing Masks Enforced,176,954,1032
2020-06-25,25,6,2020,886,87,United_Kingdom,UK,GBR,66647112,Europe,19.89433541,1.32939E-05,108,-12,Social Distancing and Wearing Masks Enforced,31,917,418
2020-06-24,24,6,2020,896,94,United_Kingdom,UK,GBR,66647112,Europe,20.30245512,1.34439E-05,10,7,Social Distancing and Wearing Masks Enforced,-56,840,685
2020-06-23,23,6,2020,639,14,United_Kingdom,UK,GBR,66647112,Europe,20.60704446,9.58781E-06,-257,-80,Social Distancing and Wearing Masks Enforced,-187,452,1209
2020-06-22,22,6,2020,687,31,United_Kingdom,UK,GBR,66647112,Europe,20.73008055,1.0308E-05,48,17,Social Distancing and Wearing Masks Enforced,-330,357,1457
2020-06-21,21,6,2020,986,71,United_Kingdom,UK,GBR,66647112,Europe,20.90113072,1.47943E-05,299,40,Social Distancing and Wearing Masks Enforced,54,1040,1494
2020-06-20,20,6,2020,1027,84,United_Kingdom,UK,GBR,66647112,Europe,21.10218969,1.54095E-05,41,13,Social Distancing and Wearing Masks Enforced,-99,928,1209
2020-06-19,19,6,2020,1013,67,United_Kingdom,UK,GBR,66647112,Europe,21.42628476,1.51995E-05,-14,-17,Social Distancing and Wearing Masks Enforced,-341,672,698
2020-06-18,18,6,2020,1102,110,United_Kingdom,UK,GBR,66647112,Europe,21.94093572,1.65349E-05,89,43,Social Distancing and Wearing Masks Enforced,39,1141,321
2020-06-17,17,6,2020,1043,120,United_Kingdom,UK,GBR,66647112,Europe,22.51410384,1.56496E-05,-59,10,Social Distancing and Wearing Masks Enforced,88,1131,800
2020-06-16,16,6,2020,822,29,United_Kingdom,UK,GBR,66647112,Europe,23.111279,1.23336E-05,-221,-91,Social Distancing and Wearing Masks Enforced,-49,773,1309
2020-06-15,15,6,2020,890,27,United_Kingdom,UK,GBR,66647112,Europe,23.49689211,1.33539E-05,68,-2,Lockdown,-199,691,1698
2020-06-14,14,6,2020,1052,107,United_Kingdom,UK,GBR,66647112,Europe,23.84949553,1.57846E-05,162,80,Lockdown,-84,968,1279
2020-06-13,13,6,2020,1017,131,United_Kingdom,UK,GBR,66647112,Europe,24.56220459,1.52595E-05,-35,24,Lockdown,-233,784,1204
2020-06-12,12,6,2020,1199,76,United_Kingdom,UK,GBR,66647112,Europe,25.67703159,1.79903E-05,182,-55,Lockdown,-129,1070,755
2020-06-11,11,6,2020,1158,164,United_Kingdom,UK,GBR,66647112,Europe,26.6313115,1.73751E-05,-41,88,Lockdown,-156,1002,415
2020-06-10,10,6,2020,1099,195,United_Kingdom,UK,GBR,66647112,Europe,27.40253771,1.64898E-05,-59,31,Lockdown,-84,1015,727
2020-06-09,9,6,2020,721,47,United_Kingdom,UK,GBR,66647112,Europe,28.19026877,1.08182E-05,-378,-148,Lockdown,-297,424,804
2020-06-08,8,6,2020,801,54,United_Kingdom,UK,GBR,66647112,Europe,29.15505176,1.20185E-05,80,7,Lockdown,215,1016,684
2020-06-07,7,6,2020,1120,143,United_Kingdom,UK,GBR,66647112,Europe,30.24437128,1.68049E-05,319,89,Lockdown,263,1383,687
2020-06-06,6,6,2020,1243,258,United_Kingdom,UK,GBR,66647112,Europe,31.65778586,1.86505E-05,123,115,Lockdown,-28,1215,694
2020-06-05,5,6,2020,1356,130,United_Kingdom,UK,GBR,66647112,Europe,33.65487165,2.0346E-05,113,-128,Lockdown,216,1572,364
2020-06-04,4,6,2020,1484,254,United_Kingdom,UK,GBR,66647112,Europe,35.69847108,2.22665E-05,128,124,Lockdown,79,1563,315
2020-06-03,3,6,2020,1441,249,United_Kingdom,UK,GBR,66647112,Europe,38.05116117,2.16213E-05,-43,-5,Lockdown,-20,1421,251
2020-06-02,2,6,2020,1079,86,United_Kingdom,UK,GBR,66647112,Europe,39.77366641,1.61897E-05,-362,-163,Lockdown,-330,749,278
2020-06-01,1,6,2020,1125,60,United_Kingdom,UK,GBR,66647112,Europe,40.91250045,1.688E-05,46,-26,Lockdown,146,1271,533
2020-05-31,31,5,2020,1527,154,United_Kingdom,UK,GBR,66647112,Europe,42.34392032,2.29117E-05,402,94,Lockdown,246,1773,334
2020-05-30,30,5,2020,1760,274,United_Kingdom,UK,GBR,66647112,Europe,43.84285999,2.64077E-05,233,120,Lockdown,64,1824,369
2020-05-29,29,5,2020,1835,343,United_Kingdom,UK,GBR,66647112,Europe,45.145242,2.75331E-05,75,69,Lockdown,98,1933,308
2020-05-28,28,5,2020,1672,422,United_Kingdom,UK,GBR,66647112,Europe,47.35388984,2.50874E-05,-163,79,Lockdown,0,1672,106
2020-05-27,27,5,2020,1624,131,United_Kingdom,UK,GBR,66647112,Europe,49.94965123,2.43671E-05,-48,-291,Lockdown,-38,1586,170
2020-05-26,26,5,2020,1364,104,United_Kingdom,UK,GBR,66647112,Europe,52.89351473,2.0466E-05,-260,-27,Lockdown,-191,1173,312
2020-05-25,25,5,2020,1527,379,United_Kingdom,UK,GBR,66647112,Europe,54.34143943,2.29117E-05,163,275,Lockdown,5,1532,287
2020-05-24,24,5,2020,2062,220,United_Kingdom,UK,GBR,66647112,Europe,55.2867167,3.09391E-05,535,-159,Lockdown,68,2130,268
2020-05-23,23,5,2020,2574,291,United_Kingdom,UK,GBR,66647112,Europe,56.78865725,3.86213E-05,512,71,Lockdown,26,2600,284
2020-05-22,22,5,2020,2718,273,United_Kingdom,UK,GBR,66647112,Europe,58.5786823,4.0782E-05,144,-18,Lockdown,48,2766,191
2020-05-21,21,5,2020,3052,328,United_Kingdom,UK,GBR,66647112,Europe,60.24267038,4.57934E-05,334,55,Lockdown,1,3053,110
2020-05-20,20,5,2020,2589,500,United_Kingdom,UK,GBR,66647112,Europe,61.18794765,3.88464E-05,-463,172,Lockdown,0,2589,131
2020-05-19,19,5,2020,1838,146,United_Kingdom,UK,GBR,66647112,Europe,62.38829974,2.75781E-05,-751,-354,Lockdown,-307,1531,226
2020-05-18,18,5,2020,2079,67,United_Kingdom,UK,GBR,66647112,Europe,64.10480322,3.11941E-05,241,-79,Lockdown,-167,1912,297
2020-05-17,17,5,2020,2526,411,United_Kingdom,UK,GBR,66647112,Europe,65.83030935,3.79011E-05,447,344,Lockdown,0,2526,220
2020-05-16,16,5,2020,2628,350,United_Kingdom,UK,GBR,66647112,Europe,69.14778243,3.94316E-05,102,-61,Lockdown,-3,2625,262
2020-05-15,15,5,2020,3307,352,United_Kingdom,UK,GBR,66647112,Europe,72.6558114,4.96196E-05,679,2,Lockdown,55,3362,138
2020-05-14,14,5,2020,3402,447,United_Kingdom,UK,GBR,66647112,Europe,75.85925104,5.1045E-05,95,95,Lockdown,0,3402,42
2020-05-13,13,5,2020,3586,614,United_Kingdom,UK,GBR,66647112,Europe,77.85033506,5.38058E-05,184,167,Lockdown,0,3586,71
2020-05-12,12,5,2020,2329,187,United_Kingdom,UK,GBR,66647112,Europe,79.53082798,3.49453E-05,-1257,-427,Lockdown,42,2371,283
2020-05-11,11,5,2020,2157,217,United_Kingdom,UK,GBR,66647112,Europe,81.24733147,3.23645E-05,-172,30,Lockdown,47,2204,301
2020-05-10,10,5,2020,3063,275,United_Kingdom,UK,GBR,66647112,Europe,83.63453168,4.59585E-05,906,58,Lockdown,-44,3019,302
2020-05-09,9,5,2020,3767,579,United_Kingdom,UK,GBR,66647112,Europe,86.49587097,5.65216E-05,704,304,Lockdown,-1,3766,258
2020-05-08,8,5,2020,3827,458,United_Kingdom,UK,GBR,66647112,Europe,88.58298316,5.74218E-05,60,-121,Lockdown,0,3827,303
2020-05-07,7,5,2020,3682,647,United_Kingdom,UK,GBR,66647112,Europe,91.07371374,5.52462E-05,-145,189,Lockdown,0,3682,38
2020-05-06,6,5,2020,3389,726,United_Kingdom,UK,GBR,66647112,Europe,92.69118818,5.08499E-05,-293,79,Lockdown,0,3389,165
2020-05-05,5,5,2020,2982,272,United_Kingdom,UK,GBR,66647112,Europe,94.88933294,4.47431E-05,-407,-454,Lockdown,84,3066,333
2020-05-04,4,5,2020,3229,253,United_Kingdom,UK,GBR,66647112,Europe,96.19621627,4.84492E-05,247,-19,Lockdown,-65,3164,425
2020-05-03,3,5,2020,4737,584,United_Kingdom,UK,GBR,66647112,Europe,98.43487292,7.10758E-05,1508,331,Lockdown,1,4738,378
2020-05-02,2,5,2020,4966,698,United_Kingdom,UK,GBR,66647112,Europe,98.7634693,7.45119E-05,229,114,Lockdown,0,4966,380
2020-05-01,1,5,2020,5442,634,United_Kingdom,UK,GBR,66647112,Europe,99.25261278,8.1654E-05,476,-64,Lockdown,0,5442,260
2020-04-30,30,4,2020,4729,769,United_Kingdom,UK,GBR,66647112,Europe,98.68694686,7.09558E-05,-713,135,Lockdown,0,4729,73
2020-04-29,29,4,2020,4706,969,United_Kingdom,UK,GBR,66647112,Europe,98.08226949,7.06107E-05,-23,200,Lockdown,0,4706,196
2020-04-28,28,4,2020,3473,320,United_Kingdom,UK,GBR,66647112,Europe,97.29003711,5.21103E-05,-1233,-649,Lockdown,-2,3471,417
2020-04-27,27,4,2020,3748,364,United_Kingdom,UK,GBR,66647112,Europe,97.31404416,5.62365E-05,275,44,Lockdown,-26,3722,443
2020-04-26,26,4,2020,4970,815,United_Kingdom,UK,GBR,66647112,Europe,97.06046978,7.45719E-05,1222,451,Lockdown,0,4970,363
2020-04-25,25,4,2020,5158,1010,United_Kingdom,UK,GBR,66647112,Europe,96.07468063,7.73927E-05,188,195,Lockdown,0,5158,344
2020-04-24,24,4,2020,5487,682,United_Kingdom,UK,GBR,66647112,Europe,95.62454859,8.23291E-05,329,-328,Lockdown,0,5487,226
2020-04-23,23,4,2020,4760,847,United_Kingdom,UK,GBR,66647112,Europe,95.09039191,7.14209E-05,-727,165,Lockdown,0,4760,63
2020-04-22,22,4,2020,4854,1224,United_Kingdom,UK,GBR,66647112,Europe,96.12569559,7.28314E-05,94,377,Lockdown,,4854,174
2020-04-21,21,4,2020,3853,570,United_Kingdom,UK,GBR,66647112,Europe,96.76788396,5.7812E-05,-1001,-654,Lockdown,0,3853,314
2020-04-20,20,4,2020,4721,432,United_Kingdom,UK,GBR,66647112,Europe,96.37626909,7.08358E-05,868,-138,Lockdown,0,4721,351
2020-04-19,19,4,2020,4956,1105,United_Kingdom,UK,GBR,66647112,Europe,95.32446057,7.43618E-05,235,673,Lockdown,0,4956,333
2020-04-18,18,4,2020,5292,913,United_Kingdom,UK,GBR,66647112,Europe,95.25694077,7.94033E-05,336,-192,Lockdown,0,5292,298
2020-04-17,17,4,2020,5065,1036,United_Kingdom,UK,GBR,66647112,Europe,94.62075416,7.59973E-05,-227,123,Lockdown,0,5065,160
2020-04-16,16,4,2020,4326,880,United_Kingdom,UK,GBR,66647112,Europe,94.39268726,6.4909E-05,-739,-156,Lockdown,0,4326,57
2020-04-15,15,4,2020,4178,1076,United_Kingdom,UK,GBR,66647112,Europe,94.67477,6.26884E-05,-148,196,Lockdown,0,4178,174
2020-04-14,14,4,2020,3489,724,United_Kingdom,UK,GBR,66647112,Europe,94.81731181,5.23504E-05,-689,-352,Lockdown,0,3489,222
2020-04-13,13,4,2020,3579,657,United_Kingdom,UK,GBR,66647112,Europe,93.87053411,5.37008E-05,90,-67,Lockdown,0,3579,244
2020-04-12,12,4,2020,4313,843,United_Kingdom,UK,GBR,66647112,Europe,92.73470094,6.4714E-05,734,186,Lockdown,0,4313,202
2020-04-11,11,4,2020,4858,1122,United_Kingdom,UK,GBR,66647112,Europe,91.06020978,7.28914E-05,545,279,Lockdown,0,4858,179
2020-04-10,10,4,2020,5131,1116,United_Kingdom,UK,GBR,66647112,Europe,88.40293035,7.69876E-05,273,-6,Lockdown,0,5131,131
2020-04-09,9,4,2020,5450,1030,United_Kingdom,UK,GBR,66647112,Europe,84.74335692,8.1774E-05,319,-86,Lockdown,0,5450,48
2020-04-08,8,4,2020,5282,1105,United_Kingdom,UK,GBR,66647112,Europe,80.12950359,7.92532E-05,-168,75,Lockdown,0,5282,162
2020-04-07,7,4,2020,3592,567,United_Kingdom,UK,GBR,66647112,Europe,75.7122079,5.38958E-05,-1690,-538,Lockdown,0,3592,171
2020-04-06,6,4,2020,4020,599,United_Kingdom,UK,GBR,66647112,Europe,72.3902335,6.03177E-05,428,32,Lockdown,0,4020,213
2020-04-05,5,4,2020,4911,756,United_Kingdom,UK,GBR,66647112,Europe,68.15599152,7.36866E-05,891,157,Lockdown,0,4911,286
2020-04-04,4,4,2020,4868,736,United_Kingdom,UK,GBR,66647112,Europe,62.67038248,7.30414E-05,-43,-20,Lockdown,0,4868,262
2020-04-03,3,4,2020,4913,657,United_Kingdom,UK,GBR,66647112,Europe,56.94920434,7.37166E-05,45,-79,Lockdown,0,4913,171
2020-04-02,2,4,2020,4514,672,United_Kingdom,UK,GBR,66647112,Europe,51.07648175,6.77299E-05,-399,15,Lockdown,0,4514,67
2020-04-01,1,4,2020,4273,403,United_Kingdom,UK,GBR,66647112,Europe,45.45733355,6.41138E-05,-241,-269,Lockdown,7,4280,185
2020-03-31,31,3,2020,2858,374,United_Kingdom,UK,GBR,66647112,Europe,39.96272187,4.28826E-05,-1415,-29,Lockdown,-5,2853,236
2020-03-30,30,3,2020,2822,212,United_Kingdom,UK,GBR,66647112,Europe,36.33765856,4.23424E-05,-36,-162,Lockdown,49,2871,314
2020-03-29,29,3,2020,3197,292,United_Kingdom,UK,GBR,66647112,Europe,32.64507545,4.79691E-05,375,80,Lockdown,36,3233,254
2020-03-28,28,3,2020,3087,288,United_Kingdom,UK,GBR,66647112,Europe,28.5653788,4.63186E-05,-110,-4,Lockdown,-2,3085,291
2020-03-27,27,3,2020,2692,181,United_Kingdom,UK,GBR,66647112,Europe,24.65973319,4.03918E-05,-395,-107,Lockdown,125,2817,206
2020-03-26,26,3,2020,2375,191,United_Kingdom,UK,GBR,66647112,Europe,21.2297271,3.56355E-05,-317,10,Lockdown,-59,2316,106
2020-03-25,25,3,2020,2338,148,United_Kingdom,UK,GBR,66647112,Europe,18.05479583,3.50803E-05,-37,-43,Lockdown,22,2360,220
2020-03-24,24,3,2020,1378,76,United_Kingdom,UK,GBR,66647112,Europe,14.76883199,2.06761E-05,-960,-72,Lockdown,-193,1185,292
2020-03-23,23,3,2020,1198,36,United_Kingdom,UK,GBR,66647112,Europe,12.78675061,1.79753E-05,-180,-40,Lockdown,-377,821,330
2020-03-22,22,3,2020,1255,58,United_Kingdom,UK,GBR,66647112,Europe,11.07924977,1.88305E-05,57,22,Social Distancing and Wearing Masks Enforced,107,1362,389
2020-03-21,21,3,2020,1055,32,United_Kingdom,UK,GBR,66647112,Europe,9.31773308,1.58296E-05,-200,-26,Social Distancing and Wearing Masks Enforced,-120,935,437
2020-03-20,20,3,2020,999,46,United_Kingdom,UK,GBR,66647112,Europe,7.81129121,1.49894E-05,-56,14,Social Distancing and Wearing Masks Enforced,-614,385,279
2020-03-19,19,3,2020,769,34,United_Kingdom,UK,GBR,66647112,Europe,6.39637619,1.15384E-05,-230,-12,Social Distancing and Wearing Masks Enforced,-75,694,133
2020-03-18,18,3,2020,611,17,United_Kingdom,UK,GBR,66647112,Europe,5.32506195,9.16769E-06,-158,-17,Social Distancing and Wearing Masks Enforced,-265,346,266
2020-03-17,17,3,2020,442,22,United_Kingdom,UK,GBR,66647112,Europe,4.46831064,6.63195E-06,-169,5,Social Distancing and Wearing Masks Enforced,142,584,438
2020-03-16,16,3,2020,361,14,United_Kingdom,UK,GBR,66647112,Europe,3.8381258,5.41659E-06,-81,-8,Social Distancing and Wearing Masks Enforced,123,484,553
2020-03-15,15,3,2020,478,19,United_Kingdom,UK,GBR,66647112,Europe,3.30396912,7.1721E-06,117,5,Social Distancing and Wearing Masks Enforced,-77,401,540
2020-03-14,14,3,2020,484,1,United_Kingdom,UK,GBR,66647112,Europe,2.60476403,7.26213E-06,6,-18,Social Distancing and Wearing Masks Enforced,-305,179,630
2020-03-13,13,3,2020,406,2,United_Kingdom,UK,GBR,66647112,Europe,1.89055454,6.09179E-06,-78,1,Social Distancing and Wearing Masks Enforced,115,521,325
2020-03-12,12,3,2020,259,0,United_Kingdom,UK,GBR,66647112,Europe,1.28737761,3.88614E-06,-147,-2,Social Distancing and Wearing Masks Enforced,-56,203,167
2020-03-11,11,3,2020,148,4,United_Kingdom,UK,GBR,66647112,Europe,0.90626583,2.22065E-06,-111,4,Social Distancing and Wearing Masks Enforced,-100,48,378
2020-03-10,10,3,2020,57,1,United_Kingdom,UK,GBR,66647112,Europe,0.68720157,8.55251E-07,-91,-3,Social Distancing and Wearing Masks Enforced,-158,0,613
2020-03-09,9,3,2020,60,0,United_Kingdom,UK,GBR,66647112,Europe,0.60167648,9.00264E-07,3,-1,Social Distancing and Wearing Masks Enforced,79,139,689
2020-03-08,8,3,2020,81,1,United_Kingdom,UK,GBR,66647112,Europe,0.51165008,1.21536E-06,21,1,Social Distancing and Wearing Masks Enforced,211,292,633
2020-03-07,7,3,2020,51,1,United_Kingdom,UK,GBR,66647112,Europe,0.39161487,7.65224E-07,-30,0,Social Distancing and Wearing Masks Enforced,235,286,712
2020-03-06,6,3,2020,56,0,United_Kingdom,UK,GBR,66647112,Europe,0.31509242,8.40246E-07,5,-1,Social Distancing and Wearing Masks Enforced,-251,0,461
2020-03-05,5,3,2020,55,0,United_Kingdom,UK,GBR,66647112,Europe,0.23106778,8.25242E-07,-1,0,Social Distancing and Wearing Masks Enforced,-305,0,156
2020-03-04,4,3,2020,40,0,United_Kingdom,UK,GBR,66647112,Europe,0.14854357,6.00176E-07,-15,0,Social Distancing and Wearing Masks Enforced,218,258,374
2020-03-03,3,3,2020,22,0,United_Kingdom,UK,GBR,66647112,Europe,0.08852597,3.30E-07,-18,0,Social Distancing and Wearing Masks Enforced,412,434,786
2020-03-02,2,3,2020,5,0,United_Kingdom,UK,GBR,66647112,Europe,0.05551628,7.5022E-08,-17,0,Social Distancing and Wearing Masks Enforced,45,50,831
2020-03-01,1,3,2020,12,0,United_Kingdom,UK,GBR,66647112,Europe,0.04801408,1.80053E-07,7,0,Social Distancing and Wearing Masks Enforced,3,15,834
2020-02-29,29,2,2020,8,0,United_Kingdom,UK,GBR,66647112,Europe,0.0300088,1.20035E-07,-4,0,Social Distancing and Wearing Masks Enforced,-51,0,783
2020-02-28,28,2,2020,4,0,United_Kingdom,UK,GBR,66647112,Europe,0.01800528,6.00176E-08,-4,0,Social Distancing and Wearing Masks Enforced,-274,0,509
2020-02-27,27,2,2020,5,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,7.5022E-08,1,0,Social Distancing and Wearing Masks Enforced,-348,0,161
2020-02-26,26,2,2020,2,0,United_Kingdom,UK,GBR,66647112,Europe,0.00600176,3.00088E-08,-3,0,Social Distancing and Wearing Masks Enforced,476,478,637
2020-02-25,25,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,0,-2,0,Social Distancing and Wearing Masks Enforced,279,279,916
2020-02-24,24,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00450132,0,0,0,Social Distancing and Wearing Masks Enforced,52,52,968
2020-02-23,23,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.01050308,1.50044E-08,1,0,Social Distancing and Wearing Masks Enforced,-66,0,902
2020-02-22,22,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00900264,0,-1,0,Social Distancing and Wearing Masks Enforced,277,277,1179
2020-02-21,21,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00900264,0,0,0,Social Distancing and Wearing Masks Enforced,-482,0,697
2020-02-20,20,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01050308,0,0,0,Social Distancing and Wearing Masks Enforced,-376,0,321
2020-02-19,19,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01050308,0,0,0,Social Distancing and Wearing Masks Enforced,450,450,771
2020-02-18,18,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,0,0,0,Social Distancing and Wearing Masks Enforced,519,519,1290
2020-02-17,17,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,0,0,0,Social Distancing and Wearing Masks Enforced,280,280,1570
2020-02-16,16,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,0,0,0,Social Distancing and Wearing Masks Enforced,96,96,1666
2020-02-15,15,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,0,0,0,Social Distancing and Wearing Masks Enforced,202,202,1868
2020-02-14,14,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.0150044,0,0,0,Social Distancing and Wearing Masks Enforced,-391,0,1477
2020-02-13,13,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.0150044,1.50044E-08,1,0,Social Distancing and Wearing Masks Enforced,-963,0,514
2020-02-12,12,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.01350396,0,-1,0,Social Distancing and Wearing Masks Enforced,554,554,1068
2020-02-11,11,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.01350396,1.50E-08,1,0,Social Distancing and Wearing Masks Enforced,1347,1348,2415
2020-02-10,10,2,2020,4,0,United_Kingdom,UK,GBR,66647112,Europe,0.01200352,6.00176E-08,3,0,Social Distancing and Wearing Masks Enforced,975,979,3390
2020-02-09,9,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00600176,0,-4,0,Social Distancing and Wearing Masks Enforced,-128,0,3262
2020-02-08,8,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00600176,0,0,0,Social Distancing and Wearing Masks Enforced,793,793,4055
2020-02-07,7,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.00600176,1.50044E-08,1,0,Social Distancing and Wearing Masks Enforced,-1068,0,2987
2020-02-06,6,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00450132,0,-1,0,Social Distancing and Wearing Masks Enforced,-1690,0,1297
2020-02-05,5,2,2020,1,0,United_Kingdom,UK,GBR,66647112,Europe,0.00450132,1.50044E-08,1,0,Social Distancing and Wearing Masks Enforced,273,274,1570
2020-02-04,4,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,0,-1,0,Social Distancing and Wearing Masks Enforced,2038,2038,3608
2020-02-03,3,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,0,0,0,Social Distancing and Wearing Masks Enforced,875,875,4483
2020-02-02,2,2,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,0,0,0,Social Distancing and Wearing Masks Enforced,261,261,4744
2020-02-01,1,2,2020,2,0,United_Kingdom,UK,GBR,66647112,Europe,0.00300088,3.00088E-08,2,0,Social Distancing and Wearing Masks Enforced,-291,0,4453
2020-01-31,31,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,-2,0,Social Distancing and Wearing Masks Enforced,-1,0,4452
2020-01-30,30,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,-2355,0,2097
2020-01-29,29,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,1628,1628,3725
2020-01-28,28,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,773,773,4498
2020-01-27,27,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,1211,1211,5709
2020-01-26,26,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,-144,0,5565
2020-01-25,25,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,1165,1165,6730
2020-01-24,24,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,-3217,0,3513
2020-01-23,23,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,-1931,0,1582
2020-01-22,22,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,962,962,2544
2020-01-21,21,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,1916,1916,4460
2020-01-20,20,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,501,501,4961
2020-01-19,19,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,2661,2661,7622
2020-01-18,18,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,-2163,0,5459
2020-01-17,17,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,-966,0,4493
2020-01-16,16,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,-2071,0,2422
2020-01-15,15,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,1453,1453,3875
2020-01-14,14,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,1800,1800,5675
2020-01-13,13,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,0,0,0,0,Social Distancing and Wearing Masks Enforced,389,389,6064
2020-01-12,12,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,836,836,6900
2020-01-11,11,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,-437,0,6463
2020-01-10,10,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,-2638,0,3825
2020-01-09,9,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,-1071,0,2754
2020-01-08,8,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,733,733,3487
2020-01-07,7,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,2325,2325,5812
2020-01-06,6,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,736,736,6548
2020-01-05,5,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,440,440,6988
2020-01-04,4,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,355,355,7343
2020-01-03,3,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,-2480,0,4863
2020-01-02,2,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,-3063,0,1800
2020-01-01,1,1,2020,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,1519,1519,3319
2019-12-31,31,12,2019,0,0,United_Kingdom,UK,GBR,66647112,Europe,,0,0,0,Social Distancing and Wearing Masks Enforced,-3319,0,0
"""
        |> fromCSV
```


