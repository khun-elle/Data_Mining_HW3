# What causes what?

### Why can’t I just get data from a few different cities and run the regression of “Crime” on “Police” to understand how more cops in the streets affect crime?

The relationship between number of polices and crime rate suffers from
endogeneity, x (number of polices) correlates with e (could be city’s
specific characteristics). Some cities that have high crime rate to
begin with will typically hire polices. So the least square estimator
can be biased. To control for heterogeneity across cities, we need
cities fixed effect.

Another problem is simultaneity. It is hard distinguish whether the
change in crime rate causes the change in number of polices or vice
versa. For example, high crime rates likely to increase marginal
productivity of police. Cities with an inordinate amount of crime,
therefore, tend to employ a large police force. Even if polices reduce
crime, the crime rate will still be high. Thus, simple linear regression
by using data from different cities will generate biased estimator.

\#\#\#How were the researchers from UPenn able to isolate this effect?
Briefly describe their approach and discuss their result in the “Table
2” below, from the researchers’ paper

They wanted to isolate the effect of number of polices on crime by
finding a variable unrelated to crime, but causes change in number of
polices, and they found the terrorism alert level was a great case. By
law, since Washington, D.C., is likely to be a terrorism target, when
the terror alert level goes to orange, then extra police are put on the
Mall and other parts of Washington to protect against terrorists. It has
nothing to do with street crime or things like that. From table 2 column
1, the coefficient on the alert level is statistically significant at
the 5 percent level and indicates that on high-alert days, total crimes
decrease by an average of seven crimes per day, or approximately 6.6
percent.

Also, they considered that it was possible that tourists were less
likely to visit Washington or to go out on high-alert day, which mean
there were going to be less victims on the street. From table 2 column
2, they verify that high-alert levels are not being confounded with
tourist levels by including logged midday Metro ridership directly in
the regression.

\#\#\#Why did they have to control for Metro ridership? What was that
trying to capture?

So there are less victims. But is it because there are less tourists?
and therefore less victims? They controlled for Metro ridership so that
they can check the hypothesis of whether high-alert levels are
confounded with tourist levels or not. By controlling for tourism, the
researchers are trying to show that it is the increased police presence,
rather than the decrease in people out-and-about that leads to the
observed decrease in crime. Controlling for ridership worked because
ridership is related to number of tourists but unrelated to crime rate.
They are trying to capture causal effect of number of polices on crime
rate.

\#\#\#Below I am showing you “Table 4” from the researchers’ paper. Just
focus on the first column of the table. Can you describe the model being
estimated here? What is the conclusion?

D.C. is split into seven police districts. Table 4 uses this fact to
find more variation in policing response to the high-alert days.
District 1 includes the National Mall. Given that District 1 includes
important targets, the researchers hypothesize that increased police
attention will be given to District 1 relative to other. Hence, one
would expect to see a larger effect of high-alert days on crime in
District 1 than other districts. Including district fixed effects in the
model (as well as day of the week fixed effects and weather effects),
the researchers find a statistically significant decrease in crime of
2.621 crimes per day (or 15%) for District 1 and a decrease in crime of
.571 for other districts, but this not statistically significant. This
extra dimension of geographic variation strengthens the researchers
conclusion that increased police presence reduces crime. In short, daily
crime drops on high-alert days in DC. Moreover, daily crime drops more
in police districts that greatly increase their police presence on high
alert days relative to those that don’t increase their police presence
by that much. Additionally, it does not appear the effects are driven by
tourism or some other factor relating to people being out-and-about,
since the researchers control for Metro ridership and still find
statistically significant effects of police on crime.

\#\#Tree modeling: dengue cases

    ## $city
    ## [1] "character"
    ## 
    ## $season
    ## [1] "character"
    ## 
    ## $total_cases
    ## [1] "numeric"
    ## 
    ## $ndvi_ne
    ## [1] "numeric"
    ## 
    ## $ndvi_nw
    ## [1] "numeric"
    ## 
    ## $ndvi_se
    ## [1] "numeric"
    ## 
    ## $ndvi_sw
    ## [1] "numeric"
    ## 
    ## $precipitation_amt
    ## [1] "numeric"
    ## 
    ## $air_temp_k
    ## [1] "numeric"
    ## 
    ## $avg_temp_k
    ## [1] "numeric"
    ## 
    ## $dew_point_temp_k
    ## [1] "numeric"
    ## 
    ## $max_air_temp_k
    ## [1] "numeric"
    ## 
    ## $min_air_temp_k
    ## [1] "numeric"
    ## 
    ## $precip_amt_kg_per_m2
    ## [1] "numeric"
    ## 
    ## $relative_humidity_percent
    ## [1] "numeric"
    ## 
    ## $specific_humidity
    ## [1] "numeric"
    ## 
    ## $tdtr_k
    ## [1] "numeric"

![](HW3_files/figure-markdown_github/setup%201.1-1.png)

    ## [1] 0.0363064

![](HW3_files/figure-markdown_github/setup%201.1-2.png)![](HW3_files/figure-markdown_github/setup%201.1-3.png)

    ## [1] 207
    ## attr(,"smoother")
    ## Call:
    ## loess(formula = object$oobag.improve ~ x, enp.target = min(max(4, 
    ##     length(x)/10), 50))
    ## 
    ## Number of Observations: 10000 
    ## Equivalent Number of Parameters: 39.99 
    ## Residual Standard Error: 0.1252

    ## [1] 30.0531

    ## [1] 28.85954

    ## [1] 27.36282

    ## [1] 28.05037

<table class="table table-striped" style="width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
**Table 2.1 RMSE per Model**
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
RMSE
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
RMSE CART
</td>
<td style="text-align:right;">
30.05310
</td>
</tr>
<tr>
<td style="text-align:left;">
RMSE CART Prune
</td>
<td style="text-align:right;">
28.85954
</td>
</tr>
<tr>
<td style="text-align:left;">
RMSE Random Forest
</td>
<td style="text-align:right;">
27.36282
</td>
</tr>
<tr>
<td style="text-align:left;">
RMSE Gradient Boosting
</td>
<td style="text-align:right;">
28.05037
</td>
</tr>
</tbody>
</table>

![](HW3_files/figure-markdown_github/setup%201.1-4.png)![](HW3_files/figure-markdown_github/setup%201.1-5.png)![](HW3_files/figure-markdown_github/setup%201.1-6.png)

\#\#Predictive model building: green certification To build the most
accurate predictive model possible, we compared multiple statistical
methods: a hand-built linear model, a linear model using forward
selection, Lasso model, and two tree-based models using bagging and
random forest, respectively. We first compared the two linear models
with Lasso by using train/test splits with a loop of 100 to calculate
the RMSE, and we concluded that Lasso did not result in an improved
prediction accuracy. Therefore, we included the tree-based models to try
and improve our predictions. In order to decide which model performs
best, out of the 5 previously described models, we employed
Leave-one-out cross validation (LOOCV) RMSE, and chose the one that
decreased the RMSE the most.

Before starting fitting regression models, we needed to omit all missing
variables in the dataset. Total observations got reduced from 7,894 to
7,820. In addition, we included green_ratings instead of LEED and
EnergyStar in all of the models, and used cd_total_07 and hd_total07
separately instead of total_dd_07. Since cluster rent is most likely a
function of Rent, we omitted it to avoid regressing the target variable
on a variable that is a part of the target variable itself.

### First Model: Hand-Built Linear Model

We built a multiple linear regression model with variables that, based
on our knowledge and intuition, can affect rent. The model and the
selected variables are shown below:

