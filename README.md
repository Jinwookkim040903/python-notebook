# python-notebook
<center>
    <img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/Logos/organization_logo/organization_logo.png" width="300" alt="cognitiveclass.ai logo"  />
</center>

<center>
    <img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/Logos/organization_logo/organization_logo.png" width="300" alt="cognitiveclass.ai logo"  />
</center>
​
  File "/tmp/ipykernel_70/1043631908.py", line 1
    <center>
    ^
SyntaxError: invalid syntax
Extracting and Visualizing Stock Data
Description
Extracting essential data from a dataset and displaying it is a necessary part of data science; therefore individuals can make correct decisions based on the data. In this assignment, you will extract some stock data, you will then display this data in a graph.

Table of Contents
Define a Function that Makes a Graph
Question 1: Use yfinance to Extract Stock Data
Question 2: Use Webscraping to Extract Tesla Revenue Data
Question 3: Use yfinance to Extract Stock Data
Question 4: Use Webscraping to Extract GME Revenue Data
Question 5: Plot Tesla Stock Graph
Question 6: Plot GameStop Stock Graph
Estimated Time Needed: 30 min

!pip install yfinance==0.1.67
#!pip install pandas==1.3.3
!pip install requests==2.26.0
!mamba install bs4==4.10.0 -y
!pip install plotly==5.3.1
Collecting yfinance==0.1.67
  Downloading yfinance-0.1.67-py2.py3-none-any.whl (25 kB)
Requirement already satisfied: pandas>=0.24 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (1.3.5)
Requirement already satisfied: requests>=2.20 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (2.28.1)
Requirement already satisfied: lxml>=4.5.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (4.9.1)
Collecting multitasking>=0.0.7
  Downloading multitasking-0.0.11-py3-none-any.whl (8.5 kB)
Requirement already satisfied: numpy>=1.15 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (1.21.6)
Requirement already satisfied: python-dateutil>=2.7.3 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from pandas>=0.24->yfinance==0.1.67) (2.8.2)
Requirement already satisfied: pytz>=2017.3 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from pandas>=0.24->yfinance==0.1.67) (2022.1)
Requirement already satisfied: charset-normalizer<3,>=2 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (2.1.0)
Requirement already satisfied: certifi>=2017.4.17 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (2022.6.15)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (1.26.11)
Requirement already satisfied: idna<4,>=2.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (3.3)
Requirement already satisfied: six>=1.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from python-dateutil>=2.7.3->pandas>=0.24->yfinance==0.1.67) (1.16.0)
Installing collected packages: multitasking, yfinance
Successfully installed multitasking-0.0.11 yfinance-0.1.67
Collecting requests==2.26.0
  Downloading requests-2.26.0-py2.py3-none-any.whl (62 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 62.3/62.3 kB 7.3 MB/s eta 0:00:00
Requirement already satisfied: certifi>=2017.4.17 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests==2.26.0) (2022.6.15)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests==2.26.0) (1.26.11)
Requirement already satisfied: idna<4,>=2.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests==2.26.0) (3.3)
Collecting charset-normalizer~=2.0.0
  Downloading charset_normalizer-2.0.12-py3-none-any.whl (39 kB)
Installing collected packages: charset-normalizer, requests
  Attempting uninstall: charset-normalizer
    Found existing installation: charset-normalizer 2.1.0
    Uninstalling charset-normalizer-2.1.0:
      Successfully uninstalled charset-normalizer-2.1.0
  Attempting uninstall: requests
    Found existing installation: requests 2.28.1
    Uninstalling requests-2.28.1:
      Successfully uninstalled requests-2.28.1
ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
ibm-cos-sdk-core 2.12.0 requires requests<3.0,>=2.27.1, but you have requests 2.26.0 which is incompatible.
Successfully installed charset-normalizer-2.0.12 requests-2.26.0

                  __    __    __    __
                 /  \  /  \  /  \  /  \
                /    \/    \/    \/    \
