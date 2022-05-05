# **정렬 알고리즘 분석**(*Sort Algorithm Analysis*)

## ※ Note !
- **정렬되지 않은 수**들이 일렬로 나열되어 있다고 가정하고, 정렬은 기본적으로 **오름차순**으로 배치하는 것으로 하고 정리했다.

## 버블 정렬(Bubble Sort)
- 왼쪽에서부터 오른쪽으로 크기 비교를 하는데 가장 왼쪽에 위치한 수와 인접한 수를 비교해가면서 큰 수를 오른쪽으로, 작은 수를 왼쪽으로 이동시키는 정렬이다.
- 정렬이 되어있는 상태라면 모르겠지만, 제대로 정렬되지 않은 상황에서는 정렬 소요 시간이 오래 걸려 비효율적인 정렬 알고리즘이다.
- 다음의 예시를 통해 버블 정렬의 이해를 확실히 하고자 한다.
```
임의의 수 7개를 입력받았다고 하자.
랜덤으로 7개 수를 입력받아도 무방함.

8 0 9 7 4 1 5
1st: 0 8 7 4 1 5 9
(0 8 9 7 4 1 5 -> 0 8 7 9 4 1 5 -> 0 8 7 4 1 5 9)

2nd : 0 7 4 1 5 8 9
(0 8 7 4 1 5 9 -> 0 7 8 4 1 5 9 -> 0 7 4 8 1 5 9 -> 0 7 4 1 8 5 9 -> 0 7 4 1 5 8 9)

3rd : 0 4 1 5 7 8 9
(0 7 4 1 5 8 9 -> 0 4 7 1 5 8 9 -> 0 4 1 7 5 8 9 -> 0 4 1 5 7 8 9)

4th : 0 1 4 5 7 8 9
(0 4 1 5 7 8 9 -> 0 1 4 5 7 8 9)

버블정렬 완료
```

### ▼ 성능 분석
- 보통 성능 분석은 해당 알고리즘이 수행되는데 걸리는 소요 시간인, 시간복잡도로 판별한다. (공간복잡도도 있지만 이번 글에선 시간 복잡도로만 알고리즘의 성능분석 관련 내용을 다뤄보려 한다.)
- 버블 정렬은 정말 버블처럼 인접한 수를 하나하나 비교해가면서 수를 정렬하므로, 모든 수를 교환할 수도 있다.
- 심지어, 수를 정렬하는 과정에서 제 자리에 찾아간 수도 버블 정렬 과정 때문에 옮겨질 수도 있다.
- 구현만 쉬울 뿐, 매우 비효율적인 알고리즘이라 잘 사용하지 않는다.
- 최상의 경우, 평균의 경우, 최악의 경우를 따져봤을 때 모두 같은 소요 시간이 걸리므로 시간 복잡도는 다음과 같다.
> 비교 횟수 : n-1, n-2, n-3, ∙∙∙, 2, 1 = n(n-1) / 2
> 교환 횟수 > 최악의 상황에서 교환하는데 최소 3번의 이동이 필요하므로 : 3(n-1) / 2 이다. 정렬이 필요없는 최선의 상황에서는 교환이 일어나지 않는다.
- <버블 정렬 시간복잡도> <br/>
최선, 평균, 최악 모두 *O(n<sup>2</sup>)* 로 동일함.

___
## 선택 정렬(Selection Sort)
- 수들이 있을 때, 그 중 가장 작은 수를 먼저 찾아서 가장 왼쪽에 있는 수와 교환한다.
- 대신, 교환이 이루어졌다면 다음 index로 이동하여 교체해야 한다.
- 다음의 예시로 이해를 돕고자 한다.