Rent<sub>β</sub> = β<sub>1</sub> cluster + β<sub>2</sub> size +
β<sub>3</sub> empl_gr + β<sub>4</sub> leasing_rate + β<sub>5</sub>
stories + β<sub>6</sub> stories\* size + β<sub>7</sub> cd_total_07\*
Electricity_Costs + β<sub>8</sub> age + β<sub>9</sub> renovated +
β<sub>10</sub> class_a + β<sub>11</sub> class_b + β<sub>12</sub>
green_rating + β<sub>13</sub> net + β<sub>14</sub> amenities +
β<sub>15</sub> cd_total_07 + β<sub>16</sub> hd_total07 + β<sub>17 </sub>
Precipitation + β<sub>18</sub> Gas_Costs + β<sub>19</sub>
Electricity_Costs + β<sub>20</sub> Electricity_Costs\*hd_total07

    ## Start:  AIC=42461.98
    ## Rent ~ 1
    ## 
    ##                     Df Sum of Sq     RSS   AIC
    ## + Electricity_Costs  1    279851 1503679 41129
    ## + class_a            1     78603 1704927 42112
    ## + leasing_rate       1     56936 1726595 42210
    ## + cluster            1     51722 1731808 42234
    ## + cd_total_07        1     50626 1732905 42239
    ## + hd_total07         1     44133 1739397 42268
    ## + size               1     33702 1749829 42315
    ## + renovated          1     27391 1756139 42343
    ## + class_b            1     26492 1757039 42347
    ## + stories            1     23957 1759574 42358
    ## + age                1     19116 1764415 42380
    ## + Precipitation      1      8528 1775002 42427
    ## + amenities          1      6525 1777006 42435
    ## + net                1      4614 1778916 42444
    ## + green_rating       1      1794 1781737 42456
    ## + empl_gr            1      1173 1782357 42459
    ## <none>                           1783530 42462
    ## + Gas_Costs          1         2 1783528 42464
    ## 
    ## Step:  AIC=41129.27
    ## Rent ~ Electricity_Costs
    ## 
    ##                 Df Sum of Sq     RSS   AIC
    ## + class_a        1     60393 1443286 40811
    ## + size           1     57485 1446194 40826
    ## + leasing_rate   1     45460 1458220 40891
    ## + Precipitation  1     42165 1461515 40909
    ## + stories        1     41986 1461693 40910
    ## + cd_total_07    1     39276 1464404 40924
    ## + hd_total07     1     33204 1470475 40957
    ## + amenities      1     25027 1478652 41000
    ## + class_b        1     16728 1486952 41044
    ## + Gas_Costs      1     15225 1488454 41052
    ## + cluster        1     12567 1491112 41066
    ## + renovated      1     11203 1492476 41073
    ## + age            1     10534 1493146 41076
    ## + net            1      8188 1495492 41089
    ## + green_rating   1       911 1502768 41127
    ## + empl_gr        1       773 1502907 41127
    ## <none>                       1503679 41129
    ## 
    ## Step:  AIC=40810.71
    ## Rent ~ Electricity_Costs + class_a
    ## 
    ##                             Df Sum of Sq     RSS   AIC
    ## + cd_total_07                1     48041 1395244 40548
    ## + hd_total07                 1     40297 1402989 40591
    ## + Precipitation              1     35007 1408279 40621
    ## + leasing_rate               1     27678 1415608 40661
    ## + size                       1     20583 1422703 40700
    ## + Gas_Costs                  1     20526 1422759 40701
    ## + cluster                    1     14938 1428348 40731
    ## + net                        1     14113 1429172 40736
    ## + stories                    1     10548 1432738 40755
    ## + class_b                    1      6918 1436368 40775
    ## + renovated                  1      4306 1438980 40789
    ## + amenities                  1      3702 1439584 40793
    ## + class_a:Electricity_Costs  1      1737 1441549 40803
    ## + green_rating               1      1020 1442265 40807
    ## + age                        1       603 1442683 40809
    ## <none>                                   1443286 40811
    ## + empl_gr                    1       357 1442929 40811
    ## 
    ## Step:  AIC=40547.98
    ## Rent ~ Electricity_Costs + class_a + cd_total_07
    ## 
    ##                                 Df Sum of Sq     RSS   AIC
    ## + cd_total_07:Electricity_Costs  1     54208 1341037 40240
    ## + Precipitation                  1     52328 1342916 40251
    ## + leasing_rate                   1     22371 1372874 40424
    ## + size                           1     22075 1373170 40425
    ## + empl_gr                        1     15473 1379771 40463
    ## + hd_total07                     1     15160 1380084 40465
    ## + stories                        1     10167 1385077 40493
    ## + cluster                        1      9561 1385684 40496
    ## + net                            1      9232 1386013 40498
    ## + renovated                      1      7139 1388106 40510
    ## + class_b                        1      6227 1389017 40515
    ## + amenities                      1      4740 1390504 40523
    ## + class_a:cd_total_07            1      2670 1392574 40535
    ## + class_a:Electricity_Costs      1      2486 1392758 40536
    ## + Gas_Costs                      1      1732 1393513 40540
    ## + green_rating                   1       569 1394676 40547
    ## + age                            1       500 1394745 40547
    ## <none>                                       1395244 40548
    ## 
    ## Step:  AIC=40240.1
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Electricity_Costs:cd_total_07
    ## 
    ##                             Df Sum of Sq     RSS   AIC
    ## + Precipitation              1    109259 1231778 39578
    ## + hd_total07                 1     64064 1276973 39859
    ## + Gas_Costs                  1     36944 1304093 40024
    ## + size                       1     24209 1316828 40100
    ## + leasing_rate               1     24058 1316979 40101
    ## + stories                    1     16352 1324685 40146
    ## + class_a:Electricity_Costs  1      8137 1332900 40195
    ## + class_b                    1      6750 1334287 40203
    ## + renovated                  1      5313 1335724 40211
    ## + net                        1      4909 1336128 40213
    ## + cluster                    1      3746 1337291 40220
    ## + amenities                  1      3107 1337929 40224
    ## + empl_gr                    1      1876 1339161 40231
    ## + class_a:cd_total_07        1      1604 1339432 40233
    ## + green_rating               1      1382 1339655 40234
    ## <none>                                   1341037 40240
    ## + age                        1        61 1340975 40242
    ## 
    ## Step:  AIC=39577.52
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     Electricity_Costs:cd_total_07
    ## 
    ##                                   Df Sum of Sq     RSS   AIC
    ## + Precipitation:Electricity_Costs  1     76716 1155062 39077
    ## + cd_total_07:Precipitation        1     40037 1191741 39321
    ## + hd_total07                       1     34754 1197024 39356
    ## + empl_gr                          1     25171 1206607 39418
    ## + leasing_rate                     1     20965 1210813 39445
    ## + size                             1     13409 1218369 39494
    ## + class_b                          1     11495 1220283 39506
    ## + class_a:Electricity_Costs        1      9310 1222468 39520
    ## + renovated                        1      8332 1223446 39526
    ## + stories                          1      6629 1225149 39537
    ## + cluster                          1      6536 1225242 39538
    ## + net                              1      4147 1227631 39553
    ## + age                              1      3301 1228477 39559
    ## + amenities                        1      2378 1229400 39564
    ## + class_a:cd_total_07              1      1093 1230685 39573
    ## + Gas_Costs                        1       382 1231396 39577
    ## <none>                                         1231778 39578
    ## + green_rating                     1       296 1231482 39578
    ## + class_a:Precipitation            1         6 1231772 39579
    ## 
    ## Step:  AIC=39076.66
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation
    ## 
    ##                             Df Sum of Sq     RSS   AIC
    ## + cd_total_07:Precipitation  1     35024 1120038 38838
    ## + leasing_rate               1     15883 1139179 38970
    ## + empl_gr                    1     15869 1139193 38970
    ## + cluster                    1      9212 1145850 39016
    ## + class_b                    1      8274 1146788 39022
    ## + age                        1      8060 1147002 39024
    ## + size                       1      7466 1147596 39028
    ## + net                        1      4808 1150254 39046
    ## + class_a:Electricity_Costs  1      4583 1150479 39048
    ## + renovated                  1      4233 1150829 39050
    ## + hd_total07                 1      3509 1151553 39055
    ## + amenities                  1      1939 1153123 39066
    ## + stories                    1      1765 1153298 39067
    ## + class_a:cd_total_07        1      1652 1153410 39067
    ## + Gas_Costs                  1      1205 1153857 39070
    ## + class_a:Precipitation      1       745 1154317 39074
    ## <none>                                   1155062 39077
    ## + green_rating               1        10 1155052 39079
    ## 
    ## Step:  AIC=38837.87
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation
    ## 
    ##                             Df Sum of Sq     RSS   AIC
    ## + leasing_rate               1   15510.5 1104527 38731
    ## + cluster                    1    8863.1 1111175 38778
    ## + age                        1    8648.3 1111390 38779
    ## + class_b                    1    7736.5 1112301 38786
    ## + size                       1    6985.2 1113053 38791
    ## + hd_total07                 1    4637.5 1115400 38807
    ## + class_a:Electricity_Costs  1    4443.8 1115594 38809
    ## + renovated                  1    4375.2 1115663 38809
    ## + net                        1    4195.5 1115843 38811
    ## + amenities                  1    2344.9 1117693 38823
    ## + stories                    1    1694.8 1118343 38828
    ## + class_a:cd_total_07        1    1113.4 1118925 38832
    ## <none>                                   1120038 38838
    ## + class_a:Precipitation      1     234.8 1119803 38838
    ## + empl_gr                    1      62.3 1119976 38839
    ## + Gas_Costs                  1      22.8 1120015 38840
    ## + green_rating               1       3.0 1120035 38840
    ## 
    ## Step:  AIC=38730.82
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + cluster                         1    8482.1 1096045 38673
    ## + age                             1    7440.6 1097087 38680
    ## + renovated                       1    4947.0 1099580 38698
    ## + class_a:Electricity_Costs       1    4894.3 1099633 38698
    ## + size                            1    4877.3 1099650 38698
    ## + class_b                         1    4795.1 1099732 38699
    ## + hd_total07                      1    4491.4 1100036 38701
    ## + net                             1    4360.4 1100167 38702
    ## + leasing_rate:class_a            1    2376.9 1102151 38716
    ## + class_a:cd_total_07             1    1614.5 1102913 38721
    ## + leasing_rate:Precipitation      1    1392.3 1103135 38723
    ## + amenities                       1    1000.8 1103527 38726
    ## + leasing_rate:cd_total_07        1     876.4 1103651 38727
    ## + stories                         1     682.6 1103845 38728
    ## + leasing_rate:Electricity_Costs  1     492.2 1104035 38729
    ## <none>                                        1104527 38731
    ## + class_a:Precipitation           1     244.9 1104283 38731
    ## + empl_gr                         1      50.3 1104477 38732
    ## + Gas_Costs                       1      42.7 1104485 38733
    ## + green_rating                    1      28.3 1104499 38733
    ## 
    ## Step:  AIC=38672.53
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + age                             1    6400.7 1089645 38629
    ## + size                            1    6081.0 1089964 38631
    ## + class_a:Electricity_Costs       1    5662.7 1090383 38634
    ## + class_b                         1    4589.5 1091456 38642
    ## + net                             1    4536.2 1091509 38642
    ## + hd_total07                      1    4460.1 1091585 38643
    ## + renovated                       1    4121.5 1091924 38645
    ## + cluster:class_a                 1    3725.0 1092320 38648
    ## + leasing_rate:class_a            1    2448.8 1093597 38657
    ## + class_a:cd_total_07             1    1828.4 1094217 38661
    ## + leasing_rate:Precipitation      1    1353.2 1094692 38665
    ## + amenities                       1    1193.5 1094852 38666
    ## + stories                         1    1145.0 1094900 38666
    ## + leasing_rate:cd_total_07        1     777.9 1095267 38669
    ## + cluster:Electricity_Costs       1     569.0 1095476 38670
    ## + leasing_rate:Electricity_Costs  1     491.4 1095554 38671
    ## + class_a:Precipitation           1     331.9 1095713 38672
    ## + cluster:Precipitation           1     286.7 1095759 38672
    ## <none>                                        1096045 38673
    ## + green_rating                    1      52.2 1095993 38674
    ## + cluster:cd_total_07             1      14.3 1096031 38674
    ## + empl_gr                         1      10.1 1096035 38674
    ## + Gas_Costs                       1       1.5 1096044 38675
    ## + cluster:leasing_rate            1       1.3 1096044 38675
    ## 
    ## Step:  AIC=38628.73
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + class_a:Electricity_Costs       1    6722.4 1082922 38582
    ## + size                            1    6060.8 1083584 38587
    ## + net                             1    4699.0 1084946 38597
    ## + cluster:class_a                 1    4418.3 1085226 38599
    ## + hd_total07                      1    3383.6 1086261 38606
    ## + leasing_rate:class_a            1    2750.9 1086894 38611
    ## + class_b                         1    2635.0 1087010 38612
    ## + age:cd_total_07                 1    1838.6 1087806 38618
    ## + stories                         1    1567.0 1088078 38619
    ## + leasing_rate:Precipitation      1    1106.2 1088538 38623
    ## + class_a:cd_total_07             1    1075.5 1088569 38623
    ## + renovated                       1    1021.0 1088624 38623
    ## + amenities                       1     940.0 1088705 38624
    ## + leasing_rate:Electricity_Costs  1     740.4 1088904 38625
    ## + leasing_rate:cd_total_07        1     739.6 1088905 38625
    ## + cluster:Electricity_Costs       1     624.6 1089020 38626
    ## + class_a:Precipitation           1     530.9 1089114 38627
    ## + age:class_a                     1     400.4 1089244 38628
    ## + age:Electricity_Costs           1     361.6 1089283 38628
    ## + cluster:age                     1     288.2 1089356 38629
    ## + cluster:Precipitation           1     285.3 1089359 38629
    ## <none>                                        1089645 38629
    ## + green_rating                    1     210.4 1089434 38629
    ## + leasing_rate:age                1     199.5 1089445 38629
    ## + cluster:leasing_rate            1      14.9 1089630 38631
    ## + empl_gr                         1       8.8 1089636 38631
    ## + Gas_Costs                       1       3.8 1089641 38631
    ## + age:Precipitation               1       3.5 1089641 38631
    ## + cluster:cd_total_07             1       1.1 1089643 38631
    ## 
    ## Step:  AIC=38582.34
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + size                            1    6440.4 1076482 38538
    ## + age:Electricity_Costs           1    5199.5 1077723 38547
    ## + net                             1    4322.4 1078600 38553
    ## + hd_total07                      1    3207.1 1079715 38561
    ## + leasing_rate:class_a            1    2641.8 1080280 38565
    ## + cluster:class_a                 1    2623.3 1080299 38565
    ## + age:cd_total_07                 1    2419.0 1080503 38567
    ## + class_b                         1    2363.7 1080558 38567
    ## + stories                         1    1854.5 1081068 38571
    ## + leasing_rate:Precipitation      1    1206.2 1081716 38576
    ## + renovated                       1    1034.0 1081888 38577
    ## + leasing_rate:cd_total_07        1     894.4 1082028 38578
    ## + class_a:cd_total_07             1     737.6 1082185 38579
    ## + cluster:Electricity_Costs       1     689.2 1082233 38579
    ## + amenities                       1     651.8 1082270 38580
    ## + age:Precipitation               1     301.1 1082621 38582
    ## <none>                                        1082922 38582
    ## + cluster:Precipitation           1     266.5 1082656 38582
    ## + age:class_a                     1     259.1 1082663 38582
    ## + green_rating                    1     194.8 1082727 38583
    ## + leasing_rate:age                1     175.0 1082747 38583
    ## + leasing_rate:Electricity_Costs  1      45.5 1082877 38584
    ## + cluster:age                     1      35.5 1082887 38584
    ## + class_a:Precipitation           1      27.3 1082895 38584
    ## + empl_gr                         1      18.3 1082904 38584
    ## + Gas_Costs                       1      17.4 1082905 38584
    ## + cluster:leasing_rate            1       2.9 1082919 38584
    ## + cluster:cd_total_07             1       2.1 1082920 38584
    ## 
    ## Step:  AIC=38537.69
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + size:Electricity_Costs          1     43090 1033392 38220
    ## + cluster:size                    1     11399 1065083 38456
    ## + size:leasing_rate               1      6969 1069512 38489
    ## + size:cd_total_07                1      6298 1070184 38494
    ## + net                             1      5240 1071241 38502
    ## + hd_total07                      1      4910 1071572 38504
    ## + age:Electricity_Costs           1      4548 1071934 38507
    ## + cluster:class_a                 1      3024 1073458 38518
    ## + age:cd_total_07                 1      2739 1073743 38520
    ## + leasing_rate:class_a            1      2148 1074334 38524
    ## + size:Precipitation              1      2011 1074470 38525
    ## + class_b                         1      1681 1074801 38527
    ## + renovated                       1      1502 1074980 38529
    ## + leasing_rate:Precipitation      1       935 1075546 38533
    ## + leasing_rate:cd_total_07        1       876 1075605 38533
    ## + stories                         1       874 1075607 38533
    ## + cluster:Electricity_Costs       1       634 1075848 38535
    ## + class_a:cd_total_07             1       542 1075940 38536
    ## + size:class_a                    1       416 1076065 38537
    ## + Gas_Costs                       1       370 1076112 38537
    ## + cluster:Precipitation           1       294 1076188 38538
    ## <none>                                        1076482 38538
    ## + age:Precipitation               1       220 1076262 38538
    ## + green_rating                    1       173 1076308 38538
    ## + empl_gr                         1       173 1076309 38538
    ## + size:age                        1       162 1076320 38539
    ## + leasing_rate:age                1       160 1076322 38539
    ## + age:class_a                     1       134 1076347 38539
    ## + cluster:age                     1        87 1076395 38539
    ## + leasing_rate:Electricity_Costs  1        63 1076419 38539
    ## + amenities                       1        54 1076427 38539
    ## + class_a:Precipitation           1        53 1076429 38539
    ## + cluster:leasing_rate            1        20 1076462 38540
    ## + cluster:cd_total_07             1         3 1076479 38540
    ## 
    ## Step:  AIC=38220.23
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + age:Electricity_Costs           1    4711.4 1028680 38186
    ## + size:cd_total_07                1    4206.2 1029185 38190
    ## + net                             1    4157.7 1029234 38191
    ## + size:Precipitation              1    4035.4 1029356 38192
    ## + cluster:size                    1    3758.2 1029633 38194
    ## + size:leasing_rate               1    3667.7 1029724 38194
    ## + cluster:class_a                 1    2798.7 1030593 38201
    ## + age:cd_total_07                 1    2265.3 1031126 38205
    ## + hd_total07                      1    2120.3 1031271 38206
    ## + size:class_a                    1    1994.8 1031397 38207
    ## + class_b                         1    1688.1 1031704 38209
    ## + cluster:Electricity_Costs       1    1502.9 1031889 38211
    ## + renovated                       1    1458.0 1031934 38211
    ## + leasing_rate:class_a            1    1415.4 1031976 38212
    ## + stories                         1    1388.9 1032003 38212
    ## + leasing_rate:Precipitation      1    1062.7 1032329 38214
    ## + leasing_rate:cd_total_07        1     727.4 1032664 38217
    ## + Gas_Costs                       1     587.6 1032804 38218
    ## + size:age                        1     530.7 1032861 38218
    ## + cluster:Precipitation           1     509.0 1032883 38218
    ## + empl_gr                         1     455.0 1032937 38219
    ## + age:Precipitation               1     366.3 1033025 38219
    ## + class_a:cd_total_07             1     330.5 1033061 38220
    ## <none>                                        1033392 38220
    ## + leasing_rate:Electricity_Costs  1     234.6 1033157 38220
    ## + class_a:Precipitation           1     216.1 1033176 38221
    ## + amenities                       1     172.3 1033219 38221
    ## + leasing_rate:age                1     171.3 1033220 38221
    ## + green_rating                    1      91.5 1033300 38222
    ## + cluster:age                     1      68.2 1033323 38222
    ## + age:class_a                     1      13.0 1033379 38222
    ## + cluster:cd_total_07             1       8.8 1033383 38222
    ## + cluster:leasing_rate            1       0.8 1033391 38222
    ## 
    ## Step:  AIC=38186.5
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + size:cd_total_07                1    4108.2 1024572 38157
    ## + net                             1    4010.4 1024670 38158
    ## + cluster:size                    1    3701.8 1024978 38160
    ## + size:Precipitation              1    3694.1 1024986 38160
    ## + size:leasing_rate               1    3661.6 1025019 38161
    ## + cluster:class_a                 1    3045.2 1025635 38165
    ## + hd_total07                      1    2016.7 1026664 38173
    ## + stories                         1    1925.7 1026755 38174
    ## + cluster:Electricity_Costs       1    1880.9 1026799 38174
    ## + size:class_a                    1    1813.5 1026867 38175
    ## + renovated                       1    1694.6 1026986 38176
    ## + class_b                         1    1640.9 1027039 38176
    ## + age:cd_total_07                 1    1617.4 1027063 38176
    ## + leasing_rate:class_a            1    1417.9 1027262 38178
    ## + leasing_rate:Precipitation      1    1085.0 1027595 38180
    ## + cluster:age                     1     667.2 1028013 38183
    ## + Gas_Costs                       1     609.6 1028071 38184
    ## + leasing_rate:cd_total_07        1     591.4 1028089 38184
    ## + size:age                        1     585.7 1028095 38184
    ## + cluster:Precipitation           1     529.3 1028151 38184
    ## + class_a:cd_total_07             1     395.9 1028284 38185
    ## + class_a:Precipitation           1     394.4 1028286 38185
    ## + empl_gr                         1     388.5 1028292 38186
    ## + amenities                       1     272.1 1028408 38186
    ## <none>                                        1028680 38186
    ## + leasing_rate:age                1     253.1 1028427 38187
    ## + leasing_rate:Electricity_Costs  1     180.1 1028500 38187
    ## + age:class_a                     1      67.3 1028613 38188
    ## + green_rating                    1      55.5 1028625 38188
    ## + age:Precipitation               1      11.6 1028669 38188
    ## + cluster:cd_total_07             1       4.6 1028676 38188
    ## + cluster:leasing_rate            1       0.3 1028680 38188
    ## 
    ## Step:  AIC=38157.2
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + size:Precipitation              1    4186.0 1020386 38127
    ## + net                             1    3468.5 1021104 38133
    ## + cluster:size                    1    2974.7 1021597 38136
    ## + hd_total07                      1    2935.1 1021637 38137
    ## + size:leasing_rate               1    2862.3 1021710 38137
    ## + age:cd_total_07                 1    2747.7 1021824 38138
    ## + cluster:class_a                 1    2567.6 1022004 38140
    ## + stories                         1    2069.3 1022503 38143
    ## + cluster:Electricity_Costs       1    1908.3 1022664 38145
    ## + class_b                         1    1758.9 1022813 38146
    ## + size:class_a                    1    1672.0 1022900 38146
    ## + renovated                       1    1601.4 1022971 38147
    ## + leasing_rate:Precipitation      1    1338.7 1023233 38149
    ## + leasing_rate:class_a            1    1235.9 1023336 38150
    ## + cluster:age                     1     506.2 1024066 38155
    ## + cluster:Precipitation           1     481.6 1024090 38156
    ## + Gas_Costs                       1     468.9 1024103 38156
    ## + size:age                        1     347.9 1024224 38157
    ## + amenities                       1     317.3 1024255 38157
    ## + leasing_rate:age                1     263.8 1024308 38157
    ## <none>                                        1024572 38157
    ## + class_a:Precipitation           1     229.9 1024342 38157
    ## + empl_gr                         1     175.4 1024397 38158
    ## + leasing_rate:Electricity_Costs  1     127.2 1024445 38158
    ## + age:class_a                     1     111.5 1024461 38158
    ## + class_a:cd_total_07             1     108.6 1024463 38158
    ## + cluster:cd_total_07             1     107.5 1024465 38158
    ## + leasing_rate:cd_total_07        1      77.7 1024494 38159
    ## + age:Precipitation               1      54.1 1024518 38159
    ## + green_rating                    1      18.5 1024554 38159
    ## + cluster:leasing_rate            1      10.5 1024562 38159
    ## 
    ## Step:  AIC=38127.19
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + hd_total07                      1    3215.4 1017171 38105
    ## + cluster:size                    1    3115.3 1017271 38105
    ## + net                             1    3101.7 1017284 38105
    ## + class_a:Precipitation           1    2644.8 1017741 38109
    ## + cluster:class_a                 1    2644.4 1017742 38109
    ## + size:leasing_rate               1    2417.2 1017969 38111
    ## + age:cd_total_07                 1    2327.0 1018059 38111
    ## + cluster:Electricity_Costs       1    1871.5 1018515 38115
    ## + size:class_a                    1    1741.9 1018644 38116
    ## + class_b                         1    1706.9 1018679 38116
    ## + renovated                       1    1336.1 1019050 38119
    ## + leasing_rate:class_a            1    1241.8 1019144 38120
    ## + stories                         1    1075.1 1019311 38121
    ## + leasing_rate:Precipitation      1     591.9 1019794 38125
    ## + Gas_Costs                       1     533.6 1019852 38125
    ## + amenities                       1     469.6 1019916 38126
    ## + cluster:age                     1     417.0 1019969 38126
    ## + cluster:Precipitation           1     316.1 1020070 38127
    ## + leasing_rate:age                1     305.3 1020081 38127
    ## <none>                                        1020386 38127
    ## + age:class_a                     1     232.3 1020154 38127
    ## + cluster:cd_total_07             1     172.7 1020213 38128
    ## + leasing_rate:Electricity_Costs  1     133.6 1020252 38128
    ## + empl_gr                         1     126.4 1020260 38128
    ## + leasing_rate:cd_total_07        1     103.0 1020283 38128
    ## + size:age                        1      97.9 1020288 38128
    ## + age:Precipitation               1      54.9 1020331 38129
    ## + class_a:cd_total_07             1      51.7 1020334 38129
    ## + cluster:leasing_rate            1       9.4 1020377 38129
    ## + green_rating                    1       5.5 1020381 38129
    ## 
    ## Step:  AIC=38104.51
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + age:hd_total07                  1    5503.5 1011667 38064
    ## + hd_total07:Electricity_Costs    1    4455.0 1012716 38072
    ## + hd_total07:Precipitation        1    4120.0 1013051 38075
    ## + age:cd_total_07                 1    3033.0 1014138 38083
    ## + net                             1    2938.4 1014232 38084
    ## + cluster:size                    1    2885.0 1014286 38084
    ## + size:hd_total07                 1    2691.5 1014479 38086
    ## + class_a:Precipitation           1    2602.0 1014569 38086
    ## + cluster:class_a                 1    2504.7 1014666 38087
    ## + cluster:Electricity_Costs       1    2312.7 1014858 38089
    ## + size:leasing_rate               1    2260.0 1014911 38089
    ## + cd_total_07:hd_total07          1    2038.6 1015132 38091
    ## + size:class_a                    1    1964.2 1015206 38091
    ## + class_a:hd_total07              1    1915.5 1015255 38092
    ## + class_b                         1    1551.4 1015619 38095
    ## + renovated                       1    1404.7 1015766 38096
    ## + leasing_rate:class_a            1    1164.0 1016007 38098
    ## + stories                         1     932.6 1016238 38099
    ## + leasing_rate:Precipitation      1     545.5 1016625 38102
    ## + amenities                       1     444.0 1016727 38103
    ## + cluster:Precipitation           1     382.2 1016789 38104
    ## + cluster:age                     1     366.7 1016804 38104
    ## + age:class_a                     1     339.9 1016831 38104
    ## + leasing_rate:age                1     298.1 1016873 38104
    ## <none>                                        1017171 38105
    ## + cluster:hd_total07              1     221.5 1016949 38105
    ## + size:age                        1     111.5 1017059 38106
    ## + leasing_rate:Electricity_Costs  1      95.3 1017075 38106
    ## + class_a:cd_total_07             1      90.8 1017080 38106
    ## + Gas_Costs                       1      90.4 1017080 38106
    ## + cluster:cd_total_07             1      66.3 1017104 38106
    ## + leasing_rate:cd_total_07        1      57.5 1017113 38106
    ## + age:Precipitation               1      49.1 1017122 38106
    ## + empl_gr                         1      28.9 1017142 38106
    ## + cluster:leasing_rate            1      28.1 1017143 38106
    ## + leasing_rate:hd_total07         1      13.5 1017157 38106
    ## + green_rating                    1      11.3 1017159 38106
    ## 
    ## Step:  AIC=38064.08
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + hd_total07:Electricity_Costs    1    5653.9 1006013 38022
    ## + hd_total07:Precipitation        1    4922.4 1006745 38028
    ## + size:hd_total07                 1    4631.7 1007035 38030
    ## + net                             1    2961.0 1008706 38043
    ## + cluster:size                    1    2900.3 1008767 38044
    ## + size:leasing_rate               1    2378.7 1009288 38048
    ## + cluster:class_a                 1    2306.5 1009361 38048
    ## + cluster:Electricity_Costs       1    2183.9 1009483 38049
    ## + class_a:Precipitation           1    2014.8 1009652 38050
    ## + size:class_a                    1    1668.6 1009999 38053
    ## + class_b                         1    1278.9 1010388 38056
    ## + leasing_rate:class_a            1    1220.4 1010447 38057
    ## + cd_total_07:hd_total07          1    1206.3 1010461 38057
    ## + age:cd_total_07                 1    1135.0 1010532 38057
    ## + stories                         1     874.4 1010793 38059
    ## + renovated                       1     855.7 1010811 38059
    ## + leasing_rate:Precipitation      1     554.8 1011112 38062
    ## + cluster:Precipitation           1     508.5 1011159 38062
    ## + amenities                       1     491.6 1011175 38062
    ## + leasing_rate:age                1     431.6 1011236 38063
    ## <none>                                        1011667 38064
    ## + age:class_a                     1     257.1 1011410 38064
    ## + cluster:age                     1     241.3 1011426 38064
    ## + cluster:cd_total_07             1     221.0 1011446 38064
    ## + Gas_Costs                       1     175.2 1011492 38065
    ## + leasing_rate:hd_total07         1     138.7 1011528 38065
    ## + leasing_rate:cd_total_07        1     117.0 1011550 38065
    ## + leasing_rate:Electricity_Costs  1     113.4 1011554 38065
    ## + cluster:hd_total07              1      91.0 1011576 38065
    ## + class_a:hd_total07              1      77.7 1011589 38065
    ## + green_rating                    1      64.9 1011602 38066
    ## + cluster:leasing_rate            1      12.4 1011655 38066
    ## + size:age                        1       7.4 1011660 38066
    ## + empl_gr                         1       6.8 1011660 38066
    ## + class_a:cd_total_07             1       6.2 1011661 38066
    ## + age:Precipitation               1       1.3 1011666 38066
    ## 
    ## Step:  AIC=38022.26
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07
    ## 
    ##                                  Df Sum of Sq     RSS   AIC
    ## + size:hd_total07                 1    6241.1  999772 37976
    ## + net                             1    3082.1 1002931 38000
    ## + cluster:size                    1    2648.5 1003365 38004
    ## + class_a:Precipitation           1    2623.4 1003390 38004
    ## + size:leasing_rate               1    2467.3 1003546 38005
    ## + cluster:Electricity_Costs       1    2322.1 1003691 38006
    ## + cluster:class_a                 1    2212.8 1003800 38007
    ## + Gas_Costs                       1    2179.4 1003834 38007
    ## + empl_gr                         1    1754.6 1004259 38011
    ## + size:class_a                    1    1737.7 1004276 38011
    ## + hd_total07:Precipitation        1    1680.5 1004333 38011
    ## + stories                         1    1163.0 1004850 38015
    ## + leasing_rate:class_a            1    1152.2 1004861 38015
    ## + class_b                         1    1071.5 1004942 38016
    ## + cd_total_07:hd_total07          1    1033.2 1004980 38016
    ## + age:cd_total_07                 1     715.0 1005298 38019
    ## + renovated                       1     634.4 1005379 38019
    ## + cluster:cd_total_07             1     546.3 1005467 38020
    ## + amenities                       1     513.5 1005500 38020
    ## + leasing_rate:age                1     510.9 1005502 38020
    ## + cluster:Precipitation           1     500.6 1005513 38020
    ## + cluster:hd_total07              1     378.2 1005635 38021
    ## + leasing_rate:Precipitation      1     348.6 1005665 38022
    ## <none>                                        1006013 38022
    ## + age:class_a                     1     234.9 1005778 38022
    ## + cluster:age                     1     228.0 1005785 38022
    ## + class_a:hd_total07              1     139.9 1005873 38023
    ## + leasing_rate:Electricity_Costs  1     102.7 1005911 38023
    ## + green_rating                    1      71.9 1005941 38024
    ## + leasing_rate:hd_total07         1      68.6 1005945 38024
    ## + leasing_rate:cd_total_07        1      46.7 1005967 38024
    ## + cluster:leasing_rate            1      15.6 1005998 38024
    ## + age:Precipitation               1      12.5 1006001 38024
    ## + size:age                        1       7.5 1006006 38024
    ## + class_a:cd_total_07             1       5.4 1006008 38024
    ## 
    ## Step:  AIC=37975.59
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + net                             1    3680.3 996092 37949
    ## + Gas_Costs                       1    3496.7 996275 37950
    ## + cluster:size                    1    2976.4 996796 37954
    ## + empl_gr                         1    2165.1 997607 37961
    ## + cluster:class_a                 1    2134.1 997638 37961
    ## + size:leasing_rate               1    2117.0 997655 37961
    ## + cluster:Electricity_Costs       1    1978.2 997794 37962
    ## + class_a:Precipitation           1    1681.7 998090 37964
    ## + class_a:hd_total07              1    1630.3 998142 37965
    ## + hd_total07:Precipitation        1    1535.2 998237 37966
    ## + size:class_a                    1    1327.2 998445 37967
    ## + leasing_rate:class_a            1    1138.3 998634 37969
    ## + class_b                         1    1104.0 998668 37969
    ## + cd_total_07:hd_total07          1     905.5 998867 37971
    ## + cluster:cd_total_07             1     721.5 999051 37972
    ## + renovated                       1     697.1 999075 37972
    ## + amenities                       1     690.4 999082 37972
    ## + leasing_rate:age                1     688.6 999083 37972
    ## + leasing_rate:Precipitation      1     487.3 999285 37974
    ## + age:cd_total_07                 1     474.2 999298 37974
    ## + age:class_a                     1     465.4 999307 37974
    ## + cluster:Precipitation           1     439.1 999333 37974
    ## + stories                         1     397.5 999375 37974
    ## + size:age                        1     312.3 999460 37975
    ## <none>                                        999772 37976
    ## + cluster:age                     1     169.2 999603 37976
    ## + cluster:hd_total07              1     127.3 999645 37977
    ## + leasing_rate:Electricity_Costs  1     118.7 999653 37977
    ## + age:Precipitation               1      93.9 999678 37977
    ## + green_rating                    1      51.7 999720 37977
    ## + leasing_rate:cd_total_07        1      43.4 999729 37977
    ## + class_a:cd_total_07             1      12.6 999760 37977
    ## + cluster:leasing_rate            1       8.0 999764 37978
    ## + leasing_rate:hd_total07         1       0.3 999772 37978
    ## 
    ## Step:  AIC=37948.75
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + Gas_Costs                       1    3410.4 992681 37924
    ## + cluster:size                    1    2998.7 993093 37927
    ## + empl_gr                         1    2287.3 993804 37933
    ## + cluster:class_a                 1    2128.9 993963 37934
    ## + size:leasing_rate               1    2001.9 994090 37935
    ## + cluster:Electricity_Costs       1    1972.6 994119 37935
    ## + class_a:hd_total07              1    1492.8 994599 37939
    ## + hd_total07:Precipitation        1    1386.5 994705 37940
    ## + class_a:Precipitation           1    1376.5 994715 37940
    ## + net:cd_total_07                 1    1272.2 994820 37941
    ## + class_b                         1    1104.2 994988 37942
    ## + leasing_rate:class_a            1    1098.3 994994 37942
    ## + size:class_a                    1    1052.3 995039 37942
    ## + cd_total_07:hd_total07          1     965.3 995127 37943
    ## + leasing_rate:age                1     685.1 995407 37945
    ## + renovated                       1     680.0 995412 37945
    ## + amenities                       1     660.1 995432 37946
    ## + cluster:cd_total_07             1     613.1 995479 37946
    ## + net:Electricity_Costs           1     559.3 995533 37946
    ## + age:cd_total_07                 1     548.3 995543 37946
    ## + leasing_rate:Precipitation      1     535.2 995557 37947
    ## + age:class_a                     1     527.6 995564 37947
    ## + size:age                        1     424.2 995668 37947
    ## + cluster:Precipitation           1     419.1 995673 37947
    ## + stories                         1     384.0 995708 37948
    ## <none>                                        996092 37949
    ## + size:net                        1     232.4 995859 37949
    ## + net:hd_total07                  1     230.3 995861 37949
    ## + cluster:age                     1     180.2 995912 37949
    ## + cluster:hd_total07              1     178.8 995913 37949
    ## + leasing_rate:net                1     148.5 995943 37950
    ## + age:Precipitation               1     133.0 995959 37950
    ## + leasing_rate:Electricity_Costs  1     100.8 995991 37950
    ## + cluster:net                     1      48.1 996044 37950
    ## + green_rating                    1      47.8 996044 37950
    ## + leasing_rate:cd_total_07        1      44.1 996048 37950
    ## + class_a:net                     1      28.0 996064 37951
    ## + cluster:leasing_rate            1      10.0 996082 37951
    ## + net:Precipitation               1       7.2 996085 37951
    ## + class_a:cd_total_07             1       0.1 996092 37951
    ## + age:net                         1       0.1 996092 37951
    ## + leasing_rate:hd_total07         1       0.1 996092 37951
    ## 
    ## Step:  AIC=37923.93
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + Gas_Costs:Electricity_Costs     1    3323.2 989358 37900
    ## + cluster:size                    1    2839.8 989842 37904
    ## + cluster:Electricity_Costs       1    2372.5 990309 37907
    ## + cluster:class_a                 1    2280.8 990401 37908
    ## + size:leasing_rate               1    1859.6 990822 37911
    ## + size:Gas_Costs                  1    1708.9 990973 37912
    ## + class_a:Precipitation           1    1576.6 991105 37914
    ## + class_a:Gas_Costs               1    1530.1 991151 37914
    ## + class_a:hd_total07              1    1239.3 991442 37916
    ## + size:class_a                    1    1157.1 991524 37917
    ## + net:cd_total_07                 1    1143.8 991538 37917
    ## + leasing_rate:class_a            1    1003.2 991678 37918
    ## + class_b                         1     996.9 991685 37918
    ## + amenities                       1     862.9 991819 37919
    ## + Precipitation:Gas_Costs         1     761.2 991920 37920
    ## + leasing_rate:age                1     644.8 992037 37921
    ## + hd_total07:Precipitation        1     604.6 992077 37921
    ## + renovated                       1     570.9 992111 37921
    ## + leasing_rate:Precipitation      1     536.2 992145 37922
    ## + net:Electricity_Costs           1     419.5 992262 37923
    ## + cd_total_07:hd_total07          1     409.6 992272 37923
    ## + net:Gas_Costs                   1     375.7 992306 37923
    ## + hd_total07:Gas_Costs            1     368.8 992313 37923
    ## + leasing_rate:Gas_Costs          1     339.4 992342 37923
    ## + size:age                        1     311.3 992370 37923
    ## + cluster:hd_total07              1     291.9 992389 37924
    ## + age:class_a                     1     276.1 992405 37924
    ## + size:net                        1     265.2 992416 37924
    ## + cluster:age                     1     264.4 992417 37924
    ## + empl_gr                         1     256.2 992425 37924
    ## <none>                                        992681 37924
    ## + stories                         1     247.2 992434 37924
    ## + cluster:cd_total_07             1     245.0 992436 37924
    ## + net:hd_total07                  1     209.9 992472 37924
    ## + leasing_rate:net                1     179.0 992502 37925
    ## + cluster:Precipitation           1     167.3 992514 37925
    ## + cd_total_07:Gas_Costs           1     153.1 992528 37925
    ## + age:Gas_Costs                   1     152.6 992529 37925
    ## + class_a:cd_total_07             1     106.6 992575 37925
    ## + leasing_rate:Electricity_Costs  1     105.1 992576 37925
    ## + cluster:Gas_Costs               1      85.7 992596 37925
    ## + leasing_rate:cd_total_07        1      72.9 992608 37925
    ## + age:cd_total_07                 1      61.1 992620 37925
    ## + class_a:net                     1      36.6 992645 37926
    ## + cluster:net                     1      15.5 992666 37926
    ## + green_rating                    1      14.9 992667 37926
    ## + cluster:leasing_rate            1       2.1 992679 37926
    ## + age:Precipitation               1       1.2 992680 37926
    ## + leasing_rate:hd_total07         1       0.2 992681 37926
    ## + net:Precipitation               1       0.2 992681 37926
    ## + age:net                         1       0.1 992681 37926
    ## 
    ## Step:  AIC=37899.71
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + cd_total_07:Gas_Costs           1    5732.6 983626 37856
    ## + cluster:size                    1    3040.5 986318 37878
    ## + empl_gr                         1    2221.6 987137 37884
    ## + cluster:class_a                 1    2171.0 987187 37885
    ## + hd_total07:Gas_Costs            1    2126.1 987232 37885
    ## + size:Gas_Costs                  1    2046.0 987312 37886
    ## + cluster:Electricity_Costs       1    1929.2 987429 37886
    ## + size:leasing_rate               1    1720.2 987638 37888
    ## + class_a:Precipitation           1    1628.2 987730 37889
    ## + net:cd_total_07                 1    1385.8 987972 37891
    ## + size:class_a                    1    1344.3 988014 37891
    ## + class_a:hd_total07              1    1341.1 988017 37891
    ## + class_a:Gas_Costs               1    1225.1 988133 37892
    ## + leasing_rate:class_a            1    1016.5 988342 37894
    ## + class_b                         1     891.4 988467 37895
    ## + amenities                       1     864.4 988494 37895
    ## + net:Electricity_Costs           1     704.0 988654 37896
    ## + cluster:cd_total_07             1     694.0 988664 37896
    ## + leasing_rate:age                1     684.0 988674 37896
    ## + net:Gas_Costs                   1     681.4 988677 37896
    ## + renovated                       1     670.4 988688 37896
    ## + age:Gas_Costs                   1     524.0 988834 37898
    ## + age:class_a                     1     473.0 988885 37898
    ## + leasing_rate:Precipitation      1     429.9 988928 37898
    ## + size:net                        1     360.4 988998 37899
    ## + leasing_rate:Gas_Costs          1     355.8 989002 37899
    ## + size:age                        1     321.4 989037 37899
    ## + cluster:Precipitation           1     301.9 989056 37899
    ## + net:hd_total07                  1     277.6 989081 37900
    ## <none>                                        989358 37900
    ## + cd_total_07:hd_total07          1     243.1 989115 37900
    ## + hd_total07:Precipitation        1     197.3 989161 37900
    ## + cluster:age                     1     190.5 989168 37900
    ## + leasing_rate:net                1     174.7 989184 37900
    ## + cluster:hd_total07              1     169.2 989189 37900
    ## + stories                         1      98.2 989260 37901
    ## + age:cd_total_07                 1      86.6 989272 37901
    ## + leasing_rate:Electricity_Costs  1      65.5 989293 37901
    ## + leasing_rate:cd_total_07        1      53.9 989304 37901
    ## + class_a:net                     1      43.4 989315 37901
    ## + cluster:net                     1      34.8 989323 37901
    ## + class_a:cd_total_07             1      33.1 989325 37901
    ## + green_rating                    1      17.0 989341 37902
    ## + Precipitation:Gas_Costs         1      13.4 989345 37902
    ## + leasing_rate:hd_total07         1      13.3 989345 37902
    ## + net:Precipitation               1       2.1 989356 37902
    ## + cluster:leasing_rate            1       1.8 989356 37902
    ## + cluster:Gas_Costs               1       0.6 989358 37902
    ## + age:net                         1       0.1 989358 37902
    ## + age:Precipitation               1       0.0 989358 37902
    ## 
    ## Step:  AIC=37856.27
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + cluster:size                    1    3254.1 980372 37832
    ## + cd_total_07:hd_total07          1    2568.5 981057 37838
    ## + cluster:class_a                 1    2318.5 981307 37840
    ## + size:Gas_Costs                  1    2279.2 981346 37840
    ## + size:leasing_rate               1    1726.9 981899 37845
    ## + size:class_a                    1    1644.9 981981 37845
    ## + class_a:Precipitation           1    1624.1 982002 37845
    ## + cluster:Electricity_Costs       1    1617.3 982008 37845
    ## + hd_total07:Gas_Costs            1    1535.7 982090 37846
    ## + class_a:Gas_Costs               1    1414.1 982212 37847
    ## + amenities                       1    1257.1 982369 37848
    ## + net:cd_total_07                 1    1202.2 982423 37849
    ## + leasing_rate:class_a            1    1130.8 982495 37849
    ## + class_a:hd_total07              1     970.8 982655 37851
    ## + leasing_rate:age                1     723.7 982902 37853
    ## + class_b                         1     711.8 982914 37853
    ## + renovated                       1     673.2 982952 37853
    ## + net:Electricity_Costs           1     623.7 983002 37853
    ## + cluster:cd_total_07             1     610.6 983015 37853
    ## + Precipitation:Gas_Costs         1     606.7 983019 37853
    ## + net:Gas_Costs                   1     552.8 983073 37854
    ## + leasing_rate:Precipitation      1     497.2 983128 37854
    ## + stories                         1     390.4 983235 37855
    ## + age:class_a                     1     349.6 983276 37855
    ## + cluster:Precipitation           1     317.9 983308 37856
    ## + class_a:cd_total_07             1     296.7 983329 37856
    ## + age:Gas_Costs                   1     291.7 983334 37856
    ## + leasing_rate:Gas_Costs          1     286.0 983340 37856
    ## + cluster:hd_total07              1     283.1 983343 37856
    ## + size:net                        1     262.5 983363 37856
    ## + net:hd_total07                  1     255.7 983370 37856
    ## <none>                                        983626 37856
    ## + cluster:age                     1     234.5 983391 37856
    ## + size:age                        1     215.8 983410 37857
    ## + empl_gr                         1     149.0 983477 37857
    ## + leasing_rate:net                1     108.6 983517 37857
    ## + leasing_rate:cd_total_07        1      74.5 983551 37858
    ## + leasing_rate:Electricity_Costs  1      70.6 983555 37858
    ## + hd_total07:Precipitation        1      48.0 983578 37858
    ## + class_a:net                     1      36.8 983589 37858
    ## + cluster:net                     1      35.3 983590 37858
    ## + age:Precipitation               1      25.0 983601 37858
    ## + age:cd_total_07                 1      15.2 983610 37858
    ## + net:Precipitation               1      14.9 983611 37858
    ## + leasing_rate:hd_total07         1       8.7 983617 37858
    ## + green_rating                    1       7.5 983618 37858
    ## + age:net                         1       0.6 983625 37858
    ## + cluster:Gas_Costs               1       0.3 983625 37858
    ## + cluster:leasing_rate            1       0.2 983625 37858
    ## 
    ## Step:  AIC=37832.35
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + cd_total_07:hd_total07          1   2768.15 977603 37812
    ## + cluster:Electricity_Costs       1   2165.09 978206 37817
    ## + size:Gas_Costs                  1   2147.54 978224 37817
    ## + size:leasing_rate               1   1866.55 978505 37819
    ## + hd_total07:Gas_Costs            1   1483.03 978888 37823
    ## + class_a:Precipitation           1   1467.93 978904 37823
    ## + class_a:Gas_Costs               1   1256.23 979115 37824
    ## + size:class_a                    1   1197.12 979174 37825
    ## + amenities                       1   1191.05 979180 37825
    ## + leasing_rate:class_a            1   1181.14 979190 37825
    ## + net:cd_total_07                 1   1103.61 979268 37826
    ## + class_a:hd_total07              1    910.55 979461 37827
    ## + cluster:cd_total_07             1    770.38 979601 37828
    ## + leasing_rate:age                1    736.40 979635 37828
    ## + Precipitation:Gas_Costs         1    690.61 979681 37829
    ## + class_b                         1    667.15 979704 37829
    ## + renovated                       1    662.11 979709 37829
    ## + net:Electricity_Costs           1    640.32 979731 37829
    ## + cluster:Precipitation           1    608.72 979763 37829
    ## + cluster:class_a                 1    589.79 979782 37830
    ## + net:Gas_Costs                   1    564.94 979807 37830
    ## + cluster:hd_total07              1    521.91 979850 37830
    ## + leasing_rate:Precipitation      1    479.19 979892 37831
    ## + stories                         1    442.29 979929 37831
    ## + size:age                        1    342.08 980029 37832
    ## + age:Gas_Costs                   1    336.18 980035 37832
    ## + age:class_a                     1    315.19 980056 37832
    ## + class_a:cd_total_07             1    275.33 980096 37832
    ## <none>                                        980372 37832
    ## + leasing_rate:Gas_Costs          1    248.63 980123 37832
    ## + size:net                        1    235.14 980136 37832
    ## + net:hd_total07                  1    216.93 980155 37833
    ## + empl_gr                         1    165.60 980206 37833
    ## + cluster:net                     1    163.50 980208 37833
    ## + cluster:leasing_rate            1    110.87 980261 37833
    ## + leasing_rate:net                1    102.38 980269 37834
    ## + hd_total07:Precipitation        1     64.11 980307 37834
    ## + leasing_rate:cd_total_07        1     63.21 980308 37834
    ## + leasing_rate:Electricity_Costs  1     59.60 980312 37834
    ## + class_a:net                     1     32.86 980339 37834
    ## + age:Precipitation               1     22.94 980349 37834
    ## + net:Precipitation               1     22.65 980349 37834
    ## + green_rating                    1     19.43 980352 37834
    ## + age:cd_total_07                 1     13.18 980358 37834
    ## + leasing_rate:hd_total07         1     12.12 980359 37834
    ## + cluster:age                     1      2.97 980369 37834
    ## + age:net                         1      1.19 980370 37834
    ## + cluster:Gas_Costs               1      0.11 980371 37834
    ## 
    ## Step:  AIC=37812.24
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + hd_total07:Gas_Costs            1    4846.2 972757 37775
    ## + size:Gas_Costs                  1    2653.0 974950 37793
    ## + size:leasing_rate               1    2009.9 975593 37798
    ## + cluster:Electricity_Costs       1    1918.2 975685 37799
    ## + class_a:Precipitation           1    1371.9 976231 37803
    ## + net:cd_total_07                 1    1324.1 976279 37804
    ## + leasing_rate:class_a            1    1275.5 976328 37804
    ## + class_a:Gas_Costs               1    1260.0 976343 37804
    ## + size:class_a                    1    1247.1 976356 37804
    ## + amenities                       1    1071.5 976532 37806
    ## + leasing_rate:age                1     729.8 976874 37808
    ## + cluster:cd_total_07             1     687.1 976916 37809
    ## + class_b                         1     612.5 976991 37809
    ## + net:Electricity_Costs           1     611.9 976991 37809
    ## + cluster:hd_total07              1     608.8 976995 37809
    ## + net:Gas_Costs                   1     594.3 977009 37809
    ## + cluster:class_a                 1     585.3 977018 37810
    ## + renovated                       1     582.9 977020 37810
    ## + class_a:hd_total07              1     568.1 977035 37810
    ## + leasing_rate:Precipitation      1     545.0 977058 37810
    ## + cluster:Precipitation           1     464.2 977139 37811
    ## + age:class_a                     1     435.1 977168 37811
    ## + age:Gas_Costs                   1     393.3 977210 37811
    ## + size:age                        1     389.4 977214 37811
    ## + stories                         1     369.1 977234 37811
    ## + size:net                        1     288.1 977315 37812
    ## + net:hd_total07                  1     272.7 977331 37812
    ## + class_a:cd_total_07             1     269.9 977333 37812
    ## <none>                                        977603 37812
    ## + leasing_rate:Gas_Costs          1     237.3 977366 37812
    ## + cluster:net                     1     164.7 977439 37813
    ## + age:Precipitation               1     122.1 977481 37813
    ## + leasing_rate:net                1     112.6 977491 37813
    ## + leasing_rate:Electricity_Costs  1     101.3 977502 37813
    ## + leasing_rate:cd_total_07        1      91.4 977512 37814
    ## + cluster:leasing_rate            1      90.5 977513 37814
    ## + hd_total07:Precipitation        1      58.4 977545 37814
    ## + Precipitation:Gas_Costs         1      45.6 977558 37814
    ## + age:cd_total_07                 1      36.0 977567 37814
    ## + class_a:net                     1      16.9 977586 37814
    ## + green_rating                    1      14.6 977589 37814
    ## + age:net                         1      12.4 977591 37814
    ## + net:Precipitation               1      11.0 977592 37814
    ## + empl_gr                         1       6.7 977597 37814
    ## + cluster:Gas_Costs               1       3.2 977600 37814
    ## + leasing_rate:hd_total07         1       1.6 977602 37814
    ## + cluster:age                     1       0.6 977603 37814
    ## 
    ## Step:  AIC=37775.38
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + hd_total07:Precipitation        1    4167.7 968590 37744
    ## + size:Gas_Costs                  1    2101.8 970655 37760
    ## + cluster:Electricity_Costs       1    2090.5 970667 37761
    ## + size:leasing_rate               1    1938.9 970818 37762
    ## + class_a:Precipitation           1    1230.1 971527 37767
    ## + net:cd_total_07                 1    1213.3 971544 37768
    ## + size:class_a                    1    1117.1 971640 37768
    ## + leasing_rate:class_a            1    1093.7 971664 37769
    ## + class_a:Gas_Costs               1    1092.4 971665 37769
    ## + amenities                       1     882.8 971874 37770
    ## + class_a:hd_total07              1     872.9 971884 37770
    ## + cluster:hd_total07              1     822.3 971935 37771
    ## + leasing_rate:age                1     668.2 972089 37772
    ## + cluster:cd_total_07             1     666.2 972091 37772
    ## + age:Gas_Costs                   1     622.5 972135 37772
    ## + cluster:class_a                 1     581.0 972176 37773
    ## + class_b                         1     580.3 972177 37773
    ## + net:Electricity_Costs           1     576.7 972181 37773
    ## + net:Gas_Costs                   1     558.9 972198 37773
    ## + age:class_a                     1     549.4 972208 37773
    ## + leasing_rate:Precipitation      1     527.1 972230 37773
    ## + cluster:Precipitation           1     495.1 972262 37773
    ## + renovated                       1     491.8 972265 37773
    ## + size:age                        1     491.2 972266 37773
    ## + Precipitation:Gas_Costs         1     340.8 972416 37775
    ## + stories                         1     321.3 972436 37775
    ## + age:Precipitation               1     309.4 972448 37775
    ## <none>                                        972757 37775
    ## + net:hd_total07                  1     218.8 972538 37776
    ## + age:cd_total_07                 1     215.3 972542 37776
    ## + leasing_rate:Gas_Costs          1     209.1 972548 37776
    ## + class_a:cd_total_07             1     204.4 972553 37776
    ## + size:net                        1     200.0 972557 37776
    ## + cluster:net                     1     187.2 972570 37776
    ## + leasing_rate:Electricity_Costs  1     121.1 972636 37776
    ## + cluster:leasing_rate            1     115.3 972642 37776
    ## + leasing_rate:net                1      81.5 972676 37777
    ## + leasing_rate:cd_total_07        1      71.1 972686 37777
    ## + empl_gr                         1      57.8 972699 37777
    ## + net:Precipitation               1      20.4 972737 37777
    ## + green_rating                    1      15.0 972742 37777
    ## + age:net                         1      14.5 972743 37777
    ## + class_a:net                     1       9.0 972748 37777
    ## + cluster:Gas_Costs               1       6.5 972751 37777
    ## + leasing_rate:hd_total07         1       1.0 972756 37777
    ## + cluster:age                     1       0.1 972757 37777
    ## 
    ## Step:  AIC=37743.8
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + size:Gas_Costs                  1   2203.21 966386 37728
    ## + cluster:Electricity_Costs       1   1669.18 966920 37732
    ## + size:leasing_rate               1   1627.23 966962 37733
    ## + amenities                       1   1529.52 967060 37733
    ## + size:class_a                    1   1229.73 967360 37736
    ## + class_a:Precipitation           1   1203.82 967386 37736
    ## + net:cd_total_07                 1   1172.08 967417 37736
    ## + class_a:hd_total07              1   1039.80 967550 37737
    ## + class_a:Gas_Costs               1   1018.03 967571 37738
    ## + leasing_rate:class_a            1   1001.57 967588 37738
    ## + cluster:cd_total_07             1    800.65 967789 37739
    ## + leasing_rate:age                1    700.29 967889 37740
    ## + cluster:class_a                 1    680.40 967909 37740
    ## + age:Gas_Costs                   1    665.01 967925 37740
    ## + cluster:Precipitation           1    658.28 967931 37740
    ## + cluster:hd_total07              1    640.10 967949 37741
    ## + age:class_a                     1    582.54 968007 37741
    ## + net:Gas_Costs                   1    520.83 968069 37742
    ## + net:Electricity_Costs           1    517.95 968072 37742
    ## + size:age                        1    429.66 968160 37742
    ## + class_b                         1    407.67 968182 37743
    ## + stories                         1    303.57 968286 37743
    ## + leasing_rate:Precipitation      1    299.52 968290 37743
    ## + age:Precipitation               1    285.86 968304 37743
    ## + size:net                        1    277.60 968312 37744
    ## <none>                                        968590 37744
    ## + renovated                       1    246.24 968343 37744
    ## + leasing_rate:Gas_Costs          1    246.09 968343 37744
    ## + net:hd_total07                  1    218.77 968371 37744
    ## + class_a:cd_total_07             1    208.98 968381 37744
    ## + cluster:net                     1    150.87 968439 37745
    ## + leasing_rate:cd_total_07        1    115.50 968474 37745
    ## + leasing_rate:net                1    111.90 968478 37745
    ## + cluster:leasing_rate            1    102.47 968487 37745
    ## + age:cd_total_07                 1     83.72 968506 37745
    ## + leasing_rate:Electricity_Costs  1     78.07 968511 37745
    ## + green_rating                    1     21.84 968568 37746
    ## + cluster:Gas_Costs               1     18.93 968571 37746
    ## + class_a:net                     1     16.92 968573 37746
    ## + net:Precipitation               1     15.28 968574 37746
    ## + age:net                         1     13.08 968576 37746
    ## + Precipitation:Gas_Costs         1     11.05 968578 37746
    ## + empl_gr                         1      8.75 968581 37746
    ## + cluster:age                     1      1.03 968588 37746
    ## + leasing_rate:hd_total07         1      0.85 968589 37746
    ## 
    ## Step:  AIC=37727.99
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + cluster:Electricity_Costs       1   1641.78 964745 37717
    ## + size:leasing_rate               1   1600.05 964786 37717
    ## + age:Gas_Costs                   1   1594.40 964792 37717
    ## + amenities                       1   1585.37 964801 37717
    ## + net:cd_total_07                 1   1147.00 965239 37721
    ## + size:class_a                    1   1120.72 965266 37721
    ## + leasing_rate:class_a            1   1112.04 965274 37721
    ## + cluster:cd_total_07             1    850.75 965536 37723
    ## + class_a:Precipitation           1    828.20 965558 37723
    ## + class_a:hd_total07              1    764.63 965622 37724
    ## + leasing_rate:age                1    760.55 965626 37724
    ## + net:Gas_Costs                   1    689.57 965697 37724
    ## + cluster:Precipitation           1    652.14 965734 37725
    ## + cluster:hd_total07              1    621.15 965765 37725
    ## + age:class_a                     1    584.48 965802 37725
    ## + size:age                        1    543.96 965842 37726
    ## + net:Electricity_Costs           1    531.58 965855 37726
    ## + cluster:class_a                 1    524.64 965862 37726
    ## + leasing_rate:Precipitation      1    516.98 965869 37726
    ## + class_b                         1    465.21 965921 37726
    ## + age:Precipitation               1    346.86 966039 37727
    ## <none>                                        966386 37728
    ## + renovated                       1    223.08 966163 37728
    ## + cluster:net                     1    207.73 966179 37728
    ## + size:net                        1    185.42 966201 37728
    ## + age:cd_total_07                 1    182.10 966204 37729
    ## + stories                         1    163.14 966223 37729
    ## + net:hd_total07                  1    152.21 966234 37729
    ## + cluster:leasing_rate            1    144.18 966242 37729
    ## + class_a:Gas_Costs               1    143.48 966243 37729
    ## + class_a:cd_total_07             1     75.31 966311 37729
    ## + Precipitation:Gas_Costs         1     71.61 966315 37729
    ## + leasing_rate:net                1     41.29 966345 37730
    ## + green_rating                    1     26.04 966360 37730
    ## + empl_gr                         1     20.78 966366 37730
    ## + leasing_rate:cd_total_07        1     16.76 966370 37730
    ## + leasing_rate:hd_total07         1      9.56 966377 37730
    ## + leasing_rate:Gas_Costs          1      7.52 966379 37730
    ## + age:net                         1      6.81 966379 37730
    ## + cluster:Gas_Costs               1      4.43 966382 37730
    ## + class_a:net                     1      3.22 966383 37730
    ## + net:Precipitation               1      1.33 966385 37730
    ## + cluster:age                     1      1.20 966385 37730
    ## + leasing_rate:Electricity_Costs  1      0.17 966386 37730
    ## 
    ## Step:  AIC=37716.7
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + age:Gas_Costs                   1   1613.72 963131 37706
    ## + size:leasing_rate               1   1571.76 963173 37706
    ## + amenities                       1   1555.47 963189 37706
    ## + net:cd_total_07                 1   1190.59 963554 37709
    ## + size:class_a                    1   1131.44 963613 37710
    ## + leasing_rate:class_a            1   1066.64 963678 37710
    ## + class_a:Precipitation           1    828.17 963916 37712
    ## + leasing_rate:age                1    824.85 963920 37712
    ## + class_a:hd_total07              1    778.45 963966 37712
    ## + net:Gas_Costs                   1    732.12 964012 37713
    ## + cluster:cd_total_07             1    589.59 964155 37714
    ## + net:Electricity_Costs           1    549.93 964195 37714
    ## + size:age                        1    538.38 964206 37714
    ## + age:class_a                     1    528.78 964216 37714
    ## + leasing_rate:Precipitation      1    514.71 964230 37715
    ## + class_b                         1    495.57 964249 37715
    ## + cluster:class_a                 1    355.48 964389 37716
    ## + age:Precipitation               1    334.42 964410 37716
    ## + cluster:Precipitation           1    255.33 964489 37717
    ## + cluster:net                     1    248.30 964496 37717
    ## <none>                                        964745 37717
    ## + cluster:leasing_rate            1    222.10 964522 37717
    ## + age:cd_total_07                 1    197.05 964547 37717
    ## + renovated                       1    194.95 964550 37717
    ## + stories                         1    179.82 964565 37717
    ## + size:net                        1    168.38 964576 37717
    ## + net:hd_total07                  1    157.58 964587 37717
    ## + class_a:Gas_Costs               1    153.68 964591 37717
    ## + Precipitation:Gas_Costs         1    107.11 964637 37718
    ## + class_a:cd_total_07             1     75.93 964669 37718
    ## + leasing_rate:net                1     36.13 964708 37718
    ## + green_rating                    1     33.79 964711 37718
    ## + leasing_rate:Gas_Costs          1     15.13 964729 37719
    ## + cluster:Gas_Costs               1     13.90 964731 37719
    ## + leasing_rate:hd_total07         1     13.78 964731 37719
    ## + cluster:age                     1     12.45 964732 37719
    ## + leasing_rate:cd_total_07        1      9.42 964735 37719
    ## + cluster:hd_total07              1      9.06 964735 37719
    ## + empl_gr                         1      5.76 964739 37719
    ## + age:net                         1      4.91 964740 37719
    ## + class_a:net                     1      2.83 964742 37719
    ## + leasing_rate:Electricity_Costs  1      0.31 964744 37719
    ## + net:Precipitation               1      0.02 964745 37719
    ## 
    ## Step:  AIC=37705.61
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + class_a:Precipitation           1   1683.70 961447 37694
    ## + amenities                       1   1630.76 961500 37694
    ## + size:leasing_rate               1   1616.15 961515 37694
    ## + leasing_rate:class_a            1   1136.76 961994 37698
    ## + net:cd_total_07                 1   1015.98 962115 37699
    ## + leasing_rate:age                1    974.81 962156 37700
    ## + size:class_a                    1    968.20 962163 37700
    ## + class_a:Gas_Costs               1    951.80 962179 37700
    ## + class_a:hd_total07              1    770.99 962360 37701
    ## + cluster:cd_total_07             1    682.70 962448 37702
    ## + size:age                        1    593.15 962538 37703
    ## + net:Gas_Costs                   1    536.15 962595 37703
    ## + cluster:class_a                 1    477.74 962653 37704
    ## + class_b                         1    442.31 962688 37704
    ## + net:Electricity_Costs           1    421.01 962710 37704
    ## + age:class_a                     1    372.86 962758 37705
    ## + cluster:Precipitation           1    359.42 962771 37705
    ## + leasing_rate:Precipitation      1    357.67 962773 37705
    ## + class_a:cd_total_07             1    284.40 962846 37705
    ## <none>                                        963131 37706
    ## + cluster:net                     1    231.33 962899 37706
    ## + stories                         1    223.57 962907 37706
    ## + cluster:leasing_rate            1    187.53 962943 37706
    ## + renovated                       1    176.83 962954 37706
    ## + Precipitation:Gas_Costs         1    156.87 962974 37706
    ## + size:net                        1    126.55 963004 37707
    ## + age:Precipitation               1    121.26 963010 37707
    ## + net:hd_total07                  1    116.40 963014 37707
    ## + age:cd_total_07                 1     67.22 963064 37707
    ## + cluster:Gas_Costs               1     65.55 963065 37707
    ## + leasing_rate:cd_total_07        1     31.39 963099 37707
    ## + leasing_rate:net                1     26.25 963105 37707
    ## + green_rating                    1     18.86 963112 37707
    ## + cluster:age                     1     14.36 963116 37707
    ## + cluster:hd_total07              1     12.76 963118 37708
    ## + leasing_rate:Electricity_Costs  1      9.24 963122 37708
    ## + class_a:net                     1      6.51 963124 37708
    ## + leasing_rate:hd_total07         1      5.94 963125 37708
    ## + net:Precipitation               1      3.45 963127 37708
    ## + leasing_rate:Gas_Costs          1      3.07 963128 37708
    ## + empl_gr                         1      1.86 963129 37708
    ## + age:net                         1      0.25 963131 37708
    ## 
    ## Step:  AIC=37693.92
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + size:leasing_rate               1   1559.00 959888 37683
    ## + amenities                       1   1374.36 960073 37685
    ## + leasing_rate:class_a            1   1246.29 960201 37686
    ## + net:cd_total_07                 1   1039.18 960408 37687
    ## + leasing_rate:age                1    898.95 960548 37689
    ## + cluster:cd_total_07             1    739.03 960708 37690
    ## + size:class_a                    1    671.60 960776 37690
    ## + size:age                        1    604.52 960843 37691
    ## + net:Gas_Costs                   1    540.48 960907 37692
    ## + leasing_rate:Precipitation      1    522.73 960924 37692
    ## + class_b                         1    495.73 960951 37692
    ## + net:Electricity_Costs           1    421.65 961025 37692
    ## + cluster:Precipitation           1    383.70 961063 37693
    ## + cluster:class_a                 1    322.94 961124 37693
    ## + class_a:hd_total07              1    256.90 961190 37694
    ## + stories                         1    253.20 961194 37694
    ## <none>                                        961447 37694
    ## + cluster:net                     1    234.40 961213 37694
    ## + Precipitation:Gas_Costs         1    222.41 961225 37694
    ## + cluster:leasing_rate            1    200.94 961246 37694
    ## + age:class_a                     1    186.42 961261 37694
    ## + renovated                       1    178.70 961268 37694
    ## + class_a:cd_total_07             1    142.79 961304 37695
    ## + net:hd_total07                  1    106.05 961341 37695
    ## + size:net                        1     94.31 961353 37695
    ## + age:cd_total_07                 1     75.81 961371 37695
    ## + cluster:Gas_Costs               1     71.00 961376 37695
    ## + class_a:Gas_Costs               1     59.16 961388 37695
    ## + leasing_rate:cd_total_07        1     44.94 961402 37696
    ## + leasing_rate:net                1     33.27 961414 37696
    ## + green_rating                    1     29.90 961417 37696
    ## + cluster:age                     1     20.49 961427 37696
    ## + leasing_rate:Electricity_Costs  1      8.32 961439 37696
    ## + age:Precipitation               1      6.54 961441 37696
    ## + empl_gr                         1      6.47 961441 37696
    ## + cluster:hd_total07              1      4.75 961442 37696
    ## + leasing_rate:hd_total07         1      2.62 961444 37696
    ## + class_a:net                     1      0.60 961447 37696
    ## + leasing_rate:Gas_Costs          1      0.04 961447 37696
    ## + age:net                         1      0.03 961447 37696
    ## + net:Precipitation               1      0.02 961447 37696
    ## 
    ## Step:  AIC=37683.23
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + amenities                       1   1678.06 958210 37672
    ## + net:cd_total_07                 1   1108.69 958779 37676
    ## + size:class_a                    1   1057.78 958830 37677
    ## + class_b                         1    789.85 959098 37679
    ## + cluster:cd_total_07             1    705.94 959182 37679
    ## + net:Gas_Costs                   1    539.73 959348 37681
    ## + leasing_rate:age                1    500.42 959388 37681
    ## + net:Electricity_Costs           1    427.26 959461 37682
    ## + cluster:Precipitation           1    424.55 959464 37682
    ## + leasing_rate:Precipitation      1    374.60 959514 37682
    ## + size:age                        1    372.98 959515 37682
    ## + leasing_rate:class_a            1    349.07 959539 37682
    ## + cluster:class_a                 1    346.11 959542 37682
    ## + class_a:hd_total07              1    264.13 959624 37683
    ## <none>                                        959888 37683
    ## + cluster:net                     1    244.06 959644 37683
    ## + Precipitation:Gas_Costs         1    185.14 959703 37684
    ## + stories                         1    172.67 959715 37684
    ## + age:class_a                     1    169.01 959719 37684
    ## + class_a:cd_total_07             1    168.57 959720 37684
    ## + renovated                       1    142.17 959746 37684
    ## + cluster:leasing_rate            1    120.84 959767 37684
    ## + net:hd_total07                  1    113.91 959774 37684
    ## + leasing_rate:net                1    109.32 959779 37684
    ## + age:cd_total_07                 1     76.04 959812 37685
    ## + cluster:Gas_Costs               1     75.85 959812 37685
    ## + size:net                        1     75.37 959813 37685
    ## + leasing_rate:cd_total_07        1     66.53 959822 37685
    ## + class_a:Gas_Costs               1     64.38 959824 37685
    ## + leasing_rate:hd_total07         1     35.18 959853 37685
    ## + green_rating                    1     30.70 959857 37685
    ## + cluster:age                     1     27.34 959861 37685
    ## + leasing_rate:Electricity_Costs  1     15.25 959873 37685
    ## + age:Precipitation               1      5.38 959883 37685
    ## + empl_gr                         1      3.33 959885 37685
    ## + class_a:net                     1      2.65 959885 37685
    ## + leasing_rate:Gas_Costs          1      2.09 959886 37685
    ## + cluster:hd_total07              1      1.66 959886 37685
    ## + age:net                         1      0.26 959888 37685
    ## + net:Precipitation               1      0.00 959888 37685
    ## 
    ## Step:  AIC=37671.55
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + amenities:Gas_Costs             1    3886.0 954324 37642
    ## + amenities:cd_total_07           1    1526.2 956684 37661
    ## + net:cd_total_07                 1    1046.4 957164 37665
    ## + class_a:amenities               1    1035.2 957175 37665
    ## + size:class_a                    1     745.0 957465 37667
    ## + amenities:Precipitation         1     675.5 957535 37668
    ## + cluster:cd_total_07             1     646.6 957563 37668
    ## + class_b                         1     577.0 957633 37669
    ## + leasing_rate:age                1     500.2 957710 37669
    ## + size:age                        1     485.3 957725 37670
    ## + net:Gas_Costs                   1     461.9 957748 37670
    ## + cluster:Precipitation           1     413.5 957797 37670
    ## + net:Electricity_Costs           1     398.9 957811 37670
    ## + leasing_rate:class_a            1     304.3 957906 37671
    ## + leasing_rate:Precipitation      1     302.6 957907 37671
    ## + cluster:class_a                 1     291.1 957919 37671
    ## + cluster:amenities               1     291.1 957919 37671
    ## + stories                         1     274.5 957936 37671
    ## + class_a:hd_total07              1     260.8 957949 37671
    ## <none>                                        958210 37672
    ## + age:class_a                     1     235.1 957975 37672
    ## + cluster:net                     1     235.0 957975 37672
    ## + renovated                       1     200.4 958010 37672
    ## + Precipitation:Gas_Costs         1     166.8 958043 37672
    ## + net:hd_total07                  1     117.3 958093 37673
    ## + leasing_rate:amenities          1     116.6 958093 37673
    ## + cluster:leasing_rate            1     116.6 958093 37673
    ## + leasing_rate:net                1     108.5 958102 37673
    ## + class_a:cd_total_07             1      95.4 958115 37673
    ## + age:amenities                   1      84.2 958126 37673
    ## + size:net                        1      75.7 958134 37673
    ## + cluster:Gas_Costs               1      71.6 958138 37673
    ## + leasing_rate:hd_total07         1      63.4 958147 37673
    ## + leasing_rate:cd_total_07        1      62.9 958147 37673
    ## + leasing_rate:Electricity_Costs  1      45.3 958165 37673
    ## + age:cd_total_07                 1      33.8 958176 37673
    ## + green_rating                    1      33.4 958177 37673
    ## + class_a:Gas_Costs               1      28.0 958182 37673
    ## + amenities:hd_total07            1      14.8 958195 37673
    ## + cluster:age                     1      10.9 958199 37673
    ## + net:amenities                   1       7.3 958203 37673
    ## + amenities:Electricity_Costs     1       3.4 958207 37674
    ## + leasing_rate:Gas_Costs          1       3.2 958207 37674
    ## + size:amenities                  1       2.3 958208 37674
    ## + age:Precipitation               1       2.0 958208 37674
    ## + cluster:hd_total07              1       1.6 958208 37674
    ## + net:Precipitation               1       1.5 958209 37674
    ## + class_a:net                     1       1.2 958209 37674
    ## + age:net                         1       0.3 958210 37674
    ## + empl_gr                         1       0.2 958210 37674
    ## 
    ## Step:  AIC=37641.77
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size + Gas_Costs:amenities
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + class_a:amenities               1   1343.77 952980 37633
    ## + size:class_a                    1    657.37 953667 37638
    ## + size:age                        1    619.63 953704 37639
    ## + cluster:cd_total_07             1    602.53 953722 37639
    ## + class_b                         1    513.95 953810 37640
    ## + leasing_rate:age                1    507.66 953816 37640
    ## + cluster:Precipitation           1    416.31 953908 37640
    ## + net:cd_total_07                 1    306.98 954017 37641
    ## + leasing_rate:class_a            1    302.23 954022 37641
    ## + age:class_a                     1    278.60 954045 37641
    ## + cluster:class_a                 1    254.62 954069 37642
    ## <none>                                        954324 37642
    ## + amenities:Precipitation         1    243.81 954080 37642
    ## + amenities:cd_total_07           1    224.68 954099 37642
    ## + class_a:hd_total07              1    192.44 954132 37642
    ## + renovated                       1    154.82 954169 37643
    ## + leasing_rate:net                1    143.07 954181 37643
    ## + Precipitation:Gas_Costs         1    139.07 954185 37643
    ## + leasing_rate:Precipitation      1    133.95 954190 37643
    ## + stories                         1    131.12 954193 37643
    ## + net:Precipitation               1    111.11 954213 37643
    ## + cluster:leasing_rate            1    104.29 954220 37643
    ## + leasing_rate:cd_total_07        1     88.57 954236 37643
    ## + net:amenities                   1     86.98 954237 37643
    ## + leasing_rate:hd_total07         1     73.28 954251 37643
    ## + cluster:net                     1     71.23 954253 37643
    ## + cluster:amenities               1     70.04 954254 37643
    ## + class_a:cd_total_07             1     69.53 954255 37643
    ## + leasing_rate:Electricity_Costs  1     66.97 954257 37643
    ## + age:cd_total_07                 1     48.90 954275 37643
    ## + age:amenities                   1     47.33 954277 37643
    ## + cluster:Gas_Costs               1     45.47 954279 37643
    ## + leasing_rate:amenities          1     41.11 954283 37643
    ## + amenities:Electricity_Costs     1     37.50 954287 37643
    ## + size:net                        1     34.51 954290 37643
    ## + green_rating                    1     26.65 954297 37644
    ## + class_a:net                     1     20.25 954304 37644
    ## + size:amenities                  1     17.07 954307 37644
    ## + age:Precipitation               1     16.21 954308 37644
    ## + cluster:age                     1     15.65 954308 37644
    ## + age:net                         1     12.59 954311 37644
    ## + net:Gas_Costs                   1      8.10 954316 37644
    ## + cluster:hd_total07              1      7.62 954316 37644
    ## + class_a:Gas_Costs               1      4.23 954320 37644
    ## + leasing_rate:Gas_Costs          1      1.48 954323 37644
    ## + amenities:hd_total07            1      1.16 954323 37644
    ## + empl_gr                         1      0.50 954324 37644
    ## + net:hd_total07                  1      0.07 954324 37644
    ## + net:Electricity_Costs           1      0.00 954324 37644
    ## 
    ## Step:  AIC=37632.75
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size + Gas_Costs:amenities + 
    ##     class_a:amenities
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + size:age                        1    821.74 952159 37628
    ## + age:amenities                   1    643.89 952336 37629
    ## + leasing_rate:age                1    556.30 952424 37630
    ## + cluster:cd_total_07             1    555.47 952425 37630
    ## + leasing_rate:class_a            1    420.38 952560 37631
    ## + cluster:Precipitation           1    409.13 952571 37631
    ## + class_b                         1    376.09 952604 37632
    ## + size:class_a                    1    323.22 952657 37632
    ## + net:cd_total_07                 1    275.91 952704 37632
    ## + age:class_a                     1    264.92 952715 37633
    ## + cluster:class_a                 1    249.61 952731 37633
    ## <none>                                        952980 37633
    ## + amenities:Precipitation         1    231.29 952749 37633
    ## + amenities:cd_total_07           1    208.16 952772 37633
    ## + class_a:hd_total07              1    183.77 952797 37633
    ## + renovated                       1    171.49 952809 37633
    ## + Precipitation:Gas_Costs         1    160.36 952820 37633
    ## + stories                         1    155.56 952825 37633
    ## + size:amenities                  1    140.08 952840 37634
    ## + leasing_rate:net                1    134.51 952846 37634
    ## + leasing_rate:amenities          1    116.64 952864 37634
    ## + net:Precipitation               1    115.48 952865 37634
    ## + leasing_rate:hd_total07         1    111.17 952869 37634
    ## + leasing_rate:cd_total_07        1     99.83 952880 37634
    ## + leasing_rate:Precipitation      1     98.66 952882 37634
    ## + leasing_rate:Electricity_Costs  1     96.50 952884 37634
    ## + cluster:leasing_rate            1     87.08 952893 37634
    ## + class_a:cd_total_07             1     67.48 952913 37634
    ## + cluster:net                     1     61.95 952918 37634
    ## + cluster:amenities               1     57.88 952922 37634
    ## + cluster:Gas_Costs               1     46.45 952934 37634
    ## + net:amenities                   1     45.19 952935 37634
    ## + amenities:hd_total07            1     29.52 952951 37635
    ## + class_a:net                     1     27.88 952952 37635
    ## + age:cd_total_07                 1     25.96 952954 37635
    ## + green_rating                    1     21.94 952958 37635
    ## + net:Gas_Costs                   1     16.22 952964 37635
    ## + size:net                        1     15.87 952964 37635
    ## + age:net                         1     15.39 952965 37635
    ## + cluster:age                     1     13.08 952967 37635
    ## + age:Precipitation               1     11.13 952969 37635
    ## + cluster:hd_total07              1      6.21 952974 37635
    ## + leasing_rate:Gas_Costs          1      6.16 952974 37635
    ## + amenities:Electricity_Costs     1      1.46 952979 37635
    ## + net:Electricity_Costs           1      1.31 952979 37635
    ## + empl_gr                         1      0.92 952979 37635
    ## + net:hd_total07                  1      0.84 952979 37635
    ## + class_a:Gas_Costs               1      0.06 952980 37635
    ## 
    ## Step:  AIC=37628.01
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size + Gas_Costs:amenities + 
    ##     class_a:amenities + age:size
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + size:class_a                    1   2125.96 950033 37613
    ## + cluster:cd_total_07             1    593.90 951565 37625
    ## + class_b                         1    517.53 951641 37626
    ## + cluster:Precipitation           1    442.13 951716 37626
    ## + leasing_rate:class_a            1    419.05 951740 37627
    ## + leasing_rate:age                1    414.89 951744 37627
    ## + age:amenities                   1    350.57 951808 37627
    ## + stories                         1    320.64 951838 37627
    ## + net:cd_total_07                 1    265.91 951893 37628
    ## + cluster:class_a                 1    254.33 951904 37628
    ## <none>                                        952159 37628
    ## + class_a:hd_total07              1    222.45 951936 37628
    ## + amenities:Precipitation         1    213.52 951945 37628
    ## + amenities:cd_total_07           1    199.94 951959 37628
    ## + Precipitation:Gas_Costs         1    173.91 951985 37629
    ## + leasing_rate:net                1    139.59 952019 37629
    ## + renovated                       1    134.85 952024 37629
    ## + leasing_rate:amenities          1    128.65 952030 37629
    ## + size:amenities                  1    113.87 952045 37629
    ## + leasing_rate:Precipitation      1    104.43 952054 37629
    ## + leasing_rate:hd_total07         1    102.78 952056 37629
    ## + net:Precipitation               1    102.05 952057 37629
    ## + leasing_rate:cd_total_07        1     96.52 952062 37629
    ## + cluster:leasing_rate            1     92.30 952066 37629
    ## + age:cd_total_07                 1     84.23 952074 37629
    ## + leasing_rate:Electricity_Costs  1     83.81 952075 37629
    ## + age:Precipitation               1     83.44 952075 37629
    ## + class_a:cd_total_07             1     80.64 952078 37629
    ## + cluster:amenities               1     75.87 952083 37629
    ## + net:amenities                   1     62.82 952096 37629
    ## + age:class_a                     1     54.17 952104 37630
    ## + cluster:net                     1     50.45 952108 37630
    ## + cluster:Gas_Costs               1     49.23 952109 37630
    ## + size:net                        1     43.39 952115 37630
    ## + green_rating                    1     33.05 952126 37630
    ## + cluster:age                     1     30.06 952129 37630
    ## + amenities:hd_total07            1     28.85 952130 37630
    ## + class_a:net                     1     16.84 952142 37630
    ## + net:Gas_Costs                   1     15.17 952143 37630
    ## + cluster:hd_total07              1      7.23 952151 37630
    ## + leasing_rate:Gas_Costs          1      6.42 952152 37630
    ## + age:net                         1      5.46 952153 37630
    ## + class_a:Gas_Costs               1      2.73 952156 37630
    ## + empl_gr                         1      1.86 952157 37630
    ## + amenities:Electricity_Costs     1      0.64 952158 37630
    ## + net:Electricity_Costs           1      0.27 952158 37630
    ## + net:hd_total07                  1      0.14 952158 37630
    ## 
    ## Step:  AIC=37612.53
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size + Gas_Costs:amenities + 
    ##     class_a:amenities + age:size + class_a:size
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + cluster:cd_total_07             1    581.98 949451 37610
    ## + leasing_rate:class_a            1    485.52 949547 37611
    ## + cluster:Precipitation           1    479.83 949553 37611
    ## + class_b                         1    357.54 949675 37612
    ## + size:amenities                  1    311.45 949721 37612
    ## + leasing_rate:age                1    291.03 949742 37612
    ## + net:cd_total_07                 1    272.76 949760 37612
    ## + age:Precipitation               1    246.43 949786 37612
    ## <none>                                        950033 37613
    ## + amenities:Precipitation         1    226.55 949806 37613
    ## + Precipitation:Gas_Costs         1    218.42 949814 37613
    ## + cluster:class_a                 1    178.31 949854 37613
    ## + stories                         1    175.73 949857 37613
    ## + amenities:cd_total_07           1    144.04 949889 37613
    ## + renovated                       1    139.91 949893 37613
    ## + age:cd_total_07                 1    129.64 949903 37613
    ## + leasing_rate:cd_total_07        1    125.75 949907 37613
    ## + leasing_rate:net                1    122.22 949910 37614
    ## + net:Precipitation               1    109.92 949923 37614
    ## + leasing_rate:hd_total07         1    103.38 949929 37614
    ## + leasing_rate:amenities          1     98.82 949934 37614
    ## + leasing_rate:Electricity_Costs  1     88.19 949944 37614
    ## + age:amenities                   1     79.05 949954 37614
    ## + cluster:leasing_rate            1     77.72 949955 37614
    ## + class_a:cd_total_07             1     67.07 949966 37614
    ## + cluster:net                     1     66.47 949966 37614
    ## + cluster:amenities               1     65.19 949967 37614
    ## + cluster:age                     1     64.87 949968 37614
    ## + green_rating                    1     63.91 949969 37614
    ## + leasing_rate:Precipitation      1     59.50 949973 37614
    ## + net:amenities                   1     54.23 949978 37614
    ## + class_a:hd_total07              1     52.41 949980 37614
    ## + cluster:Gas_Costs               1     47.27 949985 37614
    ## + age:class_a                     1     39.90 949993 37614
    ## + class_a:net                     1     31.39 950001 37614
    ## + leasing_rate:Gas_Costs          1     18.75 950014 37614
    ## + amenities:hd_total07            1     13.14 950019 37614
    ## + net:Gas_Costs                   1     10.60 950022 37614
    ## + cluster:hd_total07              1      4.83 950028 37614
    ## + empl_gr                         1      4.64 950028 37614
    ## + size:net                        1      4.55 950028 37614
    ## + net:hd_total07                  1      3.96 950029 37614
    ## + age:net                         1      2.03 950031 37615
    ## + amenities:Electricity_Costs     1      1.23 950031 37615
    ## + net:Electricity_Costs           1      0.31 950032 37615
    ## + class_a:Gas_Costs               1      0.05 950033 37615
    ## 
    ## Step:  AIC=37609.74
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size + Gas_Costs:amenities + 
    ##     class_a:amenities + age:size + class_a:size + cd_total_07:cluster
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + leasing_rate:class_a            1    439.78 949011 37608
    ## + class_b                         1    376.02 949075 37609
    ## + size:amenities                  1    339.26 949111 37609
    ## + cluster:Precipitation           1    309.94 949141 37609
    ## + net:cd_total_07                 1    298.87 949152 37609
    ## + leasing_rate:age                1    269.92 949181 37610
    ## + age:Precipitation               1    267.94 949183 37610
    ## <none>                                        949451 37610
    ## + Precipitation:Gas_Costs         1    229.90 949221 37610
    ## + cluster:class_a                 1    225.30 949225 37610
    ## + cluster:age                     1    217.70 949233 37610
    ## + stories                         1    209.15 949241 37610
    ## + amenities:Precipitation         1    201.01 949250 37610
    ## + renovated                       1    137.54 949313 37611
    ## + amenities:cd_total_07           1    129.78 949321 37611
    ## + leasing_rate:net                1    127.58 949323 37611
    ## + leasing_rate:cd_total_07        1    126.21 949324 37611
    ## + cluster:leasing_rate            1    119.55 949331 37611
    ## + net:Precipitation               1    118.50 949332 37611
    ## + cluster:hd_total07              1    110.94 949340 37611
    ## + leasing_rate:hd_total07         1    100.25 949350 37611
    ## + leasing_rate:amenities          1     99.62 949351 37611
    ## + leasing_rate:Electricity_Costs  1     80.38 949370 37611
    ## + age:cd_total_07                 1     78.29 949372 37611
    ## + age:amenities                   1     73.80 949377 37611
    ## + class_a:hd_total07              1     71.92 949379 37611
    ## + leasing_rate:Precipitation      1     65.52 949385 37611
    ## + green_rating                    1     58.95 949392 37611
    ## + cluster:amenities               1     46.55 949404 37611
    ## + net:amenities                   1     42.44 949408 37611
    ## + age:class_a                     1     41.62 949409 37611
    ## + class_a:net                     1     40.66 949410 37611
    ## + class_a:cd_total_07             1     37.60 949413 37611
    ## + cluster:net                     1     35.13 949415 37611
    ## + leasing_rate:Gas_Costs          1     21.84 949429 37612
    ## + cluster:Gas_Costs               1     15.93 949435 37612
    ## + net:Gas_Costs                   1     14.44 949436 37612
    ## + amenities:hd_total07            1      7.95 949443 37612
    ## + age:net                         1      3.20 949447 37612
    ## + size:net                        1      2.78 949448 37612
    ## + net:hd_total07                  1      2.42 949448 37612
    ## + empl_gr                         1      1.92 949449 37612
    ## + amenities:Electricity_Costs     1      1.84 949449 37612
    ## + net:Electricity_Costs           1      1.41 949449 37612
    ## + class_a:Gas_Costs               1      0.64 949450 37612
    ## 
    ## Step:  AIC=37608.11
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size + Gas_Costs:amenities + 
    ##     class_a:amenities + age:size + class_a:size + cd_total_07:cluster + 
    ##     class_a:leasing_rate
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + size:amenities                  1    389.23 948622 37607
    ## + class_b                         1    388.67 948622 37607
    ## + net:cd_total_07                 1    326.25 948685 37607
    ## + cluster:Precipitation           1    314.22 948697 37608
    ## + age:Precipitation               1    250.72 948760 37608
    ## <none>                                        949011 37608
    ## + Precipitation:Gas_Costs         1    242.55 948768 37608
    ## + stories                         1    239.68 948771 37608
    ## + cluster:class_a                 1    211.80 948799 37608
    ## + cluster:age                     1    202.06 948809 37608
    ## + amenities:Precipitation         1    193.05 948818 37609
    ## + cluster:leasing_rate            1    146.95 948864 37609
    ## + renovated                       1    141.27 948870 37609
    ## + leasing_rate:net                1    138.39 948872 37609
    ## + amenities:cd_total_07           1    134.70 948876 37609
    ## + cluster:hd_total07              1    118.61 948892 37609
    ## + leasing_rate:cd_total_07        1    116.94 948894 37609
    ## + net:Precipitation               1    113.28 948898 37609
    ## + class_a:hd_total07              1    102.93 948908 37609
    ## + green_rating                    1     79.61 948931 37609
    ## + leasing_rate:age                1     77.11 948934 37609
    ## + age:amenities                   1     75.45 948935 37609
    ## + leasing_rate:Precipitation      1     61.49 948949 37610
    ## + age:cd_total_07                 1     59.47 948951 37610
    ## + cluster:amenities               1     54.33 948957 37610
    ## + leasing_rate:hd_total07         1     47.54 948963 37610
    ## + leasing_rate:amenities          1     46.88 948964 37610
    ## + class_a:net                     1     44.79 948966 37610
    ## + net:amenities                   1     43.76 948967 37610
    ## + leasing_rate:Electricity_Costs  1     39.99 948971 37610
    ## + cluster:net                     1     36.28 948975 37610
    ## + age:class_a                     1     33.79 948977 37610
    ## + leasing_rate:Gas_Costs          1     29.28 948982 37610
    ## + class_a:cd_total_07             1     23.67 948987 37610
    ## + cluster:Gas_Costs               1     13.78 948997 37610
    ## + net:Gas_Costs                   1      9.89 949001 37610
    ## + amenities:hd_total07            1      6.83 949004 37610
    ## + size:net                        1      4.91 949006 37610
    ## + age:net                         1      3.54 949007 37610
    ## + amenities:Electricity_Costs     1      2.13 949009 37610
    ## + net:hd_total07                  1      0.81 949010 37610
    ## + net:Electricity_Costs           1      0.64 949010 37610
    ## + empl_gr                         1      0.24 949011 37610
    ## + class_a:Gas_Costs               1      0.17 949011 37610
    ## 
    ## Step:  AIC=37606.9
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + Electricity_Costs:cd_total_07 + Electricity_Costs:Precipitation + 
    ##     cd_total_07:Precipitation + Electricity_Costs:class_a + Electricity_Costs:size + 
    ##     Electricity_Costs:age + cd_total_07:size + Precipitation:size + 
    ##     age:hd_total07 + Electricity_Costs:hd_total07 + size:hd_total07 + 
    ##     Electricity_Costs:Gas_Costs + cd_total_07:Gas_Costs + cluster:size + 
    ##     cd_total_07:hd_total07 + hd_total07:Gas_Costs + Precipitation:hd_total07 + 
    ##     size:Gas_Costs + Electricity_Costs:cluster + age:Gas_Costs + 
    ##     class_a:Precipitation + leasing_rate:size + Gas_Costs:amenities + 
    ##     class_a:amenities + age:size + class_a:size + cd_total_07:cluster + 
    ##     class_a:leasing_rate + size:amenities
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + class_b                         1    458.08 948164 37605
    ## + net:cd_total_07                 1    336.80 948285 37606
    ## + cluster:Precipitation           1    312.53 948309 37606
    ## + amenities:Precipitation         1    285.40 948336 37607
    ## <none>                                        948622 37607
    ## + age:Precipitation               1    230.70 948391 37607
    ## + Precipitation:Gas_Costs         1    209.37 948412 37607
    ## + cluster:class_a                 1    206.01 948416 37607
    ## + cluster:age                     1    202.31 948419 37607
    ## + stories                         1    190.36 948431 37607
    ## + cluster:leasing_rate            1    149.43 948472 37608
    ## + amenities:cd_total_07           1    148.94 948473 37608
    ## + renovated                       1    148.12 948473 37608
    ## + leasing_rate:net                1    141.88 948480 37608
    ## + cluster:hd_total07              1    127.47 948494 37608
    ## + leasing_rate:cd_total_07        1    119.61 948502 37608
    ## + net:Precipitation               1    118.08 948504 37608
    ## + class_a:hd_total07              1    102.66 948519 37608
    ## + age:amenities                   1     84.76 948537 37608
    ## + green_rating                    1     73.54 948548 37608
    ## + leasing_rate:age                1     69.85 948552 37608
    ## + leasing_rate:Precipitation      1     68.96 948553 37608
    ## + age:cd_total_07                 1     60.25 948561 37608
    ## + amenities:hd_total07            1     52.24 948569 37608
    ## + net:amenities                   1     42.88 948579 37609
    ## + leasing_rate:hd_total07         1     42.51 948579 37609
    ## + age:class_a                     1     38.42 948583 37609
    ## + class_a:net                     1     37.89 948584 37609
    ## + cluster:amenities               1     37.71 948584 37609
    ## + leasing_rate:Electricity_Costs  1     35.14 948586 37609
    ## + cluster:net                     1     32.12 948589 37609
    ## + leasing_rate:Gas_Costs          1     30.53 948591 37609
    ## + class_a:cd_total_07             1     28.79 948593 37609
    ## + leasing_rate:amenities          1     28.75 948593 37609
    ## + cluster:Gas_Costs               1     14.57 948607 37609
    ## + net:Gas_Costs                   1     11.14 948610 37609
    ## + size:net                        1     10.68 948611 37609
    ## + age:net                         1      3.33 948618 37609
    ## + class_a:Gas_Costs               1      3.14 948618 37609
    ## + empl_gr                         1      0.84 948621 37609
    ## + net:Electricity_Costs           1      0.56 948621 37609
    ## + net:hd_total07                  1      0.10 948622 37609
    ## + amenities:Electricity_Costs     1      0.07 948622 37609
    ## 
    ## Step:  AIC=37605.13
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + age:class_b                     1   2871.98 945292 37583
    ## + size:class_b                    1   1509.88 946654 37595
    ## + class_b:Precipitation           1   1400.47 946763 37596
    ## + class_b:hd_total07              1    468.21 947695 37603
    ## + net:cd_total_07                 1    325.96 947838 37604
    ## + cluster:class_b                 1    318.98 947845 37604
    ## + cluster:Precipitation           1    316.78 947847 37605
    ## + class_b:Electricity_Costs       1    291.17 947872 37605
    ## + amenities:Precipitation         1    260.02 947904 37605
    ## <none>                                        948164 37605
    ## + age:Precipitation               1    237.60 947926 37605
    ## + stories                         1    223.93 947940 37605
    ## + renovated                       1    217.46 947946 37605
    ## + cluster:class_a                 1    209.70 947954 37605
    ## + cluster:age                     1    203.43 947960 37605
    ## + Precipitation:Gas_Costs         1    168.29 947995 37606
    ## + amenities:cd_total_07           1    151.86 948012 37606
    ## + cluster:leasing_rate            1    146.38 948017 37606
    ## + leasing_rate:net                1    138.29 948025 37606
    ## + leasing_rate:cd_total_07        1    125.86 948038 37606
    ## + cluster:hd_total07              1    119.23 948044 37606
    ## + net:Precipitation               1    118.04 948045 37606
    ## + age:cd_total_07                 1    105.25 948058 37606
    ## + leasing_rate:age                1    100.87 948063 37606
    ## + class_b:Gas_Costs               1     99.87 948064 37606
    ## + class_a:hd_total07              1     96.42 948067 37606
    ## + green_rating                    1     77.38 948086 37606
    ## + age:amenities                   1     72.78 948091 37607
    ## + leasing_rate:Precipitation      1     53.18 948110 37607
    ## + cluster:amenities               1     50.84 948113 37607
    ## + leasing_rate:class_b            1     47.30 948116 37607
    ## + class_b:net                     1     46.63 948117 37607
    ## + leasing_rate:Gas_Costs          1     46.45 948117 37607
    ## + net:amenities                   1     44.20 948119 37607
    ## + leasing_rate:hd_total07         1     44.01 948120 37607
    ## + class_b:amenities               1     43.22 948120 37607
    ## + class_a:net                     1     38.86 948125 37607
    ## + class_a:cd_total_07             1     36.18 948127 37607
    ## + amenities:hd_total07            1     36.07 948127 37607
    ## + cluster:net                     1     32.65 948131 37607
    ## + leasing_rate:amenities          1     28.55 948135 37607
    ## + leasing_rate:Electricity_Costs  1     26.36 948137 37607
    ## + class_b:cd_total_07             1     24.12 948139 37607
    ## + age:class_a                     1     21.58 948142 37607
    ## + cluster:Gas_Costs               1     15.86 948148 37607
    ## + net:Gas_Costs                   1     11.33 948152 37607
    ## + size:net                        1     10.40 948153 37607
    ## + age:net                         1      2.61 948161 37607
    ## + class_a:Gas_Costs               1      1.48 948162 37607
    ## + amenities:Electricity_Costs     1      1.08 948162 37607
    ## + empl_gr                         1      0.59 948163 37607
    ## + net:Electricity_Costs           1      0.29 948163 37607
    ## + net:hd_total07                  1      0.09 948163 37607
    ## 
    ## Step:  AIC=37583.41
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + size:class_b                    1   1397.82 943894 37574
    ## + age:class_a                     1   1200.62 944091 37575
    ## + class_b:Precipitation           1   1114.49 944177 37576
    ## + class_b:Electricity_Costs       1    644.81 944647 37580
    ## + cluster:class_b                 1    419.37 944872 37582
    ## + renovated                       1    365.80 944926 37582
    ## + net:cd_total_07                 1    333.76 944958 37583
    ## + amenities:Precipitation         1    296.63 944995 37583
    ## + stories                         1    280.61 945011 37583
    ## + cluster:Precipitation           1    255.50 945036 37583
    ## <none>                                        945292 37583
    ## + class_b:Gas_Costs               1    228.18 945063 37584
    ## + leasing_rate:cd_total_07        1    225.31 945066 37584
    ## + cluster:class_a                 1    219.80 945072 37584
    ## + cluster:age                     1    205.76 945086 37584
    ## + class_a:hd_total07              1    175.55 945116 37584
    ## + Precipitation:Gas_Costs         1    166.00 945126 37584
    ## + amenities:cd_total_07           1    142.02 945150 37584
    ## + cluster:hd_total07              1    132.73 945159 37584
    ## + leasing_rate:Gas_Costs          1    132.02 945160 37584
    ## + leasing_rate:net                1    131.38 945160 37584
    ## + net:Precipitation               1    116.35 945175 37584
    ## + cluster:leasing_rate            1    100.92 945191 37585
    ## + age:amenities                   1     99.62 945192 37585
    ## + age:Precipitation               1     96.94 945195 37585
    ## + class_b:net                     1     69.91 945222 37585
    ## + class_a:net                     1     62.37 945229 37585
    ## + age:cd_total_07                 1     56.58 945235 37585
    ## + class_b:hd_total07              1     51.37 945240 37585
    ## + leasing_rate:age                1     50.14 945241 37585
    ## + cluster:amenities               1     49.68 945242 37585
    ## + green_rating                    1     48.49 945243 37585
    ## + class_b:cd_total_07             1     45.39 945246 37585
    ## + leasing_rate:hd_total07         1     39.32 945252 37585
    ## + cluster:net                     1     37.77 945254 37585
    ## + amenities:hd_total07            1     32.18 945259 37585
    ## + leasing_rate:class_b            1     30.80 945261 37585
    ## + net:amenities                   1     25.04 945267 37585
    ## + leasing_rate:amenities          1     23.74 945268 37585
    ## + leasing_rate:Precipitation      1     21.92 945270 37585
    ## + cluster:Gas_Costs               1     18.42 945273 37585
    ## + leasing_rate:Electricity_Costs  1     17.14 945274 37585
    ## + net:Gas_Costs                   1     11.85 945280 37585
    ## + age:net                         1      9.67 945282 37585
    ## + class_b:amenities               1      9.29 945282 37585
    ## + size:net                        1      8.57 945283 37585
    ## + class_a:Gas_Costs               1      3.09 945288 37585
    ## + net:Electricity_Costs           1      1.95 945290 37585
    ## + empl_gr                         1      1.21 945290 37585
    ## + class_a:cd_total_07             1      0.45 945291 37585
    ## + amenities:Electricity_Costs     1      0.41 945291 37585
    ## + net:hd_total07                  1      0.34 945291 37585
    ## 
    ## Step:  AIC=37573.83
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + class_b:Electricity_Costs       1   1108.71 942785 37567
    ## + age:class_a                     1    978.31 942915 37568
    ## + class_b:Precipitation           1    749.84 943144 37570
    ## + cluster:class_b                 1    593.00 943301 37571
    ## + renovated                       1    433.46 943460 37572
    ## + stories                         1    359.59 943534 37573
    ## + net:cd_total_07                 1    341.13 943553 37573
    ## + amenities:Precipitation         1    333.82 943560 37573
    ## + cluster:Precipitation           1    261.31 943632 37574
    ## + leasing_rate:cd_total_07        1    249.01 943645 37574
    ## <none>                                        943894 37574
    ## + class_a:hd_total07              1    230.95 943663 37574
    ## + class_b:Gas_Costs               1    219.58 943674 37574
    ## + cluster:class_a                 1    189.08 943705 37574
    ## + class_b:amenities               1    184.90 943709 37574
    ## + Precipitation:Gas_Costs         1    170.16 943724 37574
    ## + age:amenities                   1    157.33 943736 37575
    ## + leasing_rate:Gas_Costs          1    152.86 943741 37575
    ## + leasing_rate:class_b            1    150.68 943743 37575
    ## + cluster:age                     1    144.12 943750 37575
    ## + amenities:cd_total_07           1    142.67 943751 37575
    ## + leasing_rate:net                1    134.97 943759 37575
    ## + net:Precipitation               1    117.72 943776 37575
    ## + cluster:hd_total07              1    117.14 943777 37575
    ## + age:Precipitation               1     99.02 943795 37575
    ## + cluster:leasing_rate            1     92.38 943801 37575
    ## + leasing_rate:age                1     72.86 943821 37575
    ## + class_b:net                     1     69.29 943824 37575
    ## + amenities:hd_total07            1     57.42 943836 37575
    ## + green_rating                    1     54.97 943839 37575
    ## + class_a:net                     1     52.34 943841 37575
    ## + leasing_rate:hd_total07         1     47.57 943846 37575
    ## + cluster:amenities               1     43.41 943850 37575
    ## + cluster:net                     1     35.79 943858 37576
    ## + age:cd_total_07                 1     34.16 943860 37576
    ## + net:amenities                   1     25.57 943868 37576
    ## + leasing_rate:Electricity_Costs  1     20.81 943873 37576
    ## + leasing_rate:amenities          1     20.60 943873 37576
    ## + cluster:Gas_Costs               1     16.36 943877 37576
    ## + net:Gas_Costs                   1     13.76 943880 37576
    ## + size:net                        1     11.71 943882 37576
    ## + class_b:cd_total_07             1     10.54 943883 37576
    ## + empl_gr                         1      7.28 943886 37576
    ## + leasing_rate:Precipitation      1      7.15 943887 37576
    ## + class_b:hd_total07              1      6.79 943887 37576
    ## + age:net                         1      4.71 943889 37576
    ## + net:Electricity_Costs           1      1.45 943892 37576
    ## + class_a:Gas_Costs               1      0.43 943893 37576
    ## + class_a:cd_total_07             1      0.08 943894 37576
    ## + amenities:Electricity_Costs     1      0.05 943894 37576
    ## + net:hd_total07                  1      0.00 943894 37576
    ## 
    ## Step:  AIC=37566.64
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + class_b:Precipitation           1   1841.59 940943 37553
    ## + age:class_a                     1   1182.30 941603 37559
    ## + class_b:hd_total07              1    556.15 942229 37564
    ## + net:cd_total_07                 1    422.75 942362 37565
    ## + renovated                       1    405.25 942380 37565
    ## + amenities:Precipitation         1    389.05 942396 37565
    ## + stories                         1    345.20 942440 37566
    ## + cluster:class_b                 1    329.37 942456 37566
    ## + cluster:Precipitation           1    283.33 942502 37566
    ## <none>                                        942785 37567
    ## + leasing_rate:class_b            1    196.11 942589 37567
    ## + class_a:hd_total07              1    195.71 942589 37567
    ## + leasing_rate:Electricity_Costs  1    188.69 942596 37567
    ## + cluster:class_a                 1    183.47 942602 37567
    ## + class_b:Gas_Costs               1    174.00 942611 37567
    ## + leasing_rate:cd_total_07        1    161.10 942624 37567
    ## + age:amenities                   1    151.64 942633 37567
    ## + cluster:age                     1    145.62 942639 37567
    ## + leasing_rate:net                1    132.81 942652 37568
    ## + age:Precipitation               1    125.64 942659 37568
    ## + leasing_rate:hd_total07         1    121.89 942663 37568
    ## + Precipitation:Gas_Costs         1    116.47 942669 37568
    ## + cluster:hd_total07              1    108.07 942677 37568
    ## + amenities:cd_total_07           1     99.39 942686 37568
    ## + net:Precipitation               1     94.80 942690 37568
    ## + amenities:hd_total07            1     91.22 942694 37568
    ## + cluster:leasing_rate            1     84.47 942701 37568
    ## + leasing_rate:age                1     80.16 942705 37568
    ## + class_b:net                     1     52.49 942733 37568
    ## + class_a:net                     1     51.92 942733 37568
    ## + green_rating                    1     50.46 942735 37568
    ## + class_b:amenities               1     48.10 942737 37568
    ## + class_b:cd_total_07             1     43.69 942741 37568
    ## + age:cd_total_07                 1     42.84 942742 37568
    ## + cluster:net                     1     41.44 942744 37568
    ## + cluster:amenities               1     26.63 942758 37568
    ## + net:amenities                   1     21.42 942764 37568
    ## + amenities:Electricity_Costs     1     19.17 942766 37568
    ## + leasing_rate:amenities          1     14.08 942771 37569
    ## + leasing_rate:Gas_Costs          1     11.92 942773 37569
    ## + size:net                        1     11.54 942773 37569
    ## + empl_gr                         1     11.07 942774 37569
    ## + leasing_rate:Precipitation      1      9.36 942776 37569
    ## + age:net                         1      9.32 942776 37569
    ## + cluster:Gas_Costs               1      8.06 942777 37569
    ## + class_a:Gas_Costs               1      3.31 942782 37569
    ## + net:hd_total07                  1      1.78 942783 37569
    ## + net:Electricity_Costs           1      1.30 942784 37569
    ## + net:Gas_Costs                   1      0.54 942784 37569
    ## + class_a:cd_total_07             1      0.00 942785 37569
    ## 
    ## Step:  AIC=37553.35
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + age:class_a                     1   1073.70 939870 37546
    ## + cluster:class_b                 1    451.34 940492 37552
    ## + net:cd_total_07                 1    437.80 940506 37552
    ## + renovated                       1    419.16 940524 37552
    ## + leasing_rate:Electricity_Costs  1    405.82 940538 37552
    ## + class_b:hd_total07              1    342.40 940601 37553
    ## + cluster:Precipitation           1    276.35 940667 37553
    ## + stories                         1    264.72 940679 37553
    ## + amenities:Precipitation         1    258.31 940685 37553
    ## <none>                                        940943 37553
    ## + cluster:class_a                 1    192.82 940751 37554
    ## + age:amenities                   1    187.95 940755 37554
    ## + class_a:hd_total07              1    171.16 940772 37554
    ## + leasing_rate:hd_total07         1    133.19 940810 37554
    ## + leasing_rate:class_b            1    130.58 940813 37554
    ## + leasing_rate:net                1    126.92 940817 37554
    ## + cluster:leasing_rate            1    125.61 940818 37554
    ## + leasing_rate:Precipitation      1    125.30 940818 37554
    ## + cluster:hd_total07              1    120.90 940823 37554
    ## + cluster:age                     1    118.64 940825 37554
    ## + amenities:cd_total_07           1    101.74 940842 37555
    ## + amenities:hd_total07            1    100.43 940843 37555
    ## + leasing_rate:Gas_Costs          1    100.10 940843 37555
    ## + net:Precipitation               1     98.66 940845 37555
    ## + leasing_rate:age                1     97.66 940846 37555
    ## + class_b:amenities               1     95.49 940848 37555
    ## + Precipitation:Gas_Costs         1     82.14 940861 37555
    ## + class_b:Gas_Costs               1     77.11 940866 37555
    ## + age:cd_total_07                 1     63.31 940880 37555
    ## + leasing_rate:cd_total_07        1     63.11 940880 37555
    ## + class_a:net                     1     55.79 940888 37555
    ## + class_b:net                     1     55.06 940888 37555
    ## + green_rating                    1     52.30 940891 37555
    ## + age:Precipitation               1     40.23 940903 37555
    ## + cluster:net                     1     38.46 940905 37555
    ## + amenities:Electricity_Costs     1     25.83 940918 37555
    ## + cluster:amenities               1     21.19 940922 37555
    ## + net:amenities                   1     19.27 940924 37555
    ## + leasing_rate:amenities          1     19.25 940924 37555
    ## + empl_gr                         1     12.29 940931 37555
    ## + size:net                        1      8.85 940935 37555
    ## + age:net                         1      7.85 940936 37555
    ## + cluster:Gas_Costs               1      4.91 940939 37555
    ## + net:hd_total07                  1      2.54 940941 37555
    ## + net:Electricity_Costs           1      2.17 940941 37555
    ## + class_a:Gas_Costs               1      1.43 940942 37555
    ## + class_b:cd_total_07             1      0.84 940943 37555
    ## + net:Gas_Costs                   1      0.18 940943 37555
    ## + class_a:cd_total_07             1      0.03 940943 37555
    ## 
    ## Step:  AIC=37546.42
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + cluster:class_b                 1    499.11 939371 37544
    ## + net:cd_total_07                 1    433.14 939437 37545
    ## + leasing_rate:Electricity_Costs  1    399.80 939470 37545
    ## + class_b:hd_total07              1    280.58 939589 37546
    ## + amenities:Precipitation         1    269.33 939600 37546
    ## + renovated                       1    259.37 939610 37546
    ## <none>                                        939870 37546
    ## + cluster:Precipitation           1    240.16 939630 37546
    ## + cluster:class_a                 1    202.45 939667 37547
    ## + stories                         1    174.45 939695 37547
    ## + class_b:amenities               1    156.98 939713 37547
    ## + leasing_rate:Precipitation      1    140.11 939730 37547
    ## + leasing_rate:net                1    137.68 939732 37547
    ## + cluster:leasing_rate            1    121.95 939748 37547
    ## + class_b:Gas_Costs               1    121.50 939748 37547
    ## + leasing_rate:class_b            1    118.96 939751 37547
    ## + cluster:hd_total07              1    116.49 939753 37547
    ## + cluster:age                     1    104.87 939765 37548
    ## + leasing_rate:hd_total07         1    101.85 939768 37548
    ## + green_rating                    1     94.56 939775 37548
    ## + leasing_rate:cd_total_07        1     89.26 939780 37548
    ## + net:Precipitation               1     87.87 939782 37548
    ## + class_a:hd_total07              1     86.25 939783 37548
    ## + amenities:hd_total07            1     86.23 939784 37548
    ## + age:amenities                   1     83.51 939786 37548
    ## + leasing_rate:Gas_Costs          1     82.39 939787 37548
    ## + amenities:cd_total_07           1     82.27 939787 37548
    ## + Precipitation:Gas_Costs         1     65.86 939804 37548
    ## + age:cd_total_07                 1     60.52 939809 37548
    ## + class_a:net                     1     47.47 939822 37548
    ## + class_b:net                     1     46.05 939824 37548
    ## + age:Precipitation               1     45.02 939825 37548
    ## + cluster:net                     1     38.88 939831 37548
    ## + amenities:Electricity_Costs     1     26.24 939844 37548
    ## + leasing_rate:age                1     25.76 939844 37548
    ## + cluster:amenities               1     25.66 939844 37548
    ## + empl_gr                         1     23.10 939847 37548
    ## + leasing_rate:amenities          1     22.85 939847 37548
    ## + class_a:cd_total_07             1     16.71 939853 37548
    ## + net:amenities                   1     14.54 939855 37548
    ## + cluster:Gas_Costs               1      9.99 939860 37548
    ## + size:net                        1      5.41 939864 37548
    ## + class_a:Gas_Costs               1      3.93 939866 37548
    ## + net:Electricity_Costs           1      3.10 939867 37548
    ## + net:hd_total07                  1      0.81 939869 37548
    ## + age:net                         1      0.49 939869 37548
    ## + net:Gas_Costs                   1      0.22 939870 37548
    ## + class_b:cd_total_07             1      0.10 939870 37548
    ## 
    ## Step:  AIC=37544.27
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + net:cd_total_07                 1    413.86 938957 37543
    ## + leasing_rate:Electricity_Costs  1    364.06 939007 37543
    ## + cluster:Precipitation           1    283.70 939087 37544
    ## + class_b:hd_total07              1    277.80 939093 37544
    ## + renovated                       1    265.87 939105 37544
    ## + amenities:Precipitation         1    260.15 939110 37544
    ## <none>                                        939371 37544
    ## + stories                         1    194.62 939176 37545
    ## + leasing_rate:net                1    139.56 939231 37545
    ## + class_b:amenities               1    134.73 939236 37545
    ## + leasing_rate:class_b            1    132.73 939238 37545
    ## + leasing_rate:Precipitation      1    130.27 939240 37545
    ## + cluster:leasing_rate            1    111.93 939259 37545
    ## + leasing_rate:cd_total_07        1    103.92 939267 37545
    ## + green_rating                    1     97.13 939274 37545
    ## + leasing_rate:hd_total07         1     91.88 939279 37546
    ## + age:amenities                   1     89.50 939281 37546
    ## + net:Precipitation               1     89.49 939281 37546
    ## + amenities:hd_total07            1     82.18 939288 37546
    ## + cluster:hd_total07              1     82.06 939289 37546
    ## + class_a:hd_total07              1     81.41 939289 37546
    ## + amenities:cd_total_07           1     79.24 939291 37546
    ## + cluster:amenities               1     67.92 939303 37546
    ## + Precipitation:Gas_Costs         1     62.75 939308 37546
    ## + leasing_rate:Gas_Costs          1     56.82 939314 37546
    ## + age:Precipitation               1     56.70 939314 37546
    ## + class_b:Gas_Costs               1     51.39 939319 37546
    ## + cluster:net                     1     49.08 939322 37546
    ## + class_a:net                     1     48.13 939323 37546
    ## + age:cd_total_07                 1     47.76 939323 37546
    ## + class_b:net                     1     47.09 939324 37546
    ## + cluster:age                     1     34.00 939337 37546
    ## + empl_gr                         1     25.61 939345 37546
    ## + amenities:Electricity_Costs     1     24.44 939346 37546
    ## + leasing_rate:amenities          1     22.66 939348 37546
    ## + leasing_rate:age                1     20.44 939350 37546
    ## + net:amenities                   1     19.07 939352 37546
    ## + cluster:class_a                 1      7.64 939363 37546
    ## + class_a:cd_total_07             1      6.55 939364 37546
    ## + class_b:cd_total_07             1      6.38 939364 37546
    ## + size:net                        1      4.75 939366 37546
    ## + net:Electricity_Costs           1      3.40 939367 37546
    ## + cluster:Gas_Costs               1      3.10 939368 37546
    ## + age:net                         1      0.77 939370 37546
    ## + class_a:Gas_Costs               1      0.68 939370 37546
    ## + net:hd_total07                  1      0.49 939370 37546
    ## + net:Gas_Costs                   1      0.36 939370 37546
    ## 
    ## Step:  AIC=37542.82
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net
    ## 
    ##                                  Df Sum of Sq    RSS   AIC
    ## + leasing_rate:Electricity_Costs  1    347.96 938609 37542
    ## + class_b:hd_total07              1    318.64 938638 37542
    ## + renovated                       1    270.75 938686 37543
    ## + cluster:Precipitation           1    265.97 938691 37543
    ## + net:Gas_Costs                   1    258.81 938698 37543
    ## + net:Precipitation               1    249.80 938707 37543
    ## <none>                                        938957 37543
    ## + stories                         1    197.32 938759 37543
    ## + net:hd_total07                  1    182.98 938774 37543
    ## + amenities:Precipitation         1    169.96 938787 37543
    ## + leasing_rate:Precipitation      1    151.22 938806 37544
    ## + leasing_rate:class_b            1    137.80 938819 37544
    ## + class_b:amenities               1    126.51 938830 37544
    ## + leasing_rate:net                1    114.51 938842 37544
    ## + cluster:leasing_rate            1    113.42 938843 37544
    ## + leasing_rate:cd_total_07        1    102.30 938854 37544
    ## + green_rating                    1     98.69 938858 37544
    ## + leasing_rate:hd_total07         1     91.07 938866 37544
    ## + age:amenities                   1     81.53 938875 37544
    ## + cluster:hd_total07              1     79.34 938877 37544
    ## + cluster:amenities               1     78.05 938879 37544
    ## + amenities:cd_total_07           1     72.92 938884 37544
    ## + age:cd_total_07                 1     69.32 938887 37544
    ## + amenities:hd_total07            1     63.91 938893 37544
    ## + Precipitation:Gas_Costs         1     61.97 938895 37544
    ## + class_b:Gas_Costs               1     60.94 938896 37544
    ## + class_a:hd_total07              1     58.17 938899 37544
    ## + leasing_rate:Gas_Costs          1     57.74 938899 37544
    ## + net:Electricity_Costs           1     46.25 938911 37544
    ## + cluster:net                     1     41.73 938915 37544
    ## + empl_gr                         1     36.97 938920 37545
    ## + age:Precipitation               1     34.79 938922 37545
    ## + cluster:age                     1     34.14 938923 37545
    ## + class_a:cd_total_07             1     24.76 938932 37545
    ## + net:amenities                   1     23.77 938933 37545
    ## + leasing_rate:amenities          1     22.66 938934 37545
    ## + leasing_rate:age                1     18.41 938938 37545
    ## + age:net                         1     16.05 938941 37545
    ## + class_b:net                     1     14.84 938942 37545
    ## + amenities:Electricity_Costs     1     10.22 938947 37545
    ## + cluster:class_a                 1      7.32 938949 37545
    ## + cluster:Gas_Costs               1      5.30 938951 37545
    ## + class_a:net                     1      4.56 938952 37545
    ## + size:net                        1      3.40 938953 37545
    ## + class_b:cd_total_07             1      1.40 938955 37545
    ## + class_a:Gas_Costs               1      1.32 938955 37545
    ## 
    ## Step:  AIC=37541.93
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + class_b:hd_total07           1    329.39 938279 37541
    ## + leasing_rate:Precipitation   1    315.64 938293 37541
    ## + cluster:Precipitation        1    276.53 938332 37542
    ## + net:Gas_Costs                1    268.72 938340 37542
    ## + net:Precipitation            1    247.63 938361 37542
    ## + renovated                    1    241.20 938368 37542
    ## <none>                                     938609 37542
    ## + cluster:leasing_rate         1    217.51 938391 37542
    ## + stories                      1    190.76 938418 37542
    ## + net:hd_total07               1    185.70 938423 37542
    ## + leasing_rate:class_b         1    157.18 938452 37543
    ## + amenities:Precipitation      1    154.96 938454 37543
    ## + leasing_rate:net             1    134.22 938475 37543
    ## + class_b:amenities            1    108.91 938500 37543
    ## + green_rating                 1     98.35 938510 37543
    ## + cluster:amenities            1     85.97 938523 37543
    ## + cluster:hd_total07           1     80.93 938528 37543
    ## + leasing_rate:cd_total_07     1     78.59 938530 37543
    ## + amenities:cd_total_07        1     78.28 938531 37543
    ## + Precipitation:Gas_Costs      1     77.41 938531 37543
    ## + age:amenities                1     69.21 938540 37543
    ## + age:cd_total_07              1     64.26 938545 37543
    ## + class_a:hd_total07           1     58.75 938550 37543
    ## + net:Electricity_Costs        1     53.51 938555 37543
    ## + amenities:hd_total07         1     48.41 938560 37544
    ## + cluster:age                  1     40.76 938568 37544
    ## + empl_gr                      1     39.08 938570 37544
    ## + cluster:net                  1     38.67 938570 37544
    ## + leasing_rate:amenities       1     37.60 938571 37544
    ## + age:Precipitation            1     37.51 938571 37544
    ## + class_a:cd_total_07          1     24.18 938585 37544
    ## + net:amenities                1     22.78 938586 37544
    ## + class_b:net                  1     17.59 938591 37544
    ## + class_b:Gas_Costs            1     16.67 938592 37544
    ## + leasing_rate:hd_total07      1     15.04 938594 37544
    ## + age:net                      1     12.71 938596 37544
    ## + leasing_rate:Gas_Costs       1      9.19 938600 37544
    ## + class_b:cd_total_07          1      8.96 938600 37544
    ## + class_a:net                  1      7.04 938602 37544
    ## + cluster:Gas_Costs            1      6.91 938602 37544
    ## + amenities:Electricity_Costs  1      4.53 938604 37544
    ## + cluster:class_a              1      3.63 938605 37544
    ## + leasing_rate:age             1      3.09 938606 37544
    ## + class_a:Gas_Costs            1      2.28 938607 37544
    ## + size:net                     1      2.10 938607 37544
    ## 
    ## Step:  AIC=37541.18
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + class_a:hd_total07           1   1065.86 937214 37534
    ## + leasing_rate:Precipitation   1    341.99 937937 37540
    ## + net:Gas_Costs                1    290.77 937989 37541
    ## + cluster:Precipitation        1    263.04 938016 37541
    ## + net:Precipitation            1    257.44 938022 37541
    ## <none>                                     938279 37541
    ## + renovated                    1    235.91 938044 37541
    ## + stories                      1    227.18 938052 37541
    ## + cluster:leasing_rate         1    210.98 938068 37541
    ## + leasing_rate:class_b         1    188.90 938091 37542
    ## + net:hd_total07               1    178.39 938101 37542
    ## + class_b:cd_total_07          1    172.15 938107 37542
    ## + amenities:Precipitation      1    171.55 938108 37542
    ## + leasing_rate:net             1    143.98 938135 37542
    ## + class_b:amenities            1    102.39 938177 37542
    ## + green_rating                 1     93.39 938186 37542
    ## + Precipitation:Gas_Costs      1     86.51 938193 37542
    ## + amenities:cd_total_07        1     82.72 938197 37542
    ## + age:cd_total_07              1     80.55 938199 37543
    ## + cluster:amenities            1     76.34 938203 37543
    ## + cluster:hd_total07           1     73.80 938206 37543
    ## + amenities:hd_total07         1     66.74 938213 37543
    ## + leasing_rate:cd_total_07     1     64.46 938215 37543
    ## + net:Electricity_Costs        1     63.92 938216 37543
    ## + age:amenities                1     62.26 938217 37543
    ## + cluster:age                  1     51.22 938228 37543
    ## + empl_gr                      1     48.67 938231 37543
    ## + leasing_rate:amenities       1     46.71 938233 37543
    ## + cluster:net                  1     34.42 938245 37543
    ## + age:Precipitation            1     30.26 938249 37543
    ## + net:amenities                1     19.82 938260 37543
    ## + leasing_rate:Gas_Costs       1     16.42 938263 37543
    ## + class_b:net                  1     15.86 938264 37543
    ## + leasing_rate:hd_total07      1     14.46 938265 37543
    ## + age:net                      1     13.29 938266 37543
    ## + class_b:Gas_Costs            1     10.54 938269 37543
    ## + leasing_rate:age             1      7.69 938272 37543
    ## + amenities:Electricity_Costs  1      7.61 938272 37543
    ## + cluster:Gas_Costs            1      6.72 938273 37543
    ## + class_a:net                  1      6.15 938273 37543
    ## + size:net                     1      2.56 938277 37543
    ## + class_a:Gas_Costs            1      1.04 938278 37543
    ## + class_a:cd_total_07          1      0.86 938279 37543
    ## + cluster:class_a              1      0.85 938279 37543
    ## 
    ## Step:  AIC=37534.29
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + leasing_rate:Precipitation   1    394.66 936819 37533
    ## + renovated                    1    312.95 936901 37534
    ## + cluster:Precipitation        1    272.03 936942 37534
    ## <none>                                     937214 37534
    ## + net:Precipitation            1    239.02 936975 37534
    ## + net:Gas_Costs                1    232.08 936981 37534
    ## + leasing_rate:class_b         1    209.17 937004 37535
    ## + cluster:leasing_rate         1    205.21 937008 37535
    ## + net:hd_total07               1    176.10 937037 37535
    ## + age:cd_total_07              1    171.55 937042 37535
    ## + stories                      1    153.32 937060 37535
    ## + amenities:Precipitation      1    151.54 937062 37535
    ## + class_b:cd_total_07          1    145.68 937068 37535
    ## + leasing_rate:net             1    137.49 937076 37535
    ## + class_b:amenities            1    112.11 937101 37535
    ## + class_a:cd_total_07          1    102.72 937111 37535
    ## + leasing_rate:cd_total_07     1    101.48 937112 37535
    ## + green_rating                 1     95.34 937118 37535
    ## + leasing_rate:hd_total07      1     80.46 937133 37536
    ## + cluster:amenities            1     76.83 937137 37536
    ## + age:amenities                1     74.10 937139 37536
    ## + cluster:age                  1     71.64 937142 37536
    ## + cluster:hd_total07           1     64.11 937149 37536
    ## + Precipitation:Gas_Costs      1     59.03 937155 37536
    ## + leasing_rate:amenities       1     52.79 937161 37536
    ## + empl_gr                      1     45.82 937168 37536
    ## + net:Electricity_Costs        1     40.01 937174 37536
    ## + age:Precipitation            1     33.91 937180 37536
    ## + cluster:net                  1     33.18 937180 37536
    ## + leasing_rate:Gas_Costs       1     25.20 937188 37536
    ## + amenities:cd_total_07        1     22.86 937191 37536
    ## + net:amenities                1     16.78 937197 37536
    ## + age:net                      1     14.65 937199 37536
    ## + class_b:net                  1     12.99 937201 37536
    ## + class_b:Gas_Costs            1     11.76 937202 37536
    ## + class_a:net                  1      7.85 937206 37536
    ## + class_a:Gas_Costs            1      7.57 937206 37536
    ## + cluster:Gas_Costs            1      6.45 937207 37536
    ## + amenities:Electricity_Costs  1      6.22 937207 37536
    ## + amenities:hd_total07         1      6.07 937207 37536
    ## + leasing_rate:age             1      3.82 937210 37536
    ## + size:net                     1      1.62 937212 37536
    ## + cluster:class_a              1      1.45 937212 37536
    ## 
    ## Step:  AIC=37533
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + leasing_rate:class_b         1    376.46 936442 37532
    ## + renovated                    1    318.10 936501 37532
    ## + cluster:Precipitation        1    283.59 936535 37533
    ## <none>                                     936819 37533
    ## + net:Precipitation            1    236.93 936582 37533
    ## + net:Gas_Costs                1    219.58 936599 37533
    ## + class_b:cd_total_07          1    198.79 936620 37533
    ## + amenities:Precipitation      1    191.32 936628 37533
    ## + leasing_rate:cd_total_07     1    176.36 936643 37534
    ## + age:cd_total_07              1    174.26 936645 37534
    ## + stories                      1    172.52 936646 37534
    ## + net:hd_total07               1    172.40 936646 37534
    ## + cluster:leasing_rate         1    142.02 936677 37534
    ## + leasing_rate:net             1    130.24 936689 37534
    ## + leasing_rate:Gas_Costs       1    124.77 936694 37534
    ## + class_b:amenities            1    107.66 936711 37534
    ## + class_a:cd_total_07          1     93.99 936725 37534
    ## + green_rating                 1     85.27 936734 37534
    ## + age:amenities                1     78.91 936740 37534
    ## + cluster:age                  1     78.10 936741 37534
    ## + cluster:amenities            1     73.13 936746 37534
    ## + Precipitation:Gas_Costs      1     69.39 936750 37534
    ## + cluster:hd_total07           1     67.18 936752 37534
    ## + leasing_rate:amenities       1     59.75 936759 37534
    ## + empl_gr                      1     52.32 936767 37535
    ## + age:Precipitation            1     40.35 936779 37535
    ## + net:Electricity_Costs        1     36.56 936782 37535
    ## + cluster:net                  1     33.17 936786 37535
    ## + amenities:cd_total_07        1     29.01 936790 37535
    ## + leasing_rate:age             1     24.28 936795 37535
    ## + leasing_rate:hd_total07      1     21.04 936798 37535
    ## + net:amenities                1     15.80 936803 37535
    ## + age:net                      1     14.94 936804 37535
    ## + class_b:net                  1     13.56 936805 37535
    ## + class_a:Gas_Costs            1     10.34 936809 37535
    ## + amenities:hd_total07         1      9.09 936810 37535
    ## + amenities:Electricity_Costs  1      8.43 936810 37535
    ## + class_a:net                  1      8.38 936811 37535
    ## + cluster:Gas_Costs            1      6.93 936812 37535
    ## + size:net                     1      2.00 936817 37535
    ## + class_b:Gas_Costs            1      0.92 936818 37535
    ## + cluster:class_a              1      0.13 936819 37535
    ## 
    ## Step:  AIC=37531.86
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + renovated                    1    316.51 936126 37531
    ## + cluster:Precipitation        1    285.91 936157 37531
    ## <none>                                     936442 37532
    ## + net:Precipitation            1    235.29 936207 37532
    ## + amenities:Precipitation      1    200.41 936242 37532
    ## + net:Gas_Costs                1    195.35 936247 37532
    ## + stories                      1    184.71 936258 37532
    ## + class_b:cd_total_07          1    171.62 936271 37532
    ## + age:cd_total_07              1    171.33 936271 37532
    ## + net:hd_total07               1    164.45 936278 37532
    ## + cluster:leasing_rate         1    158.75 936284 37533
    ## + leasing_rate:cd_total_07     1    143.04 936299 37533
    ## + leasing_rate:net             1    134.59 936308 37533
    ## + leasing_rate:Gas_Costs       1    118.32 936324 37533
    ## + green_rating                 1     90.37 936352 37533
    ## + class_a:cd_total_07          1     82.38 936360 37533
    ## + cluster:amenities            1     81.19 936361 37533
    ## + cluster:age                  1     79.67 936363 37533
    ## + class_b:amenities            1     72.62 936370 37533
    ## + cluster:hd_total07           1     67.87 936375 37533
    ## + Precipitation:Gas_Costs      1     66.67 936376 37533
    ## + age:amenities                1     66.26 936376 37533
    ## + empl_gr                      1     55.67 936387 37533
    ## + age:Precipitation            1     42.27 936400 37534
    ## + amenities:cd_total_07        1     38.74 936404 37534
    ## + cluster:net                  1     35.00 936407 37534
    ## + leasing_rate:amenities       1     33.55 936409 37534
    ## + net:Electricity_Costs        1     28.20 936414 37534
    ## + leasing_rate:hd_total07      1     24.28 936418 37534
    ## + net:amenities                1     18.28 936424 37534
    ## + age:net                      1     17.80 936425 37534
    ## + class_b:net                  1     13.13 936429 37534
    ## + amenities:hd_total07         1      9.98 936432 37534
    ## + amenities:Electricity_Costs  1      7.23 936435 37534
    ## + class_a:net                  1      6.25 936436 37534
    ## + class_a:Gas_Costs            1      5.36 936437 37534
    ## + cluster:Gas_Costs            1      5.27 936437 37534
    ## + size:net                     1      4.13 936438 37534
    ## + cluster:class_a              1      1.09 936441 37534
    ## + class_b:Gas_Costs            1      0.59 936442 37534
    ## + leasing_rate:age             1      0.00 936442 37534
    ## 
    ## Step:  AIC=37531.21
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + renovated:hd_total07         1   1174.05 934952 37523
    ## + age:renovated                1   1123.52 935002 37524
    ## + renovated:Precipitation      1    355.14 935771 37530
    ## + cluster:Precipitation        1    291.81 935834 37531
    ## + net:Precipitation            1    248.71 935877 37531
    ## <none>                                     936126 37531
    ## + net:Gas_Costs                1    212.25 935914 37531
    ## + amenities:Precipitation      1    183.42 935943 37532
    ## + class_b:cd_total_07          1    178.66 935947 37532
    ## + stories                      1    169.07 935957 37532
    ## + net:hd_total07               1    166.54 935959 37532
    ## + leasing_rate:cd_total_07     1    161.24 935965 37532
    ## + cluster:leasing_rate         1    159.02 935967 37532
    ## + age:cd_total_07              1    148.93 935977 37532
    ## + leasing_rate:renovated       1    131.73 935994 37532
    ## + leasing_rate:net             1    127.34 935999 37532
    ## + leasing_rate:Gas_Costs       1    118.15 936008 37532
    ## + renovated:class_a            1    113.42 936013 37532
    ## + green_rating                 1     92.79 936033 37532
    ## + class_a:cd_total_07          1     86.88 936039 37532
    ## + cluster:amenities            1     80.39 936046 37533
    ## + Precipitation:Gas_Costs      1     77.09 936049 37533
    ## + cluster:age                  1     77.07 936049 37533
    ## + class_b:amenities            1     68.64 936057 37533
    ## + size:renovated               1     64.49 936061 37533
    ## + cluster:hd_total07           1     64.17 936062 37533
    ## + age:amenities                1     51.68 936074 37533
    ## + empl_gr                      1     48.06 936078 37533
    ## + age:Precipitation            1     42.50 936083 37533
    ## + cluster:renovated            1     41.03 936085 37533
    ## + amenities:cd_total_07        1     39.63 936086 37533
    ## + cluster:net                  1     35.90 936090 37533
    ## + net:Electricity_Costs        1     35.81 936090 37533
    ## + renovated:Electricity_Costs  1     33.62 936092 37533
    ## + leasing_rate:amenities       1     30.65 936095 37533
    ## + renovated:net                1     28.29 936098 37533
    ## + leasing_rate:hd_total07      1     27.34 936099 37533
    ## + age:net                      1     18.53 936107 37533
    ## + net:amenities                1     16.59 936109 37533
    ## + class_b:net                  1     12.62 936113 37533
    ## + renovated:class_b            1      8.93 936117 37533
    ## + renovated:Gas_Costs          1      8.58 936117 37533
    ## + class_a:net                  1      6.93 936119 37533
    ## + amenities:hd_total07         1      6.85 936119 37533
    ## + class_a:Gas_Costs            1      6.54 936119 37533
    ## + amenities:Electricity_Costs  1      5.92 936120 37533
    ## + renovated:amenities          1      5.47 936120 37533
    ## + cluster:Gas_Costs            1      5.12 936121 37533
    ## + size:net                     1      2.50 936123 37533
    ## + class_b:Gas_Costs            1      1.26 936125 37533
    ## + cluster:class_a              1      1.05 936125 37533
    ## + renovated:cd_total_07        1      0.70 936125 37533
    ## + leasing_rate:age             1      0.11 936126 37533
    ## 
    ## Step:  AIC=37523.4
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + age:renovated                1    732.53 934219 37519
    ## + renovated:Electricity_Costs  1    597.77 934354 37520
    ## + cluster:Precipitation        1    286.98 934665 37523
    ## + net:Gas_Costs                1    257.14 934695 37523
    ## <none>                                     934952 37523
    ## + net:Precipitation            1    238.80 934713 37523
    ## + age:cd_total_07              1    204.27 934748 37524
    ## + stories                      1    193.98 934758 37524
    ## + leasing_rate:cd_total_07     1    160.50 934791 37524
    ## + amenities:Precipitation      1    156.33 934796 37524
    ## + net:hd_total07               1    156.10 934796 37524
    ## + class_a:cd_total_07          1    138.79 934813 37524
    ## + cluster:renovated            1    137.64 934814 37524
    ## + class_b:cd_total_07          1    134.06 934818 37524
    ## + leasing_rate:Gas_Costs       1    133.94 934818 37524
    ## + cluster:leasing_rate         1    133.81 934818 37524
    ## + leasing_rate:renovated       1    129.10 934823 37524
    ## + leasing_rate:net             1    126.50 934825 37524
    ## + renovated:Precipitation      1    120.71 934831 37524
    ## + renovated:cd_total_07        1    117.26 934835 37524
    ## + green_rating                 1     93.75 934858 37525
    ## + Precipitation:Gas_Costs      1     91.28 934861 37525
    ## + cluster:age                  1     82.68 934869 37525
    ## + class_b:amenities            1     73.18 934879 37525
    ## + cluster:amenities            1     71.27 934881 37525
    ## + empl_gr                      1     69.18 934883 37525
    ## + age:amenities                1     57.04 934895 37525
    ## + cluster:hd_total07           1     53.98 934898 37525
    ## + net:Electricity_Costs        1     47.77 934904 37525
    ## + amenities:cd_total_07        1     46.05 934906 37525
    ## + renovated:class_a            1     43.40 934908 37525
    ## + class_a:Gas_Costs            1     35.89 934916 37525
    ## + cluster:net                  1     31.54 934920 37525
    ## + renovated:net                1     27.28 934925 37525
    ## + amenities:hd_total07         1     24.08 934928 37525
    ## + leasing_rate:amenities       1     20.18 934932 37525
    ## + size:renovated               1     16.83 934935 37525
    ## + class_b:net                  1     15.15 934937 37525
    ## + leasing_rate:hd_total07      1     13.64 934938 37525
    ## + renovated:amenities          1     12.28 934940 37525
    ## + class_a:net                  1     11.84 934940 37525
    ## + net:amenities                1     11.49 934940 37525
    ## + amenities:Electricity_Costs  1     11.39 934940 37525
    ## + age:net                      1     10.98 934941 37525
    ## + class_b:Gas_Costs            1      8.15 934944 37525
    ## + age:Precipitation            1      7.37 934945 37525
    ## + cluster:Gas_Costs            1      5.21 934947 37525
    ## + renovated:class_b            1      3.72 934948 37525
    ## + size:net                     1      1.59 934950 37525
    ## + leasing_rate:age             1      1.03 934951 37525
    ## + cluster:class_a              1      0.92 934951 37525
    ## + renovated:Gas_Costs          1      0.01 934952 37525
    ## 
    ## Step:  AIC=37519.27
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + renovated:Electricity_Costs  1    380.19 933839 37518
    ## + age:cd_total_07              1    271.33 933948 37519
    ## + cluster:Precipitation        1    264.49 933955 37519
    ## + renovated:cd_total_07        1    261.34 933958 37519
    ## + net:Precipitation            1    259.23 933960 37519
    ## + net:Gas_Costs                1    250.31 933969 37519
    ## <none>                                     934219 37519
    ## + class_a:cd_total_07          1    180.75 934039 37520
    ## + amenities:Precipitation      1    174.45 934045 37520
    ## + stories                      1    160.57 934059 37520
    ## + size:renovated               1    160.38 934059 37520
    ## + leasing_rate:cd_total_07     1    150.25 934069 37520
    ## + net:hd_total07               1    147.56 934072 37520
    ## + cluster:leasing_rate         1    143.56 934076 37520
    ## + renovated:Precipitation      1    140.93 934078 37520
    ## + cluster:renovated            1    124.62 934095 37520
    ## + Precipitation:Gas_Costs      1    117.65 934102 37520
    ## + leasing_rate:Gas_Costs       1    114.17 934105 37520
    ## + leasing_rate:net             1    111.72 934108 37520
    ## + green_rating                 1    109.04 934110 37520
    ## + empl_gr                      1     91.10 934128 37521
    ## + age:amenities                1     90.58 934129 37521
    ## + class_b:amenities            1     90.08 934129 37521
    ## + cluster:age                  1     83.49 934136 37521
    ## + class_b:cd_total_07          1     81.90 934137 37521
    ## + cluster:amenities            1     68.21 934151 37521
    ## + leasing_rate:renovated       1     54.93 934164 37521
    ## + cluster:hd_total07           1     53.27 934166 37521
    ## + renovated:class_a            1     51.48 934168 37521
    ## + amenities:cd_total_07        1     49.00 934170 37521
    ## + renovated:class_b            1     48.47 934171 37521
    ## + net:Electricity_Costs        1     43.96 934175 37521
    ## + class_a:Gas_Costs            1     38.05 934181 37521
    ## + cluster:net                  1     37.29 934182 37521
    ## + amenities:hd_total07         1     28.82 934191 37521
    ## + renovated:amenities          1     21.64 934198 37521
    ## + class_b:net                  1     18.47 934201 37521
    ## + leasing_rate:amenities       1     15.95 934203 37521
    ## + age:net                      1     13.46 934206 37521
    ## + class_a:net                  1     12.76 934207 37521
    ## + class_b:Gas_Costs            1     11.32 934208 37521
    ## + leasing_rate:hd_total07      1     10.83 934209 37521
    ## + amenities:Electricity_Costs  1     10.06 934209 37521
    ## + renovated:net                1      8.91 934210 37521
    ## + net:amenities                1      7.81 934212 37521
    ## + cluster:Gas_Costs            1      6.39 934213 37521
    ## + leasing_rate:age             1      2.13 934217 37521
    ## + renovated:Gas_Costs          1      1.19 934218 37521
    ## + age:Precipitation            1      1.10 934218 37521
    ## + cluster:class_a              1      0.78 934219 37521
    ## + size:net                     1      0.62 934219 37521
    ## 
    ## Step:  AIC=37518.09
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated + Electricity_Costs:renovated
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + renovated:cd_total_07        1    602.68 933236 37515
    ## + age:cd_total_07              1    317.10 933522 37517
    ## + cluster:Precipitation        1    269.10 933570 37518
    ## + net:Precipitation            1    239.69 933599 37518
    ## <none>                                     933839 37518
    ## + amenities:Precipitation      1    219.01 933620 37518
    ## + net:Gas_Costs                1    213.20 933626 37518
    ## + renovated:Precipitation      1    202.16 933637 37518
    ## + class_a:cd_total_07          1    187.76 933651 37519
    ## + leasing_rate:cd_total_07     1    167.92 933671 37519
    ## + net:hd_total07               1    139.01 933700 37519
    ## + cluster:leasing_rate         1    137.55 933702 37519
    ## + stories                      1    134.56 933705 37519
    ## + size:renovated               1    129.02 933710 37519
    ## + green_rating                 1    122.57 933717 37519
    ## + leasing_rate:Gas_Costs       1    117.02 933722 37519
    ## + Precipitation:Gas_Costs      1    105.94 933733 37519
    ## + age:amenities                1    102.95 933736 37519
    ## + leasing_rate:net             1    100.43 933739 37519
    ## + class_b:amenities            1     94.14 933745 37519
    ## + leasing_rate:renovated       1     91.81 933747 37519
    ## + class_b:cd_total_07          1     82.39 933757 37519
    ## + cluster:age                  1     79.61 933760 37519
    ## + empl_gr                      1     77.54 933762 37519
    ## + cluster:renovated            1     76.40 933763 37519
    ## + cluster:amenities            1     67.17 933772 37520
    ## + amenities:cd_total_07        1     58.44 933781 37520
    ## + amenities:hd_total07         1     42.00 933797 37520
    ## + renovated:amenities          1     38.92 933800 37520
    ## + cluster:net                  1     38.17 933801 37520
    ## + renovated:class_b            1     37.71 933801 37520
    ## + cluster:hd_total07           1     37.70 933801 37520
    ## + renovated:class_a            1     31.07 933808 37520
    ## + net:Electricity_Costs        1     29.26 933810 37520
    ## + class_b:net                  1     17.32 933822 37520
    ## + class_a:Gas_Costs            1     17.14 933822 37520
    ## + leasing_rate:hd_total07      1     17.09 933822 37520
    ## + age:net                      1     17.08 933822 37520
    ## + age:Precipitation            1     14.98 933824 37520
    ## + leasing_rate:amenities       1     11.64 933828 37520
    ## + class_a:net                  1     10.89 933828 37520
    ## + net:amenities                1      9.17 933830 37520
    ## + renovated:net                1      7.62 933832 37520
    ## + amenities:Electricity_Costs  1      7.51 933832 37520
    ## + cluster:Gas_Costs            1      5.93 933833 37520
    ## + renovated:Gas_Costs          1      5.89 933833 37520
    ## + class_b:Gas_Costs            1      2.35 933837 37520
    ## + size:net                     1      1.13 933838 37520
    ## + cluster:class_a              1      0.86 933838 37520
    ## + leasing_rate:age             1      0.66 933838 37520
    ## 
    ## Step:  AIC=37515.04
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated + Electricity_Costs:renovated + cd_total_07:renovated
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + amenities:Precipitation      1   279.953 932957 37515
    ## + cluster:Precipitation        1   278.902 932958 37515
    ## + renovated:Gas_Costs          1   277.287 932959 37515
    ## <none>                                     933236 37515
    ## + net:Precipitation            1   218.584 933018 37515
    ## + class_b:cd_total_07          1   176.702 933060 37516
    ## + leasing_rate:cd_total_07     1   162.166 933074 37516
    ## + net:Gas_Costs                1   160.031 933076 37516
    ## + cluster:renovated            1   143.501 933093 37516
    ## + net:hd_total07               1   139.279 933097 37516
    ## + stories                      1   138.866 933098 37516
    ## + cluster:leasing_rate         1   136.405 933100 37516
    ## + leasing_rate:Gas_Costs       1   117.929 933119 37516
    ## + age:amenities                1   115.682 933121 37516
    ## + green_rating                 1   112.593 933124 37516
    ## + Precipitation:Gas_Costs      1   110.229 933126 37516
    ## + class_b:amenities            1   106.936 933130 37516
    ## + leasing_rate:net             1    85.988 933150 37516
    ## + age:cd_total_07              1    81.565 933155 37516
    ## + class_a:cd_total_07          1    80.967 933156 37516
    ## + cluster:age                  1    78.036 933158 37516
    ## + size:renovated               1    75.912 933161 37516
    ## + renovated:Precipitation      1    75.868 933161 37516
    ## + empl_gr                      1    74.563 933162 37516
    ## + cluster:amenities            1    64.769 933172 37516
    ## + leasing_rate:renovated       1    64.273 933172 37516
    ## + amenities:cd_total_07        1    54.001 933182 37517
    ## + renovated:class_a            1    51.525 933185 37517
    ## + renovated:class_b            1    48.754 933188 37517
    ## + cluster:net                  1    41.983 933194 37517
    ## + amenities:hd_total07         1    41.723 933195 37517
    ## + age:Precipitation            1    38.170 933198 37517
    ## + cluster:hd_total07           1    32.199 933204 37517
    ## + renovated:net                1    24.359 933212 37517
    ## + renovated:amenities          1    24.285 933212 37517
    ## + class_b:net                  1    17.330 933219 37517
    ## + leasing_rate:amenities       1    13.817 933223 37517
    ## + leasing_rate:hd_total07      1    13.374 933223 37517
    ## + net:Electricity_Costs        1    12.640 933224 37517
    ## + class_a:net                  1    11.958 933225 37517
    ## + age:net                      1    11.611 933225 37517
    ## + net:amenities                1     9.348 933227 37517
    ## + amenities:Electricity_Costs  1     8.990 933227 37517
    ## + cluster:Gas_Costs            1     4.303 933232 37517
    ## + class_b:Gas_Costs            1     3.042 933233 37517
    ## + cluster:class_a              1     1.816 933235 37517
    ## + size:net                     1     1.184 933235 37517
    ## + class_a:Gas_Costs            1     0.817 933236 37517
    ## + leasing_rate:age             1     0.212 933236 37517
    ## 
    ## Step:  AIC=37514.69
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated + Electricity_Costs:renovated + cd_total_07:renovated + 
    ##     Precipitation:amenities
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + cluster:Precipitation        1   282.103 932674 37514
    ## + net:Gas_Costs                1   269.001 932688 37514
    ## + net:Precipitation            1   250.455 932706 37515
    ## <none>                                     932957 37515
    ## + renovated:Gas_Costs          1   235.207 932721 37515
    ## + class_b:cd_total_07          1   205.682 932751 37515
    ## + leasing_rate:cd_total_07     1   175.177 932781 37515
    ## + net:hd_total07               1   143.693 932813 37515
    ## + cluster:renovated            1   139.311 932817 37516
    ## + leasing_rate:Gas_Costs       1   132.212 932824 37516
    ## + cluster:leasing_rate         1   131.010 932826 37516
    ## + stories                      1   105.731 932851 37516
    ## + green_rating                 1   102.034 932854 37516
    ## + Precipitation:Gas_Costs      1    98.067 932858 37516
    ## + renovated:Precipitation      1    92.871 932864 37516
    ## + cluster:amenities            1    87.717 932869 37516
    ## + leasing_rate:net             1    86.158 932870 37516
    ## + cluster:age                  1    79.250 932877 37516
    ## + size:renovated               1    76.518 932880 37516
    ## + class_a:cd_total_07          1    68.536 932888 37516
    ## + age:amenities                1    58.708 932898 37516
    ## + age:cd_total_07              1    58.354 932898 37516
    ## + class_b:amenities            1    57.552 932899 37516
    ## + empl_gr                      1    56.999 932900 37516
    ## + renovated:class_a            1    54.256 932902 37516
    ## + leasing_rate:renovated       1    54.030 932902 37516
    ## + age:Precipitation            1    49.342 932907 37516
    ## + renovated:amenities          1    48.034 932908 37516
    ## + renovated:class_b            1    46.386 932910 37516
    ## + net:Electricity_Costs        1    37.081 932919 37516
    ## + class_b:net                  1    32.161 932924 37516
    ## + cluster:hd_total07           1    30.530 932926 37516
    ## + cluster:net                  1    30.030 932926 37516
    ## + class_a:net                  1    26.894 932930 37516
    ## + amenities:cd_total_07        1    25.226 932931 37516
    ## + renovated:net                1    20.194 932936 37517
    ## + leasing_rate:hd_total07      1    16.377 932940 37517
    ## + net:amenities                1    12.727 932944 37517
    ## + leasing_rate:amenities       1    11.526 932945 37517
    ## + amenities:Electricity_Costs  1     9.103 932947 37517
    ## + class_b:Gas_Costs            1     8.619 932948 37517
    ## + cluster:Gas_Costs            1     5.249 932951 37517
    ## + age:net                      1     4.440 932952 37517
    ## + cluster:class_a              1     0.993 932956 37517
    ## + class_a:Gas_Costs            1     0.457 932956 37517
    ## + leasing_rate:age             1     0.135 932956 37517
    ## + size:net                     1     0.060 932956 37517
    ## + amenities:hd_total07         1     0.001 932957 37517
    ## 
    ## Step:  AIC=37514.33
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated + Electricity_Costs:renovated + cd_total_07:renovated + 
    ##     Precipitation:amenities + Precipitation:cluster
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + cluster:Gas_Costs            1    329.85 932345 37514
    ## + net:Gas_Costs                1    267.24 932407 37514
    ## + net:Precipitation            1    255.82 932419 37514
    ## + renovated:Gas_Costs          1    242.72 932432 37514
    ## <none>                                     932674 37514
    ## + class_b:cd_total_07          1    205.45 932469 37515
    ## + leasing_rate:cd_total_07     1    176.89 932498 37515
    ## + cluster:renovated            1    164.87 932510 37515
    ## + net:hd_total07               1    158.60 932516 37515
    ## + leasing_rate:Gas_Costs       1    141.76 932533 37515
    ## + cluster:leasing_rate         1    118.96 932555 37515
    ## + stories                      1    111.68 932563 37515
    ## + green_rating                 1    105.38 932569 37515
    ## + cluster:amenities            1     95.34 932579 37516
    ## + renovated:Precipitation      1     86.22 932588 37516
    ## + leasing_rate:net             1     84.57 932590 37516
    ## + class_a:cd_total_07          1     82.89 932592 37516
    ## + age:cd_total_07              1     75.83 932599 37516
    ## + size:renovated               1     73.53 932601 37516
    ## + Precipitation:Gas_Costs      1     65.91 932609 37516
    ## + leasing_rate:renovated       1     59.53 932615 37516
    ## + age:amenities                1     57.90 932617 37516
    ## + class_b:amenities            1     55.66 932619 37516
    ## + cluster:age                  1     51.35 932623 37516
    ## + renovated:class_a            1     47.52 932627 37516
    ## + empl_gr                      1     46.88 932628 37516
    ## + renovated:amenities          1     46.73 932628 37516
    ## + renovated:class_b            1     42.60 932632 37516
    ## + net:Electricity_Costs        1     40.07 932634 37516
    ## + age:Precipitation            1     36.90 932638 37516
    ## + class_b:net                  1     31.01 932643 37516
    ## + cluster:net                  1     29.96 932644 37516
    ## + class_a:net                  1     26.58 932648 37516
    ## + amenities:cd_total_07        1     26.46 932648 37516
    ## + renovated:net                1     20.15 932654 37516
    ## + leasing_rate:hd_total07      1     17.75 932657 37516
    ## + class_b:Gas_Costs            1     14.39 932660 37516
    ## + net:amenities                1     14.07 932660 37516
    ## + leasing_rate:amenities       1     10.56 932664 37516
    ## + amenities:Electricity_Costs  1      9.86 932665 37516
    ## + age:net                      1      6.00 932668 37516
    ## + cluster:class_a              1      2.55 932672 37516
    ## + cluster:hd_total07           1      0.17 932674 37516
    ## + amenities:hd_total07         1      0.15 932674 37516
    ## + class_a:Gas_Costs            1      0.12 932674 37516
    ## + size:net                     1      0.03 932674 37516
    ## + leasing_rate:age             1      0.02 932674 37516
    ## 
    ## Step:  AIC=37513.56
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated + Electricity_Costs:renovated + cd_total_07:renovated + 
    ##     Precipitation:amenities + Precipitation:cluster + cluster:Gas_Costs
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + net:Gas_Costs                1   267.612 932077 37513
    ## + net:Precipitation            1   265.900 932079 37513
    ## <none>                                     932345 37514
    ## + renovated:Gas_Costs          1   219.610 932125 37514
    ## + class_b:cd_total_07          1   197.706 932147 37514
    ## + cluster:renovated            1   175.514 932169 37514
    ## + leasing_rate:cd_total_07     1   168.413 932176 37514
    ## + net:hd_total07               1   162.569 932182 37514
    ## + leasing_rate:Gas_Costs       1   147.252 932197 37514
    ## + cluster:leasing_rate         1   139.514 932205 37514
    ## + stories                      1   120.396 932224 37515
    ## + green_rating                 1    99.671 932245 37515
    ## + renovated:Precipitation      1    84.622 932260 37515
    ## + class_a:cd_total_07          1    84.428 932260 37515
    ## + leasing_rate:net             1    82.933 932262 37515
    ## + cluster:amenities            1    81.584 932263 37515
    ## + size:renovated               1    77.611 932267 37515
    ## + age:cd_total_07              1    71.207 932273 37515
    ## + class_b:amenities            1    63.745 932281 37515
    ## + age:amenities                1    56.272 932288 37515
    ## + leasing_rate:renovated       1    54.565 932290 37515
    ## + renovated:class_a            1    49.014 932296 37515
    ## + renovated:amenities          1    46.148 932298 37515
    ## + renovated:class_b            1    44.300 932300 37515
    ## + Precipitation:Gas_Costs      1    41.958 932303 37515
    ## + cluster:age                  1    41.600 932303 37515
    ## + net:Electricity_Costs        1    38.616 932306 37515
    ## + empl_gr                      1    36.932 932308 37515
    ## + cluster:net                  1    36.151 932308 37515
    ## + age:Precipitation            1    28.163 932316 37515
    ## + class_b:net                  1    27.313 932317 37515
    ## + amenities:cd_total_07        1    25.126 932319 37515
    ## + cluster:hd_total07           1    24.412 932320 37515
    ## + class_a:net                  1    23.683 932321 37515
    ## + renovated:net                1    21.352 932323 37515
    ## + leasing_rate:hd_total07      1    16.842 932328 37515
    ## + net:amenities                1    12.243 932332 37515
    ## + class_b:Gas_Costs            1    10.872 932334 37515
    ## + amenities:Electricity_Costs  1    10.522 932334 37515
    ## + leasing_rate:amenities       1    10.243 932334 37515
    ## + cluster:class_a              1    10.090 932334 37515
    ## + age:net                      1     7.040 932338 37516
    ## + class_a:Gas_Costs            1     0.591 932344 37516
    ## + amenities:hd_total07         1     0.159 932344 37516
    ## + size:net                     1     0.045 932345 37516
    ## + leasing_rate:age             1     0.007 932345 37516
    ## 
    ## Step:  AIC=37513.32
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated + Electricity_Costs:renovated + cd_total_07:renovated + 
    ##     Precipitation:amenities + Precipitation:cluster + cluster:Gas_Costs + 
    ##     net:Gas_Costs
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + renovated:Gas_Costs          1   258.338 931819 37513
    ## <none>                                     932077 37513
    ## + class_b:cd_total_07          1   182.416 931895 37514
    ## + cluster:renovated            1   177.152 931900 37514
    ## + leasing_rate:cd_total_07     1   167.542 931909 37514
    ## + net:hd_total07               1   156.614 931920 37514
    ## + leasing_rate:Gas_Costs       1   141.074 931936 37514
    ## + cluster:leasing_rate         1   140.302 931937 37514
    ## + stories                      1   114.281 931963 37514
    ## + green_rating                 1    96.913 931980 37515
    ## + cluster:net                  1    94.906 931982 37515
    ## + class_a:cd_total_07          1    88.883 931988 37515
    ## + age:cd_total_07              1    88.763 931988 37515
    ## + cluster:amenities            1    87.846 931989 37515
    ## + renovated:Precipitation      1    84.167 931993 37515
    ## + net:Precipitation            1    82.782 931994 37515
    ## + size:renovated               1    75.848 932001 37515
    ## + class_b:amenities            1    61.428 932016 37515
    ## + leasing_rate:renovated       1    57.437 932020 37515
    ## + renovated:net                1    56.942 932020 37515
    ## + net:amenities                1    54.252 932023 37515
    ## + renovated:amenities          1    50.760 932026 37515
    ## + leasing_rate:net             1    48.313 932029 37515
    ## + renovated:class_a            1    44.560 932032 37515
    ## + age:amenities                1    43.780 932033 37515
    ## + cluster:age                  1    42.287 932035 37515
    ## + age:Precipitation            1    39.925 932037 37515
    ## + renovated:class_b            1    39.578 932037 37515
    ## + Precipitation:Gas_Costs      1    39.033 932038 37515
    ## + empl_gr                      1    36.403 932041 37515
    ## + class_b:net                  1    32.493 932044 37515
    ## + net:Electricity_Costs        1    26.339 932051 37515
    ## + class_a:net                  1    25.469 932051 37515
    ## + cluster:hd_total07           1    20.484 932056 37515
    ## + amenities:cd_total_07        1    17.668 932059 37515
    ## + leasing_rate:hd_total07      1    16.613 932060 37515
    ## + class_b:Gas_Costs            1    14.124 932063 37515
    ## + cluster:class_a              1    12.184 932065 37515
    ## + age:net                      1     9.662 932067 37515
    ## + leasing_rate:amenities       1     9.654 932067 37515
    ## + amenities:Electricity_Costs  1     7.739 932069 37515
    ## + size:net                     1     6.364 932071 37515
    ## + class_a:Gas_Costs            1     0.545 932076 37515
    ## + amenities:hd_total07         1     0.012 932077 37515
    ## + leasing_rate:age             1     0.009 932077 37515
    ## 
    ## Step:  AIC=37513.15
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated + Electricity_Costs:renovated + cd_total_07:renovated + 
    ##     Precipitation:amenities + Precipitation:cluster + cluster:Gas_Costs + 
    ##     net:Gas_Costs + Gas_Costs:renovated
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## + renovated:Precipitation      1    628.42 931190 37510
    ## <none>                                     931819 37513
    ## + class_b:cd_total_07          1    176.46 931642 37514
    ## + leasing_rate:cd_total_07     1    161.14 931657 37514
    ## + net:hd_total07               1    154.84 931664 37514
    ## + cluster:leasing_rate         1    144.44 931674 37514
    ## + cluster:renovated            1    140.05 931679 37514
    ## + stories                      1    131.56 931687 37514
    ## + leasing_rate:Gas_Costs       1    125.05 931694 37514
    ## + green_rating                 1    100.19 931718 37514
    ## + cluster:net                  1     90.68 931728 37514
    ## + class_a:cd_total_07          1     83.24 931735 37514
    ## + cluster:amenities            1     82.78 931736 37514
    ## + renovated:net                1     71.82 931747 37515
    ## + net:Precipitation            1     70.51 931748 37515
    ## + net:amenities                1     65.81 931753 37515
    ## + size:renovated               1     63.70 931755 37515
    ## + renovated:class_a            1     58.00 931761 37515
    ## + class_b:amenities            1     57.02 931762 37515
    ## + Precipitation:Gas_Costs      1     54.25 931764 37515
    ## + leasing_rate:net             1     53.96 931765 37515
    ## + renovated:class_b            1     51.69 931767 37515
    ## + age:amenities                1     47.69 931771 37515
    ## + leasing_rate:renovated       1     45.85 931773 37515
    ## + age:Precipitation            1     41.77 931777 37515
    ## + cluster:age                  1     41.25 931777 37515
    ## + age:cd_total_07              1     38.89 931780 37515
    ## + renovated:amenities          1     35.00 931784 37515
    ## + empl_gr                      1     33.43 931785 37515
    ## + class_b:net                  1     33.00 931786 37515
    ## + net:Electricity_Costs        1     27.61 931791 37515
    ## + class_a:net                  1     24.98 931794 37515
    ## + cluster:hd_total07           1     15.47 931803 37515
    ## + leasing_rate:hd_total07      1     15.01 931804 37515
    ## + amenities:cd_total_07        1     14.98 931804 37515
    ## + cluster:class_a              1     11.85 931807 37515
    ## + leasing_rate:amenities       1     10.64 931808 37515
    ## + amenities:Electricity_Costs  1     10.36 931808 37515
    ## + size:net                     1      9.73 931809 37515
    ## + age:net                      1      8.23 931810 37515
    ## + class_b:Gas_Costs            1      2.95 931816 37515
    ## + class_a:Gas_Costs            1      0.32 931818 37515
    ## + amenities:hd_total07         1      0.01 931819 37515
    ## + leasing_rate:age             1      0.00 931819 37515
    ## 
    ## Step:  AIC=37509.87
    ## Rent ~ Electricity_Costs + class_a + cd_total_07 + Precipitation + 
    ##     leasing_rate + cluster + age + size + hd_total07 + net + 
    ##     Gas_Costs + amenities + class_b + renovated + Electricity_Costs:cd_total_07 + 
    ##     Electricity_Costs:Precipitation + cd_total_07:Precipitation + 
    ##     Electricity_Costs:class_a + Electricity_Costs:size + Electricity_Costs:age + 
    ##     cd_total_07:size + Precipitation:size + age:hd_total07 + 
    ##     Electricity_Costs:hd_total07 + size:hd_total07 + Electricity_Costs:Gas_Costs + 
    ##     cd_total_07:Gas_Costs + cluster:size + cd_total_07:hd_total07 + 
    ##     hd_total07:Gas_Costs + Precipitation:hd_total07 + size:Gas_Costs + 
    ##     Electricity_Costs:cluster + age:Gas_Costs + class_a:Precipitation + 
    ##     leasing_rate:size + Gas_Costs:amenities + class_a:amenities + 
    ##     age:size + class_a:size + cd_total_07:cluster + class_a:leasing_rate + 
    ##     size:amenities + age:class_b + size:class_b + Electricity_Costs:class_b + 
    ##     Precipitation:class_b + class_a:age + cluster:class_b + cd_total_07:net + 
    ##     Electricity_Costs:leasing_rate + hd_total07:class_b + class_a:hd_total07 + 
    ##     Precipitation:leasing_rate + leasing_rate:class_b + hd_total07:renovated + 
    ##     age:renovated + Electricity_Costs:renovated + cd_total_07:renovated + 
    ##     Precipitation:amenities + Precipitation:cluster + cluster:Gas_Costs + 
    ##     net:Gas_Costs + Gas_Costs:renovated + Precipitation:renovated
    ## 
    ##                               Df Sum of Sq    RSS   AIC
    ## <none>                                     931190 37510
    ## + net:hd_total07               1   184.090 931006 37510
    ## + leasing_rate:cd_total_07     1   158.896 931031 37511
    ## + cluster:leasing_rate         1   146.746 931043 37511
    ## + class_a:cd_total_07          1   138.736 931051 37511
    ## + class_b:cd_total_07          1   134.171 931056 37511
    ## + leasing_rate:Gas_Costs       1   132.998 931057 37511
    ## + cluster:renovated            1   129.993 931060 37511
    ## + stories                      1   129.966 931060 37511
    ## + green_rating                 1   107.868 931082 37511
    ## + cluster:net                  1    90.925 931099 37511
    ## + cluster:amenities            1    86.941 931103 37511
    ## + renovated:net                1    73.983 931116 37511
    ## + net:amenities                1    56.877 931133 37511
    ## + net:Precipitation            1    55.919 931134 37511
    ## + class_b:amenities            1    52.472 931138 37511
    ## + age:amenities                1    50.112 931140 37511
    ## + age:cd_total_07              1    49.279 931141 37511
    ## + leasing_rate:net             1    46.886 931143 37511
    ## + leasing_rate:renovated       1    44.049 931146 37512
    ## + class_b:net                  1    42.906 931147 37512
    ## + cluster:age                  1    40.052 931150 37512
    ## + class_a:net                  1    35.893 931154 37512
    ## + empl_gr                      1    35.140 931155 37512
    ## + renovated:class_a            1    34.898 931155 37512
    ## + Precipitation:Gas_Costs      1    32.889 931157 37512
    ## + net:Electricity_Costs        1    28.089 931162 37512
    ## + renovated:class_b            1    27.030 931163 37512
    ## + class_a:Gas_Costs            1    25.750 931164 37512
    ## + amenities:Electricity_Costs  1    19.113 931171 37512
    ## + amenities:cd_total_07        1    15.405 931175 37512
    ## + cluster:hd_total07           1    15.148 931175 37512
    ## + leasing_rate:hd_total07      1    14.432 931176 37512
    ## + renovated:amenities          1    14.082 931176 37512
    ## + size:renovated               1    13.866 931176 37512
    ## + cluster:class_a              1     6.948 931183 37512
    ## + leasing_rate:amenities       1     6.276 931184 37512
    ## + age:net                      1     5.965 931184 37512
    ## + age:Precipitation            1     5.783 931184 37512
    ## + size:net                     1     4.386 931186 37512
    ## + class_b:Gas_Costs            1     1.091 931189 37512
    ## + leasing_rate:age             1     0.174 931190 37512
    ## + amenities:hd_total07         1     0.135 931190 37512

