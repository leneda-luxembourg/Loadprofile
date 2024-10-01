# Loadprofile
Fetching Loadprofile information from the LENEDA Platform

Retrieve metering data for a specific metering point. The required path parameters for this request include:

 - startDateTime: The start date and time for the request, for example, 2024-01-01T01:00:00Z. The time is in UTC.
 - endDateTime: The end date and time for the request, for example, 2024-01-10T01:00:00Z. The time is in UTC.
 - obisCode: The OBIS code of the register you want to retrieve data for, such as 1-1:2.29.0.

Please note that query parameters need to be URL-encoded. Below is an example of a properly formatted query. Here you see an example:

> [!NOTE]
> Please note that query parameters need to be URL-encoded. Below is an example of a properly formatted query:

I want to highlight a part of a code block that is written in markdown using triple backticks (```). Here is an image of what I want. code block with highlighting-imgur

I want to replicate how we highlight a sentence in a book with a highlighter/marker . I have used the <pre></pre> and <mark></mark> but these tags dont work inside code block as seen below;

```

https://api.leneda.eu/api/metering-points/LU-METERING_POINT1/time-series?startDateTime=2024-01-01T01%3A00%3A00Z&endDateTime=2024-01-10T01%3A00%3A00Z&obisCode=1-1%3A2.29.0 ~~~

```