```
임의의 수 7개를 입력받았다고 하자.
버블 정렬과 같은 수를 입력받았을 때 선택 정렬은 다음과 같다.

8 0 9 7 4 1 5

step 1
0이 가장 작으므로 8과 교환
0 8 9 7 4 1 5

step 2
0을 제외하고, 최소값 1을 8과 교환
0 1 9 7 4 8 5

step 3
0,1을 제외한 4를 9와 교환
0 1 4 7 9 8 5

step 4
0,1,4를 제외한 5를 7과 교환
0 1 4 5 9 8 7

step 5
0,1,4,5를 제외한 7을 9와 교환
0 1 4 5 7 8 9

선택정렬 완료
```
### ▼ 성능 분석
- <선택 정렬 시간복잡도> <br/>
최선, 평균, 최악 모두 *O(n<sup>2</sup>)* 로 동일함.
___
## 삽입 정렬(Insertion Sort)
- 여러 숫자 입력된 배열에서, 정렬 되지 않은 부분과 정렬된 부분을 나눠서 정렬을 진행한다.
- 정렬된 부분은 그냥 놔두면 되지만, 정렬되지 않은 부분은 정렬을 해줘야 하므로 정렬되지 않은 부분에서 특정 key값을 하나 선택해준다. 되도록이면 왼쪽에 위치한 값으로 선택한다.
- key 값을 왼쪽에 위치한 값과 비교 후 자리를 교환할 필요가 있다면, key 값에 해당하는 index를 잠시 temp에 복제해두고, 왼쪽에 위치한 값을 key index에 옮긴다. 그리고 key index에 해당하는 값을 삽입한다.
- 이해를 돕고자 다음의 예시를 들어본다.
```
이번에도 위에서 사용한 수 배열을 사용하고자 한다.

8 0 9 7 4 1 5

시작에 앞서, 이 숫자 배열은 정말 랜덤으로 배치가 되어 있어서 정렬된 부분을 어디라고 설정하기 애매한 배열이다. 따라서 바로 선택 정렬에 들어가보자.

step 1
8이 아닌 0을 key값으로 정하고, 비교 후 자리를 교환
0 8 9 7 4 1 5

step 2
key값을 이번엔 9로 설정하는데, 8과 바꿀 수 없고 그 앞의 0과도 바꿀 수 없으므로 skip!
0 8 9 7 4 1 5

step 3
key값을 7로 설정 후, 자리 교환
0 8 7 9 4 1 5
7과 8을 비교하고 자리를 또 교환
0 7 8 9 4 1 5

step 4
key값을 4로 설정하고, 왼쪽으로 이동하면서 4보다 큰 수가 나오면 계속 자리를 교환
0 7 8 4 9 1 5

0 7 4 8 9 1 5

0 4 7 8 9 1 5

step 5
key값을 1로 설정하고, 왼쪽으로 이동하면서 1보다 큰 수가 나오면 계속 자리를 교환
0 4 7 8 1 9 5

0 4 7 1 8 9 5

0 4 1 7 8 9 5

0 1 4 7 8 9 5

step 6
key값을 5로 설정하고, 왼쪽으로 이동하면서 5보다 큰 수가 나오면 계속 자리를 교환
0 1 4 7 8 5 9

0 1 4 7 5 8 9

0 1 4 5 7 8 9

삽입 정렬 완료
```
### ▼ 성능 분석
- <버블 정렬 시간복잡도> <br/>
최선, 평균, 최악 모두 *O(n<sup>2</sup>)* 로 동일함.
___
## 쉘 정렬(Shell Sort)
- 쉘 정렬은 버블 정렬이나 삽입 정렬의 단점을 보완하기 위해 고안되었고 삽입정렬을 일부 사용하는 정렬 알고리즘이다.
- 정렬되지 않은 수들이 있을 때, h번씩 끊어 부분 리스트를 만든다. 이때 h를 **간격**이라고 하자.
- 이 과정을 반복하면 h가 계속 바뀔텐데 이 h가 1이 될 때 까지 반복하고 정렬이 되는지 확인한다.
- 쉽게 정리하면, 삽입 정렬과 비슷하지만 배열이 되지 않은 랜덤상태에서 바로 배열하는 게 아니라 효율을 위해 최대한 배열이 정렬되게 만든 다음 정렬하는 것을 쉘 정렬이라 한다.
- 다음 예시를 통해 이해해보자.
```
임의로 입력받은 다음의 수 배열이 있다고 할 때, 쉘 정렬을 해보자.

19 1 10 17 7 3 21 13 5 11 8

> Step 1
처음 간격을 5로 설정 후 정렬
19 1 10 17 7 3 21 13 5 11 8

한 눈에 보기 쉽게 표로 나타냈다. 
Group1 | 19        3           8
Group2 |   1         21  
Group3 |    10         13
Group4 |      17          5
Group5 |        7           11

여기서 Group 1부터 Group 5까지 삽입 정렬을 통해 정렬이 되면 다음과 같다.
Group1 | 3        8           19
Group2 |   1         21  
Group3 |    10         13
Group4 |      5          17
Group5 |        7           11

3 1 10 5 7 8 21 13 17 11 19

> Step 2
이번에는 간격을 3으로 줄여서 다시 진행해보자.
간격을 3으로 설정하므로 Group은 1부터 3까지 분리해서 쓰면 다음과 같다.
Group1 | 3     5     21       11
Group2 |   1     7      13       19
Group3 |    10     8       17

step 1과 마찬가지로 Group1 부터 Group3까지 각각 삽입 정렬을 통해 정렬 후 나타내면 다음과 같다.
Group1 | 3     5     11       21
Group2 |   1     7      13       19
Group3 |    8     10       17

3 1 8 5 7 10 11 13 17 21 19

> Step 3
간격을 이제 1이나 2로 설정할 수 있지만 이번엔 2로 해서 정렬해보겠다.
Group1 | 3   8   7    11    17  19
Group2 |  1   5    10   13    21 

위의 Step처럼 선택 정렬을 통해 Group1, 2를 정렬 후 나타내면 다음과 같다.
Group1 | 3   7   8   11   17   19
Group2 |   1   5   10   13   21

3 1 7 5 8 10 11 13 17 21 19

> Step 4
간격을 1로 설정하고 정렬하면 정렬이 완료된다. Step 3에서 간격을 1로 설정하고 마무리해도 무방하다.
1 3 5 7 8 10 11 13 17 19 21
```
### ▼ 성능 분석
- <쉘 정렬 시간복잡도> <br/>
최선, 평균, 최악 모두 *O(n<sup>1.25</sup>)* 로 동일함. 하지만 상황에 따라 최선은 *O(n)*, 평균은 *O(n<sup>1.5</sup>)*, 최악의 경우는 *O(n<sup>2</sup>)* 인 경우도 있다.
<br/>