<table style="border-collapse:collapse; border:none;">
<tr>
<th style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm;  text-align:left; ">
 
</th>
<th colspan="2" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">
Hand-Built Linear Model
</th>
<th colspan="2" style="border-top: double; text-align:center; font-style:normal; font-weight:bold; padding:0.2cm; ">
Forward Selection Linear Model
</th>
</tr>
<tr>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  text-align:left; ">
Predictors
</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">
Estimates
</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">
p
</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">
Estimates
</td>
<td style=" text-align:center; border-bottom:1px solid; font-style:italic; font-weight:normal;  ">
p
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
(Intercept)
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
29.11
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
167.48
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cluster
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.347
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.100
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
empl gr
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.26
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
leasing rate
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.06
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.10
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.015</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
stories
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.08
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.01
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.08
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-443.21
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
1067.12
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.03
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.179
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-1.22
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-9.20
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
4.66
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
26.83
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
1.65
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
26.43
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
green rating
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.63
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.201
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
net
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-4.82
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-2.22
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.297
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.73
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.021</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-9.80
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.01
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.03
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.14
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
1.04
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
219.04
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.126
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-11020.42
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* stories
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.935
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* Electricity<br>Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.10
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* hd<br>total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.37
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.30
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* cd<br>total 07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.53
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \*<br>Precipitation
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
31.20
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \*<br>Precipitation
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* class<br>a
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-351.02
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* age
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
5.62
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.349
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* Gas<br>Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-315675.21
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
6.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cluster \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
hd total07 \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
2.55
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* hd<br>total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \*<br>cluster
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.10
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.040</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-13.08
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* Precipitation
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.21
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
leasing rate \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.032</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Gas Costs \* amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
1094.50
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-1.84
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.006</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* cluster
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.005</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* leasing rate
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.05
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.014</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.011</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.05
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* class<br>b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-437.86
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.14
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* age
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.03
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.145
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cluster \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.058
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* net
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.019</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \*<br>leasing rate
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
2.22
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.007</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
hd total07 \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* leasing<br>rate
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.015</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
leasing rate \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.03
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.075
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
hd total07 \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.02
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.030</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \*<br>renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
216.50
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.003</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.06
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.076
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* cluster
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.033</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cluster \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.36
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.134
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
net \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-349.57
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.084
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Gas Costs \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-564.35
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.010</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.08
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.022</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm; border-top:1px solid;">
Observations
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="2">
7820
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left; border-top:1px solid;" colspan="2">
7820
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; padding-top:0.1cm; padding-bottom:0.1cm;">
R<sup>2</sup> / R<sup>2</sup> adjusted
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="2">
0.399 / 0.398
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; padding-top:0.1cm; padding-bottom:0.1cm; text-align:left;" colspan="2">
0.478 / 0.474
</td>
</tr>
</table>

