# crypto_arbitrage

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about">About</a>
      <ul>
        <li><a href="#project-build">Project Build</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prework">Prework</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#use">Use</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributors">Contributors</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

<!-- ABOUT -->
## About

This project is an app that sorts through historical price action in three phases of data analysis for Bitcoin on the Bitstamp and Coinbase exchanges.

<!-- PROJECT BUILD -->
### Project Build

<!-- This section should list any major frameworks that you built your project using. Leave any add-ons/plugins for the acknowledgements section. Here are a few examples. -->

* [Python](https://www.python.org/)
* [Python CSV Reading/Writing](https://docs.python.org/3/library/csv.html)
* [Python pandas](https://pandas.pydata.org/)
* [Python matplotlib](https://matplotlib.org/)
* [Python conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html)
* [Python JupyterLab](https://jupyter.org/)

<!-- GETTING STARTED -->
## Getting Started

<!-- This is an example of how you may give instructions on setting up your project locally. To get a local copy up and running follow these simple example steps. -->
* Install Anaconda and JupyterLab on your computer. Follow the instructions for Anaconda, then install JupyterLab.

<!-- PREWORK -->
### Prework

<!-- This is an example of how to list things you need to use the software and how to install them. -->
A text editor such as [VS Code](https://code.visualstudio.com/) or [Sublime Text](https://www.sublimetext.com/)

<!-- INSTALLATION -->
### Installation

1. Clone the repo.

2. You don't need to install pip - Conda comes with pip and you can also use the command.
    conda install 'package name'
   
3. Install Conda according to the operating system.
    After install view (base) on terminal
   
4. Activate Conda Dev environment.
   ```sh
   conda activate dev
   ```
   You should now see (dev) on your terminal.

5. Install JupyterLabs
   ```sh
   pip install jupyterlab

6. Run JupyterLab
   ```sh
   jupyter lab
   ```
   A browser window should open on localhost:8889/lab

<!-- USAGE -->
## Usage

<!-- Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources. -->
Applied financial analysis in three stages to determine the arbitrage of Bitcoin.

<!-- ROADMAP -->
## Roadmap

Screenshots and code of working application

#### Exchange Comparison January 2018
![Exchange January Screen Shot][exchange-january-screenshot]

#### Exchange Comparison March 2018 - With Analysis
![Exchange March Screen Shot][exchange-march-screenshot]


#### Calculate Arbitrage Profits Sample - for January 16
  *This code has been summarized into one block for convenience*
  *and there's an analysis at the end*
```sh
  # For the date early in the dataset, measure the arbitrage spread between the two exchanges
  # by subtracting the lower-priced exchange from the higher-priced one
  arbitrage_spread_early=coinbase['Close'].loc['2018-01-16']-bitstamp['Close'].loc['2018-01-16']
  arbitrage_spread_early = arbitrage_spread_early[arbitrage_spread_early>0]
  # Use a conditional statement to generate the summary statistics for each arbitrage_spread DataFrame
  arbitrage_spread_early.describe()

  # For the date early in the dataset, calculate the spread returns by dividing the instances when the
  # arbitrage spread is positive (> 0) 
  # by the price of Bitcoin from the exchange you are buying on (the lower-priced exchange).
  spread_return_early=arbitrage_spread_early/bitstamp['Close'].loc['2018-01-16']
  # Review the spread return DataFrame
  spread_return_early.head()

  # For the date early in the dataset, determine the number of times your trades with positive returns 
  # exceed the 1% minimum threshold (.01) that you need to cover your costs
  profitable_trades_early=spread_return_early[spread_return_early>.01]
  # Review the first five profitable trades
  profitable_trades_early.head()

  # For the date early in the dataset, generate the summary statistics for the profitable trades
  # or you trades where the spread returns are are greater than 1%
  profitable_trades_early.describe()

  # For the date early in the dataset, calculate the potential profit per trade in dollars 
  # Multiply the profitable trades by the cost of the Bitcoin that was purchased
  profit_early=profitable_trades_early * bitstamp['Close'].loc['2018-01-16']
  # Drop any missing values from the profit DataFrame
  profit_per_trade_early=profit_early.dropna()
  # View the early profit DataFrame
  profit_per_trade_early

  # Generate the summary statistics for the early profit per trade DataFrame
  profit_per_trade_early.describe()

  # Plot the results for the early profit per trade DataFrame
  profit_per_trade_early.plot(figsize=(10, 7), title="Profit Per Trade - Jan 16")

  # Calculate the sum of the potential profits for the early profit per trade DataFrame
  profit_sum_early=profit_per_trade_early.sum()
  profit_sum_early

  # Use the cumsum function to calculate the cumulative profits over time for the early profit per
  # trade DataFrame
  cumulative_profit_early=profit_per_trade_early.cumsum()
  # Plot the cumulative sum of profits for the early profit per trade DataFrame
  cumulative_profit_early.plot(figsize=(10, 7), title="Cumulative Sum - January 16")

  #**Answer:** The profit information supports the trend in the narrowing of the spread
  #from January to March. As the spread narrows, so does the opportunity for profit,
  #as it is evident in the calculated results.
 ```

<!-- CONTRIBUTORS -->
## Contributors

Public Open Source

<!-- LICENSE -->
## License

None

<!-- CONTACT -->
## Contact

Avangelina Cazares