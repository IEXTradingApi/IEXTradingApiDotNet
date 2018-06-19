# IEXTradingApiDotNet
IEXTradingApiDotNet is a .NET API Wrapper allowing to retrieve data from IEX Trading endpoint (https://iextrading.com/).

## Introduction
This library acts as a .NET CORE Wrapper of IEX Trading REST API. You can find the official documentation of the REST API [here](https://iextrading.com/developer/docs/)

The IEX Trading operations that are currently covered by this wrapper are:

### Stock
1. [Quote](#quote)
2. [Chart](#chart)
3. Open-Close
4. Previous
5. Company
6. Delayed Quote
7. Price
8. Earnings
9. Book

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

<a name="chart"></a>
## CHART

***
## Display the result of a CHART date/yyyymmdd request
```

using IEXTrading;
using System;

namespace IEXTradingDotNetCore
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var connection = IEXTradingConnection.Instance;
            var operation = connection.GetQueryObject_STOCK_CHART();
            var response = operation.Query("MSFT", DateTime.Today.AddDays(-1));

            // Printout the results
            Console.WriteLine("******** RAW DATA QUOTE ********");
            Console.WriteLine(response.RawData);

            Console.WriteLine("******** STRUCTURED DATA QUOTE ********");
            var data = response.Data;
            if (data.Error)
            {
                Console.WriteLine(data.ErrorMessage);
            }
            else
            {
                Console.WriteLine("Range: " + data.Range);
                foreach(var t in data.TimeSeries)
                {
                    Console.WriteLine("Average: " + t.Average);
                    Console.WriteLine("Change: " + t.Change);
                    Console.WriteLine("Change Over Time: " + t.ChangeOverTime);
                    Console.WriteLine("Change Percent: " + t.ChangePercent);
                    Console.WriteLine("Close: " + t.Close);
                    Console.WriteLine("Date: " + t.Date);
                    Console.WriteLine("High: " + t.High);
                    Console.WriteLine("Label: " + t.Label);
                    Console.WriteLine("Low: " + t.Low);
                    Console.WriteLine("Minute: " + t.Minute);
                    Console.WriteLine("Notional: " + t.Notional);
                    Console.WriteLine("Number of Trades: " + t.NumberOfTrades);
                    Console.WriteLine("Open: " + t.Open);
                    Console.WriteLine("Unadjusted Volume: " + t.UnadjustedVolume);
                    Console.WriteLine("Volume: " + t.Volume);
                    Console.WriteLine("Vwap: " + t.Vwap);
                    Console.WriteLine("===============");
                }
            }
        }
    }
}
```

***
## Display the result of a CHART 1d request
```

using IEXTrading;
using System;

namespace IEXTradingDotNetCore
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var connection = IEXTradingConnection.Instance;
            var operation = connection.GetQueryObject_STOCK_CHART();
            var response = operation.Query("MSFT", STOCK_CHART.Const_STOCK_CHART.STOCK_CHART_input_options_fields.OneDay);

            // Printout the results
            Console.WriteLine("******** RAW DATA QUOTE ********");
            Console.WriteLine(response.RawData);

            Console.WriteLine("******** STRUCTURED DATA QUOTE ********");
            var data = response.Data;
            if (data.Error)
            {
                Console.WriteLine(data.ErrorMessage);
            }
            else
            {
                Console.WriteLine("Range: " + data.Range);
                foreach(var t in data.TimeSeries)
                {
                    Console.WriteLine("Average: " + t.Average);
                    Console.WriteLine("Change: " + t.Change);
                    Console.WriteLine("Change Over Time: " + t.ChangeOverTime);
                    Console.WriteLine("Change Percent: " + t.ChangePercent);
                    Console.WriteLine("Close: " + t.Close);
                    Console.WriteLine("Date: " + t.Date);
                    Console.WriteLine("High: " + t.High);
                    Console.WriteLine("Label: " + t.Label);
                    Console.WriteLine("Low: " + t.Low);
                    Console.WriteLine("Minute: " + t.Minute);
                    Console.WriteLine("Notional: " + t.Notional);
                    Console.WriteLine("Number of Trades: " + t.NumberOfTrades);
                    Console.WriteLine("Open: " + t.Open);
                    Console.WriteLine("Unadjusted Volume: " + t.UnadjustedVolume);
                    Console.WriteLine("Volume: " + t.Volume);
                    Console.WriteLine("Vwap: " + t.Vwap);
                    Console.WriteLine("===============");
                }
            }
        }
    }
}
```

***
## Display the result of a CHART dynamic request
```

using IEXTrading;
using System;

namespace IEXTradingDotNetCore
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var connection = IEXTradingConnection.Instance;
            var operation = connection.GetQueryObject_STOCK_CHART();
            var response = operation.Query("MSFT", STOCK_CHART.Const_STOCK_CHART.STOCK_CHART_input_options_fields.Dynamic);

            // Printout the results
            Console.WriteLine("******** RAW DATA QUOTE ********");
            Console.WriteLine(response.RawData);

            Console.WriteLine("******** STRUCTURED DATA QUOTE ********");
            var data = response.Data;
            if (data.Error)
            {
                Console.WriteLine(data.ErrorMessage);
            }
            else
            {
                Console.WriteLine("Range: " + data.Range);
                foreach(var t in data.TimeSeries)
                {
                    Console.WriteLine("Average: " + t.Average);
                    Console.WriteLine("Change: " + t.Change);
                    Console.WriteLine("Change Over Time: " + t.ChangeOverTime);
                    Console.WriteLine("Change Percent: " + t.ChangePercent);
                    Console.WriteLine("Close: " + t.Close);
                    Console.WriteLine("Date: " + t.Date);
                    Console.WriteLine("High: " + t.High);
                    Console.WriteLine("Label: " + t.Label);
                    Console.WriteLine("Low: " + t.Low);
                    Console.WriteLine("Minute: " + t.Minute);
                    Console.WriteLine("Notional: " + t.Notional);
                    Console.WriteLine("Number of Trades: " + t.NumberOfTrades);
                    Console.WriteLine("Open: " + t.Open);
                    Console.WriteLine("Unadjusted Volume: " + t.UnadjustedVolume);
                    Console.WriteLine("Volume: " + t.Volume);
                    Console.WriteLine("Vwap: " + t.Vwap);
                    Console.WriteLine("===============");
                }
            }
        }
    }
}
```
