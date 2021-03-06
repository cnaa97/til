# 버블 정렬 \(Bubble Sort\)

* 인접한 두 값을 비교해서, 왼쪽 값이 더 큰 경우 자리를 바꾸는 과정 반복해서 정렬하는 방식
* 시간복잡도 O\(n²\)

![](https://camo.githubusercontent.com/383b23979d4d7f279f8fb285b36bcdd357b10a35/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f632f63382f427562626c652d736f72742d6578616d706c652d33303070782e676966)

```javascript
function bubbleSort(array) {
  let len = array.length;
  let temp;
  for (i = 0; i < len - 1; i++) { // 순차적으로 비교하기 위한 반복문
    for (j = 0; j < len - 1 - i; j++) { // 끝까지 돌았을 때 처음부터 다시 비교
      if (array[j] > array[j + 1]) { // 두 수를 비교하여 앞 수가 뒷 수보다 크면
        temp = array[j]; // 두 수를 서로 바꿔준다
        array[j] = array[j + 1];
        array[j + 1] = temp;
      }
    }
  }
  return array;
};

bubbleSort([5,1,7,4,6,3,2,8]);
```

