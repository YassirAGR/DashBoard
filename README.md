# DashBoard
This project allows you to select a stock symbol from a dropdown menu and displays the corresponding stock price chart.

Key Components:

Importing Libraries:

jupyter_dash: Provides Jupyter Dash functionality for building interactive dashboards.
dash: Core Dash library for building web-based dashboards.
yfinance: Library for retrieving financial data from Yahoo Finance.
plotly.express: Library for creating high-quality visualizations.
Creating the Dash App:

app = JupyterDash(__name__): Initializes a Jupyter Dash app instance.
Defining the App Layout:

app.layout = html.Div(): Defines the layout structure using HTML elements.
html.H1("Stock Price Analysis Dashboard"): Displays a heading.
html.Label("Select Stock Symbol:"): Creates a label for the dropdown menu.
dcc.Dropdown(): Creates a dropdown menu with stock symbol options.
id='stock-selector': Unique identifier for the dropdown component.
options: List of stock symbol options.
{'label': 'AAPL', 'value': 'AAPL'}: Represents an option with label 'AAPL' and value 'AAPL'.
value='AAPL': Sets the default selected value to 'AAPL'.
dcc.Graph(): Creates an empty graph component to display the stock price chart.
id='stock-price-chart': Unique identifier for the graph component.
Creating the Callback Function:

@app.callback(): Decorator to define a callback function.
Output('stock-price-chart', 'figure'): Specifies the output component (graph) and its property (figure) to update.
[Input('stock-selector', 'value')]: Defines the input component (dropdown) and its property (value) to listen to.
def update_chart(selected_stock): Implementation of the callback function.
stock_data = yf.download(selected_stock, start='2022-01-01', end='2023-01-01'): Downloads historical stock data for the selected stock.
fig = px.line(stock_data, x=stock_data.index, y='Close', title=f'{selected_stock} Stock Price Analysis'): Creates a line chart using Plotly Express.
return fig: Returns the updated chart figure.
Running the Dash App:

if __name__ == '__main__':: Ensures the code runs only when the script is executed directly.
app.run_server(port=8050, mode='external'): Runs the Dash app on port 8050 in external mode.
Procfile
requirements
