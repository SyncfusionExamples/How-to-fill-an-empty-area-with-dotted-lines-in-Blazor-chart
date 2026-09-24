# How to Fill Empty Areas with Dotted Lines in a Blazor Chart

## Overview

This sample demonstrates how to fill empty regions in a Syncfusion [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts) visualization when stacking area series contain missing data points. The implementation uses two stacking area series and dynamically generates a separate line-series data source that is rendered with a dotted stroke across empty regions. This approach helps users visually identify missing data while preserving chart readability and continuity. The sample calculates boundary points from neighboring valid values and overlays a dotted line to represent the otherwise empty area.

## Key Features

- Uses `ChartSeriesType.StackingArea` to render multiple stacked area series.
- Uses `ChartSeriesType.Line` to render a dotted-line overlay across empty regions.
- Detects empty points by checking `null` values in the source data collections.
- Creates a dedicated `LineData` collection during `OnInitialized()`.
- Calculates line-series points from adjacent valid stacking-area values.
- Adds calculated points only when empty regions are identified.
- Uses `double.NaN` to break line segments and prevent unwanted connections between dotted sections.
- Binds chart data through strongly typed data collections.
- Demonstrates custom visualization of missing values without modifying the original area-series data.

## Prerequisites

- [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) or [Visual Studio Code](https://code.visualstudio.com/)
- [.NET SDK](https://dotnet.microsoft.com/en-us/download/dotnet) compatible with the project's target framework

## How to Run the Project

**Visual Studio 2022**

1. Clone or download this repository.
2. Open the project file:
   - `DottelLine/DottelLine.csproj`
3. Restore NuGet packages.
4. Build the project.
5. Run the application using `Ctrl+F5`.

**Visual Studio Code**

1. Clone or download this repository.
2. Open the repository folder in Visual Studio Code.
3. Open the integrated terminal.
4. Navigate to the project directory.

```bash
cd DottelLine
dotnet restore
dotnet run
```

5. Open the application using the local URL displayed in the terminal after the application starts.

## Project Structure

`Pages/Index.razor` - Main sample page containing the chart implementation, stacking area series configuration, empty-point detection logic, calculated line-series generation, and dotted-line visualization.

## Support and Feedback

- For general product questions, visit the [Syncfusion Community Forum](https://www.syncfusion.com/forums) or [Syncfusion Support](https://www.syncfusion.com/support).
- To report an issue specific to this sample, open a GitHub issue in this repository.
- Review the official Blazor Chart documentation: https://help.syncfusion.com/chart-sdk/blazor/charts/getting-started

## License

This is a Syncfusion sample project provided to demonstrate product usage. Review the [Syncfusion license terms](https://www.syncfusion.com/sales/pricing?category=ui-components) before using Syncfusion components in your own applications.