███████████████/  /██/  /██/  /██/  /████████████████████████
              /  / \   / \   / \   / \  \____
             /  /   \_/   \_/   \_/   \    o \__,
            / _/                       \_____/  `
            |/
        ███╗   ███╗ █████╗ ███╗   ███╗██████╗  █████╗
        ████╗ ████║██╔══██╗████╗ ████║██╔══██╗██╔══██╗
        ██╔████╔██║███████║██╔████╔██║██████╔╝███████║
        ██║╚██╔╝██║██╔══██║██║╚██╔╝██║██╔══██╗██╔══██║
        ██║ ╚═╝ ██║██║  ██║██║ ╚═╝ ██║██████╔╝██║  ██║
        ╚═╝     ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚═════╝ ╚═╝  ╚═╝

        mamba (0.15.3) supported by @QuantStack

        GitHub:  https://github.com/mamba-org/mamba
        Twitter: https://twitter.com/QuantStack

█████████████████████████████████████████████████████████████


Looking for: ['bs4==4.10.0']

pkgs/main/linux-64       [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/r/linux-64          [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) Finalizing...
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) Done
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/noarch         [====================] (00m:00s) Done
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [<=>               ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [<=>             ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [<=>             ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [ <=>                ] (00m:00s) 1 MB / ?? (2.71 MB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [ <=>                ] (00m:00s) Finalizing...
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [ <=>                ] (00m:00s) Done
pkgs/r/noarch            [====================] (00m:00s) Done
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) Finalizing...
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) Done
pkgs/r/linux-64          [====================] (00m:00s) Done
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/main/linux-64       [  <=>               ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/main/linux-64       [  <=>               ] (00m:00s) 2 MB / ?? (3.45 MB/s)
pkgs/main/linux-64       [   <=>              ] (00m:00s) 2 MB / ?? (3.45 MB/s)
pkgs/main/linux-64       [   <=>              ] (00m:00s) 3 MB / ?? (3.67 MB/s)
pkgs/main/linux-64       [    <=>             ] (00m:00s) 3 MB / ?? (3.67 MB/s)
pkgs/main/linux-64       [    <=>             ] (00m:00s) 4 MB / ?? (3.86 MB/s)
pkgs/main/linux-64       [     <=>            ] (00m:00s) 4 MB / ?? (3.86 MB/s)
pkgs/main/linux-64       [     <=>            ] (00m:00s) 4 MB / ?? (4.00 MB/s)
pkgs/main/linux-64       [     <=>            ] (00m:00s) Finalizing...
pkgs/main/linux-64       [     <=>            ] (00m:00s) Done
pkgs/main/linux-64       [====================] (00m:00s) Done

Pinned packages:
  - python 3.7.*


Transaction

  Prefix: /home/jupyterlab/conda/envs/python

  Updating specs:

   - bs4==4.10.0
   - ca-certificates
   - certifi
   - openssl


  Package               Version  Build           Channel                  Size
────────────────────────────────────────────────────────────────────────────────
  Install:
────────────────────────────────────────────────────────────────────────────────

  + bs4                  4.10.0  hd3eb1b0_0      pkgs/main/noarch        10 KB

  Change:
────────────────────────────────────────────────────────────────────────────────

  - certifi           2022.6.15  py37h89c1867_0  installed                    
  + certifi           2022.6.15  py37h06a4308_0  pkgs/main/linux-64     153 KB
  - openssl              1.1.1q  h166bdaf_0      installed                    
  + openssl              1.1.1q  h7f8727e_0      pkgs/main/linux-64       3 MB

  Upgrade:
────────────────────────────────────────────────────────────────────────────────

  - ca-certificates   2022.6.15  ha878542_0      installed                    
  + ca-certificates  2022.07.19  h06a4308_0      pkgs/main/linux-64     124 KB

  Downgrade:
────────────────────────────────────────────────────────────────────────────────

  - beautifulsoup4       4.11.1  pyha770c72_0    installed                    
  + beautifulsoup4       4.10.0  pyh06a4308_0    pkgs/main/noarch        85 KB

  Summary:

  Install: 1 packages
  Change: 2 packages
  Upgrade: 1 packages
  Downgrade: 1 packages

  Total download: 3 MB

────────────────────────────────────────────────────────────────────────────────

Downloading  [>                                        ] (00m:00s)   38.79 KB/s
Extracting   [>                                                      ] (--:--) 
Finished bs4                                  (00m:00s)              10 KB     39 KB/s
Downloading  [>                                        ] (00m:00s)   38.79 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [>                                        ] (00m:00s)   38.79 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [>                                        ] (00m:00s)   38.79 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=>                                       ] (00m:00s)  360.81 KB/s
Extracting   [>                                                      ] (--:--) 
Finished beautifulsoup4                       (00m:00s)              85 KB    322 KB/s
Downloading  [=>                                       ] (00m:00s)  360.81 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=>                                       ] (00m:00s)  360.81 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [==>                                      ] (00m:00s)  826.88 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [==>                                      ] (00m:00s)  826.88 KB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [==>                                      ] (00m:00s)  826.88 KB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Finished ca-certificates                      (00m:00s)             124 KB    469 KB/s
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Finished certifi                              (00m:00s)             153 KB    578 KB/s
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [================>                        ] (00m:00s)        2 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [================>                        ] (00m:00s)        2 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========================>                ] (00m:00s)        3 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========================>                ] (00m:00s)        3 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [======================================>  ] (00m:00s)    9.10 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [======================================>  ] (00m:00s)    9.10 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Finished openssl                              (00m:00s)               3 MB      8 MB/s
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [=========================================] (00m:00s)        5 / 5
import yfinance as yf
import pandas as pd
import requests
from bs4 import BeautifulSoup
import plotly.graph_objects as go
from plotly.subplots import make_subplots
Define Graphing Function
In this section, we define the function make_graph. You don't have to know how the function works, you should only care about the inputs. It takes a dataframe with stock data (dataframe must contain Date and Close columns), a dataframe with revenue data (dataframe must contain Date and Revenue columns), and the name of the stock.

def make_graph(stock_data, revenue_data, stock):
    fig = make_subplots(rows=2, cols=1, shared_xaxes=True, subplot_titles=("Historical Share Price", "Historical Revenue"), vertical_spacing = .3)
    stock_data_specific = stock_data[stock_data.Date <= '2021--06-14']
    revenue_data_specific = revenue_data[revenue_data.Date <= '2021-04-30']
    fig.add_trace(go.Scatter(x=pd.to_datetime(stock_data_specific.Date, infer_datetime_format=True), y=stock_data_specific.Close.astype("float"), name="Share Price"), row=1, col=1)
    fig.add_trace(go.Scatter(x=pd.to_datetime(revenue_data_specific.Date, infer_datetime_format=True), y=revenue_data_specific.Revenue.astype("float"), name="Revenue"), row=2, col=1)
    fig.update_xaxes(title_text="Date", row=1, col=1)
    fig.update_xaxes(title_text="Date", row=2, col=1)
    fig.update_yaxes(title_text="Price ($US)", row=1, col=1)
    fig.update_yaxes(title_text="Revenue ($US Millions)", row=2, col=1)
    fig.update_layout(showlegend=False,
    height=900,
    title=stock,
    xaxis_rangeslider_visible=True)
    fig.show()
Question 1: Use yfinance to Extract Stock Data
Using the Ticker function enter the ticker symbol of the stock we want to extract data on to create a ticker object. The stock is Tesla and its ticker symbol is TSLA.

tesla = yf.Ticker("TSLA")
tesla_data = tesla.history(period = "max")
tesla_data.reset_index(inplace = True)
tesla_data.head()
Using the ticker object and the function history extract stock information and save it in a dataframe named tesla_data. Set the period parameter to max so we get information for the maximum amount of time.

url = "https://www.macrotrends.net/stocks/charts/TSLA/tesla/revenue"
html_data = requests.get(url).text
soup = BeautifulSoup(html_data, "html.parser")
soup.find_all('title')
​
Reset the index using the reset_index(inplace=True) function on the tesla_data DataFrame and display the first five rows of the tesla_data dataframe using the head function. Take a screenshot of the results and code from the beginning of Question 1 to the results below.

tesla_revenue = pd.DataFrame(columns = ['Date', 'Revenue'])
​
for row in soup.find_all("tbody")[1].find_all("tr"):
    col = row.find_all("td")
    date = col[0].text
    revenue = col[1].text.replace("$", "").replace(",", "")
    
Question 2: Use Webscraping to Extract Tesla Revenue Data
Use the requests library to download the webpage https://www.macrotrends.net/stocks/charts/TSLA/tesla/revenue. Save the text of the response as a variable named html_data.

url = "https://www.macrotrends.net/stocks/charts/TSLA/tesla/revenue"
html_data = requests.get(url).text
​
Parse the html data using beautiful_soup.

soup = BeautifulSoup(html_data, "html.parser")
soup.find_all('title')
​
Using BeautifulSoup or the read_html function extract the table with Tesla Quarterly Revenue and store it into a dataframe named tesla_revenue. The dataframe should have columns Date and Revenue.

Click here if you need help locating the table
tesla_revenue = pd.DataFrame(columns = ['Date', 'Revenue'])
​
for row in soup.find_all("tbody")[1].find_all("tr"):
    col = row.find_all("td")
    date = col[0].text
    revenue = col[1].text.replace("$", "").replace(",", "")
​
Execute the following line to remove the comma and dollar sign from the Revenue column.

tesla_revenue["Revenue"] = tesla_revenue['Revenue'].str.replace(',|\$',"")
Execute the following lines to remove an null or empty strings in the Revenue column.

tesla_revenue.dropna(inplace=True)
​
tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != ""]
Display the last 5 row of the tesla_revenue dataframe using the tail function. Take a screenshot of the results.

tesla_revenue = tesla_revenue.append({"Date": date, "Revenue": revenue}, ignore_index = True)
tesla_revenue.dropna(inplace=True)
tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != ""]
tesla_revenue.tail()
Question 3: Use yfinance to Extract Stock Data
Using the Ticker function enter the ticker symbol of the stock we want to extract data on to create a ticker object. The stock is GameStop and its ticker symbol is GME.

GameStop = yf.Ticker("GME")
​
Using the ticker object and the function history extract stock information and save it in a dataframe named gme_data. Set the period parameter to max so we get information for the maximum amount of time.

gme_data = GameStop.history(period = 'max')
​
Reset the index using the reset_index(inplace=True) function on the gme_data DataFrame and display the first five rows of the gme_data dataframe using the head function. Take a screenshot of the results and code from the beginning of Question 3 to the results below.

gme_data.reset_index(inplace = True)
gme_data.head()
Question 4: Use Webscraping to Extract GME Revenue Data
Use the requests library to download the webpage https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html. Save the text of the response as a variable named html_data.

url = "https://www.macrotrends.net/stocks/charts/GME/gamestop/revenue"
html_data = requests.get(url).text
​
​
Parse the html data using beautiful_soup.

soup = BeautifulSoup(html_data, "html.parser")
soup.find_all('title')
​
​
Using BeautifulSoup or the read_html function extract the table with GameStop Quarterly Revenue and store it into a dataframe named gme_revenue. The dataframe should have columns Date and Revenue. Make sure the comma and dollar sign is removed from the Revenue column using a method similar to what you did in Question 2.

Click here if you need help locating the table
gme_revenue = pd.DataFrame(columns = ['Date', 'Revenue'])
for row in soup.find_all("tbody")[1].find_all("tr"):
    col = row.find_all("td")
    date = col[0].text
    revenue = col[1].text.replace("$", "").replace(",", "")
​
​
Display the last five rows of the gme_revenue dataframe using the tail function. Take a screenshot of the results.

    gme_revenue = gme_revenue.append({"Date": date, "Revenue": revenue}, ignore_index = True)
tesla_revenue.dropna(inplace=True)
tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != ""]
gme_revenue.tail()
Use the make_graph function to graph the Tesla Stock Data, also provide a title for the graph. The structure to call the make_graph function is make_graph(tesla_data, tesla_revenue, 'Tesla'). Note the graph will only show data upto June 2021.

make_graph(tesla_data, tesla_revenue, 'Tesla')
make_graph(tesla_data, tesla_revenue, 'Tesla')
Question 6: Plot GameStop Stock Graph
Use the make_graph function to graph the GameStop Stock Data, also provide a title for the graph. The structure to call the make_graph function is make_graph(gme_data, gme_revenue, 'GameStop'). Note the graph will only show data upto June 2021.

make_graph(gme_data, gme_revenue, 'GameStop')
​
About the Authors:
Joseph Santarcangelo has a PhD in Electrical Engineering, his research focused on using machine learning, signal processing, and computer vision to determine how videos impact human cognition. Joseph has been working for IBM since he completed his PhD.

Azim Hirjani







Change Log
Date (YYYY-MM-DD)	Version	Changed By	Change Description
2022-02-28	1.2	Lakshmi Holla	Changed the URL of GameStop
2020-11-10	1.1	Malika Singla	Deleted the Optional part
2020-08-27	1.0	Malika Singla	Added lab to GitLab
© IBM Corporation 2020. All rights reserved. 


Table of Contents
Using yfinance to Extract Stock Info
Using yfinance to Extract Historical Share Price Data
Using yfinance to Extract Historical Dividends Data
Exercise
Estimated Time Needed: 30 min

!pip install yfinance==0.1.67
#!pip install pandas==1.3.3
Collecting yfinance==0.1.67
  Downloading yfinance-0.1.67-py2.py3-none-any.whl (25 kB)
Requirement already satisfied: pandas>=0.24 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (1.3.5)
Requirement already satisfied: requests>=2.20 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (2.27.1)
Requirement already satisfied: lxml>=4.5.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (4.9.0)
Collecting multitasking>=0.0.7
  Downloading multitasking-0.0.10.tar.gz (8.2 kB)
  Preparing metadata (setup.py) ... done
Requirement already satisfied: numpy>=1.15 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (1.21.6)
Requirement already satisfied: python-dateutil>=2.7.3 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from pandas>=0.24->yfinance==0.1.67) (2.8.2)
Requirement already satisfied: pytz>=2017.3 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from pandas>=0.24->yfinance==0.1.67) (2022.1)
Requirement already satisfied: certifi>=2017.4.17 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (2022.5.18.1)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (1.26.9)
Requirement already satisfied: idna<4,>=2.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (3.3)
Requirement already satisfied: charset-normalizer~=2.0.0 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (2.0.12)
Requirement already satisfied: six>=1.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from python-dateutil>=2.7.3->pandas>=0.24->yfinance==0.1.67) (1.16.0)
Building wheels for collected packages: multitasking
  Building wheel for multitasking (setup.py) ... done
  Created wheel for multitasking: filename=multitasking-0.0.10-py3-none-any.whl size=8498 sha256=b1f48db6aba41dc05e89807585a925770c8f1985291a8a844cdccf17792a6d4d
  Stored in directory: /home/jupyterlab/.cache/pip/wheels/34/ba/79/c0260c6f1a03f420ec7673eff9981778f293b9107974679e36
Successfully built multitasking
Installing collected packages: multitasking, yfinance
Successfully installed multitasking-0.0.10 yfinance-0.1.67
import yfinance as yf
import pandas as pd
Using the yfinance Library to Extract Stock Data
Using the Ticker module we can create an object that will allow us to access functions to extract data. To do this we need to provide the ticker symbol for the stock, here the company is Apple and the ticker symbol is AAPL.

apple = yf.Ticker("AAPL")
Now we can access functions and variables to extract the type of data we need. You can view them and what they represent here https://aroussi.com/post/python-yahoo-finance.

Stock Info
Using the attribute info we can extract information about the stock as a Python dictionary.

apple_info=apple.info
apple_info
{'zip': '95014',
 'sector': 'Technology',
 'fullTimeEmployees': 154000,
 'longBusinessSummary': 'Apple Inc. designs, manufactures, and markets smartphones, personal computers, tablets, wearables, and accessories worldwide. It also sells various related services. In addition, the company offers iPhone, a line of smartphones; Mac, a line of personal computers; iPad, a line of multi-purpose tablets; AirPods Max, an over-ear wireless headphone; and wearables, home, and accessories comprising AirPods, Apple TV, Apple Watch, Beats products, HomePod, and iPod touch. Further, it provides AppleCare support services; cloud services store services; and operates various platforms, including the App Store that allow customers to discover and download applications and digital content, such as books, music, video, games, and podcasts. Additionally, the company offers various services, such as Apple Arcade, a game subscription service; Apple Music, which offers users a curated listening experience with on-demand radio stations; Apple News+, a subscription news and magazine service; Apple TV+, which offers exclusive original content; Apple Card, a co-branded credit card; and Apple Pay, a cashless payment service, as well as licenses its intellectual property. The company serves consumers, and small and mid-sized businesses; and the education, enterprise, and government markets. It distributes third-party applications for its products through the App Store. The company also sells its products through its retail and online stores, and direct sales force; and third-party cellular network carriers, wholesalers, retailers, and resellers. Apple Inc. was incorporated in 1977 and is headquartered in Cupertino, California.',
 'city': 'Cupertino',
 'phone': '408 996 1010',
 'state': 'CA',
 'country': 'United States',
 'companyOfficers': [],
 'website': 'https://www.apple.com',
 'maxAge': 1,
 'address1': 'One Apple Park Way',
 'industry': 'Consumer Electronics',
 'ebitdaMargins': 0.33842,
 'profitMargins': 0.26407,
 'grossMargins': 0.43322,
 'operatingCashflow': 116425998336,
 'revenueGrowth': 0.086,
 'operatingMargins': 0.30926,
 'ebitda': 130633998336,
 'targetLowPrice': 155,
 'recommendationKey': 'buy',
 'grossProfits': 152836000000,
 'freeCashflow': 84384628736,
 'targetMedianPrice': 190,
 'currentPrice': 131.56,
 'earningsGrowth': 0.086,
 'currentRatio': 0.927,
 'returnOnAssets': 0.21695,
 'numberOfAnalystOpinions': 43,
 'targetMeanPrice': 187.43,
 'debtToEquity': 178.016,
 'returnOnEquity': 1.49271,
 'targetHighPrice': 214,
 'totalCash': 51511001088,
 'totalDebt': 119980998656,
 'totalRevenue': 386017001472,
 'totalCashPerShare': 3.183,
 'financialCurrency': 'USD',
 'revenuePerShare': 23.471,
 'quickRatio': 0.76,
 'recommendationMean': 1.9,
 'exchange': 'NMS',
 'shortName': 'Apple Inc.',
 'longName': 'Apple Inc.',
 'exchangeTimezoneName': 'America/New_York',
 'exchangeTimezoneShortName': 'EDT',
 'isEsgPopulated': False,
 'gmtOffSetMilliseconds': '-14400000',
 'quoteType': 'EQUITY',
 'symbol': 'AAPL',
 'messageBoardId': 'finmb_24937',
 'market': 'us_market',
 'annualHoldingsTurnover': None,
 'enterpriseToRevenue': 5.694,
 'beta3Year': None,
 'enterpriseToEbitda': 16.824,
 '52WeekChange': -0.0055933595,
 'morningStarRiskRating': None,
 'forwardEps': 6.55,
 'revenueQuarterlyGrowth': None,
 'sharesOutstanding': 16185199616,
 'fundInceptionDate': None,
 'annualReportExpenseRatio': None,
 'totalAssets': None,
 'bookValue': 4.158,
 'sharesShort': 113283277,
 'sharesPercentSharesOut': 0.0069999998,
 'fundFamily': None,
 'lastFiscalYearEnd': 1632528000,
 'heldPercentInstitutions': 0.59621,
 'netIncomeToCommon': 101934997504,
 'trailingEps': 6.137,
 'lastDividendValue': 0.23,
 'SandP52WeekChange': -0.13017213,
 'priceToBook': 31.640211,
 'heldPercentInsiders': 0.00072999997,
 'nextFiscalYearEnd': 1695600000,
 'yield': None,
 'mostRecentQuarter': 1648252800,
 'shortRatio': 0.99,
 'sharesShortPreviousMonthDate': 1651190400,
 'floatShares': 16168348412,
 'beta': 1.20009,
 'enterpriseValue': 2197792358400,
 'priceHint': 2,
 'threeYearAverageReturn': None,
 'lastSplitDate': 1598832000,
 'lastSplitFactor': '4:1',
 'legalType': None,
 'lastDividendDate': 1651795200,
 'morningStarOverallRating': None,
 'earningsQuarterlyGrowth': 0.058,
 'priceToSalesTrailing12Months': 5.5161424,
 'dateShortInterest': 1653955200,
 'pegRatio': 2.23,
 'ytdReturn': None,
 'forwardPE': 20.085495,
 'lastCapGain': None,
 'shortPercentOfFloat': 0.0069999998,
 'sharesShortPriorMonth': 103977276,
 'impliedSharesOutstanding': 0,
 'category': None,
 'fiveYearAverageReturn': None,
 'previousClose': 130.06,
 'regularMarketOpen': 130.065,
 'twoHundredDayAverage': 158.9273,
 'trailingAnnualDividendYield': 0.006766108,
 'payoutRatio': 0.14310001,
 'volume24Hr': None,
 'regularMarketDayHigh': 133.079,
 'navPrice': None,
 'averageDailyVolume10Day': 89503450,
 'regularMarketPreviousClose': 130.06,
 'fiftyDayAverage': 151.6678,
 'trailingAnnualDividendRate': 0.88,
 'open': 130.065,
 'toCurrency': None,
 'averageVolume10days': 89503450,
 'expireDate': None,
 'algorithm': None,
 'dividendRate': 0.92,
 'exDividendDate': 1651795200,
 'circulatingSupply': None,
 'startDate': None,
 'regularMarketDayLow': 129.81,
 'currency': 'USD',
 'trailingPE': 21.437183,
 'regularMarketVolume': 134520290,
 'lastMarket': None,
 'maxSupply': None,
 'openInterest': None,
 'marketCap': 2129324802048,
 'volumeAllCurrencies': None,
 'strikePrice': None,
 'averageVolume': 96058793,
 'dayLow': 129.81,
 'ask': 131.58,
 'askSize': 800,
 'volume': 134520290,
 'fiftyTwoWeekHigh': 182.94,
 'fromCurrency': None,
 'fiveYearAvgDividendYield': 1.08,
 'fiftyTwoWeekLow': 129.04,
 'bid': 131.55,
 'tradeable': False,
 'dividendYield': 0.0069999998,
 'bidSize': 1300,
 'dayHigh': 133.079,
 'regularMarketPrice': 131.56,
 'preMarketPrice': None,
 'logo_url': 'https://logo.clearbit.com/apple.com'}
We can get the 'country' using the key country

apple_info['country']
'United States'
Extracting Share Price
A share is the single smallest part of a company's stock that you can buy, the prices of these shares fluctuate over time. Using the history() method we can get the share price of the stock over a certain period of time. Using the period parameter we can set how far back from the present to get data. The options for period are 1 day (1d), 5d, 1 month (1mo) , 3mo, 6mo, 1 year (1y), 2y, 5y, 10y, ytd, and max.

apple_share_price_data = apple.history(period="max")
The format that the data is returned in is a Pandas DataFrame. With the Date as the index the share Open, High, Low, Close, Volume, and Stock Splits are given for each day.

apple_share_price_data.head()
Open	High	Low	Close	Volume	Dividends	Stock Splits
Date							
1980-12-12	0.100178	0.100614	0.100178	0.100178	469033600	0.0	0.0
1980-12-15	0.095388	0.095388	0.094952	0.094952	175884800	0.0	0.0
1980-12-16	0.088418	0.088418	0.087983	0.087983	105728000	0.0	0.0
1980-12-17	0.090160	0.090596	0.090160	0.090160	86441600	0.0	0.0
1980-12-18	0.092774	0.093210	0.092774	0.092774	73449600	0.0	0.0
We can reset the index of the DataFrame with the reset_index function. We also set the inplace paramter to True so the change takes place to the DataFrame itself.

apple_share_price_data.reset_index(inplace=True)
We can plot the Open price against the Date:

apple_share_price_data.plot(x="Date", y="Open")
<AxesSubplot:xlabel='Date'>

Extracting Dividends
Dividends are the distribution of a companys profits to shareholders. In this case they are defined as an amount of money returned per share an investor owns. Using the variable dividends we can get a dataframe of the data. The period of the data is given by the period defined in the 'history` function.

apple.dividends
Date
1987-05-11    0.000536
1987-08-10    0.000536
1987-11-17    0.000714
1988-02-12    0.000714
1988-05-16    0.000714
                ...   
