# Historical-Schedules-API
Aviation Edge [Historical Schedules API](https://aviation-edge.com/historical-flight-schedules-api/) provides the latest recorded data of airport schedules worlwide, on a given date or date range. It has global coverage with the exception of military and private airfields. We save and collect the real-time data we provide through our Schedules API and provide this in a separate API. The historical API has the same amount of details for each flight in the schedule with even more filters available. Delay and cancellation data stored, making the API perfect for compensation claims and historical flight analysis/comparisons.

### Documentation
You may find input parameters, output examples with explanations for each item, filter list, and more in the [documentation](https://aviation-edge.com/developers/).

### Example Fields of Use
- Websites, tools or apps on historical flight status
- Viewing historical flight delays and cancellations for flight compensation
- Viewing changes in airport or airline traffic over time
- Avrage delay and cancellation analysis
- Flight schedule changes analysis

### Request 
For the departure schedule of a certain airport on a certain date:

**GET** `https://aviation-edge.com/v2/public/flightsHistory?key=[API_KEY]&code=JFK&type=departure&date_from=YYYY-MM-DD`

For the arrival schedule of a certain airport on a certain date:

**GET** `https://aviation-edge.com/v2/public/flightsHistory?key=[API_KEY]&code=JFK&type=arrival&date_from=YYYY-MM-DD`

For the schedule of a certain airport of a certain date range (also available for arrival):

**GET** `https://aviation-edge.com/v2/public/flightsHistory?key=[API_KEY]&code=JFK&type=departure&date_from=YYYY-MM-DD&date_to=YYYY-MM-DD`

For the schedule of a certain airport on a certain date (or range) but only flights with a certain status:

**GET** `https://aviation-edge.com/v2/public/flightsHistory?key=[API_KEY]&code=JFK&type=arrival&date_from=YYYY-MM-DD&date_to=YYYY-MM-DD&status=cancelled`

For tracking individual historical flights:

**GET** `https://aviation-edge.com/v2/public/flightsHistory?key=[API_KEY]&code=JFK&type=departure&date_from=YYYY-MM-DD&date_to=YYYY-MM-DD&flight_number=[1234]`

For filtering the flights of a certain airline from the arrival schedule of a certain airport on a certain date (also available for departure schedules and as a date range):

**GET** `https://aviation-edge.com/v2/public/flightsHistory?key=[API_KEY]&code=JFK&type=arrival&date_from=YYYY-MM-DD&&airline_iata=TK`

### Filters
```
&code=          (obligatory) Departure or arrival airport IATA code
&type=          (obligatory) Either "departure" or "arrival" as both within the same query is not possible
&date_from=     (obligatory) Requested date in YYYY-MM-DD format. Can be used alone for a single date or in combination with "&date_to" to define a range.

&date_to=       end date of the requested date range
&dep_iataCode=  filter of departure airport if "arrival" for "&type=" was chosen, based on the airport IATA code
&arr_iataCode=  filter of arrival airport if "departure" for "&type=" was chosen, based on the airport IATA code
&airline_iata=  option to filter airline based on airline IATA code
&flight_num=    option to filter a specific flight based on its flight number
```

### Response
```
[
{"type": "arrival", 
"status": "landed", 
"departure": 
{
"iataCode": "eyw",
"icaoCode": "keyw", 
"gate": "8", 
"delay": 15, 
"scheduledTime": "2021-11-02t16:55:00.000", 
"actualTime": "2021-11-02t17:09:00.000", 
"estimatedRunway": "2021-11-02t17:09:00.000", 
"actualRunway": "2021-11-02t17:09:00.000"
},
"arrival": 
{"iataCode": "iah", 
"icaoCode": "kiah", 
"terminal": "b", 
"baggage": "b3", 
"gate": "76", 
"scheduledTime": "2021-11-02t19:00:00.000", 
"estimatedTime": "2021-11-02t18:46:00.000", 
"actualTime": "2021-11-02t18:55:00.000",
"estimatedRunway": "2021-11-02t18:55:00.000",
"actualRunway": "2021-11-02t18:55:00.000"},
"airline":
{"name": "united airlines", 
"iataCode": "ua", 
"icaoCode": "ual"
}, 
"flight": 
{"number": "6264", 
"iataNumber": "ua6264", 
"icaoNumber": "ual6264"}
}
]
```

### Access & Support
[Contact us](https://aviation-edge.com/contact/) via email for any questions or support requests.

[Get your API key](https://aviation-edge.com/premium-api/) in a minute and start testing the data right away. The API is provided through API subscriptions. All plans grant access to the Historical Schedules API and other APIs with a difference of the monthly API call limit. Choose the best plan for you and upgrade, downgrade or cancel your plan anytime without  commitments.

### License
The use of the API is subject to Aviation Edge [Terms and Conditions](https://aviation-edge.com/api-terms-of-service/).
