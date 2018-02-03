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
4. Company

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
                Console.WriteLine("Symbol: " + data.Symbol);
                Console.WriteLine("CompanyName: " + data.CompanyName);
                Console.WriteLine("PrimaryExchange: " + data.PrimaryExchange);
                Console.WriteLine("Sector: " + data.Sector);
                Console.WriteLine("CalculationPrice: " + data.CalculationPrice);
                Console.WriteLine("Open: " + data.Open);
                Console.WriteLine("OpenTime: " + data.OpenTime);
                Console.WriteLine("Close: " + data.Close);
                Console.WriteLine("CloseTime: " + data.CloseTime);
                Console.WriteLine("LatestPrice: " + data.LatestPrice);
                Console.WriteLine("LatestSource: " + data.LatestSource);
                Console.WriteLine("LatestTime: " + data.LatestTime);
                Console.WriteLine("LatestUpdate: " + data.LatestUpdate);
                Console.WriteLine("LatestVolume: " + data.LatestVolume);
                Console.WriteLine("IEXRealtimePrice: " + data.IEXRealtimePrice);
                Console.WriteLine("IEXRealtimeSize: " + data.IEXRealtimeSize);
                Console.WriteLine("IEXLastUpdated: " + data.IEXLastUpdated);
                Console.WriteLine("DelayedPrice: " + data.DelayedPrice);
                Console.WriteLine("DelayedPriceTime: " + data.DelayedPriceTime);
                Console.WriteLine("PreviousClose: " + data.PreviousClose);
                Console.WriteLine("Change: " + data.Change);
                Console.WriteLine("ChangePercent: " + data.ChangePercent);
                Console.WriteLine("IEXMarketPercent: " + data.IEXMarketPercent);
                Console.WriteLine("IEXVolume: " + data.IEXVolume);
                Console.WriteLine("AvgTotalVolume: " + data.AvgTotalVolume);
                Console.WriteLine("IEXBidPrice: " + data.IEXBidPrice);
                Console.WriteLine("IEXBidSize: " + data.IEXBidSize);
                Console.WriteLine("IEXAskPrice: " + data.IEXAskPrice);
                Console.WriteLine("IEXAskSize: " + data.IEXAskSize);
                Console.WriteLine("MarketCap: " + data.MarketCap);
                Console.WriteLine("PeRatio: " + data.PeRatio);
                Console.WriteLine("Week52High: " + data.Week52High);
                Console.WriteLine("Week52Low: " + data.Week52Low);
                Console.WriteLine("YtdChange: " + data.YtdChange);
            }
        }
    }
}

```
