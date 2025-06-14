- 다익스트라 알고리즘 : 최단 경로 탐색 알고리즘의 한 종류
	- ex_) 네트워크나 그래프에서 가장 효율적인 경로 찾기
## 1. 목적
- 최단 경로 탐색
### 1. 최단 경로 탐색
- 한 지점 -> 다른 지점 까지의 최단 경로 찾기
- 한 지점 -> 다른 모든 지점까지의 최단 경로 찾기
- 모든 지점 -> 다른 모든 지점까지의 최단 경로 찾기
## 2. 유형
### 1. 그리디(탐욕기법) 알고리즘에 기반
- 노드를 탐색, 매 상황에서 비용이 가장 작은 노드를 선택(해당 과정 반복) -> 최적의 해 찾음
	- 노드 : 각 지점
	- 간선 : 노드들을 연결하는 통로
## 3. 동작 과정

### 1. 특징
- 큐 우선순위 
- 배열 구조(직관적으로 보는 방법)
- 출발 지점 -> 모든 노드까지의 최단 경로
	1. 출발 노드 설정
	2. 최단 거리 테이블 초기화 
		- 최단 거리 테이블 : 각 노드에 대한 현재까지의 최단 거리 정보를 가지도록 함
	3. 아직 방문하지 않은 노드 중 최단 거리가 가장 짧은 노드를 선택
	4. 선택된 노드를 통해 인접한 노드들의 최단 거리 갱신 => 해당 과정 반복

>[!note] 지연시간 계산법
>세개의 값 중 평균값 구하거나 최소값 사용
>ex_) 1ms, 1ms, 1ms 일때 (1+1+1)/3

## 4. 활용 분야
- 네트워크
	- 기본적으로 최적 해를 찾아서 노드(라우터)간을 이동, 경로를 저장
	- but!! 트래픽이 가득 차는 등의 문제가 생기면 다른 노드로 우회함
- 네트워크 정보 수집 명령어 : `traceroute www.~~~~`

>[!note] 네트워크 경로 특징
>네트워크는 한번 수집한 테이블은 저장 해두고, 출발지와 목적지가 같으면 같은 경로를 가르킴.
>네트워크 경로는 변수가 일어나지 않는 이상 변하지 않음

- RTT(Round Trip Time) : 출발 지점 -> 도착지점 데이터 패킷이 전송 되었다가 다시 돌아오는 시간

## 5. 응용(교수님 논문)
- 논문 주제 : 동일한 URL 정보를 비교하는 앱 프로그램
	- 클라이언트에서 능동적인 피싱 사이트 탐지를 위한 IP 탐지 모델(트레이스 정보는 PC만 해당)
	- 미러링 피싱사이트 탐지를 위한 IP 수집 기반 모델
- 다익스트라 알고리즘 사용
	1. 출발지
	2. 목적지 정보 확인
	3. 클라이언트가 직접 사이트에 대한 목적지 정보를 수집할 수 있게 하고 비교할수 있는 프로그램을 만들수 있다.
	4. Url = Url(목적지 정보가 다르게 나와 확인 가능 => 피싱사이트 정보 확인 가능)

# 코드
```java
package Mentoring_05_22;
import java.util.*;

public class Car{
	static class Edge{
		String target;
		double weight;
		
		Edge(String target, double weight){
			this.target = target;
			this.weight = weight;
		}
	}
	public static Map<String, Double> simpleDijkstra(Map<String, List<Edge>> graph, String start){
		Map<String , Double> distances = new HashMap<>();
		
		Map<String, Boolean> visited = new HashMap<>();
		
		for(String node : graph.keySet()){
			distances.put(node, Double.POSITIVE_INFINITY);
			visited.put(node, false);
		}
		
		distances.put(start, 0.0);
		
		for(int i = 0; i<graph.size(); i++){
			String currentNode = null;
			double minDistance = Double.POSITIVE_INFINITY;
			
			for(String node : graph.keySet()){
				if(!visited.get(node) && distances.get(node) < minDistance){
					currentNode = node;
				}
			}
			if(currnentNode == null) break;
			
			visited.put(currentNode, true);
			
			for(Edge edge : graph.get(currentNode)){
				
			}
		}
	}
}
```