```java
 //최댓값을 배열에서 찾기(arr-> stream으로 변환한다음 int로 가져옴!
        // range의 Intstream을 만들어서 filter를 한다(최댓값인 인덱스만)
        // array로 변환!
import java.util.Arrays;
import java.util.List;
import java.util.stream.IntStream;
class Solution {
    public int[] solution(int[] arr) {
       
      int max = Arrays.stream(arr).max().getAsInt();
         return IntStream.range(0, arr.length).filter(i-> max == arr[i]).toArray();
        
      
        
    }
}

```


```java
class Solution{
	public int[] solution(int[] arr){
		//최댓값 구하기
		int max = 0;
		for(int a : arr) if(a>max) max = a;
		
		//최댓값이 몇 개인지 확인하기
		int count = 0;
		for(int a : arr) if(a == max) count++;
		//배열 만들기
		int[] answer = new int[count];
		int index= 0;
		for(int i=0; i<arr.length; i++){
			if(arr[i] == max) answer[index++] = i;
		}
		return answer;
	}
}
```