___
## 힙 정렬(Heap Sort) - Priority Queue
- 힙 정렬은 우선순위 큐(Priority Queue)를 활용하여 구현한 알고리즘 중 하나이다.
- Priority Queue에서는 **삽입, 삭제** 과정이 자유롭기에, 힙 정렬에서도 이것을 이용해야 한다.
- 힙 정렬을 그림으로 구현하게 되면 **완전 이진 트리** 형식으로 구현되는데, 구현 방법으로는 **Max heap(부모노드 >= 자식노드) or Min heap(부모노드 <= 자식노드)** 두 가지가 있다.
- 앞의 Note! 에서 오름차순으로 정렬한다고 미리 밝혔으므로, Min heap을 기반으로 정리하는게 맞지만, 힙 정렬에서만은 Min heap과 Max heap 정렬을 간단하게 다시 정리해보려고 한다.
```
다음의 트리 구조를 가진 힙 노드가 있다고 하자.
             100
        70         80
     60    50    40  20
   10  30

트리는 항상 1번부터 시작이기에 배열로 나타낼 때도 0번 index는 null값으로 지정해두고 시작한다.
따라서 위의 트리를 배열로 나타내면 다음과 같다.
________________________________
|  |100|70|80|60|50|40|20|10|30|
________________________________

Max heap을 통해 내림차순으로 나타내면 다음과 같이 정렬된다.
             100
        80         70
     60    50    40  30
   10  20

> 100 80 70 60 50 40 30 20 10

Min heap을 통해 오름차순으로 나타내면 다음과 같이 정렬된다.
             10
        20         30
     40    50    60  70
   80  100

> 10 20 30 40 50 60 70 80 100
```
### ▼ 성능 분석
- <힙 정렬 시간복잡도>
최선, 평균, 최악 모두 *O(nlogn)* 로 동일함.<br/>
___
## 퀵 정렬(Quick Sort)
- 이름에서 알 수 있듯이 가장 빠른 속도를 자랑하는 퀵 정렬이다.
- 정렬되지 않은 수 중에서 가장 왼쪽에 있는 수를 고르는데 그 수를 Pivot이라고 하자. (Pivot은 어떤 것을 고르든 상관 X)
- Pivot보다 작은 수를 왼쪽, 큰 수를 오른쪽으로 이동시키며 정렬을 한다.
```
숫자 7개를 입력받았다고 하자.
8 0 9 7 4 1 5

> Step 1
8을 pivot으로 선택하면, 8보다 작은 수는 8의 왼쪽으로 옮겨지고 8보다 큰 수는 오른쪽으로 옮겨진다.

 왼쪽에서 오른쪽으로 오면서(이걸 Low라고 칭하자) 8보다 작은 수를 찾고, 오른쪽에서 왼쪽으로 오면서(이걸 High라고 칭하자) 8보다 큰 수를 찾는다. 찾으면 그 수를 교환한다.
8 0 9 7 4 1 5 -> 8 0 5 7 4 1 9

여기서 1과 8을 바꿔주면 다음과 같다.
1 0 5 7 4 8 9
pivot을 기준으로 왼쪽엔 8보다 작은 수, 오른 쪽엔 8보다 큰 수가 정렬되었다.

> Step 2
8을 기준으로 오른쪽 부분은 정렬이 완료되었으므로 왼쪽 부분만 정렬을 다시 한다.
1을 새로운 pivot으로 삼고, 정렬을 다시 해본다.
1 0 5 7 4 -> 1 0 4 5 7 -> 0 1 4 5 7

왼쪽 부분이 정렬이 완료 되었으므로 기존의 값들과 합쳐서 최종으로 오름차순으로 정렬된 값을 확인한다.
0 1 4 5 7 8 9

※ Low와 High가 엇갈리면 순환을 멈추고, pivot값과 high값을 바꿔준다!
```
### ▼ 성능 분석
- <퀵 정렬 시간복잡도> <br/>
최선, 평균 : *O(nlogn)* <br/>
최악 : *O(n^2)*
___

