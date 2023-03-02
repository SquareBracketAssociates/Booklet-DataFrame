## DataFrame by example

"Question 1"
weather at: 01:30 at: #temperature.

"Question 2"
(weather group: #temperature by: #type aggregateUsing: #average) at: #snow.
  baseline: 'DataFrame';
  repository: 'github://PolyMathOrg/DataFrame/src';
  load.
  withKeys: (#('01:10' '01:30' '01:50' '02:10' '02:30') collect: #asTime)
  values: #(2.4 0.5 -1.2 -2.3 3.2)
  name: #temperature.
  withKeys: #(temperature precipitation type)
  values: #(0.5 true rain).
  withValues: #(2.4 0.5 -1.2 -2.3 3.2)
  name: #temperature.
  withValues: #(2.4 0.5 -1.2 -2.3 3.2).
DataSeries >> at: ifAbsent:
DataSeries >> at: put:
DataSeries >> removeAt:
DataSeries >> atIndex:
DataSeries >> atIndex: put:
DataSeries >> removeAtIndex:
DataSeries >> at: transform: ifAbsent:
DataSeries >> atIndex: transform:
b := DataSeries withValues: #(-2 -0.5 1 3) name: #b.
DataSeries >> cos
DataSeries >> sin
DataSeries >> tan
DataSeries >> exp
DataSeries >> ln
DataSeries >> log
DataSeries >> log:
DataSeries >> sqrt
DataSeries >> **
DataSeries >> max
DataSeries >> range
DataSeries >> average
DataSeries >> median
DataSeries >> mode
DataSeries >> quantile:
DataSeries >> quartile:
DataSeries >> zerothQuartile
DataSeries >> firstQuartile
DataSeries >> secondQuartile
DataSeries >> thirdQuartile
DataSeries >> fourthQuartile
DataSeries >> interquartileRange
temperature median. "0.5"
temperature stdev. "2.3253"
temperature variance. "5.407"
temperature fourthQuartile = temperature max. "true"
temperature secondQuartile = temperature median. "true"
temperature interquartileRange = (temperature thirdQuartile - temperature firstQuartile). "true"
temperature range = (temperature max - temperature min). "true"
temperature variance = (temperature stdev ** 2). "true"

precipitation := DataSeries
  withKeys: keys
  values: #(true true true false true)
  name: #precipitation.

type := DataSeries
  withKeys: keys
  values: #(rain rain snow - rain)
  name: #type.
type uniqueValues. "#(- rain snow)"
	(2.4 true rain)
	(0.5 true rain)
	(-1.2 true snow)
	(-2.3 false -)
	(3.2 true rain)).
  (2.4 0.5 -1.2 -2.3 3.2)
  (true true true false true)
  (rain rain snow - rain)).
  (2.4 0.5 -1.2 -2.3 3.2)
  (true true true false true)
  (rain rain snow - rain)).

weather columnNames: #(temperature precipitation type).
weather rowNames: (#('01:10' '01:30' '01:50' '02:10' '02:30')
		collect: #asTime).
DataFrame class >> withRows: rowNames:
DataFrame class >> withRows: rowNames: columnNames:
DataFrame class >> withColumns: columnNames:
DataFrame class >> withColumns: rowNames:
DataFrame class >> withColumns: rowNames: columnNames:
DataFrame class >> withColumnNames:
DataFrame class >> withRowNames: columnNames:
  withRowNames: (#('01:10' '01:30' '01:50' '02:10' '02:30') collect: #asTime)
  columnNames: #(temperature precipitation type).
weather numberOfColumns. "3"
weather columnNames.
weather column: #temperature.
weather column: #temperature put: #(1.2 -2.1 3.4 -5.9 -0.4).
weather columnAt: 1.
weather columnAt: 1 put: #(2.4 0.5 -1.2 -2.3 3.2).
weather rowsAt: #(2 3 4).
weather rowsFrom: 2 to: 4.
weather columnsAt: #(2 3).
weather columnsFrom: 2 to: 3.
weather columns: #(precipitation temperature).
DataFrame >> rowsAt: put:
DataFrame >> rowsFrom: to: put:
DataFrame >> columns: put:
DataFrame >> columnsAt: put:
DataFrame >> columnsFrom: to: put:
  addColumn: #(86 79 23 16 90)
  named: #humidity
  atPosition: 2.
  addRow: #(2.0 81 true rain)
  named: '2:50' asTime.
  withValues: #(39 39 32 24 14 14)
  name: #wind.

weather
  addColumn: wind
  atPosition: 2.
weather removeRowAt: 6.
  row at: #temperature transform: [ :celsius |
    celsius * 9/5 + 32 ] ].
  (row at: #temperature) < 32 ].
  (row at: #temperature) < 32 ].
  row at: #humidity transform: [ :percent | percent / 100 ].
  row removeAt: #precipitation.
  row ].
  (row at: #temperature) < 32 ].
  detect: [ :row | (row at: #temperature) < 20 ]
  ifNone: [ 'not found' ].
	inject: 0
	into: [ :sum :row | sum + row ].
	group: #temperature
	by: #type
	aggregateUsing: #average
  as: #averageTemperature.
  groupBy: #type
  aggregate: {
    #temperature using: #size as: #count .
    #temperature using: #min as: #minTemperature .
    #temperature using: #max as: #maxTemperature .
    #humidity using: #average as: #avgHumidity }.
  "Read data frame from a given location using a given DataFrameReader. Location can be a file reference, a database connection, or something else (depending on the implementation of the reader)"
  ^ aDataFrameReader readFrom: aLocation
  "Write data frame to a given location using a given DataFrameWriter. Location can be a file reference, a database connection, or something else (depending on the implementation of the writer)"
  aDataFrameWriter write: self to: aLocation
DataFrame class >> readFromCsv: withSeparator:
DataFrame class >> readFromCsvWithRowNames:
DataFrame class >> readFromCsvWithRowNames: separator:
DataFrame >> writeToCsv:
DataFrame >> writeToCsv: withSeparator: