install.packages(c("quantmod","tidyquant"))

# Load required libraries
library(quantmod)
library(tidyverse)
library(tidyquant)

# Define the stock symbol (SPY in this case)
stock_symbol <- "SPY"

# Download stock data using quantmod
getSymbols(stock_symbol, src = "yahoo", from = "2000-01-01")

# Extract the adjusted closing prices
stock_data <- Cl(get(stock_symbol))

# Create a tibble using tidyverse
stock_tibble <- tibble(date = index(stock_data), price = as.numeric(stock_data))

# Add a new column for the percentage change from the previous day
stock_tibble <- stock_tibble %>%
  mutate(per_chg_from_day_prior = c(NA, diff(price)/lag(price)[-1]))

#Drop NAs:
stock_tibble<- stock_tibble%>%
  drop_na()

# Save the tibble to a CSV file named "spy.csv"
write_csv(stock_tibble, "spy.csv")

View(stock_tibble)
