- 6조 (이다혜, 조소영, 김건우, 민선규)
- 6.5 User Applications Built with Spark
- 6.6 Interactive Data Mining
- 7. Discussion

## 6.5 User Applications Built with Spark
In-Memory Analytics Conviva Inc, a video distribu-tion company, used Spark to accelerate a number of data analytics reports that previously ran over Hadoop. 
For example, one report ran as a series of Hive [1] queries that computed various statistics for a customer. 

```md
인메모리 
```

These queries all worked on the same subset of the data (recordsmatching a customer-provided filter), but performed ag-gregations (averages, percentiles, and COUNT DISTINCT) over different grouping fields, requiring separate MapRe-duce jobs. 
By implementing the queries in Spark andloading the subset of data shared across them once into an RDD, the company was able to speed up the report by 40×. A report on 200 GB of compressed data that took 20 hours on a Hadoop cluster now runs in 30 minutes using only two Spark machines. Furthermore, the Spark program only required 96 GB of RAM, because it only stored the rows and columns matching the customer’s fil-ter in an RDD, not the whole decompressed file.
Traffic Modeling Researchers in the Mobile Millen- nium project at Berkeley [18] parallelized a learning al-gorithm for inferring road traffic congestion from spo-radic automobile GPS measurements. 
The source data were a 10,000 link road network for a metropolitan area,
as well as 600,000 samples of point-to-point trip timesfor GPS-equipped automobiles (travel times for each path may include multiple road links). 
Using a traffic model, the system can estimate the time it takes to travelacross individual road links. 
The researchers trained this model using an expectation maximization (EM) algo-rithm that repeats two map and reduceByKey steps itera-tively. The application scales nearly linearly from 20 to 80 nodes with 4 cores each, as shown in Figure 13(a).

![](Attached_file/스크린샷%202026-04-07%20오후%204.21.07.png)

Twitter Spam Classification The Monarch project at Berkeley [29] used Spark to identify link spam in Twitter messages. 
They implemented a logistic regression classi- fier on top of Spark similar to the example in Section 6.1,
but they used a distributed reduceByKey to sum the gradi-ent vectors in parallel. In Figure 13(b) we show the scal-ing results for training a classifier over a 50 GB subset
of the data: 250,000 URLs and 107 features/dimensions
related to the network and content properties of the pages at each URL. The scaling is not as close to linear due to a higher fixed communication cost per iteration.

## 6.6 Interactive Data Mining

To demonstrate Spark’ ability to interactively query big datasets, we used it to analyze 1TB of Wikipedia page view logs (2 years of data). 
For this experiment, we used 100 m2.4xlarge EC2 instances with 8 cores and 68 GB
of RAM each. 
We ran queries to find total views of (1) all pages, (2) pages with titles exactly matching a given word, and (3) pages with titles partially matching a word.
Each query scanned the entire input data. 
Figure 14 shows the response times of the queries on the full dataset and half and one-tenth of the data. Even at 1 TB of data, queries on Spark took 5–7 seconds. 
This was more than an order of magnitude faster than work-ing with on-disk data; for example, querying the 1 TB file from disk took 170s. This illustrates that RDDs make
Spark a powerful tool for interactive data mining.

## 7 Discussion

Although RDDs seem to offer a limited programming in- terface due to their immutable nature and coarse-grained transformations, we have found them suitable for a wide
class of applications. In particular, RDDs can express a surprising number of cluster programming models that have so far been proposed as separate frameworks, al-lowing users to compose these models in one program(e.g., run a MapReduce operation to build a graph, then run Pregel on it) and share data between them. 
In this sec-tion, we discuss which programming models RDDs canexpress and why they are so widely applicable (§7.1). 
In addition, we discuss another benefit of the lineage infor-mation in RDDs that we are pursuing, which is to facili-tate debugging across these models (§7.2).