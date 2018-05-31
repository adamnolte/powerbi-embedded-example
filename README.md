# Power BI Embedded Examples

## Power BI Javascript Library
https://github.com/Microsoft/PowerBI-JavaScript

## Basic Example
1. Follow Instructions here to setup power bi report and azure function - https://www.taygan.co/blog/2018/05/14/embedded-analytics-with-power-bi
   * You do not need to setup dedicated capacity.
   * Note: I have modified the return value from the function slightly in my version of [run.csx](https://github.com/ajnolte12/powerbi-embedded-example/blob/master/azure-function/run.csx)
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

| Tenancy   | Industry     | size |
| --------- | ------------ | ---- |
| tenancy-1 | Finance      | 5    |
| tenancy-1 | Energy       | 15    |
| tenancy-2 | Healthcare   | 20    |
| tenancy-2 | Construction | 25    |

2. As before, create a report in Power BI using that dataset and setup your azure function to give you an embed token to that report.
3. With the angular app started, type into the input box and click filter
4. The filtering logic can be seen in [app.component.ts](https://github.com/ajnolte12/powerbi-embedded-example/blob/master/angular-ui-example/src/app/app.component.ts)
5. For more information on filtering go to
   * https://github.com/Microsoft/PowerBI-JavaScript/wiki/Filters
   * https://www.kasperonbi.com/embed-your-power-bi-report-with-predefined-filters/

See below for securely filtering by tenancy

### Printing a report
See
  * https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embedding---Basic-interactions#print-a-report
  * https://ideas.powerbi.com/forums/265200-power-bi-ideas/suggestions/15295617-allow-printing-from-power-bi-embedded

### Filtering a report by tenancy

To filter by tenancy you will need to implement Row Level Security. If you filter by tenancy client side, all the data from every tenancy will be downloaded to the client then filtered creating a security risk. Filtering using RLS lets the Power BI service filter by tenancy so only the users tenancy data will be downloaded.

https://community.powerbi.com/t5/Developer/Doubt-about-embed-token-and-filtering/td-p/275045
https://docs.microsoft.com/en-us/power-bi/service-admin-rls

Then you will pass in the role in your Azure Function [run.csx](https://github.com/ajnolte12/powerbi-embedded-example/blob/master/azure-function/run.csx#L41) when requesting the embed token.
