# How-to-fill-an-empty-area-with-dotted-lines-in-Blazor-chart
 

This article explains how to fill the empty area with dotted lines in [Blazor chart](https://www.syncfusion.com/blazor-components/blazor-charts)

**Creating stacking series chart with empty points**

To demonstrate this, consider the [two stacking area series](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Charts.ChartSeriesType.html#Syncfusion_Blazor_Charts_ChartSeriesType_StackingArea). If it is populated data have a NaN or null, then it will be plotted as shown in the following image.

**C#**

```cshtml
@using Syncfusion.Blazor.Charts

<SfChart Width="500">

    <ChartPrimaryXAxis ValueType="Syncfusion.Blazor.Charts.ValueType.Category"/>
  
    <ChartSeriesCollection>
        <ChartSeries DataSource="@MedalDetails" XName="X" YName="Y" Type="ChartSeriesType.StackingArea">            
        </ChartSeries>
        <ChartSeries DataSource="@MedalDetails1" XName="X" YName="Y" Type="ChartSeriesType.StackingArea">             
        </ChartSeries>        
    </ChartSeriesCollection>
     
</SfChart>

@code{

    public bool IsEmpty = false;

    public class ChartData
    {
        public double X { get; set; }
        public double? Y { get; set; }

    }

    public List<ChartData> MedalDetails = new List<ChartData>
    {
        new ChartData{ X=2000, Y= 25 },
        new ChartData{ X=2001, Y= 10 },
        new ChartData{ X=2002, Y= 15 },
        new ChartData{ X=2003, Y= null },
        new ChartData{ X=2004, Y= 10 },
        new ChartData{ X=2005, Y= 5 },
        new ChartData{ X=2006, Y= 20 },
        new ChartData{ X=2007, Y= 15 },
        new ChartData{ X=2008, Y= 12 },
        new ChartData{ X=2009, Y= null },
        new ChartData{ X=2010, Y= 15 },
        new ChartData{ X=2011, Y= 20 },
    };
    public List<ChartData> MedalDetails1 = new List<ChartData>
    {
        new ChartData{ X=2000, Y= 5 },
        new ChartData{ X=2001, Y= 5 },
        new ChartData{ X=2002, Y= 5 },
        new ChartData{ X=2003, Y= null },
        new ChartData{ X=2004, Y= 5 },
        new ChartData{ X=2005, Y= 5 },
        new ChartData{ X=2006, Y= 5 },
        new ChartData{ X=2007, Y= 5 },
        new ChartData{ X=2008, Y= 5 },
        new ChartData{ X=2009, Y= null },
        new ChartData{ X=2010, Y= 5 },
        new ChartData{ X=2011, Y= 5 },

    };
}

```

**Stacking series with empty points**

![](/empty-points.png)

**Filling the empty points with dotted line**

In order to fill this empty space with dotted lines, use [Line Series](https://www.syncfusion.com/blazor-components/blazor-charts/chart-types/line-chart) with calculated data from two stacking area series's data collection as shown in the following code sample.

**C#**

```cshtml

    public List<ChartData> LineData = new List<ChartData> { };

    protected override void OnInitialized()
    {
        for ( int i = 0; i < MedalDetails.Count; i++)
        {

            if (MedalDetails[i].Y == null && MedalDetails1[i].Y == null)
            {
                IsEmpty = true;
            }
            else
            {
                IsEmpty = false;
            }                

            if (IsEmpty)
            {
                if ((MedalDetails[i - 1].Y)!=null)
                {
                    LineData.Add(new ChartData{X = MedalDetails[i - 1].X,Y = 0});
                    LineData.Add(new ChartData { X = MedalDetails[i - 1].X, Y = (MedalDetails[i - 1].Y + MedalDetails1[i - 1].Y)});
                }

                if ( (MedalDetails1[i + 1].Y)!=null)
                {
                    LineData.Add(new ChartData { X = MedalDetails[i + 1].X, Y = (MedalDetails[i + 1].Y + MedalDetails1[i + 1].Y)});
                    LineData.Add(new ChartData { X = MedalDetails[i + 1].X, Y = 0 });
                    LineData.Add(new ChartData { X = MedalDetails[i + 1].X, Y = double.NaN });

                }            

            }                                                                                               
        }

    }     


```

**Empty points with dotted line**

![](/empty-points-with-dotted-line.png)

**Conclusion**

I hope you enjoyed learning how to fill the empty area with dotted line in Blazor Chart Component.

You can refer to our [Blazor Chart feature tour](https://www.syncfusion.com/blazor-components/blazor-charts) page to know about its other groundbreaking feature representations and [documentation](https://blazor.syncfusion.com/documentation/chart/getting-started), and how to quickly get started for configuration specifications. You can also explore our [Blazor Chart example](https://blazor.syncfusion.com/demos/chart/line?theme=bootstrap5) to understand how to create and manipulate data.

For current customers, you can check out our components from the [License and Downloads](https://www.syncfusion.com/sales/teamlicense) page. If you are new to Syncfusion, you can try our 30-day [free trial](https://www.syncfusion.com/downloads/blazor) to check out our other controls.

If you have any queries or require clarifications, please let us know in the comments section below. You can also contact us through our [support forums](https://www.syncfusion.com/forums), [support portal](https://support.syncfusion.com/create), or [feedback portal](https://www.syncfusion.com/feedback/blazor-components?control=charts). We are always happy to assist you!