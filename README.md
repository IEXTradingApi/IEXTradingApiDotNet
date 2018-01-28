# IEXTradingApiDotNet
IEXTradingApiDotNet is a .NET API Wrapper allowing to retrieve data from IEX Trading endpoint (https://iextrading.com/).

## Introduction
This library acts as a .NET CORE Wrapper of IEX Trading REST API. You can find the official documentation of the REST API [here](https://iextrading.com/developer/docs/)

The IEX Trading operations that are currently covered by this wrapper are:

### Stock
1. [Quote](#quote)
2. Chart
3. Open-Close
4. Previous

<a name="quote"></a>
## QUOTE

***
## Display the result of a QUOTE request
```

using IEXTrading;
using IEXTradingDotNetCore.STOCK_QUOTE;
using System;

namespace IEXTradingDotNetCore
{
    public class Program
    {
        static void Main(string[] args)
        {
            var connection = IEXTradingConnection.Instance;
            var stockQuoteOperation = connection.GetQueryObject_STOCK_QUOTE();
            stockQuoteOperation.FilterBy(Const_STOCK_QUOTE.STOCK_QUOTE_fields.CloseTime,
                Const_STOCK_QUOTE.STOCK_QUOTE_fields.DelayedPriceTime);
            var responseStockQuoteOperation = stockQuoteOperation.Query("MSFT");

            // Printout the results
            Console.WriteLine("******** RAW DATA QUOTE ********");
            Console.WriteLine(responseStockQuoteOperation.RawData);

            Console.WriteLine("******** STRUCTURED DATA QUOTE ********");
            var data = responseStockQuoteOperation.Data;
            if (data.Error)
            {
                Console.WriteLine(data.ErrorMessage);
            }
            else
            {
                Console.WriteLine(data.Symbol);
                Console.WriteLine(data.CompanyName);
                Console.WriteLine(data.PrimaryExchange);
                Console.WriteLine(data.Sector);
                Console.WriteLine(data.CalculationPrice);
                Console.WriteLine(data.Open);
                Console.WriteLine(data.OpenTime);
                Console.WriteLine(data.Close);
                Console.WriteLine(data.CloseTime);
                Console.WriteLine(data.LatestPrice);
                Console.WriteLine(data.LatestSource);
                Console.WriteLine(data.LatestTime);
                Console.WriteLine(data.LatestUpdate);
                Console.WriteLine(data.LatestVolume);
                Console.WriteLine(data.IEXRealtimePrice);
                Console.WriteLine(data.IEXRealtimeSize);
                Console.WriteLine(data.IEXLastUpdated);
                Console.WriteLine(data.DelayedPrice);
                Console.WriteLine(data.DelayedPriceTime);
                Console.WriteLine(data.PreviousClose);
                Console.WriteLine(data.Change);
                Console.WriteLine(data.ChangePercent);
                Console.WriteLine(data.IEXMarketPercent);
                Console.WriteLine(data.IEXVolume);
                Console.WriteLine(data.AvgTotalVolume);
                Console.WriteLine(data.IEXBidPrice);
                Console.WriteLine(data.IEXBidSize);
                Console.WriteLine(data.IEXAskPrice);
                Console.WriteLine(data.IEXAskSize);
                Console.WriteLine(data.MarketCap);
                Console.WriteLine(data.PeRatio);
                Console.WriteLine(data.Week52High);
                Console.WriteLine(data.Week52Low);
                Console.WriteLine(data.YtdChange);
            }
        }
    }
}

```
