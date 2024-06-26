
> [!IMPORTANT]
> On June 26 2024, Linux Foundation announced the merger of its financial services umbrella, the Fintech Open Source Foundation ([FINOS](https://finos.org)), with OS-Climate, an open source community dedicated to building data technologies, modeling, and analytic tools that will drive global capital flows into climate change mitigation and resilience; OS-Climate projects are in the process of transitioning to the [FINOS governance framework](https://community.finos.org/docs/governance); read more on [finos.org/press/finos-join-forces-os-open-source-climate-sustainability-esg](https://finos.org/press/finos-join-forces-os-open-source-climate-sustainability-esg)

# SEC DERA Ingestion Pipeline

The [Division of Economic and Risk Analysis](https://www.sec.gov/dera) (DERA) was created in September 2009 to integrate financial economics and rigorous data analytics into the core mission of the SEC. The Division is involved across the entire range of SEC activities, including policy-making, rule-making, enforcement, and examination.

Data is central to DERA's mission. The SEC requires all companies that trade on US stock exchanges to make certain data available, and DERA collects and publishes that data. A summary for of that data is listed as [Financial Statements](https://www.sec.gov/dera/data/financial-statement-data-sets.html) and a more detailed version is listed as [Financial Statements and Notes](https://www.sec.gov/dera/data/financial-statement-and-notes-data-set.html).

The principal notebook for implementing this pipeline is [DERA-ingest](notebooks/DERA-ingest.ipynb). It performs a basic ingestion of the SEC data, marrying company names to [Global Legal Entity Identifiers](https://www.gleif.org/en) where it can. There are hundreds of millions of rows of data for just the past few years of annual reports, and we could increase that considerably by ingesting quarterly reports as well. But so far there's no need for that.

Once the basic financial data has been ingested, a second notebook ([SEC Corp Financials](notebooks/SEC%20Corp%20Financials.ipynb)) makes the data "easy to use" by summarizing market float (aka market cap), annual revneues, income, and reported cash, debt, and assets at the time of the annual report. We also apply some crosswalks to make it easier to connect the SIC-based SEC data with ISIC codes used internationally.

In the future this pipeline will use the [ESG Matching](https://github.com/os-climate/esg-matching) services of the [Data Commons](https://github.com/os-climate/os_c_data_commons). As well we are looking at ingesting the more detailed DERA information so that analyses can be run on business segments, not only whole consolidated reporting entities.

If you have questions, please file [Issues](https://github.com/os-climate/itr-data-pipeline/issues). If you have answers, please contribute [Pull Requests](https://github.com/os-climate/itr-data-pipeline/pulls)!

---

Project based on the [cookiecutter]("https://drivendata.github.io/cookiecutter-data-science/") data science project template.
