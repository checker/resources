# Community Resources
This is a collection of useful resources from our community.

## Scraping 101
Many free resources exist for helping you to crawl and scrape the vast amount of information on the internet. No matter what language you are most comfortable with, there are options for you.

### Network/HTTP Requests
Each programmatic request you make to the target website is called a network or HTTP request. Several libraries exist in every programming language under the sun to help you send these types of requests.

- [Axios](https://github.com/axios/axios) (Javascript and Node.js)
- [Guzzle](https://github.com/guzzle/guzzle) (PHP)
- [Requests](https://requests.readthedocs.io/en/master/) (Python)
- [Requests-HTML](https://requests-html.kennethreitz.org/) (Python) - This is a fork of the Requests module linked directly above that includes full Javascript support, so that you can render Javascript-heavy web pages and extract the data.


### Data Extraction
- [BeautifulSoup](https://pypi.org/project/beautifulsoup4/) (Python) 
- [MechanicalSoup](https://pypi.org/project/MechanicalSoup/) (Python)
- [Scrapy](https://scrapy.org/) (Python)
- [Cheerio](https://cheerio.js.org/) (Javascript and Node.js)

### Proxies
Sometimes in order to scrape successfully without being IP-banned or rate-limited, you need to use a number of different IP addresses that you switch out automatically with each request to the target server. These IP addresses are called proxies.


#### Finding Proxies
- [Pastebin](https://pastebin.com)
- [StormProxies](https://stormproxies.com/) [PAID]
- [ProxyMesh](https://proxymesh.com/) [PAID]

**Unverified Sites**

These are sites that provide seemingly free proxies, but their quality and effectiveness is unknown. Be aware that these sites might be tracking your use of the proxies, so keep that in mind. Use at your own risk!

- https://hidemy.name/en/proxy-list/
- http://www.freeproxylists.net/
- https://free-proxy-list.net/

#### Programmatic Proxy Verification
In your script, you are going to want to verify that each of your proxies is working before using it in a request to the target server. The easiest way to do that is to ping Google.com by making a single request with each proxy in your list to Google's primary domain.

**Sample Code:**
```python
import requests

def check_proxy(proxy):
    proxy_dictionary = {
        'http:' : proxy,
        'https:' : proxy,
        'socks' : proxy
    }

    try:
        response = requests.get('https://google.com', timeout=4, proxies=proxy_dictionary)
        if response.status_code === 200:
            return true
        else:
            raise Exception("Bad Proxy!")
    except Exception as error:
        print(error)
```