2021-05-07    0.220000
2021-08-06    0.220000
2021-11-05    0.220000
2022-02-04    0.220000
2022-05-06    0.230000
Name: Dividends, Length: 75, dtype: float64
We can plot the dividends overtime:

apple.dividends.plot()
<AxesSubplot:xlabel='Date'>

Exercise
Now using the Ticker module create an object for AMD (Advanced Micro Devices) with the ticker symbol is AMD called; name the object amd.

amd = yf.Ticker("AMD")
Question 1 Use the key 'country' to find the country the stock belongs to, remember it as it will be a quiz question.

amd_info=amd.info
amd_info
amd_info['country']
'United States'
Question 2 Use the key 'sector' to find the sector the stock belongs to, remember it as it will be a quiz question.

amd_info["sector"]
'Technology'
Question 3 Obtain stock data for AMD using the history function, set the period to max. Find the Volume traded on the first day (first row).

amd_share_price_data = amd.history(period="max")
amd_share_price_data.max()
Open            1.632800e+02
High            1.644600e+02
Low             1.561000e+02
Close           1.619100e+02
Volume          3.250584e+08
Dividends       0.000000e+00
Stock Splits    2.000000e+00
dtype: float64
About the Authors:
Joseph Santarcangelo has a PhD in Electrical Engineering, his research focused on using machine learning, signal processing, and computer vision to determine how videos impact human cognition. Joseph has been working for IBM since he completed his PhD.

Azim Hirjani







Change Log
Date (YYYY-MM-DD)	Version	Changed By	Change Description
2020-11-10	1.1	Malika Singla	Deleted the Optional part
2020-08-27	1.0	Malika Singla	Added lab to GitLab
© IBM Corporation 2020. All rights reserv



labs/PY0220EN
Notebook

Python


Apache Toree - Scala


Julia 1.1.1


R


Swift

Console

Python


Apache Toree - Scala


Julia 1.1.1


R


Swift

Elyra
Generic Pipeline Editor

Pipeline Editor

Pipeline Editor

Python Editor

R Editor

Documentation

Other
Terminal

Text File

Markdown File

Julia File

Show Contextual Help











Markdown

Publish



Run as Pipeline


Python

<center>
    <img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/Logos/organization_logo/organization_logo.png" width="300" alt="cognitiveclass.ai logo"  />
</center>

<center>
    <img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/Logos/organization_logo/organization_logo.png" width="300" alt="cognitiveclass.ai logo"  />
</center>
​
  File "/tmp/ipykernel_70/1043631908.py", line 1
    <center>
    ^
SyntaxError: invalid syntax
Extracting and Visualizing Stock Data
Description
Extracting essential data from a dataset and displaying it is a necessary part of data science; therefore individuals can make correct decisions based on the data. In this assignment, you will extract some stock data, you will then display this data in a graph.

Table of Contents
Define a Function that Makes a Graph
Question 1: Use yfinance to Extract Stock Data
Question 2: Use Webscraping to Extract Tesla Revenue Data
Question 3: Use yfinance to Extract Stock Data
Question 4: Use Webscraping to Extract GME Revenue Data
Question 5: Plot Tesla Stock Graph
Question 6: Plot GameStop Stock Graph
Estimated Time Needed: 30 min

!pip install yfinance==0.1.67
#!pip install pandas==1.3.3
!pip install requests==2.26.0
!mamba install bs4==4.10.0 -y
!pip install plotly==5.3.1
Collecting yfinance==0.1.67
  Downloading yfinance-0.1.67-py2.py3-none-any.whl (25 kB)
Requirement already satisfied: pandas>=0.24 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (1.3.5)
Requirement already satisfied: requests>=2.20 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (2.28.1)
Requirement already satisfied: lxml>=4.5.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (4.9.1)
Collecting multitasking>=0.0.7
  Downloading multitasking-0.0.11-py3-none-any.whl (8.5 kB)
Requirement already satisfied: numpy>=1.15 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (1.21.6)
Requirement already satisfied: python-dateutil>=2.7.3 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from pandas>=0.24->yfinance==0.1.67) (2.8.2)
Requirement already satisfied: pytz>=2017.3 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from pandas>=0.24->yfinance==0.1.67) (2022.1)
Requirement already satisfied: charset-normalizer<3,>=2 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (2.1.0)
Requirement already satisfied: certifi>=2017.4.17 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (2022.6.15)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (1.26.11)
Requirement already satisfied: idna<4,>=2.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (3.3)
Requirement already satisfied: six>=1.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from python-dateutil>=2.7.3->pandas>=0.24->yfinance==0.1.67) (1.16.0)
Installing collected packages: multitasking, yfinance
Successfully installed multitasking-0.0.11 yfinance-0.1.67
Collecting requests==2.26.0
  Downloading requests-2.26.0-py2.py3-none-any.whl (62 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 62.3/62.3 kB 7.3 MB/s eta 0:00:00
Requirement already satisfied: certifi>=2017.4.17 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests==2.26.0) (2022.6.15)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests==2.26.0) (1.26.11)
Requirement already satisfied: idna<4,>=2.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests==2.26.0) (3.3)
Collecting charset-normalizer~=2.0.0
  Downloading charset_normalizer-2.0.12-py3-none-any.whl (39 kB)
Installing collected packages: charset-normalizer, requests
  Attempting uninstall: charset-normalizer
    Found existing installation: charset-normalizer 2.1.0
    Uninstalling charset-normalizer-2.1.0:
      Successfully uninstalled charset-normalizer-2.1.0
  Attempting uninstall: requests
    Found existing installation: requests 2.28.1
    Uninstalling requests-2.28.1:
      Successfully uninstalled requests-2.28.1
ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
ibm-cos-sdk-core 2.12.0 requires requests<3.0,>=2.27.1, but you have requests 2.26.0 which is incompatible.
Successfully installed charset-normalizer-2.0.12 requests-2.26.0

                  __    __    __    __
                 /  \  /  \  /  \  /  \
                /    \/    \/    \/    \