### 코드 구현(정렬 수행 시간)
```java
1-1) 정렬 수행시간 코드 (힙 제외) - 정렬되어 있는 경우
package Sort;
import java.util.Scanner;

public class SortTest extends Thread {
    public static void main(String[] args) {
        System.out.print("input 크기 입력 : ");
        Scanner sc = new Scanner(System.in);
        int snum = sc.nextInt();
 
        int[] num = new int[snum];
 
        System.out.println("배열 생성 시작!");
        for (int i = 0; i < snum; i++) {
            // num[i] = (int) (Math.random() * snum);
            // 랜덤 배열이 아닌 정상적으로 배열된 상황이므로 이 부분을 지워준다.
        }
        System.out.println("배열 생성완료");
        System.out.println();
 
        Bubble bubble = new Bubble(num);
        Selection selection = new Selection(num);
        Insertion insertion = new Insertion(num);
        Shell shell = new Shell(num);
        // Quick quick = new Quick(num);
         
        bubble.start(); 
        selection.start(); 
        insertion.start(); 
        shell.start();
        // quick.start();
    }
    /*
    public static void swap(int[] a, int pl, int pr) {
    	int b = a[pl];
    	a[pl] = a[pr];
    	a[pr] = b;
    }
    
    public static void quickSort(int[] a, int left, int right) {
    	int pl = left;
    	int pr = right;
    	int pivot = a[ (a[left] + a[right]) / 2];
    	
    	do {
    		while(a[pl] < pivot)
    			pl++;
    		while(a[pr]>pivot)
    			pr--;
    		if(pl <= pr) {
    			swap(a, pl, pr);
    			pl++;
    			pr--;
    		}
    	} while(pl <= pr);
    	if(left < pr)
    		quickSort(a, left, pr);
    	else if(pl < right)
    		quickSort(a, pl, right);
    }
 */
}
 
class Bubble extends Thread {
    int[] a;
    int b;
 
    Bubble(int[] array) {
        a = array;
    }
 
    public void run() {
        System.out.println("버블 정렬 시작");
        long start = System.currentTimeMillis();
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a.length - i - 1; j++) {
                if (a[j] > a[j + 1]) {
                    b = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = b;
                }
            }
        }
        long endTime = System.currentTimeMillis();

        System.out.println("버블정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
    }
}
 
class Selection extends Thread {
    int[] a;
    int b;
 
    Selection(int[] array) {
        a = array;
    }
 
    public void run() {
        System.out.println("선택 정렬 시작");
        long start = System.currentTimeMillis();
        for (int i = 0; i < a.length - 1; i++) {
            for (int j = i + 1; j < a.length; j++) {
                if (a[i] > a[j]) {
                    b = a[j];
                    a[j] = a[i];
                    a[i] = b;
                }
            }
        }
        long endTime = System.currentTimeMillis();

        System.out.println("선택정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
    }
}
 
class Insertion extends Thread {
    int[] a;
    int b, j;
 
    Insertion(int[] array) {
        a = array;
    }
 
    public void run() {
        System.out.println("삽입정렬 시작!");
        long start = System.currentTimeMillis();
        for (int i = 1; i < a.length; i++) {
            b = a[i];
            for (j = i - 1; j >= 0 && a[j] > b; j--) {
                a[j + 1] = a[j];
            }
            a[j + 1] = b;
        }
        long endTime = System.currentTimeMillis();

        System.out.println("삽입정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
    }
}

class Shell extends Thread {
	int[] a;
	int b;
	
	Shell(int[] array) {
		a = array;
	}
	
	public void run() {
		System.out.println("쉘 정렬 시작");
		long start = System.currentTimeMillis();
		for(int h  = a.length/2; h > 0; h /= 2) {
			for(int i = h; i < a.length; i++) {
				int j;
				int b = a[i];
				
				for(j = i - h; j >= 0 && a[j] > b; j -= h) {
					a[j + h] = a[j];
				}
				a[j + h] = b;
			}
		}
		long endTime = System.currentTimeMillis();
		System.out.println("쉘 정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
	}
}

/*
class Quick extends Thread {
	int[] a;

	Quick(int[] array) {
		a = array;
	}
	public void swap(int[] a, int pl, int pr) {
    	int b = a[pl];
    	a[pl] = a[pr];
    	a[pr] = b;
    }
    
    public void quickSort(int[] a, int left, int right) {
    	int pl = left;
    	int pr = right;
    	int pivot = a[ (a[left] + a[right]) / 2];
    	
    	do {
    		while(a[pl] < pivot)
    			pl++;
    		while(a[pr]>pivot)
    			pr--;
    		if(pl <= pr) {
    			swap(a, pl, pr);
    			pl++;
    			pr--;
    		}
    	} while(pl <= pr);
    	
    	if(left < pr)
    		quickSort(a, left, pr);
    	
    	if(pl < right)
    		quickSort(a, pl, right);
    }
	
	public void run() {
		System.out.println("퀵 정렬 시작");
		long start = System.currentTimeMillis();
		quickSort(a, 0, a.length - 1);
		
		long endTime = System.currentTimeMillis();
		System.out.println("퀵 정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
	}
}
*/



1-2) 정렬 수행시간 코드 (힙 제외) - 랜덤 배열
package Sort;
import java.util.Scanner;

public class SortTest extends Thread {
    public static void main(String[] args) {
        System.out.print("배열크기를 정해주세요 : ");
        Scanner sc = new Scanner(System.in);
        int snum = sc.nextInt();
 
        int[] num = new int[snum];
 
        System.out.println("랜덤배열 생성시작");
        for (int i = 0; i < snum; i++) {
            num[i] = (int) (Math.random() * snum);

        }
        System.out.println("랜덤배열 생성완료");
        System.out.println();
 
        Bubble bubble = new Bubble(num);
        Selection selection = new Selection(num);
        Insertion insertion = new Insertion(num);
        Shell shell = new Shell(num);
        // Quick quick = new Quick(num);
         
        bubble.start(); 
        selection.start(); 
        insertion.start(); 
        shell.start();
        // quick.start();
    }
    /*
    public static void swap(int[] a, int pl, int pr) {
    	int b = a[pl];
    	a[pl] = a[pr];
    	a[pr] = b;
    }
    
    public static void quickSort(int[] a, int left, int right) {
    	int pl = left;
    	int pr = right;
    	int pivot = a[ (a[left] + a[right]) / 2];
    	
    	do {
    		while(a[pl] < pivot)
    			pl++;
    		while(a[pr]>pivot)
    			pr--;
    		if(pl <= pr) {
    			swap(a, pl, pr);
    			pl++;
    			pr--;
    		}
    	} while(pl <= pr);
    	if(left < pr)
    		quickSort(a, left, pr);
    	else if(pl < right)
    		quickSort(a, pl, right);
    }
 */
}
 
class Bubble extends Thread {
    int[] a;
    int b;
 
    Bubble(int[] array) {
        a = array;
    }
 
    public void run() {
        System.out.println("버블정렬 시작");
        long start = System.currentTimeMillis();
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a.length - i - 1; j++) {
                if (a[j] > a[j + 1]) {
                    b = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = b;
                }
            }
        }
        long endTime = System.currentTimeMillis();

        System.out.println("버블정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
    }
}
 
class Selection extends Thread {
    int[] a;
    int b;
 
    Selection(int[] array) {
        a = array;
    }
 
    public void run() {
        System.out.println("선택정렬 시작!");
        long start = System.currentTimeMillis();
        for (int i = 0; i < a.length - 1; i++) {
            for (int j = i + 1; j < a.length; j++) {
                if (a[i] > a[j]) {
                    b = a[j];
                    a[j] = a[i];
                    a[i] = b;
                }
            }
        }
        long endTime = System.currentTimeMillis();

        System.out.println("선택정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
    }
}
 
class Insertion extends Thread {
    int[] a;
    int b, j;
 
    Insertion(int[] array) {
        a = array;
    }
 
    public void run() {
        System.out.println("삽입정렬 시작!");
        long start = System.currentTimeMillis();
        for (int i = 1; i < a.length; i++) {
            b = a[i];
            for (j = i - 1; j >= 0 && a[j] > b; j--) {
                a[j + 1] = a[j];
            }
            a[j + 1] = b;
        }
        long endTime = System.currentTimeMillis();

        System.out.println("삽입정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
    }
}

class Shell extends Thread {
	int[] a;
	int b;
	
	Shell(int[] array) {
		a = array;
	}
	
	public void run() {
		System.out.println("쉘 정렬 시작");
		long start = System.currentTimeMillis();
		for(int h  = a.length/2; h > 0; h /= 2) {
			for(int i = h; i < a.length; i++) {
				int j;
				int b = a[i];
				
				for(j = i - h; j >= 0 && a[j] > b; j -= h) {
					a[j + h] = a[j];
				}
				a[j + h] = b;
			}
		}
		long endTime = System.currentTimeMillis();
		System.out.println("쉘 정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
	}
}

/*
class Quick extends Thread {
	int[] a;

	Quick(int[] array) {
		a = array;
	}
	public void swap(int[] a, int pl, int pr) {
    	int b = a[pl];
    	a[pl] = a[pr];
    	a[pr] = b;
    }
    
    public void quickSort(int[] a, int left, int right) {
    	int pl = left;
    	int pr = right;
    	int pivot = a[ (a[left] + a[right]) / 2];
    	
    	do {
    		while(a[pl] < pivot)
    			pl++;
    		while(a[pr]>pivot)
    			pr--;
    		if(pl <= pr) {
    			swap(a, pl, pr);
    			pl++;
    			pr--;
    		}
    	} while(pl <= pr);
    	
    	if(left < pr)
    		quickSort(a, left, pr);
    	
    	if(pl < right)
    		quickSort(a, pl, right);
    }
	
	public void run() {
		System.out.println("퀵 정렬 시작");
		long start = System.currentTimeMillis();
		quickSort(a, 0, a.length - 1);
		
		long endTime = System.currentTimeMillis();
		System.out.println("퀵 정렬 끝. 수행시간 : " + (endTime - start) / 1000.0f + "초");
	}
}
*/
1-3) 정렬 수행시간 코드 (힙 제외) - 역순으로 배열되어 있는 경우

2) 힙 정렬 코드 구현
package Sort;
public class HeapSort {
	int [] heapsort(int[] data) {
		int len = data.length;
		
		for(int l = len/2; l > 0; l--) {
			downHeap(data, l, len);
		}
		
		do {
			int temp = data[0];
			data[0] = data[len-1];
			data[len-1] = temp;
			len = len-1;
			downHeap(data, 1, len);
		} while(len > 1);
		
		return data;
	}
	
	private void downHeap(int[] data, int l, int len) {
		int right;
		int temp = data[l - 1];
		while(l <= len/2) { 
			right = 2 * l; 
			if((right < len) && (data[right - 1] < data[right])) { 
				right++;
			}
			if(temp >= data[right - 1]) { 
				break;
			}
			data[l - 1] = data[right - 1];
			l = right;
		}
		data[l - 1] = temp;
	}
	public static void main(String[] args) {
		int [] data = {100, 70, 80, 60, 50, 40, 20, 10, 30};
		System.out.println("> 힙 정렬 전");
		
		for(int i = 0; i < data.length; i++) {
			System.out.print(data[i]+" ");
		}
		
		System.out.println();
		HeapSort test = new HeapSort();
		test.heapsort(data);
		
		System.out.println("> 힙 정렬 후");
		for(int i=0; i < data.length; i++) {
			System.out.print(data[i]+" ");
		}
	}
}

```
-  **버블정렬, 선택정렬, 삽입정렬 쉘정렬, 퀵 정렬** 까지 구현했으나 **퀵 정렬** 은 계속 **overflow** 오류가 발생하여 주석처리 했다. 
- 힙 정렬 알고리즘의 수행시간을 코드로 구현하기가 생각보다 어려워 힙 정렬 코드 구현에 집중했고 관련된 자료를 찾아서 수행 시간에 대한 개념을 이해하는 방법을 택했다. 위의 힙 정렬 코드는 위의 힙 정렬 파트에서 DownHeap을 이용하여 오름차순으로 정리한 코드이다.

