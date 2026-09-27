# 📈 yfinance: Guía Maestra de Datos de Mercado & Análisis Financiero

> **Origen:** [GitHub ranaroussi/yfinance](https://github.com/ranaroussi/yfinance)  
> **Documentación Oficial Web:** [https://ranaroussi.github.io/yfinance/](https://ranaroussi.github.io/yfinance/)  
> **Comunidad:** 15,000+ Stars en GitHub ⭐ | 100M+ Descargas anuales en PyPI  
> **Licencia:** Apache 2.0 (Open Source)  

---

## 1. Instalación y Setup

```bash
# Instalación estándar
pip install yfinance pandas requests-cache

# Para dashboards y visualización completa
pip install yfinance plotly matplotlib streamlit
```

---

## 2. Descarga de Precios Históricos

```python
import yfinance as yf

# 1. Ticker Individual (ej: Apple)
apple = yf.Ticker("AAPL")
hist = apple.history(period="1y", interval="1d")
print(hist[['Open', 'High', 'Low', 'Close', 'Volume']].tail())

# 2. Descarga Masiva de Múltiples Activos
tickers = ["AAPL", "NVDA", "MSFT", "BTC-USD", "ETH-USD"]
data = yf.download(tickers, start="2024-01-01", group_by='ticker')
print(data['NVDA']['Close'].tail())
```

---

## 3. Parámetros de Periodos e Intervalos

| Parámetro | Valores | Descripción |
| :--- | :--- | :--- |
| `period` | `1d, 5d, 1mo, 3mo, 6mo, 1y, 2y, 5y, 10y, ytd, max` | Rango total de tiempo solicitado. |
| `interval` | `1m, 2m, 5m, 15m, 30m, 60m, 90m, 1h, 1d, 5d, 1wk, 1mo, 3mo` | Granularidad temporal de las velas. |
| `auto_adjust` | `True / False` | Ajuste automático de precios por splits y dividendos. |

---

## 4. Análisis Fundamental y Estados Financieros

```python
import yfinance as yf

nvda = yf.Ticker("NVDA")

# Ratios y Metadatos
info = nvda.info
print(f"Market Cap: ${info.get('marketCap'):,}")
print(f"Trailing P/E: {info.get('trailingPE')} | Forward P/E: {info.get('forwardPE')}")

# Estados Financieros
financials = nvda.financials          # Cuenta de resultados
balance = nvda.balance_sheet          # Balance general
cashflow = nvda.cashflow              # Flujo de caja
```

---

## 5. Dividendos, Splits y Opciones

```python
import yfinance as yf

msft = yf.Ticker("MSFT")

# Dividendos y Splits
print(msft.dividends.tail())
print(msft.splits)

# Cadena de Opciones
exp_date = msft.options[0]
chain = msft.option_chain(exp_date)
calls = chain.calls[['strike', 'lastPrice', 'volume', 'impliedVolatility']]
print(calls.head())
```

---

## 6. Screener del Mercado y Búsqueda de Noticias

```python
import yfinance as yf

# Noticias por palabra clave
search = yf.Search("artificial intelligence", news_count=5)
for n in search.news:
    print(f"📰 {n['title']} ({n['publisher']})")

# Screener de mayores subidas del día
screener = yf.Screener()
screener.set_predefined_body('day_gainers')
print("Gainers:", len(screener.response.get('quotes', [])))
```

---

## 📚 Enlaces de Referencia
- **GitHub:** [https://github.com/ranaroussi/yfinance](https://github.com/ranaroussi/yfinance)
- **Documentación Oficial:** [https://ranaroussi.github.io/yfinance/](https://ranaroussi.github.io/yfinance/)