███████████████/  /██/  /██/  /██/  /████████████████████████
              /  / \   / \   / \   / \  \____
             /  /   \_/   \_/   \_/   \    o \__,
            / _/                       \_____/  `
            |/
        ███╗   ███╗ █████╗ ███╗   ███╗██████╗  █████╗
        ████╗ ████║██╔══██╗████╗ ████║██╔══██╗██╔══██╗
        ██╔████╔██║███████║██╔████╔██║██████╔╝███████║
        ██║╚██╔╝██║██╔══██║██║╚██╔╝██║██╔══██╗██╔══██║
        ██║ ╚═╝ ██║██║  ██║██║ ╚═╝ ██║██████╔╝██║  ██║
        ╚═╝     ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚═════╝ ╚═╝  ╚═╝

        mamba (0.15.3) supported by @QuantStack

        GitHub:  https://github.com/mamba-org/mamba
        Twitter: https://twitter.com/QuantStack

█████████████████████████████████████████████████████████████


Looking for: ['bs4==4.10.0']

pkgs/main/linux-64       [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/r/linux-64          [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1011.39 KB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) Finalizing...
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) Done
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/noarch         [====================] (00m:00s) Done
pkgs/main/linux-64       [=>                ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [<=>               ] (00m:00s) 324 KB / ?? (1.04 MB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [=>              ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [<=>             ] (00m:00s) 304 KB / ?? (997.13 KB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [=>              ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [<=>             ] (00m:00s) 304 KB / ?? (996.97 KB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [ <=>                ] (00m:00s) 1 MB / ?? (2.71 MB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [ <=>                ] (00m:00s) Finalizing...
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/r/noarch            [ <=>                ] (00m:00s) Done
pkgs/r/noarch            [====================] (00m:00s) Done
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) 1 MB / ?? (2.90 MB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) Finalizing...
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/r/linux-64          [ <=>                ] (00m:00s) Done
pkgs/r/linux-64          [====================] (00m:00s) Done
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/main/linux-64       [  <=>               ] (00m:00s) 1 MB / ?? (2.89 MB/s)
pkgs/main/linux-64       [  <=>               ] (00m:00s) 2 MB / ?? (3.45 MB/s)
pkgs/main/linux-64       [   <=>              ] (00m:00s) 2 MB / ?? (3.45 MB/s)
pkgs/main/linux-64       [   <=>              ] (00m:00s) 3 MB / ?? (3.67 MB/s)
pkgs/main/linux-64       [    <=>             ] (00m:00s) 3 MB / ?? (3.67 MB/s)
pkgs/main/linux-64       [    <=>             ] (00m:00s) 4 MB / ?? (3.86 MB/s)
pkgs/main/linux-64       [     <=>            ] (00m:00s) 4 MB / ?? (3.86 MB/s)
pkgs/main/linux-64       [     <=>            ] (00m:00s) 4 MB / ?? (4.00 MB/s)
pkgs/main/linux-64       [     <=>            ] (00m:00s) Finalizing...
pkgs/main/linux-64       [     <=>            ] (00m:00s) Done
pkgs/main/linux-64       [====================] (00m:00s) Done

Pinned packages:
  - python 3.7.*


Transaction

  Prefix: /home/jupyterlab/conda/envs/python

  Updating specs:

   - bs4==4.10.0
   - ca-certificates
   - certifi
   - openssl


  Package               Version  Build           Channel                  Size
────────────────────────────────────────────────────────────────────────────────
  Install:
────────────────────────────────────────────────────────────────────────────────

  + bs4                  4.10.0  hd3eb1b0_0      pkgs/main/noarch        10 KB

  Change:
────────────────────────────────────────────────────────────────────────────────

  - certifi           2022.6.15  py37h89c1867_0  installed                    
  + certifi           2022.6.15  py37h06a4308_0  pkgs/main/linux-64     153 KB
  - openssl              1.1.1q  h166bdaf_0      installed                    
  + openssl              1.1.1q  h7f8727e_0      pkgs/main/linux-64       3 MB

  Upgrade:
────────────────────────────────────────────────────────────────────────────────

  - ca-certificates   2022.6.15  ha878542_0      installed                    
  + ca-certificates  2022.07.19  h06a4308_0      pkgs/main/linux-64     124 KB

  Downgrade:
────────────────────────────────────────────────────────────────────────────────

  - beautifulsoup4       4.11.1  pyha770c72_0    installed                    
  + beautifulsoup4       4.10.0  pyh06a4308_0    pkgs/main/noarch        85 KB

  Summary:

  Install: 1 packages
  Change: 2 packages
  Upgrade: 1 packages
  Downgrade: 1 packages

  Total download: 3 MB

────────────────────────────────────────────────────────────────────────────────

Downloading  [>                                        ] (00m:00s)   38.79 KB/s
Extracting   [>                                                      ] (--:--) 
Finished bs4                                  (00m:00s)              10 KB     39 KB/s
Downloading  [>                                        ] (00m:00s)   38.79 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [>                                        ] (00m:00s)   38.79 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [>                                        ] (00m:00s)   38.79 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=>                                       ] (00m:00s)  360.81 KB/s
Extracting   [>                                                      ] (--:--) 
Finished beautifulsoup4                       (00m:00s)              85 KB    322 KB/s
Downloading  [=>                                       ] (00m:00s)  360.81 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=>                                       ] (00m:00s)  360.81 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [==>                                      ] (00m:00s)  826.88 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [==>                                      ] (00m:00s)  826.88 KB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [==>                                      ] (00m:00s)  826.88 KB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Finished ca-certificates                      (00m:00s)             124 KB    469 KB/s
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Finished certifi                              (00m:00s)             153 KB    578 KB/s
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [================>                        ] (00m:00s)        2 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [================>                        ] (00m:00s)        2 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========================>                ] (00m:00s)        3 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [========================>                ] (00m:00s)        3 / 5
Downloading  [====>                                    ] (00m:00s)    1.37 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [======================================>  ] (00m:00s)    9.10 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [======================================>  ] (00m:00s)    9.10 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Finished openssl                              (00m:00s)               3 MB      8 MB/s
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    9.44 MB/s
Extracting   [=========================================] (00m:00s)        5 / 5
import yfinance as yf
import pandas as pd
import requests
from bs4 import BeautifulSoup
import plotly.graph_objects as go
from plotly.subplots import make_subplots
Define Graphing Function
In this section, we define the function make_graph. You don't have to know how the function works, you should only care about the inputs. It takes a dataframe with stock data (dataframe must contain Date and Close columns), a dataframe with revenue data (dataframe must contain Date and Revenue columns), and the name of the stock.

def make_graph(stock_data, revenue_data, stock):
    fig = make_subplots(rows=2, cols=1, shared_xaxes=True, subplot_titles=("Historical Share Price", "Historical Revenue"), vertical_spacing = .3)
    stock_data_specific = stock_data[stock_data.Date <= '2021--06-14']
    revenue_data_specific = revenue_data[revenue_data.Date <= '2021-04-30']
    fig.add_trace(go.Scatter(x=pd.to_datetime(stock_data_specific.Date, infer_datetime_format=True), y=stock_data_specific.Close.astype("float"), name="Share Price"), row=1, col=1)
    fig.add_trace(go.Scatter(x=pd.to_datetime(revenue_data_specific.Date, infer_datetime_format=True), y=revenue_data_specific.Revenue.astype("float"), name="Revenue"), row=2, col=1)
    fig.update_xaxes(title_text="Date", row=1, col=1)
    fig.update_xaxes(title_text="Date", row=2, col=1)
    fig.update_yaxes(title_text="Price ($US)", row=1, col=1)
    fig.update_yaxes(title_text="Revenue ($US Millions)", row=2, col=1)
    fig.update_layout(showlegend=False,
    height=900,
    title=stock,
    xaxis_rangeslider_visible=True)
    fig.show()
Question 1: Use yfinance to Extract Stock Data
Using the Ticker function enter the ticker symbol of the stock we want to extract data on to create a ticker object. The stock is Tesla and its ticker symbol is TSLA.

tesla = yf.Ticker("TSLA")
tesla_data = tesla.history(period = "max")
tesla_data.reset_index(inplace = True)
tesla_data.head()
Using the ticker object and the function history extract stock information and save it in a dataframe named tesla_data. Set the period parameter to max so we get information for the maximum amount of time.

url = "https://www.macrotrends.net/stocks/charts/TSLA/tesla/revenue"
html_data = requests.get(url).text
soup = BeautifulSoup(html_data, "html.parser")
soup.find_all('title')
​
Reset the index using the reset_index(inplace=True) function on the tesla_data DataFrame and display the first five rows of the tesla_data dataframe using the head function. Take a screenshot of the results and code from the beginning of Question 1 to the results below.

tesla_revenue = pd.DataFrame(columns = ['Date', 'Revenue'])
​
for row in soup.find_all("tbody")[1].find_all("tr"):
    col = row.find_all("td")
    date = col[0].text
    revenue = col[1].text.replace("$", "").replace(",", "")
    
Question 2: Use Webscraping to Extract Tesla Revenue Data
Use the requests library to download the webpage https://www.macrotrends.net/stocks/charts/TSLA/tesla/revenue. Save the text of the response as a variable named html_data.

url = "https://www.macrotrends.net/stocks/charts/TSLA/tesla/revenue"
html_data = requests.get(url).text
​
Parse the html data using beautiful_soup.

soup = BeautifulSoup(html_data, "html.parser")
soup.find_all('title')
​
Using BeautifulSoup or the read_html function extract the table with Tesla Quarterly Revenue and store it into a dataframe named tesla_revenue. The dataframe should have columns Date and Revenue.

Click here if you need help locating the table
tesla_revenue = pd.DataFrame(columns = ['Date', 'Revenue'])
​
for row in soup.find_all("tbody")[1].find_all("tr"):
    col = row.find_all("td")
    date = col[0].text
    revenue = col[1].text.replace("$", "").replace(",", "")
​
Execute the following line to remove the comma and dollar sign from the Revenue column.

tesla_revenue["Revenue"] = tesla_revenue['Revenue'].str.replace(',|\$',"")
Execute the following lines to remove an null or empty strings in the Revenue column.

tesla_revenue.dropna(inplace=True)
​
tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != ""]
Display the last 5 row of the tesla_revenue dataframe using the tail function. Take a screenshot of the results.

tesla_revenue = tesla_revenue.append({"Date": date, "Revenue": revenue}, ignore_index = True)
tesla_revenue.dropna(inplace=True)
tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != ""]
tesla_revenue.tail()
Question 3: Use yfinance to Extract Stock Data
Using the Ticker function enter the ticker symbol of the stock we want to extract data on to create a ticker object. The stock is GameStop and its ticker symbol is GME.

GameStop = yf.Ticker("GME")
​
Using the ticker object and the function history extract stock information and save it in a dataframe named gme_data. Set the period parameter to max so we get information for the maximum amount of time.

gme_data = GameStop.history(period = 'max')
​
Reset the index using the reset_index(inplace=True) function on the gme_data DataFrame and display the first five rows of the gme_data dataframe using the head function. Take a screenshot of the results and code from the beginning of Question 3 to the results below.

gme_data.reset_index(inplace = True)
gme_data.head()
Question 4: Use Webscraping to Extract GME Revenue Data
Use the requests library to download the webpage https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html. Save the text of the response as a variable named html_data.

url = "https://www.macrotrends.net/stocks/charts/GME/gamestop/revenue"
html_data = requests.get(url).text
​
​
Parse the html data using beautiful_soup.

soup = BeautifulSoup(html_data, "html.parser")
soup.find_all('title')
​
​
Using BeautifulSoup or the read_html function extract the table with GameStop Quarterly Revenue and store it into a dataframe named gme_revenue. The dataframe should have columns Date and Revenue. Make sure the comma and dollar sign is removed from the Revenue column using a method similar to what you did in Question 2.

Click here if you need help locating the table
gme_revenue = pd.DataFrame(columns = ['Date', 'Revenue'])
for row in soup.find_all("tbody")[1].find_all("tr"):
    col = row.find_all("td")
    date = col[0].text
    revenue = col[1].text.replace("$", "").replace(",", "")
​
​
Display the last five rows of the gme_revenue dataframe using the tail function. Take a screenshot of the results.

    gme_revenue = gme_revenue.append({"Date": date, "Revenue": revenue}, ignore_index = True)
tesla_revenue.dropna(inplace=True)
tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != ""]
gme_revenue.tail()
Use the make_graph function to graph the Tesla Stock Data, also provide a title for the graph. The structure to call the make_graph function is make_graph(tesla_data, tesla_revenue, 'Tesla'). Note the graph will only show data upto June 2021.

make_graph(tesla_data, tesla_revenue, 'Tesla')
make_graph(tesla_data, tesla_revenue, 'Tesla')
Question 6: Plot GameStop Stock Graph
Use the make_graph function to graph the GameStop Stock Data, also provide a title for the graph. The structure to call the make_graph function is make_graph(gme_data, gme_revenue, 'GameStop'). Note the graph will only show data upto June 2021.

make_graph(gme_data, gme_revenue, 'GameStop')
​
About the Authors:
Joseph Santarcangelo has a PhD in Electrical Engineering, his research focused on using machine learning, signal processing, and computer vision to determine how videos impact human cognition. Joseph has been working for IBM since he completed his PhD.

Azim Hirjani







Change Log
Date (YYYY-MM-DD)	Version	Changed By	Change Description
2022-02-28	1.2	Lakshmi Holla	Changed the URL of GameStop
2020-11-10	1.1	Malika Singla	Deleted the Optional part
2020-08-27	1.0	Malika Singla	Added lab to GitLab
© IBM Corporation 2020. All rights reserved. 
​
​
​
​
​
​
​
​
​
​
​
​
​
​










Markdown

Publish



Run as Pipeline


Python

Extracting Stock Data Using a Python Library
cognitiveclass.ai logo
A company's stock share is a piece of the company more precisely:

A stock (also known as equity) is a security that represents the ownership of a fraction of a corporation. This entitles the owner of the stock to a proportion of the corporation's assets and profits equal to how much stock they own. Units of stock are called "shares." [1]

An investor can buy a stock and sell it later. If the stock price increases, the investor profits, If it decreases,the investor with incur a loss.  Determining the stock price is complex; it depends on the number of outstanding shares, the size of the company's future profits, and much more. People trade stocks throughout the day the stock ticker is a report of the price of a certain stock, updated continuously throughout the trading session by the various stock market exchanges.

You are a data scientist working for a hedge fund; it's your job to determine any suspicious stock activity. In this lab you will extract stock data using a Python library. We will use the yfinance library, it allows us to extract data for stocks returning data in a pandas dataframe. You will use the lab to extract.

Table of Contents
Using yfinance to Extract Stock Info
Using yfinance to Extract Historical Share Price Data
Using yfinance to Extract Historical Dividends Data
Exercise
Estimated Time Needed: 30 min

!pip install yfinance==0.1.67
#!pip install pandas==1.3.3
Collecting yfinance==0.1.67
  Downloading yfinance-0.1.67-py2.py3-none-any.whl (25 kB)
Requirement already satisfied: pandas>=0.24 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (1.3.5)
Requirement already satisfied: requests>=2.20 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (2.27.1)
Requirement already satisfied: lxml>=4.5.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (4.9.0)
Collecting multitasking>=0.0.7
  Downloading multitasking-0.0.10.tar.gz (8.2 kB)
  Preparing metadata (setup.py) ... done
Requirement already satisfied: numpy>=1.15 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from yfinance==0.1.67) (1.21.6)
Requirement already satisfied: python-dateutil>=2.7.3 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from pandas>=0.24->yfinance==0.1.67) (2.8.2)
Requirement already satisfied: pytz>=2017.3 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from pandas>=0.24->yfinance==0.1.67) (2022.1)
Requirement already satisfied: certifi>=2017.4.17 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (2022.5.18.1)
Requirement already satisfied: urllib3<1.27,>=1.21.1 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (1.26.9)
Requirement already satisfied: idna<4,>=2.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (3.3)
Requirement already satisfied: charset-normalizer~=2.0.0 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from requests>=2.20->yfinance==0.1.67) (2.0.12)
Requirement already satisfied: six>=1.5 in /home/jupyterlab/conda/envs/python/lib/python3.7/site-packages (from python-dateutil>=2.7.3->pandas>=0.24->yfinance==0.1.67) (1.16.0)
Building wheels for collected packages: multitasking
  Building wheel for multitasking (setup.py) ... done
  Created wheel for multitasking: filename=multitasking-0.0.10-py3-none-any.whl size=8498 sha256=b1f48db6aba41dc05e89807585a925770c8f1985291a8a844cdccf17792a6d4d
  Stored in directory: /home/jupyterlab/.cache/pip/wheels/34/ba/79/c0260c6f1a03f420ec7673eff9981778f293b9107974679e36
Successfully built multitasking
Installing collected packages: multitasking, yfinance
Successfully installed multitasking-0.0.10 yfinance-0.1.67
import yfinance as yf
import pandas as pd
Using the yfinance Library to Extract Stock Data
Using the Ticker module we can create an object that will allow us to access functions to extract data. To do this we need to provide the ticker symbol for the stock, here the company is Apple and the ticker symbol is AAPL.

apple = yf.Ticker("AAPL")
Now we can access functions and variables to extract the type of data we need. You can view them and what they represent here https://aroussi.com/post/python-yahoo-finance.

Stock Info
Using the attribute info we can extract information about the stock as a Python dictionary.

apple_info=apple.info
apple_info
{'zip': '95014',
 'sector': 'Technology',
 'fullTimeEmployees': 154000,
 'longBusinessSummary': 'Apple Inc. designs, manufactures, and markets smartphones, personal computers, tablets, wearables, and accessories worldwide. It also sells various related services. In addition, the company offers iPhone, a line of smartphones; Mac, a line of personal computers; iPad, a line of multi-purpose tablets; AirPods Max, an over-ear wireless headphone; and wearables, home, and accessories comprising AirPods, Apple TV, Apple Watch, Beats products, HomePod, and iPod touch. Further, it provides AppleCare support services; cloud services store services; and operates various platforms, including the App Store that allow customers to discover and download applications and digital content, such as books, music, video, games, and podcasts. Additionally, the company offers various services, such as Apple Arcade, a game subscription service; Apple Music, which offers users a curated listening experience with on-demand radio stations; Apple News+, a subscription news and magazine service; Apple TV+, which offers exclusive original content; Apple Card, a co-branded credit card; and Apple Pay, a cashless payment service, as well as licenses its intellectual property. The company serves consumers, and small and mid-sized businesses; and the education, enterprise, and government markets. It distributes third-party applications for its products through the App Store. The company also sells its products through its retail and online stores, and direct sales force; and third-party cellular network carriers, wholesalers, retailers, and resellers. Apple Inc. was incorporated in 1977 and is headquartered in Cupertino, California.',
 'city': 'Cupertino',
 'phone': '408 996 1010',
 'state': 'CA',
 'country': 'United States',
 'companyOfficers': [],
 'website': 'https://www.apple.com',
 'maxAge': 1,
 'address1': 'One Apple Park Way',
 'industry': 'Consumer Electronics',
 'ebitdaMargins': 0.33842,
 'profitMargins': 0.26407,
 'grossMargins': 0.43322,
 'operatingCashflow': 116425998336,
 'revenueGrowth': 0.086,
 'operatingMargins': 0.30926,
 'ebitda': 130633998336,
 'targetLowPrice': 155,
 'recommendationKey': 'buy',
 'grossProfits': 152836000000,
 'freeCashflow': 84384628736,
 'targetMedianPrice': 190,
 'currentPrice': 131.56,
 'earningsGrowth': 0.086,
 'currentRatio': 0.927,
 'returnOnAssets': 0.21695,
 'numberOfAnalystOpinions': 43,
 'targetMeanPrice': 187.43,
 'debtToEquity': 178.016,
 'returnOnEquity': 1.49271,
 'targetHighPrice': 214,
 'totalCash': 51511001088,
 'totalDebt': 119980998656,
 'totalRevenue': 386017001472,
 'totalCashPerShare': 3.183,
 'financialCurrency': 'USD',
 'revenuePerShare': 23.471,
 'quickRatio': 0.76,
 'recommendationMean': 1.9,
 'exchange': 'NMS',
 'shortName': 'Apple Inc.',
 'longName': 'Apple Inc.',
 'exchangeTimezoneName': 'America/New_York',
 'exchangeTimezoneShortName': 'EDT',
 'isEsgPopulated': False,
 'gmtOffSetMilliseconds': '-14400000',
 'quoteType': 'EQUITY',
 'symbol': 'AAPL',
 'messageBoardId': 'finmb_24937',
 'market': 'us_market',
 'annualHoldingsTurnover': None,
 'enterpriseToRevenue': 5.694,
 'beta3Year': None,
 'enterpriseToEbitda': 16.824,
 '52WeekChange': -0.0055933595,
 'morningStarRiskRating': None,
 'forwardEps': 6.55,
 'revenueQuarterlyGrowth': None,
 'sharesOutstanding': 16185199616,
 'fundInceptionDate': None,
 'annualReportExpenseRatio': None,
 'totalAssets': None,
 'bookValue': 4.158,
 'sharesShort': 113283277,
 'sharesPercentSharesOut': 0.0069999998,
 'fundFamily': None,
 'lastFiscalYearEnd': 1632528000,
 'heldPercentInstitutions': 0.59621,
 'netIncomeToCommon': 101934997504,
 'trailingEps': 6.137,
 'lastDividendValue': 0.23,
 'SandP52WeekChange': -0.13017213,
 'priceToBook': 31.640211,
 'heldPercentInsiders': 0.00072999997,
 'nextFiscalYearEnd': 1695600000,
 'yield': None,
 'mostRecentQuarter': 1648252800,
 'shortRatio': 0.99,
 'sharesShortPreviousMonthDate': 1651190400,
 'floatShares': 16168348412,
 'beta': 1.20009,
 'enterpriseValue': 2197792358400,
 'priceHint': 2,
 'threeYearAverageReturn': None,
 'lastSplitDate': 1598832000,
 'lastSplitFactor': '4:1',
 'legalType': None,
 'lastDividendDate': 1651795200,
 'morningStarOverallRating': None,
 'earningsQuarterlyGrowth': 0.058,
 'priceToSalesTrailing12Months': 5.5161424,
 'dateShortInterest': 1653955200,
 'pegRatio': 2.23,
 'ytdReturn': None,
 'forwardPE': 20.085495,
 'lastCapGain': None,
 'shortPercentOfFloat': 0.0069999998,
 'sharesShortPriorMonth': 103977276,
 'impliedSharesOutstanding': 0,
 'category': None,
 'fiveYearAverageReturn': None,
 'previousClose': 130.06,
 'regularMarketOpen': 130.065,
 'twoHundredDayAverage': 158.9273,
 'trailingAnnualDividendYield': 0.006766108,
 'payoutRatio': 0.14310001,
 'volume24Hr': None,
 'regularMarketDayHigh': 133.079,
 'navPrice': None,
 'averageDailyVolume10Day': 89503450,
 'regularMarketPreviousClose': 130.06,
 'fiftyDayAverage': 151.6678,
 'trailingAnnualDividendRate': 0.88,
 'open': 130.065,
 'toCurrency': None,
 'averageVolume10days': 89503450,
 'expireDate': None,
 'algorithm': None,
 'dividendRate': 0.92,
 'exDividendDate': 1651795200,
 'circulatingSupply': None,
 'startDate': None,
 'regularMarketDayLow': 129.81,
 'currency': 'USD',
 'trailingPE': 21.437183,
 'regularMarketVolume': 134520290,
 'lastMarket': None,
 'maxSupply': None,
 'openInterest': None,
 'marketCap': 2129324802048,
 'volumeAllCurrencies': None,
 'strikePrice': None,
 'averageVolume': 96058793,
 'dayLow': 129.81,
 'ask': 131.58,
 'askSize': 800,
 'volume': 134520290,
 'fiftyTwoWeekHigh': 182.94,
 'fromCurrency': None,
 'fiveYearAvgDividendYield': 1.08,
 'fiftyTwoWeekLow': 129.04,
 'bid': 131.55,
 'tradeable': False,
 'dividendYield': 0.0069999998,
 'bidSize': 1300,
 'dayHigh': 133.079,
 'regularMarketPrice': 131.56,
 'preMarketPrice': None,
 'logo_url': 'https://logo.clearbit.com/apple.com'}
We can get the 'country' using the key country

apple_info['country']
'United States'
Extracting Share Price
A share is the single smallest part of a company's stock that you can buy, the prices of these shares fluctuate over time. Using the history() method we can get the share price of the stock over a certain period of time. Using the period parameter we can set how far back from the present to get data. The options for period are 1 day (1d), 5d, 1 month (1mo) , 3mo, 6mo, 1 year (1y), 2y, 5y, 10y, ytd, and max.

apple_share_price_data = apple.history(period="max")
The format that the data is returned in is a Pandas DataFrame. With the Date as the index the share Open, High, Low, Close, Volume, and Stock Splits are given for each day.

apple_share_price_data.head()
Open	High	Low	Close	Volume	Dividends	Stock Splits
Date							
1980-12-12	0.100178	0.100614	0.100178	0.100178	469033600	0.0	0.0
1980-12-15	0.095388	0.095388	0.094952	0.094952	175884800	0.0	0.0
1980-12-16	0.088418	0.088418	0.087983	0.087983	105728000	0.0	0.0
1980-12-17	0.090160	0.090596	0.090160	0.090160	86441600	0.0	0.0
1980-12-18	0.092774	0.093210	0.092774	0.092774	73449600	0.0	0.0
We can reset the index of the DataFrame with the reset_index function. We also set the inplace paramter to True so the change takes place to the DataFrame itself.

apple_share_price_data.reset_index(inplace=True)
We can plot the Open price against the Date:

apple_share_price_data.plot(x="Date", y="Open")
<AxesSubplot:xlabel='Date'>

Extracting Dividends
Dividends are the distribution of a companys profits to shareholders. In this case they are defined as an amount of money returned per share an investor owns. Using the variable dividends we can get a dataframe of the data. The period of the data is given by the period defined in the 'history` function.

