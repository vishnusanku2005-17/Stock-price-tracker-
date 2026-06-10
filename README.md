# Stock-price-tracker-
# Hardcoded stock prices
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 140,
    "MSFT": 330,
    "AMZN": 145
}

total_investment = 0
portfolio = {}

print("Available Stocks:")
for stock, price in stock_prices.items():
    print(f"{stock}: ${price}")

# Number of stocks to enter
n = int(input("\nHow many different stocks do you own? "))

for i in range(n):
    stock_name = input("\nEnter stock symbol: ").upper()
    quantity = int(input("Enter quantity: "))

    if stock_name in stock_prices:
        portfolio[stock_name] = quantity
        investment = stock_prices[stock_name] * quantity
        total_investment += investment
    else:
        print("Stock not found! Skipping...")

# Display portfolio summary
print("\n----- Portfolio Summary -----")
for stock, quantity in portfolio.items():
    value = stock_prices[stock] * quantity
    print(f"{stock}: {quantity} shares × ${stock_prices[stock]} = ${value}")

print(f"\nTotal Investment Value: ${total_investment}")

# Optional: Save to a text file
save = input("\nDo you want to save the result to a file? (yes/no): ").lower()

if save == "yes":
    with open("portfolio.txt", "w") as file:
        file.write("Portfolio Summary\n")
        file.write("-----------------\n")

        for stock, quantity in portfolio.items():
            value = stock_prices[stock] * quantity
            file.write(
                f"{stock}: {quantity} shares × ${stock_prices[stock]} = ${value}\n"
            )

        file.write(f"\nTotal Investment Value: ${total_investment}")

    print("Portfolio saved to 'portfolio.txt'")
