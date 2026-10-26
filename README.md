# n8n Automation Workflows

n8n workflows I built for collecting and storing market data.

## CRYPTO: Binance historical data to Supabase

`CRYPTO_CLEAN.json` pulls daily price history (klines) for a list of coins from the public Binance API and saves it to a Supabase table.

**Flow:**

1. **Define Coins List:** a Code node holds the list of symbols to fetch
2. **Loop Over Items:** processes the coins in batches to stay within rate limits
3. **Fetch Klines from Binance:** HTTP request to `api.binance.com/api/v3/klines`
4. **Format Klines Data:** a Code node turns Binance's arrays into clean rows (open, high, low, close, volume, time)
5. **Save to Supabase:** inserts the rows into the database

## How to use

1. In n8n, go to **Workflows → Import from file** and choose `CRYPTO_CLEAN.json`.
2. Add your own Supabase credentials to the **Save to Supabase** node. No credentials are stored in this file.
3. Edit the coin list in **Define Coins List**, then run the workflow.
