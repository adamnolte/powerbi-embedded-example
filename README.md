# Power BI Embedded Examples

## Power BI Javascript Library
https://github.com/Microsoft/PowerBI-JavaScript

## Basic Example
1. Follow Instructions here to setup power bi report and azure function - https://www.taygan.co/blog/2018/05/14/embedded-analytics-with-power-bi
   * You do not need to setup dedicated capacity.
2. Replace `var getEmbedToken = "INSERT_YOUR_AZURE_FUNCTION_URL_HERE";` in [jquery-example.html](https://github.com/ajnolte12/powerbi-embedded-example/blob/master/jquery-example.html#L19) with your azure function url.
3. Load [jquery-example.html](https://github.com/ajnolte12/powerbi-embedded-example/blob/master/jquery-example.html) in your web browser.
4. Your report should display

## Using Angular App Instead of HTML File
1. Follow the same instructions as above to create report and azure function.
2. Replace `const embedGeneratorUrl = '<insert azure function url here>';` in [app.component.ts](https://github.com/ajnolte12/powerbi-embedded-example/blob/master/angular-ui-example/src/app/app.component.ts#L19)
3. Run `npm install` from inside the angular-ui-example directory
4. Run `ng serve` from inside the angular-ui-example directory
5. Once started you should see your site at `http://localhost:4200`

### Using filters
1. Setup a dataset formatted like the following

| Tenancy   | Group   | size |
| --------- | ------- | ---- |
| tenancy-1 | group-1 | 5    |
| tenancy-1 | group-2 | 15    |
| tenancy-2 | group-1 | 20    |
| tenancy-2 | group-2 | 25    |

2. As before, create a report in Power BI using that dataset and setup your azure function to give you an embed token to that report.
3. With the angular app started, include your fitlers into your query string param `http://localhost:4200/?tenancy=tenancy-1&group=group-1`
4. The filtering logic can be seen in [app.component.ts](https://github.com/ajnolte12/powerbi-embedded-example/blob/master/angular-ui-example/src/app/app.component.ts)
5. For more information on filtering go to https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters

### Printing a report
See https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embedding---Basic-interactions#print-a-report