apple.dividends
Date
1987-05-11    0.000536
1987-08-10    0.000536
1987-11-17    0.000714
1988-02-12    0.000714
1988-05-16    0.000714
                ...   
2021-05-07    0.220000
2021-08-06    0.220000
2021-11-05    0.220000
2022-02-04    0.220000
2022-05-06    0.230000
Name: Dividends, Length: 75, dtype: float64
We can plot the dividends overtime:

apple.dividends.plot()
<AxesSubplot:xlabel='Date'>

Exercise
Now using the Ticker module create an object for AMD (Advanced Micro Devices) with the ticker symbol is AMD called; name the object amd.

amd = yf.Ticker("AMD")
Question 1 Use the key 'country' to find the country the stock belongs to, remember it as it will be a quiz question.

amd_info=amd.info
amd_info
amd_info['country']
'United States'
Question 2 Use the key 'sector' to find the sector the stock belongs to, remember it as it will be a quiz question.

amd_info["sector"]
'Technology'
Question 3 Obtain stock data for AMD using the history function, set the period to max. Find the Volume traded on the first day (first row).

amd_share_price_data = amd.history(period="max")
amd_share_price_data.max()
Open            1.632800e+02
High            1.644600e+02
Low             1.561000e+02
Close           1.619100e+02
Volume          3.250584e+08
Dividends       0.000000e+00
Stock Splits    2.000000e+00
dtype: float64
About the Authors:
Joseph Santarcangelo has a PhD in Electrical Engineering, his research focused on using machine learning, signal processing, and computer vision to determine how videos impact human cognition. Joseph has been working for IBM since he completed his PhD.

Azim Hirjani







Change Log
Date (YYYY-MM-DD)	Version	Changed By	Change Description
2020-11-10	1.1	Malika Singla	Deleted the Optional part
2020-08-27	1.0	Malika Singla	Added lab to GitLab
© IBM Corporation 2020. All rights reserved. 










Markdown

Publish



Run as Pipeline


Python

Skills Network Logo

Web Scraping Lab
Estimated time needed: 30 minutes

Objectives
After completing this lab you will be able to:

Table of Contents
Beautiful Soup Object
Tag
Children, Parents, and Siblings
HTML Attributes
Navigable String
Filter
find All
find
HTML Attributes
Navigable String
Downloading And Scraping The Contents Of A Web
Estimated time needed: 25 min

For this lab, we are going to be using Python and several Python libraries. Some of these libraries might be installed in your lab environment or in SN Labs. Others may need to be installed by you. The cells below will install these libraries when executed.

!mamba install bs4==4.10.0 -y
!pip install lxml==4.6.4
!mamba install html5lib==1.1 -y
# !pip install requests==2.26.0

                  __    __    __    __
                 /  \  /  \  /  \  /  \
                /    \/    \/    \/    \
███████████████/  /██/  /██/  /██/  /████████████████████████
              /  / \   / \   / \   / \  \____
             /  /   \_/   \_/   \_/   \    o \__,
            / _/                       \_____/  `
            |/
        ███╗   ███╗ █████╗ ███╗   ███╗██████╗  █████╗
        ████╗ ████║██╔══██╗████╗ ████║██╔══██╗██╔══██╗
        ██╔████╔██║███████║██╔████╔██║██████╔╝███████║
        ██║╚██╔╝██║██╔══██║██║╚██╔╝██║██╔══██╗██╔══██║
        ██║ ╚═╝ ██║██║  ██║██║ ╚═╝ ██║██████╔╝██║  ██║
        ╚═╝     ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚═════╝ ╚═╝  ╚═╝

        mamba (0.15.3) supported by @QuantStack

        GitHub:  https://github.com/mamba-org/mamba
        Twitter: https://twitter.com/QuantStack

█████████████████████████████████████████████████████████████


Looking for: ['bs4==4.10.0']

pkgs/main/linux-64       [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1016.85 KB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1016.85 KB/s)
pkgs/r/linux-64          [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1016.85 KB/s)
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1016.85 KB/s)
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/r/noarch            [<=>                 ] (00m:00s) 
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1016.85 KB/s)
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/r/noarch            [=>                ] (00m:00s) 312 KB / ?? (1.00 MB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1016.85 KB/s)
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/r/noarch            [<=>                 ] (00m:00s) Finalizing...
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1016.85 KB/s)
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/r/noarch            [<=>                 ] (00m:00s) Done
pkgs/r/noarch            [====================] (00m:00s) Done
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [=>             ] (00m:00s) 308 KB / ?? (1016.85 KB/s)
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) Finalizing...
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/noarch         [<=>                 ] (00m:00s) Done
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/main/noarch         [====================] (00m:00s) Done
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/r/linux-64          [=>                ] (00m:00s) 320 KB / ?? (1.03 MB/s)
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/r/linux-64          [<=>                 ] (00m:00s) Finalizing...
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/r/linux-64          [<=>                 ] (00m:00s) Done
pkgs/r/linux-64          [====================] (00m:00s) Done
pkgs/main/linux-64       [=>                ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/linux-64       [<=>               ] (00m:00s) 336 KB / ?? (1.08 MB/s)
pkgs/main/linux-64       [ <=>                ] (00m:00s) 1 MB / ?? (3.24 MB/s)
pkgs/main/linux-64       [  <=>               ] (00m:00s) 1 MB / ?? (3.24 MB/s)
pkgs/main/linux-64       [  <=>               ] (00m:00s) 2 MB / ?? (3.72 MB/s)
pkgs/main/linux-64       [   <=>              ] (00m:00s) 2 MB / ?? (3.72 MB/s)
pkgs/main/linux-64       [   <=>              ] (00m:00s) 3 MB / ?? (4.03 MB/s)
pkgs/main/linux-64       [    <=>             ] (00m:00s) 3 MB / ?? (4.03 MB/s)
pkgs/main/linux-64       [    <=>             ] (00m:00s) 4 MB / ?? (4.26 MB/s)
pkgs/main/linux-64       [    <=>             ] (00m:00s) Finalizing...
pkgs/main/linux-64       [    <=>             ] (00m:00s) Done
pkgs/main/linux-64       [====================] (00m:00s) Done

Pinned packages:
  - python 3.7.*


Transaction

  Prefix: /home/jupyterlab/conda/envs/python

  Updating specs:

   - bs4==4.10.0
   - ca-certificates
   - certifi
   - openssl


  Package               Version  Build           Channel                  Size
────────────────────────────────────────────────────────────────────────────────
  Install:
────────────────────────────────────────────────────────────────────────────────

  + beautifulsoup4       4.10.0  pyh06a4308_0    pkgs/main/noarch        85 KB
  + bs4                  4.10.0  hd3eb1b0_0      pkgs/main/noarch        10 KB
  + soupsieve             2.3.1  pyhd3eb1b0_0    pkgs/main/noarch        34 KB

  Change:
────────────────────────────────────────────────────────────────────────────────

  - certifi         2022.5.18.1  py37h89c1867_0  installed                    
  + certifi         2022.5.18.1  py37h06a4308_0  pkgs/main/linux-64     147 KB
  - openssl              1.1.1o  h166bdaf_0      installed                    
  + openssl              1.1.1o  h7f8727e_0      pkgs/main/linux-64       3 MB

  Summary:

  Install: 3 packages
  Change: 2 packages

  Total download: 3 MB

────────────────────────────────────────────────────────────────────────────────

Downloading  [>                                        ] (00m:00s)   38.94 KB/s
Extracting   [>                                                      ] (--:--) 
Finished bs4                                  (00m:00s)              10 KB     39 KB/s
Downloading  [>                                        ] (00m:00s)   38.94 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [>                                        ] (00m:00s)   38.94 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [>                                        ] (00m:00s)   38.94 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [>                                        ] (00m:00s)  170.64 KB/s
Extracting   [>                                                      ] (--:--) 
Finished soupsieve                            (00m:00s)              34 KB    132 KB/s
Downloading  [>                                        ] (00m:00s)  170.64 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [>                                        ] (00m:00s)  170.64 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=>                                       ] (00m:00s)  493.19 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=>                                       ] (00m:00s)  493.19 KB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [=>                                       ] (00m:00s)  493.19 KB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Finished beautifulsoup4                       (00m:00s)              85 KB    325 KB/s
Downloading  [=>                                       ] (00m:00s)  493.19 KB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [=>                                       ] (00m:00s)  493.19 KB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [===>                                     ] (00m:00s)    1.01 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Finished certifi                              (00m:00s)             147 KB    552 KB/s
Downloading  [===>                                     ] (00m:00s)    1.01 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [===>                                     ] (00m:00s)    1.01 MB/s
Extracting   [========>                                ] (00m:00s)        1 / 5
Downloading  [===>                                     ] (00m:00s)    1.01 MB/s
Extracting   [================>                        ] (00m:00s)        2 / 5
Downloading  [===>                                     ] (00m:00s)    1.01 MB/s
Extracting   [================>                        ] (00m:00s)        2 / 5
Downloading  [===>                                     ] (00m:00s)    1.01 MB/s
Extracting   [========================>                ] (00m:00s)        3 / 5
Downloading  [===>                                     ] (00m:00s)    1.01 MB/s
Extracting   [========================>                ] (00m:00s)        3 / 5
Downloading  [===>                                     ] (00m:00s)    1.01 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [==========>                              ] (00m:00s)    2.38 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [==========>                              ] (00m:00s)    2.38 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    8.61 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Finished openssl                              (00m:00s)               3 MB      8 MB/s
Downloading  [=========================================] (00m:00s)    8.61 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    8.61 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    8.61 MB/s
Extracting   [================================>        ] (00m:00s)        4 / 5
Downloading  [=========================================] (00m:00s)    8.61 MB/s
Extracting   [=========================================] (00m:00s)        5 / 5
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
Collecting lxml==4.6.4
  Downloading lxml-4.6.4-cp37-cp37m-manylinux_2_17_x86_64.manylinux2014_x86_64.manylinux_2_24_x86_64.whl (6.3 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 6.3/6.3 MB 52.8 MB/s eta 0:00:0000:0100:01
Installing collected packages: lxml
  Attempting uninstall: lxml
    Found existing installation: lxml 4.9.0
    Uninstalling lxml-4.9.0:
      Successfully uninstalled lxml-4.9.0
Successfully installed lxml-4.6.4

                  __    __    __    __
                 /  \  /  \  /  \  /  \
                /    \/    \/    \/    \
███████████████/  /██/  /██/  /██/  /████████████████████████
              /  / \   / \   / \   / \  \____
             /  /   \_/   \_/   \_/   \    o \__,
            / _/                       \_____/  `
            |/
        ███╗   ███╗ █████╗ ███╗   ███╗██████╗  █████╗
        ████╗ ████║██╔══██╗████╗ ████║██╔══██╗██╔══██╗
        ██╔████╔██║███████║██╔████╔██║██████╔╝███████║
        ██║╚██╔╝██║██╔══██║██║╚██╔╝██║██╔══██╗██╔══██║
        ██║ ╚═╝ ██║██║  ██║██║ ╚═╝ ██║██████╔╝██║  ██║
        ╚═╝     ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝╚═════╝ ╚═╝  ╚═╝

        mamba (0.15.3) supported by @QuantStack

        GitHub:  https://github.com/mamba-org/mamba
        Twitter: https://twitter.com/QuantStack

