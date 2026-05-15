---
title: Small & Large Lighter Cup
date: 2023-11-05 00:00:00 +09:00
categories: [BOJ]
tags: [FWHT, catalan]
math: true
---

1등 올솔브

매우 잘했다. 일단 실수를 하나도 안 했고, 쉬운 문제 순서대로 잘 찾아서 빠르게 풀었다.

**카탈란 증명**과 **fast mobius transform**을 써 본 게 교육적이어서 좋았다.

셋은 적당한듯?

---

B : 열심히 case work.

C : 카탈란 증명을 알고 있으면 nCr로 정리 가능하다.

(max값이 x 이하인 경우의 수)는 $\binom{2N}{N}$ - (max값이 x 초과인 경우의 수)로 구할 수 있다.

(max값이 정확히 x인 경우의 수) = (max값이 x 이하인 경우의 수) - (max값이 x-1 이하인 경우의 수)

D : 난 subset enumeration $O(3^M)$, inverse fast mobius transform $O(M 2^M)$, FWHT $O(M2^M)$을 모두 사용했다.

1. 모든 (x^y)값에 대해, 이 값을 만드는 모든 (x,y)쌍에 대해 sum of A[x]*B[y]를 알아야 한다.
2. 모든 (x|y) - (x^y)값에 대해, 이 값을 만드는 모든 (x,y)쌍에 대해 sum of A[x]*B[y]를 알아야 한다.

위 두 가지를 할 수 있다면, (x^y)값을 모두 넣어놓은 뒤에 (x|y) - (x^y)값이 큰 순으로 뽑으면 된다.

**핵심 관찰: (x|y) - (x^y) = (x&y)**

1에다 XOR FWHT를 썼다.

2에다 각 {x, (x&y)} pair를 열거하는 데 $O(3^N)$을 쓰고, 여기서 y값의 후보들의 합을 구하기 위해 fast mobius transform을 했다.