### Second Model: Model Based on Forward Selection

For the second model, we used forward selection in order to select
variables that improve the prediction accuracy.

The table below lists the variables and estimates for the hand-built
multiple linear regression model and for the forward selected regression
model, respectively.

<table style="border-collapse:collapse; border:none;">
<caption style="font-weight: bold; text-align:left;">
**Table 1.0: Coefficients of the Hand-Built and Forward Selection Linear
Models**
</caption>
<tr>
<th style="border-top: double; text-align:center; font-style:italic; font-weight:normal; padding:0.2cm; border-bottom:1px solid black; text-align:left; ">
 
</th>
<th colspan="2" style="border-top: double; text-align:center; font-style:italic; font-weight:normal; padding:0.2cm; border-bottom:1px solid black;">
Hand-Built Linear Model
</th>
<th colspan="2" style="border-top: double; text-align:center; font-style:italic; font-weight:normal; padding:0.2cm; border-bottom:1px solid black;">
Forward Selection Linear Model
</th>
</tr>
<tr>
<td style=" color: red; border-bottom:1px solid black; text-align:left; ">
Predictors
</td>
<td style=" color: red; border-bottom:1px solid black; ">
Estimates
</td>
<td style=" color: red; border-bottom:1px solid black; ">
p
</td>
<td style=" color: red; border-bottom:1px solid black; ">
Estimates
</td>
<td style=" color: red; border-bottom:1px solid black; ">
p
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
(Intercept)
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
29.11
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
167.48
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cluster
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.347
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.100
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
empl gr
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.26
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
leasing rate
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.06
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.10
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.015</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
stories
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.08
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.01
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.08
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-443.21
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
1067.12
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.03
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.179
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-1.22
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-9.20
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
4.66
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
26.83
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
1.65
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
26.43
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
green rating
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.63
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.201
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
net
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-4.82
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-2.22
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.297
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.73
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.021</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-9.80
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.01
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.03
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.14
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
1.04
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
219.04
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.126
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-11020.42
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* stories
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.935
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* Electricity<br>Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.10
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* hd<br>total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.37
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.30
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* cd<br>total 07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.53
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \*<br>Precipitation
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
31.20
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \*<br>Precipitation
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* class<br>a
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-351.02
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* age
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
5.62
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.349
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* Gas<br>Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-315675.21
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
6.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cluster \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
hd total07 \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
2.55
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* hd<br>total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \*<br>cluster
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.10
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.040</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-13.08
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* Precipitation
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.21
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
leasing rate \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.032</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Gas Costs \* amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
1094.50
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-1.84
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.006</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* size
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* cluster
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.005</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* leasing rate
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.05
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.014</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.011</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.05
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
size \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \* class<br>b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-437.86
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.14
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* age
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.03
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.145
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cluster \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.058
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* net
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.019</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \*<br>leasing rate
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
2.22
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.007</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
hd total07 \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
class a \* hd total07
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* leasing<br>rate
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.015</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
leasing rate \* class b
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.03
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.075
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
hd total07 \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>\<0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
age \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.02
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.030</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Electricity Costs \*<br>renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
216.50
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.001</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cd total 07 \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.003</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* amenities
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.06
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.076
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* cluster
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-0.00
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.033</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
cluster \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.36
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.134
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
net \* Gas Costs
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-349.57
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.084
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Gas Costs \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
-564.35
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.010</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; ">
Precipitation \* renovated
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
0.08
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:center;  ">
<strong>0.022</strong>
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; color: blue; border-top:1px solid;">
Observations
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; color: blue; text-align:center; border-top:1px solid;" colspan="2">
7820
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; color: blue; text-align:center; border-top:1px solid;" colspan="2">
7820
</td>
</tr>
<tr>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; text-align:left; color: blue;">
R<sup>2</sup> / R<sup>2</sup> adjusted
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; color: blue; text-align:center;" colspan="2">
0.399 / 0.398
</td>
<td style=" padding:0.2cm; text-align:left; vertical-align:top; color: blue; text-align:center;" colspan="2">
0.478 / 0.474
</td>
</tr>
</table>