█████████████████████████████████████████████████████████████


Looking for: ['html5lib==1.1']

pkgs/main/linux-64       Using cache
pkgs/main/noarch         Using cache
pkgs/r/linux-64          Using cache
pkgs/r/noarch            Using cache

Pinned packages:
  - python 3.7.*


Transaction

  Prefix: /home/jupyterlab/conda/envs/python

  Updating specs:

   - html5lib==1.1
   - ca-certificates
   - certifi
   - openssl


  Package         Version  Build         Channel                 Size
───────────────────────────────────────────────────────────────────────
  Install:
───────────────────────────────────────────────────────────────────────

  + html5lib          1.1  pyhd3eb1b0_0  pkgs/main/noarch       91 KB
  + webencodings    0.5.1  py37_1        pkgs/main/linux-64     19 KB

  Summary:

  Install: 2 packages

  Total download: 110 KB

───────────────────────────────────────────────────────────────────────

Downloading  [======>                                  ] (00m:00s)   75.18 KB/s
Extracting   [>                                                      ] (--:--) 
Finished webencodings                         (00m:00s)              19 KB     75 KB/s
Downloading  [======>                                  ] (00m:00s)   75.18 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [======>                                  ] (00m:00s)   75.18 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [======>                                  ] (00m:00s)   75.18 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=========================================] (00m:00s)  431.05 KB/s
Extracting   [>                                                      ] (--:--) 
Finished html5lib                             (00m:00s)              91 KB    356 KB/s
Downloading  [=========================================] (00m:00s)  431.05 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=========================================] (00m:00s)  431.05 KB/s
Extracting   [>                                                      ] (--:--) 
Downloading  [=========================================] (00m:00s)  431.05 KB/s
Extracting   [====================>                    ] (00m:00s)        1 / 2
Downloading  [=========================================] (00m:00s)  431.05 KB/s
Extracting   [====================>                    ] (00m:00s)        1 / 2
Downloading  [=========================================] (00m:00s)  431.05 KB/s
Extracting   [=========================================] (00m:00s)        2 / 2
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
Import the required modules and functions

from bs4 import BeautifulSoup # this module helps in web scrapping.
import requests  # this module helps us to download a web page
Beautiful Soup Objects
Beautiful Soup is a Python library for pulling data out of HTML and XML files, we will focus on HTML files. This is accomplished by representing the HTML as a set of objects with methods used to parse the HTML. We can navigate the HTML as a tree and/or filter out what we are looking for.

Consider the following HTML:

%%html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>
<h3><b id='boldest'>Lebron James</b></h3>
<p> Salary: $ 92,000,000 </p>
<h3> Stephen Curry</h3>
<p> Salary: $85,000, 000 </p>
<h3> Kevin Durant </h3>
<p> Salary: $73,200, 000</p>
</body>
</html>
Page Title
Lebron James
Salary: $ 92,000,000

Stephen Curry
Salary: $85,000, 000

Kevin Durant
Salary: $73,200, 000

We can store it as a string in the variable HTML:

html="<!DOCTYPE html><html><head><title>Page Title</title></head><body><h3><b id='boldest'>Lebron James</b></h3><p> Salary: $ 92,000,000 </p><h3> Stephen Curry</h3><p> Salary: $85,000, 000 </p><h3> Kevin Durant </h3><p> Salary: $73,200, 000</p></body></html>"
To parse a document, pass it into the BeautifulSoup constructor, the BeautifulSoup object, which represents the document as a nested data structure:

s= BeautifulSoup(html, "html.parser")
First, the document is converted to Unicode, (similar to ASCII), and HTML entities are converted to Unicode characters. Beautiful Soup transforms a complex HTML document into a complex tree of Python objects. The BeautifulSoup object can create other types of objects. In this lab, we will cover BeautifulSoup and Tag objects that for the purposes of this lab are identical, and NavigableString objects.

We can use the method prettify() to display the HTML in the nested structure:

print(soup.prettify())
<!DOCTYPE html>
<html>
 <head>
  <title>
   Page Title
  </title>
 </head>
 <body>
  <h3>
   <b id="boldest">
    Lebron James
   </b>
  </h3>
  <p>
   Salary: $ 92,000,000
  </p>
  <h3>
   Stephen Curry
  </h3>
  <p>
   Salary: $85,000, 000
  </p>
  <h3>
   Kevin Durant
  </h3>
  <p>
   Salary: $73,200, 000
  </p>
 </body>
</html>
Tags
Let's say we want the title of the page and the name of the top paid player we can use the Tag. The Tag object corresponds to an HTML tag in the original document, for example, the tag title.

tag_object=soup.title
print("tag object:",tag_object)
tag object: <title>Page Title</title>
we can see the tag type bs4.element.Tag

print("tag object type:",type(tag_object))
tag object type: <class 'bs4.element.Tag'>
If there is more than one Tag with the same name, the first element with that Tag name is called, this corresponds to the most paid player:

tag_object=soup.h3
tag_object
<h3><b id="boldest">Lebron James</b></h3>
Enclosed in the bold attribute b, it helps to use the tree representation. We can navigate down the tree using the child attribute to get the name.

Children, Parents, and Siblings
As stated above the Tag object is a tree of objects we can access the child of the tag or navigate down the branch as follows:

tag_child =tag_object.b
tag_child
<b id="boldest">Lebron James</b>
You can access the parent with the  parent

parent_tag=tag_child.parent
parent_tag
<h3><b id="boldest">Lebron James</b></h3>
this is identical to

tag_object
<h3><b id="boldest">Lebron James</b></h3>
tag_object parent is the body element.

tag_object.parent
<body><h3><b id="boldest">Lebron James</b></h3><p> Salary: $ 92,000,000 </p><h3> Stephen Curry</h3><p> Salary: $85,000, 000 </p><h3> Kevin Durant </h3><p> Salary: $73,200, 000</p></body>
sibling_2=sibling_1.next_sibling
sibling_2
<h3> Stephen Curry</h3>
tag_object sibling is the paragraph element

sibling_1=tag_object.next_sibling
sibling_1
<p> Salary: $ 92,000,000 </p>
sibling_2 is the header element which is also a sibling of both sibling_1 and tag_object

sibling_2=sibling_1.next_sibling
sibling_2
<h3> Stephen Curry</h3>
Exercise: next_sibling
Using the object sibling_2 and the property next_sibling to find the salary of Stephen Curry:

Click here for the solution
HTML Attributes
If the tag has attributes, the tag id="boldest" has an attribute id whose value is boldest. You can access a tag’s attributes by treating the tag like a dictionary:

tag_child['id']
'boldest'
You can access that dictionary directly as attrs:

tag_child.attrs
{'id': 'boldest'}
You can also work with Multi-valued attribute check out [1] for more.

We can also obtain the content if the attribute of the tag using the Python get() method.

tag_child.get('id')
'boldest'
Navigable String
A string corresponds to a bit of text or content within a tag. Beautiful Soup uses the NavigableString class to contain this text. In our HTML we can obtain the name of the first player by extracting the sting of the Tag object tag_child as follows:

tag_string=tag_child.string
tag_string
'Lebron James'
we can verify the type is Navigable String

type(tag_string)
bs4.element.NavigableString
A NavigableString is just like a Python string or Unicode string, to be more precise. The main difference is that it also supports some BeautifulSoup features. We can covert it to sting object in Python:

unicode_string = str(tag_string)
unicode_string
'Lebron James'
Filter
Filters allow you to find complex patterns, the simplest filter is a string. In this section we will pass a string to a different filter method and Beautiful Soup will perform a match against that exact string. Consider the following HTML of rocket launchs:

%%html
<table>
  <tr>
    <td id='flight' >Flight No</td>
    <td>Launch site</td> 
    <td>Payload mass</td>
   </tr>
  <tr> 
    <td>1</td>
    <td><a href='https://en.wikipedia.org/wiki/Florida'>Florida</a></td>
    <td>300 kg</td>
  </tr>
  <tr>
    <td>2</td>
    <td><a href='https://en.wikipedia.org/wiki/Texas'>Texas</a></td>
    <td>94 kg</td>
  </tr>
  <tr>
    <td>3</td>
    <td><a href='https://en.wikipedia.org/wiki/Florida'>Florida<a> </td>
    <td>80 kg</td>
  </tr>
</table>
Flight No	Launch site	Payload mass
1	Florida	300 kg
2	Texas	94 kg
3	Florida	80 kg
We can store it as a string in the variable table:

table="<table><tr><td id='flight'>Flight No</td><td>Launch site</td> <td>Payload mass</td></tr><tr> <td>1</td><td><a href='https://en.wikipedia.org/wiki/Florida'>Florida<a></td><td>300 kg</td></tr><tr><td>2</td><td><a href='https://en.wikipedia.org/wiki/Texas'>Texas</a></td><td>94 kg</td></tr><tr><td>3</td><td><a href='https://en.wikipedia.org/wiki/Florida'>Florida<a> </td><td>80 kg</td></tr></table>"
table_bs = BeautifulSoup(table, "html.parser")
find All
The find_all() method looks through a tag’s descendants and retrieves all descendants that match your filters.

The Method signature for find_all(name, attrs, recursive, string, limit, **kwargs)

Name
When we set the name parameter to a tag name, the method will extract all the tags with that name and its children.

table_rows=table_bs.find_all('tr')
table_rows
[<tr><td id="flight">Flight No</td><td>Launch site</td> <td>Payload mass</td></tr>,
 <tr> <td>1</td><td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a></a></a></td><td>300 kg</td></tr>,
 <tr><td>2</td><td><a href="https://en.wikipedia.org/wiki/Texas">Texas</a></td><td>94 kg</td></tr>,
 <tr><td>3</td><td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a> </a></a></td><td>80 kg</td></tr>]
The result is a Python Iterable just like a list, each element is a tag object:

first_row =table_rows[0]
first_row
<tr><td id="flight">Flight No</td><td>Launch site</td> <td>Payload mass</td></tr>
The type is tag

print(type(first_row))
<class 'bs4.element.Tag'>
we can obtain the child

first_row.td
<td id="flight">Flight No</td>
If we iterate through the list, each element corresponds to a row in the table:

for i,row in enumerate(table_rows):
    print("row",i,"is",row)
    
row 0 is <tr><td id="flight">Flight No</td><td>Launch site</td> <td>Payload mass</td></tr>
row 1 is <tr> <td>1</td><td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a></a></a></td><td>300 kg</td></tr>
row 2 is <tr><td>2</td><td><a href="https://en.wikipedia.org/wiki/Texas">Texas</a></td><td>94 kg</td></tr>
row 3 is <tr><td>3</td><td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a> </a></a></td><td>80 kg</td></tr>
As row is a cell object, we can apply the method find_all to it and extract table cells in the object cells using the tag td, this is all the children with the name td. The result is a list, each element corresponds to a cell and is a Tag object, we can iterate through this list as well. We can extract the content using the string attribute.

for i,row in enumerate(table_rows):
    print("row",i)
    cells=row.find_all('td')
    for j,cell in enumerate(cells):
        print('colunm',j,"cell",cell)
row 0
colunm 0 cell <td id="flight">Flight No</td>
colunm 1 cell <td>Launch site</td>
colunm 2 cell <td>Payload mass</td>
row 1
colunm 0 cell <td>1</td>
colunm 1 cell <td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a></a></a></td>
colunm 2 cell <td>300 kg</td>
row 2
colunm 0 cell <td>2</td>
colunm 1 cell <td><a href="https://en.wikipedia.org/wiki/Texas">Texas</a></td>
colunm 2 cell <td>94 kg</td>
row 3
colunm 0 cell <td>3</td>
colunm 1 cell <td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a> </a></a></td>
colunm 2 cell <td>80 kg</td>
If we use a list we can match against any item in that list.

list_input=table_bs .find_all(name=["tr", "td"])
list_input
[<tr><td id="flight">Flight No</td><td>Launch site</td> <td>Payload mass</td></tr>,
 <td id="flight">Flight No</td>,
 <td>Launch site</td>,
 <td>Payload mass</td>,
 <tr> <td>1</td><td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a></a></a></td><td>300 kg</td></tr>,
 <td>1</td>,
 <td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a></a></a></td>,
 <td>300 kg</td>,
 <tr><td>2</td><td><a href="https://en.wikipedia.org/wiki/Texas">Texas</a></td><td>94 kg</td></tr>,
 <td>2</td>,
 <td><a href="https://en.wikipedia.org/wiki/Texas">Texas</a></td>,
 <td>94 kg</td>,
 <tr><td>3</td><td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a> </a></a></td><td>80 kg</td></tr>,
 <td>3</td>,
 <td><a href="https://en.wikipedia.org/wiki/Florida">Florida<a> </a></a></td>,
 <td>80 kg</td>]
Attributes
If the argument is not recognized it will be turned into a filter on the tag’s attributes. For example the id argument, Beautiful Soup will filter against each tag’s id attribute. For example, the first td elements have a value of id of flight, therefore we can filter based on that id value.

table_bs.find_all(id="flight")
[<td id="flight">Flight No</td>]
We can find all the elements that have links to the Florida Wikipedia page:

list_input=table_bs.find_all(href="https://en.wikipedia.org/wiki/Florida")
list_input
[<a href="https://en.wikipedia.org/wiki/Florida">Florida<a></a></a>,
 <a href="https://en.wikipedia.org/wiki/Florida">Florida<a> </a></a>]
