# Stock Price Forecasting

Stock prices forecasting has always been a challenging task. 
Although many research projects try to address the problem, few of them pay attention to the varying degrees of dependencies between stock prices. 
We introduce a hybrid model that improves the prediction of stock prices by emphasizing the dependencies between adjacent stock prices. 
The proposed model, ResNLS, is mainly composed of two neural architectures, ResNet and LSTM. 
ResNet serves as a feature extractor to identify dependencies between stock prices, while LSTM analyzes the initial time series data with the combination of dependencies, which are considered as residuals. 
Our experiment reveals that when the closing price data for the previous 5 consecutive trading days is used as input, the performance of the model (ResNLS-5) is optimal compared to those with other inputs. 
Furthermore, ResNLS-5 demonstrates at least a 20% improvement over current state-of-the-art baselines. 
To verify whether ResNLS-5 can help clients effectively avoid risks and earn profits in the stock market, we construct a quantitative trading framework for back testing. 
The result shows that the trading strategy based on ResNLS-5 predictions can successfully mitigate losses during declining stock prices and generate profits in periods of rising stock prices. 

![ResNLS Architecture](image/resnls.png)

## Model

Despite the wide adoption of machine learning and deep learning in stock price prediction, few approaches explicitly account for the varying degrees of dependency between adjacent stock prices. 
ResNLS addresses this by combining **ResNet** and **LSTM** into a hybrid architecture:

- **ResNet** acts as a feature extractor to capture dependencies between stock prices across time windows.
- **LSTM** analyzes the raw time-series data jointly with these dependency features (treated as residuals).

## Experiments

- **Dataset**: CSI 300 index (`sh.000001`), 2012–2022.
- **Input**: Closing prices of the previous 5 consecutive trading days.
- **Train/Test Split**: ~90% / ~10%.
- **Result**: ResNLS achieves at least 20% improvement over state-of-the-art baselines. Backtesting confirms the trading strategy can mitigate losses in downturns and generate profits in uptrends.

## Usage

```bash
python src/resnls.py
```

## Project Structure

```
.
├── image/
│   └── resnls.png
├── src/
│   └── resnls.py
├── LICENSE.txt
├── README.md
├── requirements.txt
└── .gitignore
```