### Third Model: Lasso Model

By using a shrinkage method like Lasso, we depart from optimality and
concentrate on stabilizing the system. Since the two linear models above
include many variables, there is the possibility of high variance
because each nonzero independent variable included in the model incurs a
cost of employing data to estimate it, hence, increasing the variance.
Through Lasso model, we make the cost we incur from having many
variables explicit. Therefore, through coefficient shrinkage, we can
reduce their variance.

The variable regression and the accuracy of the Lasso model fit largely
depend on the choice of lambda. The coefficient plot below shows that
depending on the value of the tuning parameter, some of the coefficients
will be set equal to 0.

![](HW3_files/figure-markdown_github/setup%201.4-1.png)

By employing Lasso model, we consider the variance-bias trade off, and
examine lambda. If lambda is high, the variance decreases but bias
increases.

We used cross-validation as a method to select the tuning parameter,
lambda. We chose a grid of lambda values that vary from 10^(-2) to 10^10
and computed the leave-one-out cross validation error for each of these
values. The tuning parameter of 0.008 has the smallest cross validation
error, so we chose it for the refit of the Lasso model. The graph below
illustrates the lambda with the least CV Mean Squared Error(MSE).
However, the dip of the CV MSE, where the lambda gives a small error, is
not very pronounced, resulting in a wide range of values for lambda that
will give similar errors.

