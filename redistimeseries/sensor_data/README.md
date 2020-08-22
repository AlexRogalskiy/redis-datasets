## Creating

```
TS.CREATE temperature:4:12 RETENTION 40 LABELS sensor_id 4 area_id 32
OK
TS.CREATE temperature:5:15 RETENTION 50 LABELS sensor_id 5 area_id 40
OK
TS.CREATE temperature:6:18 RETENTION 60 LABELS sensor_id 6 area_id 48
OK
```



## Adding


```
TS.ADD temperature:4:12 404505606707 30
TS.ADD temperature:4:12 404505606708 31
TS.ADD temperature:5:15 505606707808 50
TS.ADD temperature:5:15 606707808909 51
TS.ADD temperature:6:18 606707808909 60
TS.ADD temperature:6:18 606707808910 61
```

## Last Sample

```
TS.GET temperature:5:15
1) (integer) 606707808909
```

```
TS.GET temperature:4:12
1) (integer) 404505606708
2) 31
```

## using Filters

```
TS.MGET FILTER area_id=32
1) 1) "temperature:4:12"
   2) (empty array)
   3) 1) (integer) 404505606708
      2) 31

```
## With Labels

```
 TS.MGET WITHLABELS FILTER area_id=32
1) 1) "temperature:4:12"
   2) 1) 1) "sensor_id"
         2) "4"
      2) 1) "area_id"
         2) "32"
   3) 1) (integer) 404505606708
      2) 31

 ```
 
 ## Query a range across one or multiple time-series


```
TS.RANGE temperature:5:15 505606707808 5056067070810
1) 1) (integer) 606707808909
   2) 51

```

```
TS.RANGE temperature:4:12 404505606707 404505606710
1) 1) (integer) 404505606707
   2) 30
2) 1) (integer) 404505606708
   2) 31
```





