- 6조 (이다혜, 조소영, 김건우, 민선규)
- 6.5 User Applications Built with Spark
- 6.6 Interactive Data Mining
- 7. Discussion

## 6.5 User Applications Built with Spark
In-Memory Analytics Conviva Inc, a video distribu-tion company, used Spark to accelerate a number of data analytics reports that previously ran over Hadoop. 
For example, one report ran as a series of Hive [1] queries that computed various statistics for a customer.

```md
인메모리 분석 비디오 배포 회사인 Conviva Inc는 이전에 Hadoop에서 실행되던 여러 데이터 분석 보고서의 속도를 높이기 위해 Spark를 사용했습니다.
예를 들어, 한 보고서는 고객에 대한 다양한 통계를 계산하는 일련의 Hive[1] 쿼리로 실행되었습니다.
```

These queries all worked on the same subset of the data (recordsmatching a customer-provided filter), but performed ag-gregations (averages, percentiles, and COUNT DISTINCT) over different grouping fields, requiring separate MapRe-duce jobs. 
By implementing the queries in Spark andloading the subset of data shared across them once into an RDD, the company was able to speed up the report by 40×. A report on 200 GB of compressed data that took 20 hours on a Hadoop cluster now runs in 30 minutes using only two Spark machines. Furthermore, the Spark program only required 96 GB of RAM, because it only stored the rows and columns matching the customer’s fil-ter in an RDD, not the whole decompressed file.

```md
이러한 쿼리는 모두 동일한 데이터 하위 집합(고객이 제공한 필터와 일치하는 레코드)에 대해 작동했지만, 서로 다른 그룹화 필드에 대해 ag-gregation(평균, 백분위수 및 COUNT DISTINCT)을 수행했기 때문에 별도의 MapRe-duce 작업이 필요했습니다.
이 회사는 Spark에서 쿼리를 구현하고 쿼리 간에 공유된 데이터의 하위 집합을 RDD에 한 번 로드함으로써 보고서의 속도를 40배까지 높일 수 있었습니다. Hadoop 클러스터에서 20시간이 걸리던 200GB의 압축 데이터에 대한 보고서가 이제 단 두 대의 Spark 머신을 사용해 30분 만에 실행됩니다. 또한, 압축 해제된 파일 전체가 아니라 고객의 필터와 일치하는 행과 열만 RDD에 저장했기 때문에 Spark 프로그램에는 96GB의 RAM만 필요했습니다.
```

Traffic Modeling Researchers in the Mobile Millen- nium project at Berkeley [18] parallelized a learning al-gorithm for inferring road traffic congestion from spo-radic automobile GPS measurements.
The source data were a 10,000 link road network for a metropolitan area,
as well as 600,000 samples of point-to-point trip timesfor GPS-equipped automobiles (travel times for each path may include multiple road links). 
Using a traffic model, the system can estimate the time it takes to travelacross individual road links. 
The researchers trained this model using an expectation maximization (EM) algo-rithm that repeats two map and reduceByKey steps itera-tively. The application scales nearly linearly from 20 to 80 nodes with 4 cores each, as shown in Figure 13(a).

```md
버클리의 모바일 밀레니엄 프로젝트[18]에 참여한 교통 모델링 연구원들은 차량의 GPS 측정값으로부터 도로 교통 혼잡을 추론하기 위한 학습 알고리즘을 병렬화했습니다.
소스 데이터는 대도시 지역의 10,000개 링크 도로 네트워크였습니다,
GPS가 장착된 자동차의 지점 간 이동 시간 샘플 60만 개(각 경로의 이동 시간에는 여러 도로 링크가 포함될 수 있음)입니다.
이 시스템은 교통 모델을 사용하여 개별 도로 링크를 이동하는 데 걸리는 시간을 추정할 수 있습니다.
연구원들은 두 개의 맵과 reduceByKey 단계를 반복적으로 반복하는 기대 최대화(EM) 알고리즘을 사용하여 이 모델을 학습시켰습니다. 이 애플리케이션은 그림 13(a)와 같이 코어가 각각 4개인 20개에서 80개 노드로 거의 선형적으로 확장됩니다.
```

![](Attached_file/스크린샷%202026-04-07%20오후%204.21.07.png)

Twitter Spam Classification The Monarch project at Berkeley [29] used Spark to identify link spam in Twitter messages. 
They implemented a logistic regression classi- fier on top of Spark similar to the example in Section 6.1,
but they used a distributed reduceByKey to sum the gradi-ent vectors in parallel. In Figure 13(b) we show the scal-ing results for training a classifier over a 50 GB subset
of the data: 250,000 URLs and 107 features/dimensions
related to the network and content properties of the pages at each URL. The scaling is not as close to linear due to a higher fixed communication cost per iteration.