![](HW3_files/figure-markdown_github/setup%201.5-1.png)

Since lambda is very close to 0, approximately 0.008, Lasso’s results
will be very close to the least squares models with high variance and
low bias. The table below shows the Lasso coefficient estimates. Using
lambda = 0.008, all the 17 coefficient estimates are nonzero.

<table class="table table-striped" style="width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
**Table 3.1 Lasso Model Predictor Estimates**
</caption>
<thead>
<tr>
<th style="text-align:left;">
Predictor
</th>
<th style="text-align:right;">
Estimate
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
(Intercept)
</td>
<td style="text-align:right;">
28.4209220
</td>
</tr>
<tr>
<td style="text-align:left;">
cluster
</td>
<td style="text-align:right;">
1.0790629
</td>
</tr>
<tr>
<td style="text-align:left;">
size
</td>
<td style="text-align:right;">
1.6126260
</td>
</tr>
<tr>
<td style="text-align:left;">
empl_gr
</td>
<td style="text-align:right;">
3.5145064
</td>
</tr>
<tr>
<td style="text-align:left;">
leasing_rate
</td>
<td style="text-align:right;">
1.3993137
</td>
</tr>
<tr>
<td style="text-align:left;">
stories
</td>
<td style="text-align:right;">
-0.8507419
</td>
</tr>
<tr>
<td style="text-align:left;">
age
</td>
<td style="text-align:right;">
-0.4085134
</td>
</tr>
<tr>
<td style="text-align:left;">
renovated
</td>
<td style="text-align:right;">
-0.9499765
</td>
</tr>
<tr>
<td style="text-align:left;">
class_a
</td>
<td style="text-align:right;">
2.6833697
</td>
</tr>
<tr>
<td style="text-align:left;">
class_b
</td>
<td style="text-align:right;">
1.0581586
</td>
</tr>
<tr>
<td style="text-align:left;">
green_rating
</td>
<td style="text-align:right;">
-0.2469625
</td>
</tr>
<tr>
<td style="text-align:left;">
net
</td>
<td style="text-align:right;">
-1.0126713
</td>
</tr>
<tr>
<td style="text-align:left;">
amenities
</td>
<td style="text-align:right;">
0.3392292
</td>
</tr>
<tr>
<td style="text-align:left;">
cd_total_07
</td>
<td style="text-align:right;">
-2.1842729
</td>
</tr>
<tr>
<td style="text-align:left;">
hd_total07
</td>
<td style="text-align:right;">
1.8199030
</td>
</tr>
<tr>
<td style="text-align:left;">
Precipitation
</td>
<td style="text-align:right;">
6.4168899
</td>
</tr>
<tr>
<td style="text-align:left;">
Gas_Costs
</td>
<td style="text-align:right;">
-4.5819721
</td>
</tr>
<tr>
<td style="text-align:left;">
Electricity_Costs
</td>
<td style="text-align:right;">
9.4421085
</td>
</tr>
</tbody>
</table>

