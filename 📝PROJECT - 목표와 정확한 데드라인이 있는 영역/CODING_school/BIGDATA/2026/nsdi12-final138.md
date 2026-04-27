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

### 7.1 Expressing Existing Programming Models

RDDs can efficiently express a number of cluster pro-gramming models that have so far been proposed inde-pendently. By “efficiently,” we mean that not only can
RDDs be used to produce the same output as programs
written in these models, but that RDDs can also capture the optimizations that these frameworks perform, such as keeping specific data in memory, partitioning it to min-
imize communication, and recovering from failures efficiently. The models expressible using RDDs include:MapReduce: This model can be expressed using the flatMap and groupByKey operations in Spark, or reduce-ByKey if there is a combiner.
DryadLINQ: The DryadLINQ system provides a wider range of operators than MapReduce over the more general Dryad runtime, but these are all bulk operators
that correspond directly to RDD transformations available in Spark (map, groupByKey, join, etc).
SQL: Like DryadLINQ expressions, SQL queries perform data-parallel operations on sets of records.
Pregel: Google’s Pregel [22] is a specialized model for iterative graph applications that at first looks quite different from the set-oriented programming models in other
systems. In Pregel, a program runs as a series of coordinated “supersteps.” On each superstep, each vertex in the graph runs a user function that can update state associated with the vertex, change the graph topology, and send messages to other vertices for use in the next superstep.
This model can express many graph algorithms, including shortest paths, bipartite matching, and PageRank.
The key observation that lets us implement this model with RDDs is that Pregel applies the same user function to all the vertices on each iteration. Thus, we can store the
vertex states for each iteration in an RDD and perform a bulk transformation (flatMap) to apply this function and generate an RDD of messages. We can then join this
RDD with the vertex states to perform the message ex-change. Equally importantly, RDDs allow us to keep vertex states in memory like Pregel does, to minimize com-
munication by controlling their partitioning, and to support partial recovery on failures. We have implemented Pregel as a 200-line library on top of Spark and refer the
reader to [33] for more details.
Iterative MapReduce: Several recently proposed systems, including HaLoop [7] and Twister [11], provide aniterative MapReduce model where the user gives the system a series of MapReduce jobs to loop. The systems keep data partitioned consistently across iterations, and Twister can also keep it in memory. Both optimizations
are simple to express with RDDs, and we were able to implement HaLoop as a 200-line library using Spark.
Batched Stream Processing: Researchers have recently proposed several incremental processing systems for applications that periodically update a result with
new data [21, 15, 4]. For example, an application updating statistics about ad clicks every 15 minutes should be able to combine intermediate state from the previous 15-
minute window with data from new logs. These systems perform bulk operations similar to Dryad, but store application state in distributed filesystems. Placing the inter-
mediate state in RDDs would speed up their processing.
Explaining the Expressivity of RDDs Why are RDDs able to express these diverse programming models? 
The reason is that the restrictions on RDDs have little impact in many parallel applications. In particular, although RDDs can only be created through bulk transformations,many parallel programs naturally apply the same opera-
tion to many records, making them easy to express. Similarly, the immutability of RDDs is not an obstacle because one can create multiple RDDs to represent versions
of the same dataset. Indeed, many of today’s MapReduce
applications run over filesystems that do not allow up dates to files, such as HDFS.
One final question is why previous frameworks have not offered the same level of generality. 
We believe that this is because these systems explored specific problems
that MapReduce and Dryad do not handle well, such as iteration, without observing that the common cause of these problems was a lack of data sharing abstractions.

