# Loadprofile
Fetching Loadprofile information from the LENEDA Platform

Retrieve metering data for a specific metering point. The required path parameters for this request include:

 - startDateTime: The start date and time for the request, for example, 2024-01-01T01:00:00Z. The time is in UTC.
 - endDateTime: The end date and time for the request, for example, 2024-01-10T01:00:00Z. The time is in UTC.
 - obisCode: The OBIS code of the register you want to retrieve data for, such as 1-1:2.29.0.

Please note that query parameters need to be URL-encoded. Below is an example of a properly formatted query. Here you see an example:

> [!NOTE]
> Please note that query parameters need to be URL-encoded. Below is an example of a properly formatted query:


```

https://api.leneda.eu/api/metering-points/LU-METERING_POINT1/time-series?startDateTime=2024-01-01T01%3A00%3A00Z&endDateTime=2024-01-10T01%3A00%3A00Z&obisCode=1-1%3A2.29.0 ~~~

```

If the above API call with the encoded parameters is getting executed then you can expect a result which is formated in the following way:


```

{
  "meteringPointCode": "LU-ELEC-PROD00000000000000000-002",
  "obisCode": "1-1:2.29.0",
  "intervalLength": "PT15M",
  "unit": "kW",
  "items": [
    {
      "value": 14.588,
      "startedAt": "2024-07-01T01:00:00Z",
      "type": "Actual",
      "version": 1,
      "calculated": false
    },
    {
      "value": 22.214,
      "startedAt": "2024-07-01T01:15:00Z",
      "type": "Actual",
      "version": 1,
      "calculated": false
    },
    {
      "value": 8.827,
      "startedAt": "2024-07-01T01:30:00Z",
      "type": "Actual",
      "version": 1,
      "calculated": false
    }
  ]
}

```

A curl statement to execute could look like the following:

```

curl -X 'GET' \
  'https://api.test.nedp.eu/api/metering-points/LU3712/time-series?startDateTime=2024-01-10&endDateTime=2024-01-12&obisCode=1-1%3A2.29.0' \
  -H 'accept: */*' \
  -H 'x-energy-id: LUXE-PH-KE-12345'

```

Executable code could look like the following


```
import pandas as pd
import requests

# Define the URL, headers, and query parameters
url = 'https://api.test.nedp.eu/api/metering-points/LU3712/time-series'
headers = {
    'accept': '*/*',
    'x-energy-id': 'LUXE-PH-KE-12345'
}
params = {
    'startDateTime': '2024-01-10',
    'endDateTime': '2024-01-12',
    'obisCode': '1-1:2.29.0'
}

# Make the GET request to the API
response = requests.get(url, headers=headers, params=params)

# Check if the request was successful
if response.status_code == 200:
    # Parse the JSON response
    response_data = response.json()
    
    # Convert the 'items' part of the response data to a pandas DataFrame
    df = pd.DataFrame(response_data['items'])
    
    # Display the DataFrame
    print(df)
else:
    # Print an error message if the request fails
    print(f"Error: {response.status_code} - {response.text}")


```