Next, we use train/test splits with a loop of 100 to calculate the
average RMSE of each of the three models shown above. Table 1.2
illustrates the average RMSE for each of the models.

<table class="table table-striped" style="width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
**Table 1.2 Average RMSE per Model**
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
Average RMSE
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Hand-Built Linear Model
</td>
<td style="text-align:right;">
11.75309
</td>
</tr>
<tr>
<td style="text-align:left;">
Forward Selection Linear Model
</td>
<td style="text-align:right;">
11.05393
</td>
</tr>
<tr>
<td style="text-align:left;">
Lasso
</td>
<td style="text-align:right;">
12.13637
</td>
</tr>
</tbody>
</table>

### Tree-Based Models

Since Lasso model results in higher RMSE than the linear regression
models, we decided to perform two tree decision models using bagging and
random forest.

**Bagging**

    ## 
    ## Call:
    ##  randomForest(formula = Rent ~ cluster + size + empl_gr + leasing_rate +      stories + age + renovated + class_a + class_b + green_rating +      net + amenities + cd_total_07 + hd_total07 + Precipitation +      Gas_Costs + Electricity_Costs, data = greenbuildings_train,      mtry = 17, importance = TRUE) 
    ##                Type of random forest: regression
    ##                      Number of trees: 500
    ## No. of variables tried at each split: 17
    ## 
    ##           Mean of squared residuals: 54.32594
    ##                     % Var explained: 76.67

The plot below shows that the bagging procedure can produce quite
accurate predictions most of the time.

![](HW3_files/figure-markdown_github/setup%201.9-1.png)

**Random Forest**

    We also ran a random forest model since it is an improvement procedure over bagging. Random forest also builds decision trees by bootstrapping the training samples. We again used 500 number of trees to be bootstrapped. However, instead of considering all variables in each split, random forest chooses only a set of these variables for the tree split. We decided to use a square root of the number of the original variables, which is sqrt(17), approximately 4 variables. Therefore, at each split, a new sample of these 4 predictors is taken. 

    By using a different sample of 4 predictors in each split instead of all 17 variables, we avoid the highly correlated predictions that result from bagging. Random forest produced less correlated predictions. In the bagging procedure, since all variables are used, majority of trees will use the strong predictor at the top of tree, which will result in increased correlation of the predictions. Hence, bagging will usually not lead to a smaller reduction in variance than random forest because it averages highly correlated predictions. Therefore, by averaging uncorrelated quantities, random forest will generally result in a higher decrease in variance in the average of the resulting trees. 

The plot below illustrates the accuracy of the random forest prediction
model.

![](HW3_files/figure-markdown_github/setup%201.10-1.png) \#\#\#
Comparison of all 5 Predictive Models: Hand-Built Linear Model, Forward
Selection, Lasso, Bagging and Random Forest

    To compare all five models run so far, we are using a cross validation performance measure: the Leave-one-out cross validation (LOOCV). Table 3.3 below lists each RMSE found from performing the CV. 

<table class="table table-striped" style="width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
**Table 1.3 LOOCV RMSE per Model**
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
LOOCV RMSE
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
LOOCV RMSE Rent Hand-Built Model
</td>
<td style="text-align:right;">
11.773307
</td>
</tr>
<tr>
<td style="text-align:left;">
LOOCV RMSE Rent Forward Selection Model
</td>
<td style="text-align:right;">
11.101607
</td>
</tr>
<tr>
<td style="text-align:left;">
LOOCV RMSE Model Lasso Model
</td>
<td style="text-align:right;">
12.150734
</td>
</tr>
<tr>
<td style="text-align:left;">
LOOCV RMSE Model Bagging Model
</td>
<td style="text-align:right;">
7.125477
</td>
</tr>
<tr>
<td style="text-align:left;">
LOOCV RMSE Model RandomForest Model
</td>
<td style="text-align:right;">
7.498559
</td>
</tr>
</tbody>
</table>

**Random Forest as the best predictive model possible**

    The tree decision models perform almost twice better than the remaining three models, based on the RMSE. We decided to use Random Forest as a predictive model for rent since its does not differ as much from the RMSE of bagging, and the procedure it uses usually results in an improvement over bagging as mentioned before. 

    Below is a list of the variable importance for each variable used in Random Forest. The first column shows the increase in Mean Squared Error if that particular variable is omitted from the model. The MSE is calculated based on the out of bag samples. The second column shows the increase in node purity that results from splits over that variable. The increase in node purity is averaged over all trees. As shown below, the most important variable based on MSE is "age" because if omitted, the MSE increases the most. However, Electricity costs and Size increase the most node purity. 

<table class="table table-striped" style="width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
**Table 3.4 Variable Importance in Random Forest Model**
</caption>
<thead>
<tr>
<th style="text-align:left;">
Predictor
</th>
<th style="text-align:right;">
% Increase in MSE
</th>
<th style="text-align:right;">
Increase in Node Purity
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
cluster
</td>
<td style="text-align:right;">
33.67561
</td>
<td style="text-align:right;">
173655.970
</td>
</tr>
<tr>
<td style="text-align:left;">
size
</td>
<td style="text-align:right;">
51.61232
</td>
<td style="text-align:right;">
233627.848
</td>
</tr>
<tr>
<td style="text-align:left;">
empl_gr
</td>
<td style="text-align:right;">
22.41081
</td>
<td style="text-align:right;">
90028.369
</td>
</tr>
<tr>
<td style="text-align:left;">
leasing_rate
</td>
<td style="text-align:right;">
48.73707
</td>
<td style="text-align:right;">
135629.774
</td>
</tr>
<tr>
<td style="text-align:left;">
stories
</td>
<td style="text-align:right;">
48.71409
</td>
<td style="text-align:right;">
130973.467
</td>
</tr>
<tr>
<td style="text-align:left;">
age
</td>
<td style="text-align:right;">
56.67080
</td>
<td style="text-align:right;">
133105.855
</td>
</tr>
<tr>
<td style="text-align:left;">
renovated
</td>
<td style="text-align:right;">
24.02045
</td>
<td style="text-align:right;">
20920.776
</td>
</tr>
<tr>
<td style="text-align:left;">
class_a
</td>
<td style="text-align:right;">
35.99361
</td>
<td style="text-align:right;">
32885.244
</td>
</tr>
<tr>
<td style="text-align:left;">
class_b
</td>
<td style="text-align:right;">
28.00347
</td>
<td style="text-align:right;">
18816.059
</td>
</tr>
<tr>
<td style="text-align:left;">
green_rating
</td>
<td style="text-align:right;">
11.80040
</td>
<td style="text-align:right;">
4632.693
</td>
</tr>
<tr>
<td style="text-align:left;">
net
</td>
<td style="text-align:right;">
11.84986
</td>
<td style="text-align:right;">
2827.275
</td>
</tr>
<tr>
<td style="text-align:left;">
amenities
</td>
<td style="text-align:right;">
27.20071
</td>
<td style="text-align:right;">
17033.275
</td>
</tr>
<tr>
<td style="text-align:left;">
cd_total_07
</td>
<td style="text-align:right;">
27.77591
</td>
<td style="text-align:right;">
71952.154
</td>
</tr>
<tr>
<td style="text-align:left;">
hd_total07
</td>
<td style="text-align:right;">
19.91727
</td>
<td style="text-align:right;">
152051.047
</td>
</tr>
<tr>
<td style="text-align:left;">
Precipitation
</td>
<td style="text-align:right;">
20.91840
</td>
<td style="text-align:right;">
100778.783
</td>
</tr>
<tr>
<td style="text-align:left;">
Gas_Costs
</td>
<td style="text-align:right;">
25.32302
</td>
<td style="text-align:right;">
81242.030
</td>
</tr>
<tr>
<td style="text-align:left;">
Electricity_Costs
</td>
<td style="text-align:right;">
24.44913
</td>
<td style="text-align:right;">
241126.265
</td>
</tr>
</tbody>
</table>

### The Effect of Green Rating on Rent

Figure 3.5 illustrates the partial dependence plot of the marginal
effect that the green rating has on the outcome of Random Forest.

![](HW3_files/figure-markdown_github/setup%201.13-1.png)

It is difficlut to esitmate the partial effect of green_rating on rent
in a random forest model since tree based models are nonlinear in
coefficients. So, by random forest, we can only find approximation to
the average effect of green_rating.

To find the average change in rental income per square foot considering
green ratings and holding all other variables fixed, we calculated the
difference between predicted values given a green rating and a non-green
rating keeping all other variables the same. (Since green ratings is a
dummy variable, to find the effect of the variable, we subtracted all
predicted values given green_rating=0 from predicted values given
green_rating=1, holding all other variables constant.) Afterwards, we
took the average of the differences of predicted values to find the
average effect of green ratings on rent price. Therefore, the average
effect of green ratings on the rent price is approximately “0.3”. This
means that if the building is green then the rent will be on average 0.3
dollars per square foot per calendar year more expensive than if the
building is non-green, holding all else fixed.

<table class="table table-striped" style="width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
**Table 1.4 Average Effect on the Green Rating Variable on Rent**
</caption>
<thead>
<tr>
<th style="text-align:right;">
Average Green Rating Effect on Rent
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
0.2882893
</td>
</tr>
</tbody>
</table>

### Conclusions:

1.  The best predictive models possible for price are the tree-based
    models, Random Forest and Bagging;
2.  The average change in rental income per square foot associated with
    green certification, holding other features of the building
    constant, is 0.3 dollars per square foot.

