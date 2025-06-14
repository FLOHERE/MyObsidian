- 다익스트라 알고리즘 : 최단 경로 탐색 알고리즘의 한 종류로, 하나의 노드에서 다른 모든 노드까지의 최단 거리를 구하는 알고리즘이다.
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

public class Car{ // 간선(Edge) 를 나타내는 클래스 : 목표 노드와 가중치 조합
	static class Edge{
		String target;
		double weight;
		
		Edge(String target, double weight){
			this.target = target;
			this.weight = weight;
		}
	}
	// 단순 다익스트라 알고리즘 구현
	public static Map<String, Double> simpleDijkstra(Map<String, List<Edge>> graph, String start){
		//각 노드까지의 최단 거리를 저장 할 맵
		Map<String , Double> distances = new HashMap<>();
		
		//노드 방문 여부를 저장 할 맵
		Map<String, Boolean> visited = new HashMap<>();
		
		//초기화 : 모든 노드의 거리를 무한대로 설정 -> 방문 여부는 false
		for(String node : graph.keySet()){
			distances.put(node, Double.POSITIVE_INFINITY);
			visited.put(node, false);
		}
		
		// 시작 노드의 거리는 0으로 설정
		distances.put(start, 0.0);
		
		//그래프에 있는 노드 수만큼 반복
		for(int i = 0; i<graph.size(); i++){
			String currentNode = null;
			double minDistance = Double.POSITIVE_INFINITY;
			
			//방문 하지 않은 노드 중 현재까지의 거리가 가장 짧은 노드 선택
			for(String node : graph.keySet()){
				if(!visited.get(node) && distances.get(node) < minDistance){
					currentNode = node;
				}
			}
			
			//더이상 방문할 노드가 없으면 반복 종료
			if(currnentNode == null) break;
			
			//현재 노드를 방문 처리
			visited.put(currentNode, true);
			
			//인접 노드에 대해 거리 갱신 시도
			for(Edge edge : graph.get(currentNode)){
				double newDist = distances.get(currentNode) + edge.weight;
				if(newDist < distances.get(edge.target)){
					distances.put(edge.targe, newDist);
				}
			}
			
		}
		//최종 거리 맵 반환
		return distances;
	}
	public static void main(String[] args){
		//그래프 정의 : 각 노드에서 연결된 노드와 가중치(지연 시간 등)
		Map<String, List<Edge>> graph = new HashMap<>();
		graph.put("300.200.1.1", Arrays.asList(new Edge("182.30.1.333", 1)));
		graph.put("182.30.1.333", Arrays.asList(new Edge("218.154.215.1", 11.3)));
        graph.put("218.154.215.1", Arrays.asList(new Edge("112.174.50.142", 10.7)));
        graph.put("112.174.50.142", Arrays.asList(new Edge("112.174.16.62", 10)));
        graph.put("112.174.16.62", Arrays.asList(new Edge("218.55.246.31", 12.7)));
        graph.put("218.55.246.31", new ArrayList<>());  // 마지막 노드는 연결된 노드 없음
		
        // 시작 노드와 도착 노드 지정
        String start = "300.200.1.1";
        String end = "218.55.246.31";
		
        // 다익스트라 실행
        Map<String, Double> distances = simpleDijkstra(graph, start);
		
        // 결과 출력
        System.out.printf("%s → %s 최단 거리: %.2f ms%n", start, end, distances.get(end));
	}
}
//결과 : 300.200.1.1 → 218.55.246.31 최단 거리: 45.70 ms
```