If we set the href attribute to True, regardless of what the value is, the code finds all tags with href value:

table_bs.find_all(href=True)
[<a href="https://en.wikipedia.org/wiki/Florida">Florida<a></a></a>,
 <a href="https://en.wikipedia.org/wiki/Texas">Texas</a>,
 <a href="https://en.wikipedia.org/wiki/Florida">Florida<a> </a></a>]
There are other methods for dealing with attributes and other related methods; Check out the following link

Exercise: find_all
Using the logic above, find all the elements without href value

table_bs.find_all(href=False)
[<a href="https://en.wikipedia.org/wiki/Florida">Florida<a></a></a>,
 <a href="https://en.wikipedia.org/wiki/Texas">Texas</a>,
 <a href="https://en.wikipedia.org/wiki/Florida">Florida<a> </a></a>]
Click here for the solution
Using the soup object soup, find the element with the id attribute content set to "boldest".

soup.find_all(id="boldest")
[<b id="boldest">Lebron James</b>]
Click here for the solution
string
With string you can search for strings instead of tags, where we find all the elments with Florida:

table_bs.find_all(string="Florida")
['Florida', 'Florida']
find
The find_all() method scans the entire document looking for results, it’s if you are looking for one element you can use the find() method to find the first element in the document. Consider the following two table:

%%html
<h3>Rocket Launch </h3>
​
<p>
<table class='rocket'>
  <tr>
    <td>Flight No</td>
    <td>Launch site</td> 
    <td>Payload mass</td>
  </tr>
  <tr>
    <td>1</td>
    <td>Florida</td>
    <td>300 kg</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Texas</td>
    <td>94 kg</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Florida </td>
    <td>80 kg</td>
  </tr>
</table>
</p>
<p>
​
<h3>Pizza Party  </h3>
  
    
<table class='pizza'>
  <tr>
    <td>Pizza Place</td>
    <td>Orders</td> 
    <td>Slices </td>
   </tr>
  <tr>
    <td>Domino's Pizza</td>
    <td>10</td>
    <td>100</td>
  </tr>
  <tr>
    <td>Little Caesars</td>
    <td>12</td>
    <td >144 </td>
  </tr>
  <tr>
    <td>Papa John's </td>
    <td>15 </td>
    <td>165</td>
  </tr>
​
Rocket Launch
Flight No	Launch site	Payload mass
1	Florida	300 kg
2	Texas	94 kg
3	Florida	80 kg
Pizza Party
Pizza Place	Orders	Slices
Domino's Pizza	10	100
Little Caesars	12	144
Papa John's	15	165
We store the HTML as a Python string and assign two_tables:

two_tables="<h3>Rocket Launch </h3><p><table class='rocket'><tr><td>Flight No</td><td>Launch site</td> <td>Payload mass</td></tr><tr><td>1</td><td>Florida</td><td>300 kg</td></tr><tr><td>2</td><td>Texas</td><td>94 kg</td></tr><tr><td>3</td><td>Florida </td><td>80 kg</td></tr></table></p><p><h3>Pizza Party  </h3><table class='pizza'><tr><td>Pizza Place</td><td>Orders</td> <td>Slices </td></tr><tr><td>Domino's Pizza</td><td>10</td><td>100</td></tr><tr><td>Little Caesars</td><td>12</td><td >144 </td></tr><tr><td>Papa John's </td><td>15 </td><td>165</td></tr>"
We create a BeautifulSoup object two_tables_bs

two_tables_bs= BeautifulSoup(two_tables, 'html.parser')
We can find the first table using the tag name table

two_tables_bs.find("table")
<table class="rocket"><tr><td>Flight No</td><td>Launch site</td> <td>Payload mass</td></tr><tr><td>1</td><td>Florida</td><td>300 kg</td></tr><tr><td>2</td><td>Texas</td><td>94 kg</td></tr><tr><td>3</td><td>Florida </td><td>80 kg</td></tr></table>
We can filter on the class attribute to find the second table, but because class is a keyword in Python, we add an underscore.

two_tables_bs.find("table",class_='pizza')
<table class="pizza"><tr><td>Pizza Place</td><td>Orders</td> <td>Slices </td></tr><tr><td>Domino's Pizza</td><td>10</td><td>100</td></tr><tr><td>Little Caesars</td><td>12</td><td>144 </td></tr><tr><td>Papa John's </td><td>15 </td><td>165</td></tr></table>
Downloading And Scraping The Contents Of A Web Page
We Download the contents of the web page:

url = "http://www.ibm.com"
We use get to download the contents of the webpage in text format and store in a variable called data:

data  = requests.get(url).text 
We create a BeautifulSoup object using the BeautifulSoup constructor

soup = BeautifulSoup(data,"html.parser")  # create a soup object using the variable 'data'
Scrape all links

for link in soup.find_all('a',href=True):  # in html anchor/link is represented by the tag <a>
​
    print(link.get('href'))
​
#main-content
http://www.ibm.com
https://www.ibm.com/analytics/data-fabric/?lnk=ushpv18l1
#ibm-hp--tech-section
https://www.ibm.com/consulting/?lnk=ushpv18intro2
https://research.ibm.com/blog/accelerated-discovery-film?lnk=ushpv18r1
https://research.ibm.com/blog/accelerated-discovery-film?lnk=ushpv18r1
https://research.ibm.com/publications/an-integrated-photonics-engine-for-unsupervised-correlation-detection?lnk=ushpv18r2#publication-notes
https://research.ibm.com/blog/qiskit-runtime-for-useful-quantum-computing?lnk=ushpv18r3
https://research.ibm.com/blog/earth-day-2022?lnk=ushpv18r4
https://www.ibm.com/thought-leadership/new-creators/stephanie-carruthers/?lnk=ushpv18f1
https://www.ibm.com/blogs/internet-of-things/intelligent-asset-management-strategy-benefits/?lnk=ushpv18f2
https://www.ibm.com/thought-leadership/institute-business-value/report/mastering-hybrid-cloud?lnk=ushpv18f3
https://www.ibm.com/garage?lnk=ushpv18f4
https://www.ibm.com/case-studies/search?lnk=ushpv18mAll
https://www.ibm.com/case-studies/micro-strategies-inc/?lnk=ushpv18m1
https://www.ibm.com/case-studies/pandora-jewellery/?lnk=ushpv18m2
https://www.ibm.com/case-studies/samsung-electronics/?lnk=ushpv18m3
https://www.ibm.com/products?types[0]=trial&lnk=STW_US_MPDISC_BNR_BTN&lnk2=THP&lnk3=ushpv18tAll
https://www.ibm.com/products/offers-and-discounts?link=ushpv18t5&lnk2=trial_mktpl_MPDISC
https://www.ibm.com/products/cloud-pak-for-data/scale-trustworthy-ai?lnk=ushpv18t1&lnk2=trial_Verify&psrc=none&pexp=def
https://www.ibm.com/verify/verify-identity?lnk=ushpv18t2&lnk2=trial_Verify&psrc=none&pexp=def
https://www.ibm.com/products/cognos-analytics?lnk=ushpv18t3&lnk2=trial_CogAnalytics&psrc=none&pexp=def
https://www.ibm.com/search?lnk=ushpv18srch&locale=en-us&q=
https://www.ibm.com/products?lnk=ushpv18p1&lnk2=trial_mktpl&psrc=none&pexp=def
https://www.ibm.com/cloud/hybrid?lnk=ushpv18pt14
https://www.ibm.com/watson?lnk=ushpv18pt17
https://www.ibm.com/it-infrastructure?lnk=ushpv18pt19
https://www.ibm.com/blockchain?lnk=ushpv18pt4
https://www.ibm.com/security/products?lnk=ushpv18pt9
https://www.ibm.com/analytics/products?lnk=ushpv18pt1
https://www.ibm.com/cloud/automation?lnk=ushpv18ct21
https://www.ibm.com/quantum-computing?lnk=ushpv18pt16
https://www.ibm.com/mysupport/s/?language=en_US&lnk=ushpv18ct11
https://www.ibm.com/training/?lnk=ushpv18ct15
https://community.ibm.com/community/user/home/?lnk=ushpv18ct20
https://developer.ibm.com/?lnk=ushpv18ct9
https://www.ibm.com/garage?lnk=ushpv18pt18
https://www.ibm.com/docs/en?lnk=ushpv18ct14
https://www.redbooks.ibm.com/?lnk=ushpv18ct10
https://www.ibm.com/subscribe/?lnk=ushpv18ct22
https://www-03.ibm.com/employment/technicaltalent/developer/?lnk=ushpv18ct2
https://www.ibm.com/
Scrape all images Tags
for link in soup.find_all('img'):# in html image is represented by the tag <img>
    print(link)
    print(link.get('src'))
<img alt="" aria-hidden="true" role="presentation" src="data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTA1NSIgaGVpZ2h0PSI1MjcuNSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2ZXJzaW9uPSIxLjEiLz4=" style="max-width:100%;display:block;margin:0;border:none;padding:0"/>
data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTA1NSIgaGVpZ2h0PSI1MjcuNSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2ZXJzaW9uPSIxLjEiLz4=
<img alt="leadspace mobile image" class="ibm-resize" decoding="async" src="https://1.dam.s81c.com/p/077d6f8237251350/2022031-ls-data-driven-mobile-720x360.png" style="position:absolute;top:0;left:0;bottom:0;right:0;box-sizing:border-box;padding:0;border:none;margin:auto;display:block;width:0;height:0;min-width:100%;max-width:100%;min-height:100%;max-height:100%"/>
https://1.dam.s81c.com/p/077d6f8237251350/2022031-ls-data-driven-mobile-720x360.png
<img alt=" " class="bx--image__img" src="https://1.dam.s81c.com/p/08243aa1b03b6088/20220606-r1-accelerated-discovery-26724-1600x900.jpg"/>
https://1.dam.s81c.com/p/08243aa1b03b6088/20220606-r1-accelerated-discovery-26724-1600x900.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/p/08333674a8263003/20220613-r-light-computing-1600x900.png"/>
https://1.dam.s81c.com/p/08333674a8263003/20220613-r-light-computing-1600x900.png
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/p/07bbb0107dc3d30b/20220412-research-26578-Qiskit-PAYGO-800x450.jpg"/>
https://1.dam.s81c.com/p/07bbb0107dc3d30b/20220412-research-26578-Qiskit-PAYGO-800x450.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/p/07d5a7f25cc3d90f/20220502-r-earth-day-26621-800x450.jpg"/>
https://1.dam.s81c.com/p/07d5a7f25cc3d90f/20220502-r-earth-day-26621-800x450.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/p/08333674a8263000/20220613-f-new-creators-stephanie-carruthers-26732-444x320.jpg"/>
https://1.dam.s81c.com/p/08333674a8263000/20220613-f-new-creators-stephanie-carruthers-26732-444x320.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/p/08333674a8263010/20220613-26720-intelligent-asset-management-444x333.jpg"/>
https://1.dam.s81c.com/p/08333674a8263010/20220613-26720-intelligent-asset-management-444x333.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/p/08333674a8a63012/20220613-26530-mastering-hybrid-cloud-ibv-report-444x333.jpg"/>
https://1.dam.s81c.com/p/08333674a8a63012/20220613-26530-mastering-hybrid-cloud-ibv-report-444x333.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/public/content/dam/worldwide-content/homepage/ul/g/c9/39/20220110-f-garage-tour-and-consulting-26338.png"/>
https://1.dam.s81c.com/public/content/dam/worldwide-content/homepage/ul/g/c9/39/20220110-f-garage-tour-and-consulting-26338.png
<img alt=" " class="bx--image__img" src="https://1.dam.s81c.com/p/07d5a7f256c3d284/20220425-Micro-Strategies-Secure-Lever-26597-1600x900.jpg"/>
https://1.dam.s81c.com/p/07d5a7f256c3d284/20220425-Micro-Strategies-Secure-Lever-26597-1600x900.jpg
<img alt=" " class="bx--image__img" src="https://1.dam.s81c.com/p/0824479375c53465/20220606-m-pandora-jewelry-26707-1600x900.jpg"/>
https://1.dam.s81c.com/p/0824479375c53465/20220606-m-pandora-jewelry-26707-1600x900.jpg
<img alt=" " class="bx--image__img" src="https://1.dam.s81c.com/p/08244793754533a5/20220530-m-samsung-electronics-26697-1600x900.jpg"/>
https://1.dam.s81c.com/p/08244793754533a5/20220530-m-samsung-electronics-26697-1600x900.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/p/075b9d6845a4394a/Watson-Studio-trial-800x450.jpg"/>
https://1.dam.s81c.com/p/075b9d6845a4394a/Watson-Studio-trial-800x450.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/public/content/dam/worldwide-content/homepage/ul/g/ac/2e/Security-Verify-Trial-800x450.jpg"/>
https://1.dam.s81c.com/public/content/dam/worldwide-content/homepage/ul/g/ac/2e/Security-Verify-Trial-800x450.jpg
<img alt=" " class="bx--image__img bx--card__img" src="https://1.dam.s81c.com/p/0795cae91aa515c7/20220404-t-ibm-cognos-analytics-with-watson.png"/>
https://1.dam.s81c.com/p/0795cae91aa515c7/20220404-t-ibm-cognos-analytics-with-watson.png
Scrape data from HTML tables
#The below url contains an html table with data about colors and color codes.
url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/labs/datasets/HTMLColorCodes.html"
Before proceeding to scrape a web site, you need to examine the contents, and the way data is organized on the website. Open the above url in your browser and check how many rows and columns are there in the color table.

# get the contents of the webpage in text format and store in a variable called data
data  = requests.get(url).text
soup = BeautifulSoup(data,"html.parser")
#find a html table in the web page
table = soup.find('table') # in html table is represented by the tag <table>
#Get all rows from the table
for row in table.find_all('tr'): # in html table row is represented by the tag <tr>
    # Get all columns in each row.
    cols = row.find_all('td') # in html a column is represented by the tag <td>
    color_name = cols[2].string # store the value in column 3 as color_name
    color_code = cols[3].string # store the value in column 4 as color_code
    print("{}--->{}".format(color_name,color_code))