## Predictive model building: California housing

    ## Start:  AIC=370949.5
    ## medianHouseValue ~ (longitude + latitude + housingMedianAge + 
    ##     totalRooms + totalBedrooms + population + households + medianIncome) - 
    ##     longitude - latitude
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + totalBedrooms:medianIncome      1 2.7010e+12 9.1500e+13 370471
    ## + households:medianIncome         1 2.6563e+12 9.1544e+13 370479
    ## + totalRooms:medianIncome         1 2.2250e+12 9.1975e+13 370557
    ## + population:medianIncome         1 1.4223e+12 9.2778e+13 370700
    ## + housingMedianAge:totalBedrooms  1 1.0381e+12 9.3162e+13 370769
    ## + housingMedianAge:households     1 1.0048e+12 9.3196e+13 370774
    ## + totalBedrooms:households        1 6.2423e+11 9.3576e+13 370842
    ## + housingMedianAge:totalRooms     1 3.2719e+11 9.3873e+13 370894
    ## + totalRooms:totalBedrooms        1 1.5466e+11 9.4046e+13 370924
    ## + totalRooms:households           1 1.2421e+11 9.4076e+13 370930
    ## + housingMedianAge:population     1 5.1053e+10 9.4149e+13 370943
    ## + totalBedrooms:population        1 4.7707e+10 9.4153e+13 370943
    ## + population:households           1 3.5711e+10 9.4165e+13 370945
    ## <none>                                         9.4200e+13 370950
    ## + totalRooms:population           1 8.6880e+09 9.4192e+13 370950
    ## + housingMedianAge:medianIncome   1 1.8110e+08 9.4200e+13 370952
    ## - totalBedrooms                   1 6.5144e+11 9.4852e+13 371061
    ## - households                      1 1.4320e+12 9.5632e+13 371197
    ## - totalRooms                      1 2.3773e+12 9.6578e+13 371359
    ## - population                      1 4.5612e+12 9.8762e+13 371728
    ## - housingMedianAge                1 8.1425e+12 1.0234e+14 372316
    ## - medianIncome                    1 8.9254e+13 1.8345e+14 381953
    ## 
    ## Step:  AIC=370471.2
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + housingMedianAge:totalBedrooms  1 1.2327e+12 9.0267e+13 370249
    ## + housingMedianAge:households     1 1.2102e+12 9.0289e+13 370253
    ## + totalBedrooms:households        1 7.6228e+11 9.0737e+13 370335
    ## + housingMedianAge:totalRooms     1 5.9622e+11 9.0903e+13 370365
    ## + totalRooms:totalBedrooms        1 2.9521e+11 9.1204e+13 370420
    ## + totalRooms:households           1 2.7810e+11 9.1221e+13 370423
    ## + housingMedianAge:medianIncome   1 1.2558e+11 9.1374e+13 370451
    ## + population:medianIncome         1 9.0244e+10 9.1409e+13 370457
    ## + housingMedianAge:population     1 7.6619e+10 9.1423e+13 370459
    ## + totalBedrooms:population        1 3.4928e+10 9.1465e+13 370467
    ## + population:households           1 2.8807e+10 9.1471e+13 370468
    ## + households:medianIncome         1 2.4614e+10 9.1475e+13 370469
    ## <none>                                         9.1500e+13 370471
    ## + totalRooms:medianIncome         1 5.1630e+09 9.1494e+13 370472
    ## + totalRooms:population           1 5.5416e+08 9.1499e+13 370473
    ## - households                      1 9.6325e+11 9.2463e+13 370642
    ## - totalBedrooms:medianIncome      1 2.7010e+12 9.4200e+13 370950
    ## - population                      1 3.5738e+12 9.5073e+13 371102
    ## - totalRooms                      1 5.0021e+12 9.6502e+13 371348
    ## - housingMedianAge                1 7.5551e+12 9.9055e+13 371779
    ## 
    ## Step:  AIC=370249.2
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + housingMedianAge:population     1 1.6912e+12 8.8576e+13 369939
    ## + housingMedianAge:totalRooms     1 3.5704e+11 8.9910e+13 370186
    ## + totalRooms:population           1 3.0001e+11 8.9967e+13 370196
    ## + housingMedianAge:medianIncome   1 2.0156e+11 9.0065e+13 370214
    ## + totalBedrooms:households        1 1.4319e+11 9.0124e+13 370225
    ## + population:medianIncome         1 1.0790e+11 9.0159e+13 370231
    ## + totalBedrooms:population        1 1.0707e+11 9.0160e+13 370232
    ## + population:households           1 9.9745e+10 9.0167e+13 370233
    ## <none>                                         9.0267e+13 370249
    ## + totalRooms:medianIncome         1 6.9446e+09 9.0260e+13 370250
    ## + households:medianIncome         1 4.8861e+09 9.0262e+13 370250
    ## + housingMedianAge:households     1 1.8021e+09 9.0265e+13 370251
    ## + totalRooms:totalBedrooms        1 1.2421e+09 9.0266e+13 370251
    ## + totalRooms:households           1 1.1487e+09 9.0266e+13 370251
    ## - households                      1 6.3703e+11 9.0904e+13 370363
    ## - housingMedianAge:totalBedrooms  1 1.2327e+12 9.1500e+13 370471
    ## - totalBedrooms:medianIncome      1 2.8955e+12 9.3162e+13 370769
    ## - population                      1 3.3285e+12 9.3595e+13 370845
    ## - totalRooms                      1 3.6668e+12 9.3934e+13 370905
    ## 
    ## Step:  AIC=369938.9
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + housingMedianAge:households     1 3.9991e+11 8.8176e+13 369866
    ## + totalBedrooms:households        1 3.0855e+11 8.8267e+13 369883
    ## + housingMedianAge:medianIncome   1 2.2137e+11 8.8354e+13 369900
    ## + population:medianIncome         1 1.3131e+11 8.8444e+13 369916
    ## + housingMedianAge:totalRooms     1 6.9002e+10 8.8507e+13 369928
    ## + totalRooms:households           1 3.8741e+10 8.8537e+13 369934
    ## + totalRooms:population           1 2.3730e+10 8.8552e+13 369937
    ## + totalRooms:medianIncome         1 2.0371e+10 8.8555e+13 369937
    ## + totalRooms:totalBedrooms        1 1.5795e+10 8.8560e+13 369938
    ## <none>                                         8.8576e+13 369939
    ## + population:households           1 4.5437e+09 8.8571e+13 369940
    ## + households:medianIncome         1 2.1487e+09 8.8574e+13 369941
    ## + totalBedrooms:population        1 1.4260e+09 8.8574e+13 369941
    ## - households                      1 1.7966e+11 8.8755e+13 369970
    ## - housingMedianAge:population     1 1.6912e+12 9.0267e+13 370249
    ## - housingMedianAge:totalBedrooms  1 2.8472e+12 9.1423e+13 370459
    ## - totalBedrooms:medianIncome      1 3.0300e+12 9.1606e+13 370492
    ## - totalRooms                      1 4.3744e+12 9.2950e+13 370733
    ## 
    ## Step:  AIC=369866.2
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + totalBedrooms:households        1 2.8401e+11 8.7892e+13 369815
    ## + housingMedianAge:medianIncome   1 1.8399e+11 8.7992e+13 369834
    ## + population:medianIncome         1 6.7649e+10 8.8108e+13 369856
    ## + housingMedianAge:totalRooms     1 6.4226e+10 8.8112e+13 369856
    ## + totalRooms:households           1 3.1362e+10 8.8144e+13 369862
    ## + totalRooms:totalBedrooms        1 3.0874e+10 8.8145e+13 369862
    ## - housingMedianAge:totalBedrooms  1 3.4046e+08 8.8176e+13 369864
    ## + totalRooms:population           1 2.0866e+10 8.8155e+13 369864
    ## + totalRooms:medianIncome         1 1.3068e+10 8.8163e+13 369866
    ## + households:medianIncome         1 1.2194e+10 8.8164e+13 369866
    ## <none>                                         8.8176e+13 369866
    ## + population:households           1 2.8712e+09 8.8173e+13 369868
    ## + totalBedrooms:population        1 2.2917e+09 8.8173e+13 369868
    ## - housingMedianAge:households     1 3.9991e+11 8.8576e+13 369939
    ## - housingMedianAge:population     1 2.0893e+12 9.0265e+13 370251
    ## - totalBedrooms:medianIncome      1 3.1179e+12 9.1294e+13 370438
    ## - totalRooms                      1 4.6298e+12 9.2806e+13 370709
    ## 
    ## Step:  AIC=369814.9
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + totalRooms:population           1 1.3333e+12 8.6558e+13 369565
    ## + totalRooms:households           1 1.1788e+12 8.6713e+13 369594
    ## + totalBedrooms:population        1 1.1070e+12 8.6785e+13 369608
    ## + population:households           1 9.3741e+11 8.6954e+13 369640
    ## + totalRooms:totalBedrooms        1 8.7231e+11 8.7019e+13 369652
    ## + housingMedianAge:medianIncome   1 1.7338e+11 8.7718e+13 369784
    ## + housingMedianAge:totalRooms     1 8.4650e+10 8.7807e+13 369801
    ## + population:medianIncome         1 7.5949e+10 8.7816e+13 369803
    ## - housingMedianAge:totalBedrooms  1 1.0754e+09 8.7893e+13 369813
    ## + totalRooms:medianIncome         1 1.5323e+10 8.7876e+13 369814
    ## + households:medianIncome         1 1.2063e+10 8.7880e+13 369815
    ## <none>                                         8.7892e+13 369815
    ## - totalBedrooms:households        1 2.8401e+11 8.8176e+13 369866
    ## - housingMedianAge:households     1 3.7537e+11 8.8267e+13 369883
    ## - housingMedianAge:population     1 2.2318e+12 9.0124e+13 370227
    ## - totalBedrooms:medianIncome      1 3.1705e+12 9.1062e+13 370398
    ## - totalRooms                      1 4.8308e+12 9.2723e+13 370696
    ## 
    ## Step:  AIC=369564.5
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + housingMedianAge:medianIncome   1 1.3589e+11 8.6423e+13 369541
    ## + totalRooms:households           1 1.0732e+11 8.6451e+13 369546
    ## + totalRooms:totalBedrooms        1 1.0508e+11 8.6453e+13 369546
    ## + population:medianIncome         1 9.1994e+10 8.6466e+13 369549
    ## + totalRooms:medianIncome         1 4.5105e+10 8.6513e+13 369558
    ## + housingMedianAge:totalRooms     1 2.6068e+10 8.6532e+13 369562
    ## - housingMedianAge:totalBedrooms  1 4.7162e+09 8.6563e+13 369563
    ## <none>                                         8.6558e+13 369565
    ## + households:medianIncome         1 5.8733e+09 8.6553e+13 369565
    ## + population:households           1 3.3607e+09 8.6555e+13 369566
    ## + totalBedrooms:population        1 2.2638e+09 8.6556e+13 369566
    ## - housingMedianAge:households     1 2.5821e+11 8.6817e+13 369612
    ## - housingMedianAge:population     1 9.1005e+11 8.7468e+13 369735
    ## - totalRooms:population           1 1.3333e+12 8.7892e+13 369815
    ## - totalBedrooms:households        1 1.5965e+12 8.8155e+13 369864
    ## - totalBedrooms:medianIncome      1 3.1087e+12 8.9667e+13 370145
    ## 
    ## Step:  AIC=369540.6
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + housingMedianAge:totalRooms     1 1.6148e+11 8.6261e+13 369512
    ## + totalRooms:totalBedrooms        1 1.0793e+11 8.6315e+13 369522
    ## + totalRooms:households           1 9.4519e+10 8.6328e+13 369525
    ## + population:medianIncome         1 8.3536e+10 8.6339e+13 369527
    ## + totalRooms:medianIncome         1 3.3690e+10 8.6389e+13 369536
    ## - housingMedianAge:totalBedrooms  1 1.3829e+09 8.6424e+13 369539
    ## <none>                                         8.6423e+13 369541
    ## + totalBedrooms:population        1 3.4675e+09 8.6419e+13 369542
    ## + population:households           1 3.4510e+09 8.6419e+13 369542
    ## + households:medianIncome         1 2.3837e+09 8.6420e+13 369542
    ## - housingMedianAge:medianIncome   1 1.3589e+11 8.6558e+13 369565
    ## - housingMedianAge:households     1 2.3435e+11 8.6657e+13 369583
    ## - housingMedianAge:population     1 9.1118e+11 8.7334e+13 369712
    ## - totalRooms:population           1 1.2958e+12 8.7718e+13 369784
    ## - totalBedrooms:households        1 1.5485e+12 8.7971e+13 369832
    ## - totalBedrooms:medianIncome      1 3.2437e+12 8.9666e+13 370147
    ## 
    ## Step:  AIC=369511.7
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + population:medianIncome         1 1.1930e+11 8.6142e+13 369491
    ## + totalRooms:medianIncome         1 7.0386e+10 8.6191e+13 369500
    ## + totalBedrooms:population        1 5.1307e+10 8.6210e+13 369504
    ## + totalRooms:totalBedrooms        1 4.6355e+10 8.6215e+13 369505
    ## + totalRooms:households           1 3.5908e+10 8.6225e+13 369507
    ## + population:households           1 1.1867e+10 8.6249e+13 369511
    ## <none>                                         8.6261e+13 369512
    ## + households:medianIncome         1 6.5874e+09 8.6254e+13 369512
    ## - housingMedianAge:totalBedrooms  1 1.7478e+10 8.6279e+13 369513
    ## - housingMedianAge:totalRooms     1 1.6148e+11 8.6423e+13 369541
    ## - housingMedianAge:households     1 2.1683e+11 8.6478e+13 369551
    ## - housingMedianAge:medianIncome   1 2.7130e+11 8.6532e+13 369562
    ## - housingMedianAge:population     1 7.1758e+11 8.6979e+13 369646
    ## - totalRooms:population           1 1.1297e+12 8.7391e+13 369725
    ## - totalBedrooms:households        1 1.4377e+12 8.7699e+13 369783
    ## - totalBedrooms:medianIncome      1 3.1127e+12 8.9374e+13 370095
    ## 
    ## Step:  AIC=369490.9
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms + 
    ##     population:medianIncome
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + households:medianIncome         1 9.1696e+10 8.6050e+13 369475
    ## + totalRooms:households           1 4.6799e+10 8.6095e+13 369484
    ## + totalRooms:totalBedrooms        1 4.6236e+10 8.6096e+13 369484
    ## + totalRooms:medianIncome         1 3.3048e+10 8.6109e+13 369487
    ## + totalBedrooms:population        1 1.6841e+10 8.6125e+13 369490
    ## <none>                                         8.6142e+13 369491
    ## + population:households           1 1.2810e+09 8.6140e+13 369493
    ## - housingMedianAge:totalBedrooms  1 3.9954e+10 8.6182e+13 369497
    ## - population:medianIncome         1 1.1930e+11 8.6261e+13 369512
    ## - housingMedianAge:households     1 1.5862e+11 8.6300e+13 369519
    ## - housingMedianAge:totalRooms     1 1.9724e+11 8.6339e+13 369527
    ## - housingMedianAge:medianIncome   1 2.8304e+11 8.6425e+13 369543
    ## - housingMedianAge:population     1 6.6975e+11 8.6812e+13 369617
    ## - totalRooms:population           1 1.1333e+12 8.7275e+13 369705
    ## - totalBedrooms:households        1 1.4571e+12 8.7599e+13 369766
    ## - totalBedrooms:medianIncome      1 1.6595e+12 8.7801e+13 369804
    ## 
    ## Step:  AIC=369475.3
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms + 
    ##     population:medianIncome + households:medianIncome
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + totalRooms:medianIncome         1 4.4267e+10 8.6006e+13 369469
    ## + totalRooms:totalBedrooms        1 4.3866e+10 8.6006e+13 369469
    ## + totalRooms:households           1 3.8220e+10 8.6012e+13 369470
    ## + totalBedrooms:population        1 1.7631e+10 8.6032e+13 369474
    ## <none>                                         8.6050e+13 369475
    ## + population:households           1 1.2913e+09 8.6049e+13 369477
    ## - housingMedianAge:totalBedrooms  1 2.4988e+10 8.6075e+13 369478
    ## - totalBedrooms:medianIncome      1 7.9180e+10 8.6129e+13 369488
    ## - households:medianIncome         1 9.1696e+10 8.6142e+13 369491
    ## - housingMedianAge:households     1 1.9986e+11 8.6250e+13 369512
    ## - population:medianIncome         1 2.0441e+11 8.6254e+13 369512
    ## - housingMedianAge:totalRooms     1 2.3927e+11 8.6289e+13 369519
    ## - housingMedianAge:medianIncome   1 2.7983e+11 8.6330e+13 369527
    ## - housingMedianAge:population     1 6.5223e+11 8.6702e+13 369598
    ## - totalRooms:population           1 1.1050e+12 8.7155e+13 369684
    ## - totalBedrooms:households        1 1.4422e+12 8.7492e+13 369748
    ## 
    ## Step:  AIC=369468.8
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms + 
    ##     population:medianIncome + households:medianIncome + totalRooms:medianIncome
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + totalRooms:totalBedrooms        1 3.7210e+10 8.5969e+13 369464
    ## + totalRooms:households           1 3.1285e+10 8.5975e+13 369465
    ## + totalBedrooms:population        1 2.2764e+10 8.5983e+13 369466
    ## <none>                                         8.6006e+13 369469
    ## + population:households           1 2.5884e+09 8.6003e+13 369470
    ## - housingMedianAge:totalBedrooms  1 3.0472e+10 8.6036e+13 369473
    ## - totalRooms:medianIncome         1 4.4267e+10 8.6050e+13 369475
    ## - households:medianIncome         1 1.0292e+11 8.6109e+13 369487
    ## - totalBedrooms:medianIncome      1 1.0946e+11 8.6115e+13 369488
    ## - population:medianIncome         1 1.6529e+11 8.6171e+13 369498
    ## - housingMedianAge:households     1 2.0093e+11 8.6207e+13 369505
    ## - housingMedianAge:totalRooms     1 2.6882e+11 8.6275e+13 369518
    ## - housingMedianAge:medianIncome   1 2.8396e+11 8.6290e+13 369521
    ## - housingMedianAge:population     1 6.4098e+11 8.6647e+13 369589
    ## - totalRooms:population           1 1.1235e+12 8.7129e+13 369681
    ## - totalBedrooms:households        1 1.4655e+12 8.7471e+13 369746
    ## 
    ## Step:  AIC=369463.6
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms + 
    ##     population:medianIncome + households:medianIncome + totalRooms:medianIncome + 
    ##     totalRooms:totalBedrooms
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + totalBedrooms:population        1 1.1370e+11 8.5855e+13 369444
    ## + population:households           1 1.0213e+11 8.5866e+13 369446
    ## <none>                                         8.5969e+13 369464
    ## + totalRooms:households           1 2.3583e+09 8.5966e+13 369465
    ## - totalRooms:totalBedrooms        1 3.7210e+10 8.6006e+13 369469
    ## - totalRooms:medianIncome         1 3.7611e+10 8.6006e+13 369469
    ## - housingMedianAge:totalBedrooms  1 4.8440e+10 8.6017e+13 369471
    ## - households:medianIncome         1 9.9649e+10 8.6068e+13 369481
    ## - totalBedrooms:medianIncome      1 1.0371e+11 8.6072e+13 369482
    ## - housingMedianAge:households     1 1.3347e+11 8.6102e+13 369487
    ## - population:medianIncome         1 1.6603e+11 8.6135e+13 369493
    ## - housingMedianAge:totalRooms     1 1.8662e+11 8.6155e+13 369497
    ## - housingMedianAge:medianIncome   1 2.4730e+11 8.6216e+13 369509
    ## - totalRooms:population           1 5.7881e+11 8.6547e+13 369572
    ## - housingMedianAge:population     1 6.7682e+11 8.6645e+13 369591
    ## - totalBedrooms:households        1 8.5600e+11 8.6825e+13 369625
    ## 
    ## Step:  AIC=369443.8
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms + 
    ##     population:medianIncome + households:medianIncome + totalRooms:medianIncome + 
    ##     totalRooms:totalBedrooms + totalBedrooms:population
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + totalRooms:households           1 1.6549e+11 8.5689e+13 369414
    ## - totalRooms:population           1 3.6920e+09 8.5859e+13 369442
    ## <none>                                         8.5855e+13 369444
    ## + population:households           1 7.4384e+09 8.5847e+13 369444
    ## - totalRooms:medianIncome         1 4.3324e+10 8.5898e+13 369450
    ## - housingMedianAge:households     1 6.2403e+10 8.5917e+13 369454
    ## - population:medianIncome         1 7.6848e+10 8.5932e+13 369457
    ## - totalBedrooms:medianIncome      1 9.7511e+10 8.5952e+13 369461
    ## - households:medianIncome         1 1.0012e+11 8.5955e+13 369461
    ## - housingMedianAge:totalBedrooms  1 1.0626e+11 8.5961e+13 369462
    ## - totalBedrooms:population        1 1.1370e+11 8.5969e+13 369464
    ## - totalRooms:totalBedrooms        1 1.2814e+11 8.5983e+13 369466
    ## - housingMedianAge:totalRooms     1 2.4486e+11 8.6100e+13 369489
    ## - housingMedianAge:medianIncome   1 3.0074e+11 8.6156e+13 369500
    ## - housingMedianAge:population     1 6.1325e+11 8.6468e+13 369559
    ## - totalBedrooms:households        1 6.8961e+11 8.6545e+13 369574
    ## 
    ## Step:  AIC=369413.9
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms + 
    ##     population:medianIncome + households:medianIncome + totalRooms:medianIncome + 
    ##     totalRooms:totalBedrooms + totalBedrooms:population + totalRooms:households
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## - totalRooms:totalBedrooms        1 5.0481e+09 8.5694e+13 369413
    ## + population:households           1 1.3218e+10 8.5676e+13 369413
    ## <none>                                         8.5689e+13 369414
    ## - population:medianIncome         1 3.0802e+10 8.5720e+13 369418
    ## - totalRooms:medianIncome         1 3.9451e+10 8.5729e+13 369420
    ## - housingMedianAge:totalBedrooms  1 4.8061e+10 8.5737e+13 369421
    ## - households:medianIncome         1 6.9395e+10 8.5759e+13 369425
    ## - totalBedrooms:medianIncome      1 1.0020e+11 8.5790e+13 369431
    ## - totalRooms:population           1 1.3022e+11 8.5820e+13 369437
    ## - housingMedianAge:households     1 1.3530e+11 8.5825e+13 369438
    ## - totalRooms:households           1 1.6549e+11 8.5855e+13 369444
    ## - housingMedianAge:totalRooms     1 2.5525e+11 8.5945e+13 369461
    ## - totalBedrooms:population        1 2.7683e+11 8.5966e+13 369465
    ## - housingMedianAge:medianIncome   1 2.8080e+11 8.5970e+13 369466
    ## - totalBedrooms:households        1 6.6285e+11 8.6352e+13 369539
    ## - housingMedianAge:population     1 7.1729e+11 8.6407e+13 369550
    ## 
    ## Step:  AIC=369412.9
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms + 
    ##     population:medianIncome + households:medianIncome + totalRooms:medianIncome + 
    ##     totalBedrooms:population + totalRooms:households
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## + population:households           1 1.7045e+10 8.5677e+13 369412
    ## <none>                                         8.5694e+13 369413
    ## + totalRooms:totalBedrooms        1 5.0481e+09 8.5689e+13 369414
    ## - population:medianIncome         1 3.1482e+10 8.5726e+13 369417
    ## - totalRooms:medianIncome         1 4.0016e+10 8.5734e+13 369419
    ## - housingMedianAge:totalBedrooms  1 4.4313e+10 8.5739e+13 369419
    ## - households:medianIncome         1 6.7610e+10 8.5762e+13 369424
    ## - totalBedrooms:medianIncome      1 1.0268e+11 8.5797e+13 369431
    ## - totalRooms:population           1 1.3521e+11 8.5830e+13 369437
    ## - housingMedianAge:households     1 2.1965e+11 8.5914e+13 369453
    ## - housingMedianAge:totalRooms     1 2.6602e+11 8.5960e+13 369462
    ## - housingMedianAge:medianIncome   1 2.7984e+11 8.5974e+13 369465
    ## - totalBedrooms:population        1 2.8006e+11 8.5975e+13 369465
    ## - totalRooms:households           1 2.8858e+11 8.5983e+13 369466
    ## - totalBedrooms:households        1 6.6860e+11 8.6363e+13 369539
    ## - housingMedianAge:population     1 7.2263e+11 8.6417e+13 369550
    ## 
    ## Step:  AIC=369411.6
    ## medianHouseValue ~ housingMedianAge + totalRooms + totalBedrooms + 
    ##     population + households + medianIncome + totalBedrooms:medianIncome + 
    ##     housingMedianAge:totalBedrooms + housingMedianAge:population + 
    ##     housingMedianAge:households + totalBedrooms:households + 
    ##     totalRooms:population + housingMedianAge:medianIncome + housingMedianAge:totalRooms + 
    ##     population:medianIncome + households:medianIncome + totalRooms:medianIncome + 
    ##     totalBedrooms:population + totalRooms:households + population:households
    ## 
    ##                                  Df  Sum of Sq        RSS    AIC
    ## <none>                                         8.5677e+13 369412
    ## - population:households           1 1.7045e+10 8.5694e+13 369413
    ## + totalRooms:totalBedrooms        1 1.2209e+09 8.5676e+13 369413
    ## - population:medianIncome         1 2.8856e+10 8.5706e+13 369415
    ## - totalRooms:medianIncome         1 4.0357e+10 8.5718e+13 369417
    ## - housingMedianAge:totalBedrooms  1 5.7652e+10 8.5735e+13 369421
    ## - households:medianIncome         1 6.9150e+10 8.5747e+13 369423
    ## - totalBedrooms:medianIncome      1 1.0167e+11 8.5779e+13 369429
    ## - totalRooms:population           1 1.3080e+11 8.5808e+13 369435
    ## - housingMedianAge:households     1 1.5607e+11 8.5833e+13 369440
    ## - totalBedrooms:population        1 2.2648e+11 8.5904e+13 369453
    ## - housingMedianAge:totalRooms     1 2.4345e+11 8.5921e+13 369456
    ## - housingMedianAge:medianIncome   1 2.7745e+11 8.5955e+13 369463
    ## - totalRooms:households           1 2.7978e+11 8.5957e+13 369463
    ## - totalBedrooms:households        1 6.6708e+11 8.6345e+13 369538
    ## - housingMedianAge:population     1 7.1716e+11 8.6395e+13 369547

    ## lm(formula = medianHouseValue ~ housingMedianAge + totalRooms + 
    ##     totalBedrooms + population + households + medianIncome + 
    ##     totalBedrooms:medianIncome + housingMedianAge:totalBedrooms + 
    ##     housingMedianAge:population + housingMedianAge:households + 
    ##     totalBedrooms:households + totalRooms:population + housingMedianAge:medianIncome + 
    ##     housingMedianAge:totalRooms + population:medianIncome + households:medianIncome + 
    ##     totalRooms:medianIncome + totalBedrooms:population + totalRooms:households + 
    ##     population:households, data = CAhousing_train)

    ##                    (Intercept)               housingMedianAge 
    ##                   1.915245e+04                   4.099958e+02 
    ##                     totalRooms                  totalBedrooms 
    ##                  -3.110722e+01                   9.371459e+01 
    ##                     population                     households 
    ##                  -8.707988e+00                  -1.841397e+01 
    ##                   medianIncome     totalBedrooms:medianIncome 
    ##                   3.526012e+04                   2.004160e+01 
    ## housingMedianAge:totalBedrooms    housingMedianAge:population 
    ##                   2.791696e+00                  -1.359092e+00 
    ##    housingMedianAge:households       totalBedrooms:households 
    ##                   5.045104e+00                  -1.178825e-01 
    ##          totalRooms:population  housingMedianAge:medianIncome 
    ##                  -4.274055e-03                   2.027825e+02 
    ##    housingMedianAge:totalRooms        population:medianIncome 
    ##                  -5.688283e-01                  -2.049298e+00 
    ##        households:medianIncome        totalRooms:medianIncome 
    ##                   2.000886e+01                  -1.043315e+00 
    ##       totalBedrooms:population          totalRooms:households 
    ##                   3.811943e-02                   1.707646e-02 
    ##          population:households 
    ##                  -7.638732e-03

![](HW3_files/figure-markdown_github/setup%201.15-1.png)

    ## [1] 0.002383654

![](HW3_files/figure-markdown_github/setup%201.15-2.png)![](HW3_files/figure-markdown_github/setup%201.15-3.png)

    ## [1] 2119
    ## attr(,"smoother")
    ## Call:
    ## loess(formula = object$oobag.improve ~ x, enp.target = min(max(4, 
    ##     length(x)/10), 50))
    ## 
    ## Number of Observations: 10000 
    ## Equivalent Number of Parameters: 39.99 
    ## Residual Standard Error: 2154000

<table class="table table-striped" style="width: auto !important; margin-left: auto; margin-right: auto;">
<caption>
**Table 4.1 RMSE per Model**
</caption>
<thead>
<tr>
<th style="text-align:left;">
</th>
<th style="text-align:right;">
RMSE
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Linear Regression
</td>
<td style="text-align:right;">
77741.63
</td>
</tr>
<tr>
<td style="text-align:left;">
Stepwise
</td>
<td style="text-align:right;">
74092.34
</td>
</tr>
<tr>
<td style="text-align:left;">
Single Tree
</td>
<td style="text-align:right;">
77639.70
</td>
</tr>
<tr>
<td style="text-align:left;">
Single Tree Pruned
</td>
<td style="text-align:right;">
79019.94
</td>
</tr>
<tr>
<td style="text-align:left;">
Random Forest
</td>
<td style="text-align:right;">
66299.14
</td>
</tr>
<tr>
<td style="text-align:left;">
Gradient Boosting
</td>
<td style="text-align:right;">
66186.75
</td>
</tr>
</tbody>
</table>

![](HW3_files/figure-markdown_github/setup%201.16-1.png)

![](HW3_files/figure-markdown_github/setup%201.17-1.png)

![](HW3_files/figure-markdown_github/setup%201.18-1.png)