```md
트위터 스팸 분류 버클리의 모나크 프로젝트[29]에서는 트위터 메시지에서 링크 스팸을 식별하기 위해 Spark를 사용했습니다.
이들은 6.1절의 예제와 유사한 로지스틱 회귀 분류를 Spark 위에 구현했습니다,
하지만 이들은 분산된 reduceByKey를 사용해 점진적 벡터를 병렬로 합산했습니다. 그림 13(b)는 50GB의 하위 집합에 대한 분류기 훈련의 확장 결과를 보여줍니다.
에 대한 확장 결과를 보여줍니다: 250,000개의 URL과 107개의 특징/차원
각 URL에 있는 페이지의 네트워크 및 콘텐츠 속성과 관련된 107개의 특징/차원을 포함합니다. 반복당 고정 통신 비용이 더 높기 때문에 스케일링이 선형에 가깝지 않습니다.
```

## 6.6 Interactive Data Mining

To demonstrate Spark’ ability to interactively query big datasets, we used it to analyze 1TB of Wikipedia page view logs (2 years of data). 
For this experiment, we used 100 m2.4xlarge EC2 instances with 8 cores and 68 GB
of RAM each. 
We ran queries to find total views of (1) all pages, (2) pages with titles exactly matching a given word, and (3) pages with titles partially matching a word.
Each query scanned the entire input data. 
Figure 14 shows the response times of the queries on the full dataset and half and one-tenth of the data. Even at 1 TB of data, queries on Spark took 5–7 seconds. 
This was more than an order of magnitude faster than work-ing with on-disk data; for example, querying the 1 TB file from disk took 170s. This illustrates that RDDs make
Spark a powerful tool for interactive data mining.

```md
빅데이터 세트를 대화형으로 쿼리하는 Spark의 기능을 입증하기 위해 1TB의 Wikipedia 페이지 뷰 로그(2년치 데이터)를 분석하는 데 사용했습니다.
이 실험에서는 각각 8코어와 68GB의 RAM을 갖춘 100m2.4배 큰 EC2 인스턴스 100개를 사용했습니다.
의 RAM을 갖춘 100개의 2.4배 크기 EC2 인스턴스를 사용했습니다.
(1) 모든 페이지, (2) 주어진 단어와 정확히 일치하는 제목의 페이지, (3) 단어와 부분적으로 일치하는 제목의 페이지의 총 조회수를 찾기 위해 쿼리를 실행했습니다.
각 쿼리는 전체 입력 데이터를 스캔했습니다.
그림 14는 전체 데이터 세트와 절반 및 1/10 데이터에 대한 쿼리의 응답 시간을 보여줍니다. 1TB의 데이터에서도 Spark의 쿼리는 5~7초가 걸렸습니다.
이는 온디스크 데이터로 작업하는 것보다 훨씬 더 빠른 속도였습니다.
```

## 7 Discussion

Although RDDs seem to offer a limited programming in- terface due to their immutable nature and coarse-grained transformations, we have found them suitable for a wide
class of applications. In particular, RDDs can express a surprising number of cluster programming models that have so far been proposed as separate frameworks, al-lowing users to compose these models in one program(e.g., run a MapReduce operation to build a graph, then run Pregel on it) and share data between them. 
In this sec-tion, we discuss which programming models RDDs canexpress and why they are so widely applicable (§7.1). 
In addition, we discuss another benefit of the lineage infor-mation in RDDs that we are pursuing, which is to facili-tate debugging across these models (§7.2).

```md
RDD는 불변의 특성과 거친 단위의 변환으로 인해 프로그래밍이 제한적인 것처럼 보이지만, 다양한 애플리케이션에 적합하다는 것을 알게 되었습니다.
클래스의 애플리케이션에 적합합니다. 특히, RDD는 지금까지 별도의 프레임워크로 제안되어 왔던 의외로 많은 수의 클러스터 프로그래밍 모델을 표현할 수 있어 사용자가 하나의 프로그램에서 이러한 모델을 구성하고(예: 그래프를 만들기 위해 MapReduce 작업을 실행한 다음 그 위에 Pregel을 실행) 데이터를 공유할 수 있게 해줍니다.
이 섹션에서는 RDD가 표현할 수 있는 프로그래밍 모델과 이 모델이 널리 적용되는 이유에 대해 설명합니다(§7.1).
또한 이러한 모델에서 디버깅을 용이하게 하는 RDD의 계보 정보의 또 다른 이점에 대해서도 설명합니다(§7.2).
```

