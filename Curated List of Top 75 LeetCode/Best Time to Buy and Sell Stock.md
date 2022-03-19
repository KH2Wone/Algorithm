# Best Time to Buy and Sell Stock

## 문제

## 풀이

### 첫 시도, 시간 초과로 실패

```javascript
const maxProfit = function (prices) {
  let profit = 0;
  for (let i = 0; i < prices.length; i++) {
    for (let j = i + 1; j < prices.length; j++) {
      const subtract = prices[j] - prices[i];
      if (subtract > profit) profit = subtract;
    }
  }
  return profit;
};
```

야심차게 다 풀었다고 생각했는데 시간 초과로 실패다. 온갖 조건을 넣어주어도 해결이 되지 않았다.

### 성공한 코드

```javascript
const maxProfit = function (prices) {
  let profit = 0;
  let buy = prices[0];

  for (let i = 1; i < prices.length; i++) {
    if (buy > prices[i]) {
      buy = prices[i];
    } else {
      profit = Math.max(profit, prices[i] - buy);
    }
  }
  return profit;
};
```

## 설명

일단 처음에 주식을 가장 저렴할 때 구매하고 그 이후에 가장 비쌀 때 팔아야 최고의 이득이 남는다.  
평소 주식에 관심있던 나는 이런 데이터가 있다면 좋겠군 이라고 생각했다 (있을리 없음) ㅋㅋㅋㅋㅋ  
아무튼 이런식으로 조금 이입해서 읽어본 문제..라서 그런지 해결하는데 오래 걸렸다. 처음에 시간 초과걸리고 구글링하면서 이해가 안되어 헤매다가 답을 찾았다.  
어차피 가장 작은 값이 매수가 될거고 그 값 이후의 날짜(index)중에서 보다 큰 값을 연산한 뒤 가장 큰 이익인 값이 출력될 것이다. 이 과정을 반복문을 통해 해결한다.  
그래서 우선 기준인 buy라는 우선 매수 값이 필요하다.
매수 값이 현재 i 값보다 클 경우 매수 값을 작은 i로 바꾸어준다.  
그게 아니라면 (else), 결과 값인 profit에 원래 profit값과 연산한 값을 비교해서 더 큰 값(이익이 더 큰 값)을 profit에 담는다.  
그러면 반복문을 통해 profit에 가장 큰 이익이 되는 값이 담길 것이고 반복문이 종료된 후 그 값을 출력하면 된다.