Color Name--->None
lightsalmon--->#FFA07A
salmon--->#FA8072
darksalmon--->#E9967A
lightcoral--->#F08080
coral--->#FF7F50
tomato--->#FF6347
orangered--->#FF4500
gold--->#FFD700
orange--->#FFA500
darkorange--->#FF8C00
lightyellow--->#FFFFE0
lemonchiffon--->#FFFACD
papayawhip--->#FFEFD5
moccasin--->#FFE4B5
peachpuff--->#FFDAB9
palegoldenrod--->#EEE8AA
khaki--->#F0E68C
darkkhaki--->#BDB76B
yellow--->#FFFF00
lawngreen--->#7CFC00
chartreuse--->#7FFF00
limegreen--->#32CD32
lime--->#00FF00
forestgreen--->#228B22
green--->#008000
powderblue--->#B0E0E6
lightblue--->#ADD8E6
lightskyblue--->#87CEFA
skyblue--->#87CEEB
deepskyblue--->#00BFFF
lightsteelblue--->#B0C4DE
dodgerblue--->#1E90FF
Scrape data from HTML tables into a DataFrame using BeautifulSoup and Pandas
import pandas as pd
#The below url contains html tables with data about world population.
url = "https://en.wikipedia.org/wiki/World_population"
Before proceeding to scrape a web site, you need to examine the contents, and the way data is organized on the website. Open the above url in your browser and check the tables on the webpage.

# get the contents of the webpage in text format and store in a variable called data
data  = requests.get(url).text
soup = BeautifulSoup(data,"html.parser")
#find all html tables in the web page
tables = soup.find_all('table') # in html table is represented by the tag <table>
# we can see how many tables were found by checking the length of the tables list
len(tables)
26
Assume that we are looking for the 10 most densly populated countries table, we can look through the tables list and find the right one we are look for based on the data in each table or we can search for the table name if it is in the table but this option might not always work.

for index,table in enumerate(tables):
    if ("10 most densely populated countries" in str(table)):
        table_index = index
print(table_index)
5
See if you can locate the table name of the table, 10 most densly populated countries, below.

print(tables[table_index].prettify())
<table class="wikitable sortable" style="text-align:right">
 <caption>
  10 most densely populated countries
  <small>
   (with population above 5 million)
  </small>
 </caption>
 <tbody>
  <tr>
   <th>
    Rank
   </th>
   <th>
    Country
   </th>
   <th>
    Population
   </th>
   <th>
    Area
    <br/>
    <small>
     (km
     <sup>
      2
     </sup>
     )
    </small>
   </th>
   <th>
    Density
    <br/>
    <small>
     (pop/km
     <sup>
      2
     </sup>
     )
    </small>
   </th>
  </tr>
  <tr>
   <td>
    1
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="600" data-file-width="900" decoding="async" height="15" src="//upload.wikimedia.org/wikipedia/commons/thumb/4/48/Flag_of_Singapore.svg/23px-Flag_of_Singapore.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/4/48/Flag_of_Singapore.svg/35px-Flag_of_Singapore.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/4/48/Flag_of_Singapore.svg/45px-Flag_of_Singapore.svg.png 2x" width="23"/>
    </span>
    <a href="/wiki/Singapore" title="Singapore">
     Singapore
    </a>
   </td>
   <td>
    5,704,000
   </td>
   <td>
    710
   </td>
   <td>
    8,033
   </td>
  </tr>
  <tr>
   <td>
    2
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="600" data-file-width="1000" decoding="async" height="14" src="//upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Flag_of_Bangladesh.svg/23px-Flag_of_Bangladesh.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Flag_of_Bangladesh.svg/35px-Flag_of_Bangladesh.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Flag_of_Bangladesh.svg/46px-Flag_of_Bangladesh.svg.png 2x" width="23"/>
    </span>
    <a href="/wiki/Bangladesh" title="Bangladesh">
     Bangladesh
    </a>
   </td>
   <td>
    171,670,000
   </td>
   <td>
    143,998
   </td>
   <td>
    1,192
   </td>
  </tr>
  <tr>
   <td>
    3
   </td>
   <td align="left">
    <p>
     <span class="flagicon">
      <img alt="" class="thumbborder" data-file-height="600" data-file-width="1200" decoding="async" height="12" src="//upload.wikimedia.org/wikipedia/commons/thumb/0/00/Flag_of_Palestine.svg/23px-Flag_of_Palestine.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/0/00/Flag_of_Palestine.svg/35px-Flag_of_Palestine.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/0/00/Flag_of_Palestine.svg/46px-Flag_of_Palestine.svg.png 2x" width="23"/>
     </span>
     <a href="/wiki/State_of_Palestine" title="State of Palestine">
      Palestine
     </a>
    </p>
   </td>
   <td>
    5,266,785
   </td>
   <td>
    6,020
   </td>
   <td>
    847
   </td>
  </tr>
  <tr>
   <td>
    4
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="600" data-file-width="900" decoding="async" height="15" src="//upload.wikimedia.org/wikipedia/commons/thumb/5/59/Flag_of_Lebanon.svg/23px-Flag_of_Lebanon.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/5/59/Flag_of_Lebanon.svg/35px-Flag_of_Lebanon.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/5/59/Flag_of_Lebanon.svg/45px-Flag_of_Lebanon.svg.png 2x" width="23"/>
    </span>
    <a href="/wiki/Lebanon" title="Lebanon">
     Lebanon
    </a>
   </td>
   <td>
    6,856,000
   </td>
   <td>
    10,452
   </td>
   <td>
    656
   </td>
  </tr>
  <tr>
   <td>
    5
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="600" data-file-width="900" decoding="async" height="15" src="//upload.wikimedia.org/wikipedia/commons/thumb/7/72/Flag_of_the_Republic_of_China.svg/23px-Flag_of_the_Republic_of_China.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/7/72/Flag_of_the_Republic_of_China.svg/35px-Flag_of_the_Republic_of_China.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/7/72/Flag_of_the_Republic_of_China.svg/45px-Flag_of_the_Republic_of_China.svg.png 2x" width="23"/>
    </span>
    <a href="/wiki/Taiwan" title="Taiwan">
     Taiwan
    </a>
   </td>
   <td>
    23,604,000
   </td>
   <td>
    36,193
   </td>
   <td>
    652
   </td>
  </tr>
  <tr>
   <td>
    6
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="600" data-file-width="900" decoding="async" height="15" src="//upload.wikimedia.org/wikipedia/commons/thumb/0/09/Flag_of_South_Korea.svg/23px-Flag_of_South_Korea.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/0/09/Flag_of_South_Korea.svg/35px-Flag_of_South_Korea.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/0/09/Flag_of_South_Korea.svg/45px-Flag_of_South_Korea.svg.png 2x" width="23"/>
    </span>
    <a href="/wiki/South_Korea" title="South Korea">
     South Korea
    </a>
   </td>
   <td>
    51,781,000
   </td>
   <td>
    99,538
   </td>
   <td>
    520
   </td>
  </tr>
  <tr>
   <td>
    7
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="720" data-file-width="1080" decoding="async" height="15" src="//upload.wikimedia.org/wikipedia/commons/thumb/1/17/Flag_of_Rwanda.svg/23px-Flag_of_Rwanda.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/1/17/Flag_of_Rwanda.svg/35px-Flag_of_Rwanda.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/1/17/Flag_of_Rwanda.svg/45px-Flag_of_Rwanda.svg.png 2x" width="23"/>
    </span>
    <a href="/wiki/Rwanda" title="Rwanda">
     Rwanda
    </a>
   </td>
   <td>
    12,374,000
   </td>
   <td>
    26,338
   </td>
   <td>
    470
   </td>
  </tr>
  <tr>
   <td>
    8
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="600" data-file-width="1000" decoding="async" height="14" src="//upload.wikimedia.org/wikipedia/commons/thumb/5/56/Flag_of_Haiti.svg/23px-Flag_of_Haiti.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/5/56/Flag_of_Haiti.svg/35px-Flag_of_Haiti.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/5/56/Flag_of_Haiti.svg/46px-Flag_of_Haiti.svg.png 2x" width="23"/>
    </span>
    <a href="/wiki/Haiti" title="Haiti">
     Haiti
    </a>
   </td>
   <td>
    11,578,000
   </td>
   <td>
    27,065
   </td>
   <td>
    428
   </td>
  </tr>
  <tr>
   <td>
    9
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="600" data-file-width="900" decoding="async" height="15" src="//upload.wikimedia.org/wikipedia/commons/thumb/2/20/Flag_of_the_Netherlands.svg/23px-Flag_of_the_Netherlands.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/2/20/Flag_of_the_Netherlands.svg/35px-Flag_of_the_Netherlands.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/2/20/Flag_of_the_Netherlands.svg/45px-Flag_of_the_Netherlands.svg.png 2x" width="23"/>
    </span>
    <a href="/wiki/Netherlands" title="Netherlands">
     Netherlands
    </a>
   </td>
   <td>
    17,660,000
   </td>
   <td>
    41,526
   </td>
   <td>
    425
   </td>
  </tr>
  <tr>
   <td>
    10
   </td>
   <td align="left">
    <span class="flagicon">
     <img alt="" class="thumbborder" data-file-height="800" data-file-width="1100" decoding="async" height="15" src="//upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Flag_of_Israel.svg/21px-Flag_of_Israel.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Flag_of_Israel.svg/32px-Flag_of_Israel.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Flag_of_Israel.svg/41px-Flag_of_Israel.svg.png 2x" width="21"/>
    </span>
    <a href="/wiki/Israel" title="Israel">
     Israel
    </a>
   </td>
   <td>
    9,430,000
   </td>
   <td>
    22,072
   </td>
   <td>
    427
   </td>
  </tr>
 </tbody>
</table>

population_data = pd.DataFrame(columns=["Rank", "Country", "Population", "Area", "Density"])
​
for row in tables[table_index].tbody.find_all("tr"):
    col = row.find_all("td")
    if (col != []):
        rank = col[0].text
        country = col[1].text
        population = col[2].text.strip()
        area = col[3].text.strip()
        density = col[4].text.strip()
        population_data = population_data.append({"Rank":rank, "Country":country, "Population":population, "Area":area, "Density":density}, ignore_index=True)
​
population_data
Rank	Country	Population	Area	Density
0	1	Singapore	5,704,000	710	8,033
1	2	Bangladesh	171,670,000	143,998	1,192
2	3	\n Palestine\n\n	5,266,785	6,020	847
3	4	Lebanon	6,856,000	10,452	656
4	5	Taiwan	23,604,000	36,193	652
5	6	South Korea	51,781,000	99,538	520
6	7	Rwanda	12,374,000	26,338	470
7	8	Haiti	11,578,000	27,065	428
8	9	Netherlands	17,660,000	41,526	425
9	10	Israel	9,430,000	22,072	427
Scrape data from HTML tables into a DataFrame using BeautifulSoup and read_html
Using the same url, data, soup, and tables object as in the last section we can use the read_html function to create a DataFrame.

Remember the table we need is located in tables[table_index]

We can now use the pandas function read_html and give it the string version of the table as well as the flavor which is the parsing engine bs4.

pd.read_html(str(tables[5]), flavor='bs4')
[   Rank      Country  Population  Area(km2)  Density(pop/km2)
 0     1    Singapore     5704000        710              8033
 1     2   Bangladesh   171670000     143998              1192
 2     3    Palestine     5266785       6020               847
 3     4      Lebanon     6856000      10452               656
 4     5       Taiwan    23604000      36193               652
 5     6  South Korea    51781000      99538               520
 6     7       Rwanda    12374000      26338               470
 7     8        Haiti    11578000      27065               428
 8     9  Netherlands    17660000      41526               425
 9    10       Israel     9430000      22072               427]
The function read_html always returns a list of DataFrames so we must pick the one we want out of the list.

population_data_read_html = pd.read_html(str(tables[5]), flavor='bs4')[0]
​
population_data_read_html
Rank	Country	Population	Area(km2)	Density(pop/km2)
0	1	Singapore	5704000	710	8033
1	2	Bangladesh	171670000	143998	1192
2	3	Palestine	5266785	6020	847
3	4	Lebanon	6856000	10452	656
4	5	Taiwan	23604000	36193	652
5	6	South Korea	51781000	99538	520
6	7	Rwanda	12374000	26338	470
7	8	Haiti	11578000	27065	428
8	9	Netherlands	17660000	41526	425
9	10	Israel	9430000	22072	427
Scrape data from HTML tables into a DataFrame using read_html
We can also use the read_html function to directly get DataFrames from a url.

dataframe_list = pd.read_html(url, flavor='bs4')
We can see there are 25 DataFrames just like when we used find_all on the soup object.

len(dataframe_list)
26
Finally we can pick the DataFrame we need out of the list.

dataframe_list[5]
Rank	Country	Population	Area(km2)	Density(pop/km2)
0	1	Singapore	5704000	710	8033
1	2	Bangladesh	171670000	143998	1192
2	3	Palestine	5266785	6020	847
3	4	Lebanon	6856000	10452	656
4	5	Taiwan	23604000	36193	652
5	6	South Korea	51781000	99538	520
6	7	Rwanda	12374000	26338	470
7	8	Haiti	11578000	27065	428
8	9	Netherlands	17660000	41526	425
9	10	Israel	9430000	22072	427
We can also use the match parameter to select the specific table we want. If the table contains a string matching the text it will be read.

pd.read_html(url, match="10 most densely populated countries", flavor='bs4')[0]
Rank	Country	Population	Area(km2)	Density(pop/km2)
0	1	Singapore	5704000	710	8033
1	2	Bangladesh	171670000	143998	1192
2	3	Palestine	5266785	6020	847
3	4	Lebanon	6856000	10452	656
4	5	Taiwan	23604000	36193	652
5	6	South Korea	51781000	99538	520
6	7	Rwanda	12374000	26338	470
7	8	Haiti	11578000	27065	428
8	9	Netherlands	17660000	41526	425
9	10	Israel	9430000	22072	427
Authors
Ramesh Sannareddy

Other Contributors
Rav Ahuja

Change Log
Date (YYYY-MM-DD)	Version	Changed By	Change Description
2021-08-04	0.2	Made changes to markdown of nextsibling	
2020-10-17	0.1	Joseph Santarcangelo Created initial version of the lab	






Copyright © 2020 IBM Corporation. This notebook and its source code are released under the terms of the MIT License.
