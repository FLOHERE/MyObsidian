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
- 최단거리 탐색 알고리즘 (다익스트라)
	- 네트워크의 최단거리 이동 코드 화

```java
package Mentoring_05_22; // 해당 클래스가 포함된 패키지 이름 지정

import java.util.*; // Java의 유틸리티 클래스들을 모두 import (예: Map, List, HashMap 등 사용 가능)

public class Network {
	
    // 그래프의 간선(Edge)을 표현하는 내부 클래스
    static class Edge {
        String target; // 연결된 대상 노드의 이름(IP 주소 형태로 표현됨)
        double weight; // 간선의 가중치 (예: 지연 시간 ms)
		
        // 생성자: 간선 객체를 생성할 때 대상 노드와 가중치를 설정
        Edge(String target, double weight) {
            this.target = target;
            this.weight = weight;
        }
    }

    // 다익스트라 알고리즘을 간단히 구현한 메소드
    public static Map<String, Double> simpleDijkstra(Map<String, List<Edge>> graph, String start) {
        // 각 노드까지의 최단 거리를 저장할 맵. 기본값은 무한대(INFINITY)
        Map<String, Double> distances = new HashMap<>();

        // 각 노드의 방문 여부를 저장하는 맵. 초기에는 전부 false로 설정
        Map<String, Boolean> visited = new HashMap<>();

        // 그래프에 있는 모든 노드에 대해 초기화 작업 수행
        for (String node : graph.keySet()) {
            distances.put(node, Double.POSITIVE_INFINITY); // 처음엔 거리를 무한대로 설정
            visited.put(node, false); // 아직 방문하지 않았음을 표시
        }

        // 시작 노드의 거리는 0으로 설정 (자기 자신까지 거리는 0이므로)
        distances.put(start, 0.0);

        // 그래프에 있는 노드 수만큼 반복하며 최소 거리 계산
        for (int i = 0; i < graph.size(); i++) {
            String currentNode = null; // 현재 선택된 노드를 저장할 변수
            double minDistance = Double.POSITIVE_INFINITY; // 현재 최소 거리를 저장할 변수

            // 아직 방문하지 않은 노드 중에서 최단 거리인 노드를 찾음
            for (String node : graph.keySet()) {
                if (!visited.get(node) && distances.get(node) < minDistance) {
                    minDistance = distances.get(node); // 최소 거리 갱신
                    currentNode = node; // 해당 노드를 현재 노드로 설정
                }
            }

            // 더 이상 방문할 수 있는 노드가 없으면 알고리즘 종료
            if (currentNode == null) break;

            // 현재 노드를 방문했다고 표시
            visited.put(currentNode, true);

            // 현재 노드에 연결된 모든 인접 노드들에 대해 거리 계산
            for (Edge edge : graph.get(currentNode)) {
                double newDist = distances.get(currentNode) + edge.weight; 
                // 시작 노드 → 현재 노드 + 현재 노드 → 인접 노드 거리
                
                // 새로운 거리가 기존 거리보다 작으면 최단 거리로 갱신
                if (newDist < distances.get(edge.target)) {
                    distances.put(edge.target, newDist);
                }
            }
        }

        // 계산된 최단 거리 맵 반환
        return distances;
    }

    public static void main(String[] args) {

        // 그래프 구성: 각 노드에서 어떤 노드로 얼마나의 거리(지연 시간)를 가지고 연결되어 있는지 정의
        Map<String, List<Edge>> graph = new HashMap<>();
        graph.put("300.200.1.1", Arrays.asList(new Edge("182.30.1.333", 1))); 
        // 노드 A → B (1ms)
        graph.put("182.30.1.333", Arrays.asList(new Edge("218.154.215.1", 11.3))); 
        // B → C (11.3ms)
        graph.put("218.154.215.1", Arrays.asList(new Edge("112.174.50.142", 10.7))); 
        // C → D (10.7ms)
        graph.put("112.174.50.142", Arrays.asList(new Edge("112.174.16.62", 10))); 
        // D → E (10ms)
        graph.put("112.174.16.62", Arrays.asList(new Edge("218.55.246.31", 12.7))); 
        // E → F (12.7ms)
        graph.put("218.55.246.31", new ArrayList<>()); 
        // 마지막 노드는 더 이상 연결된 노드 없음 (종착지)

        // 다익스트라 알고리즘 실행을 위한 시작 노드와 종료 노드 정의
        String start = "300.200.1.1"; // 출발지
        String end = "218.55.246.31"; // 도착지

        // 최단 거리 계산 실행
        Map<String, Double> distances = simpleDijkstra(graph, start);

        // 결과 출력: 시작 노드부터 도착 노드까지의 최단 거리 출력
        System.out.printf("%s → %s 최단 거리: %.2f ms%n", start, end, distances.get(end));
    }
}

```

- Map : key-value 로 이루어진 값
	- Map은 interface 이다
	- `Map<key 자료형, value 자료형> map이름 = new HashMap<>();`
- `HashMap<>();` : Map을 실체화 해주는 클래스(객체를 만드는 구조)
	- Map을 쓰기 위한 준비단계
- 예시

```java
Map<String, Integer> map = new HashMap<>();
//문자열을 키로 하고, 정수를 값으로 가지는 Map을 만들건데, 실제 구현은 HashMap으로 하겠다.
```

- `.put(k, v)` : Map에 데이터 넣기
	- key : IP 주소(노드)
	- value : Edge(노드들과의 거리 정보)
- `.get(k)` : Map에서 데이터 꺼내기

```java
graph.put("300.200.1.1", Arrays.asList(new Edge("182.30.1.333", 1)));
//노드 300.200.1.1에서 연결된 노드는 182.30.1.333이고,
//거리는 1이다 => 이 정보를 graph라는 Map에 저장
```

- ArrayList
	- 빈 리스트 만들고 값 넣기
```java
List<String> list = new ArrayList<>();
list.add("사과");//나중에 값 추가

List<String> list = Arrays.asList("사과"); //리스트 만들면서 바로 값 넣기도 가능
```

- 배열과 리스트의 차이점(참조)

| 항목        | 배열 (`Array`)                | 리스트 (`List`)                              |
| --------- | --------------------------- | ----------------------------------------- |
| **크기**    | 고정됨 → 생성할 때 크기 지정 필요        | 가변 → 필요하면 나중에 값 추가 가능                     |
| **선언 방식** | `int[] arr = new int[3];`   | `List<Integer> list = new ArrayList<>();` |
| **값 추가**  | 위치 지정해서 값 대입 → `arr[0] = 1` | `.add()`로 값 추가 → `list.add(1)`            |
| **초기화**   | 미리 크기를 정해두고 하나씩 대입          | 한꺼번에 넣거나 비워두고 나중에 추가                      |
| **유연성**   | 제한적 (길이 바꾸기 어렵고, 타입 고정)     | 유연함 (길이 자동 증가, 타입 지정 가능)                  |

- this 왜씀?
	- **헷갈림을 방지하고 오버라이딩이나 변수 이름 중복 상황에서 정확히 내가 원하는 걸 가리키게 하려고** 

```java
class Student {
    String name;
		
    Student(String name) {
        // 이때 둘 다 name이니까 혼란 생김
        this.name = name;  // this.name → 필드, name → 매개변수
    }
}
```

