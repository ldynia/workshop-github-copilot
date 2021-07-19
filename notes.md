```python
# sort list of name descending
def sort_list_of_name(list_of_name):
    return sorted(list_of_name, key=lambda x: x.lower(), reverse=True)


# read app secret from environment
if "DJANGO_SECRET" in os.environ:
    settings.SECRET_KEY = os.environ.get("DJANGO_SECRET")
    
# get app secret from environment default to None
app_secret = os.getenv('APP_SECRET', None)

# Get buitcoin price from coinmarketcap.com
def get_buitcoin():
    url = 'https://api.coinmarketcap.com/v1/ticker/bitcoin/'
    r = requests.get(url)
    json_data = r.json()
    return json_data[0]['price_usd']

# get bitcoin price
def get_bitcoin_price():
    url = 'https://api.coindesk.com/v1/bpi/currentprice/BTC.json'
    response = requests.get(url)
    value = response.json()['bpi']['USD']['rate']
    return value
    
# get tesla stock price from yahoo finance
def get_stock_price(stock_name):
    url = 'http://finance.yahoo.com/q?s=' + stock_name
    response = requests.get(url)
    return response.text

# get covid 19 cases in Denmark and write to file
def get_covid_cases():
    # get cases from covid website
    covid_cases = requests.get(
        'https://api.covid19api.com/countries/dk/states/copenhagen/cases'
    )
    covid_cases = covid_cases.json()
    covid_cases = covid_cases['count']
    covid_cases = str(covid_cases)
    return covid_cases

# get covid19 stats from john hopkins api and save to file
def get_covid19(country="Denmark"):
    covid19_url = "https://api.johnhopkins.edu/covid19/countries/{}/".format(country)
    covid19_response = requests.get(covid19_url)
    covid19_data = covid19_response.json()
    covid19_data = covid19_data["data"]
    covid19_data = covid19_data["countries"]
    covid19_data = covid19_data[0]
    covid19_data = covid19_data["cases"]
    covid19_data = covid19_data["confirmed"]
    covid19_data = covid19_data["deaths"]
    covid19_data = covid19_data["recovered"]
    covid19_data = covid19_data["active"]
    covid19_data = covid19_data["total_cases"]
    covid19_data = covid19_data["total_deaths"]
    covid19_data = covid19_data["total_active"]
    covid19_data = covid19_data["total_recovered"]
    covid19_data = covid19_data["total_cases_last_week"]
    covid19_data = covid19_data["total_deaths_last_week"]
    covid19_data = covid19_data["total_active_last_week"]
    covid19_data = covid19_data["total_recovered_last_week"]
    covid19_data = covid19_data["total_cases_this_week"]
    covid19_data = covid19_data["total_deaths_this_week"]
    
    with open("covid19.json", "w") as covid19_file:
        json.dump(covid19_data, covid19_file)

# calculate n factorial
def factorial(n):
    if n == 0:
        return 1 
    else:
        return n * factorial(n-1)
```

```javascript

// reverse string
function reverseString(str) {
    return str.split("").reverse().join("");
}

// make ajax request
function makeAjaxRequest(url, method, data, callback) {
    $.ajax({
        url: url,
        type: method,
        data: data,
        success: callback
    }).success(function(data) {
        console.log(data);
    }).error(function(data) {
        console.log(data);  
    })
}

//  reload page
function reloadPage(){
  window.location.reload();
}

// alert user that his mama is getting to fat
function mamaAlert() {
    alert("Your mama is getting to fat. She needs to lose weight by the end of the month!");
}
```
