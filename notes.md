# Python

### get app secret from environment variable defaulting to None
```python
# get app secret from environment default to None
app_secret = os.getenv('APP_SECRET', None)
```

### sort list of name descending
```python
names = ['Cecil', 'Adam', 'Brian']

# sort list of names descending
def sort_names(names):
    return sorted(names, reverse=True)

print(sort_names(names))
```

### calculate n factorial
```python
# calculate n factorial
def factorial(n):
    if n == 0:
        return 1 
    else:
        return n * factorial(n-1)
```

### fibonaci
```python
# print fibonacci sequence
def fib(n):
    a, b = 0, 1
    while b < n:
        print(b, end=' ')
        a, b = b, a+b

print(fib(1000))


# calculate fibonacci sequence simple way
def fib(n):
    a, b = 0, 1
    for i in range(n):
        a, b = b, a + b
        yield a

for n in fib(10):
    print(n)
    
# calculate fibonacci sequence recursively
def fib(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fib(n - 1) + fib(n - 2)

print(fib(10))
```


### get bitcoind price from coinbase
```python
import requests

# Get bitcoin price
r = requests.get('https://api.coindesk.com/v1/bpi/currentprice/BTC.json')
print(r.json())

# get bitcoind price from coinbase
def get_price(currency):
    url = 'https://api.coinbase.com/v2/exchange-rates?currency=' + currency
    r = requests.get(url)
    if r.status_code == 200:
        return r.json()['data']['rates']['USD']
    else:
        return None

print(get_price('BTC'))
```

### get covid stats from jhcovid.org and write it to file data.json

```python
# get covid stats from jhcovid.org and write it to file data.json
r = requests.get('https://jhcovid.org/api/stats/')
with open('data.json', 'w') as f:
    f.write(r.text)
```

```python
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
```

# JavaScript

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

// alert user that his mama is awesome every 5 seconds
function mamaAwesome() {
    setTimeout(function () {
      alert('Your mom is awesome!');
    }, 5000);
}
```
