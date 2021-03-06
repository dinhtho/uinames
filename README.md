uinames.com
=======

This is the repo for [uinames.com](http://uinames.com). Feel free to contribute to the project by adding names. Keep in mind that more isn't better. Quality over quantity. Quality being the most common/popular names in a region.

### The Algorithm
When the option to pick a region at random is selected, a region will be picked based on the amount of possible name-combinations for that region. A region with more names is more likely to be picked, and regions with less names are less likely to be picked. I propose having a maximum of 100 male names, 100 female names and 300 last names per region. That's 60.000 possible combinations per region.

### The Layout (JSON)
    [
      {
        "region": "Region",
        "male": ["Male", "First", "Names"],
        "female": ["Female", "First", "Names"],
        "surnames": ["Last", "Names"]
      },
      {etc}
    ]

### The API
All responses are returned as JSON(P), with no request limit. Please keep the amount of calls to a minimum though, and cache responses whenever possible.

#### Basic usage
    http://uinames.com/api/
    ---
    {
      "name":"John",
      "surname":"Doe",
      "gender":"male",
      "region":"United States"
    }
#### Optional Parameters
Number of names to return, between `1` and `500`:
<pre>http://uinames.com/api/<strong>?amount=25</strong></pre>

Limit results to the `male` or `female` gender:
<pre>http://uinames.com/api/<strong>?gender=female</strong></pre>

Region-specific results:
<pre>http://uinames.com/api/<strong>?region=germany</strong></pre>

Require a minimum number of characters in a name:
<pre>http://uinames.com/api/<strong>?minlen=25</strong></pre>

Require a maximum number of characters in a name:
<pre>http://uinames.com/api/<strong>?maxlen=75</strong></pre>

For JSONP, specify a callback function to wrap results in:
<pre>http://uinames.com/api/<strong>?callback=example</strong></pre>

#### Extended Usage
Additional randomized personal data is served if the `ext` parameter is detected. Photos offered are from the authorized section on [http://uifaces.com](uifaces.com):
<pre>
http://uinames.com/api/<strong>?ext</strong>
---
{
  "name": "John",
  "surname": "Doe",
  "gender": "male",
  "region": "United States",
  "age": 29,
  "title": "mr",
  "phone": "(123) 456 7890",
  "birthday": {
  "dmy": "19/06/1987", // day, month, year
  "mdy": "06/19/1987", // month, day, year
  "raw": 551062610 // UNIX timestamp
  },
  "email": "john.doe@example.com",
  "password": "Doe87(!",
  "credit_card": {
    "expiration": "12/20",
    "number": "1234-5678-1234-5678",
    "pin": 1234,
    "security": 123
  },
  "photo": "http://uinames.com/api/photos/male/1.jpg"
}
</pre>
#### Exception handling
Error messages have the following format:
<pre>{"error":"Region or language not found"}</pre>

### Author
This project is initiated and maintained by [@thomweerd](http://twitter.com/thomweerd).

### Credit
This massive collection of names wouldn't have been as complete without the help of [these wonderful people](https://github.com/thm/uinames/network/members). Thanks for all the contributions and the continued support!

Special thanks to [Claudio Albertin](http://github.com/ClaudioAlbertin) for his work on the API.

### License
Parts of this repository are licensed. Except where otherwise stated, any code not covered by this license is published under exclusive copyright. See [LICENSE.md](LICENSE.md) to learn more.