```md
### 7.1 기존 프로그래밍 모델의 표현

RDD는 지금까지 독립적으로 제안되어 온 여러 클러스터 프로그래밍 모델을 효율적으로 표현할 수 있습니다. 여기서 “효율적으로”라는 말은,
RDD를 사용하여 이러한 모델로 작성된 프로그램과
동일한 출력을 생성할 수 있을 뿐만 아니라, 특정 데이터를 메모리에 유지하거나, 통신량을 최소화하기 위해 데이터를 분할하거나,
오류로부터 효율적으로 복구하는 등 해당 프레임워크가 수행하는 최적화 기능까지 RDD가 포착할 수 있음을 의미합니다. RDD를 사용하여 표현할 수 있는 모델은 다음과 같습니다:MapReduce: 이 모델은 Spark의 flatMap 및 groupByKey 연산을 사용하여 표현할 수 있으며, 결합기(combiner)가 있는 경우 reduceByKey를 사용할 수도 있습니다.
DryadLINQ: DryadLINQ 시스템은 보다 일반적인 Dryad 런타임 위에서 MapReduce보다 더 광범위한 연산자를 제공하지만, 이들은 모두 Spark에서 사용할 수 있는 RDD 변환(map, groupByKey, join 등)과 직접적으로 대응하는 일괄 연산자입니다.
SQL: DryadLINQ 표현식과 마찬가지로, SQL 쿼리는 레코드 집합에 대해 데이터 병렬 연산을 수행합니다.
Pregel: Google의 Pregel[22]은 반복적 그래프 애플리케이션을 위한 특수한 모델로, 처음 보기에 다른 시스템의 집합 지향 프로그래밍 모델과는 상당히 다르게 보입니다.
Pregel에서 프로그램은 일련의 조정된 “슈퍼스텝(supersteps)”으로 실행됩니다. 각 슈퍼스텝에서 그래프의 각 정점은 해당 정점과 관련된 상태를 업데이트하고, 그래프 토폴로지를 변경하며, 다음 슈퍼스텝에서 사용하기 위해 다른 정점들에 메시지를 보낼 수 있는 사용자 함수를 실행합니다.
이 모델은 최단 경로, 이분 매칭, 페이지랭크(PageRank)를 포함한 많은 그래프 알고리즘을 표현할 수 있습니다.
RDD를 사용하여 이 모델을 구현할 수 있게 해주는 핵심적인 관찰점은, Pregel이 각 반복에서 모든 정점에 동일한 사용자 함수를 적용한다는 것입니다. 따라서 우리는
각 반복에 대한 정점 상태를 RDD에 저장하고, 일괄 변환(flatMap)을 수행하여 이 함수를 적용하고 메시지 RDD를 생성할 수 있습니다. 그런 다음 이
RDD를 정점 상태와 조인하여 메시지 교환을 수행할 수 있습니다. 마찬가지로 중요한 점은, RDD를 사용하면 Pregel과 마찬가지로 정점 상태를 메모리에 보관하고, 파티셔닝을 제어하여 통신을 최소화하며, 오류 발생 시 부분 복구를 지원할 수 있다는 것입니다. 우리는 Spark 위에서 200줄 분량의 라이브러리로 Pregel을 구현했으며,
자세한 내용은 [33]을 참조하시기 바랍니다.
반복적 MapReduce: HaLoop [7] 및 Twister [11]를 포함한 최근 제안된 여러 시스템은 사용자가 시스템에 반복할 일련의 MapReduce 작업을 제공하는 반복적 MapReduce 모델을 제공합니다. 이 시스템들은 반복 과정 전반에 걸쳐 데이터 파티셔닝을 일관되게 유지하며, Twister는 이를 메모리에 보관할 수도 있습니다. 두 가지 최적화 모두
RDD를 사용하여 간단히 표현할 수 있으며, 우리는 Spark를 사용하여 200줄 분량의 라이브러리로 HaLoop를 구현할 수 있었습니다.
배치 스트림 처리: 연구자들은 최근 새로운 데이터로 결과를 주기적으로 업데이트하는 애플리케이션을 위한 여러 증분 처리 시스템을 제안했습니다 [21, 15, 4]. 예를 들어, 15분마다 광고 클릭 통계를 업데이트하는 애플리케이션은 지난 15분
기간의 중간 상태를 새로운 로그 데이터와 결합할 수 있어야 합니다. 이러한 시스템은 Dryad와 유사한 대량 연산을 수행하지만, 애플리케이션 상태를 분산 파일 시스템에 저장합니다. 중간
상태를 RDD에 저장하면 처리 속도가 빨라질 것입니다.
RDD의 표현력 설명: RDD는 왜 이러한 다양한 프로그래밍 모델을 표현할 수 있을까요? 
그 이유는 RDD에 대한 제약 조건이 많은 병렬 애플리케이션에서 거의 영향을 미치지 않기 때문이다. 특히, RDD는 일괄 변환을 통해서만 생성될 수 있지만, 많은 병렬 프로그램은 자연스럽게 동일한 연산을
여러 레코드에 적용하므로 이를 표현하기 쉽다. 마찬가지로, RDD의 불변성은 동일한 데이터 세트의 여러 버전을 나타내기 위해 여러 RDD를 생성할 수 있으므로
장애물이 되지 않는다. 실제로 오늘날의 많은 MapReduce
애플리케이션은 HDFS와 같이 파일 업데이트를 허용하지 않는 파일 시스템 위에서 실행됩니다.
마지막으로, 왜 기존의 프레임워크들은 이와 같은 수준의 일반성을 제공하지 못했는지 의문이 듭니다.
우리는 이러한 시스템들이 반복(iteration)과 같이 MapReduce와 Dryad가 잘 처리하지 못하는 특정 문제들을 탐구했을 뿐,
이러한 문제들의 공통된 원인이 데이터 공유 추상화의 부재라는 사실을 간과했기 때문이라고 생각합니다.
```

### 7.2 Leveraging RDDs for Debugging

While we initially designed RDDs to be deterministically
recomputable for fault tolerance, this property also facil-
itates debugging. In particular, by logging the lineage of
RDDs created during a job, one can (1) reconstruct these
RDDs later and let the user query them interactively and
(2) re-run any task from the job in a single-process de-
bugger, by recomputing the RDD partitions it depends
on. Unlike traditional replay debuggers for general dis-
tributed systems [13], which must capture or infer the
order of events across multiple nodes, this approach adds
virtually zero recording overhead because only the RDD
lineage graph needs to be logged.9 We are currently de-
veloping a Spark debugger based on these ideas [33].

```md
7.2 디버깅을 위한 RDD 활용
RDD는 원래 내결함성을 위해 결정론적으로
재계산 가능하도록 설계되었지만, 이러한 특성은
디버깅에도 도움이 됩니다. 특히, 작업 중에 생성된 RDD의 계보를
로깅함으로써, (1) 나중에 이러한 RDD를 재구성하여
사용자가 대화형으로 쿼리할 수 있게 하고,
(2) 해당 작업의 모든 태스크를 단일 프로세스 디버거에서
의존하는 RDD 파티션을 재계산하여
다시 실행할 수 있습니다. 여러 노드에 걸친 이벤트 순서를 포착하거나 추론해야 하는
일반적인 분산 시스템을 위한 기존의 리플레이 디버거[13]와 달리,
이 접근 방식은 RDD 계보 그래프만 로깅하면 되므로
기록 오버헤드가 사실상 제로에 가깝습니다.9 우리는 현재 이러한
아이디어를 바탕으로 Spark 디버거를 개발 중입니다[33].
```