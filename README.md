# Puppeteer Cluster

This repo simplifies the use of the strong coupling of the original repo

When you use puppeteer-cluster, you may want to perform some necessary operations after logging in to a certain website or before executing batch processing, but the original warehouse cannot do it.

So I modified part of the code, You can do this
```
const browser = await puppeteer.launch(
        { 
            executablePath: findChromePath.executablePath,
        }
)
await doLogin(browser.newPage())
// login after to spider data
const cluster = await Cluster.launch({
        concurrency: Cluster.CONCURRENCY_PAGE,
        maxConcurrency: 2,
        retryLimit: 2,
        browser,
    });
cluster.queue('https://domain/product/B0084M66QS')
cluster.queue('https://domain/product/B01CU2954W')
```


