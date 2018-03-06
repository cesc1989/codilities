## Integers in Range

Write a function:

`def solution(a, b, k)`

that, given three integers A, B and K, returns the number of integers within the range [A..B] that are divisible by K, i.e.:

{ i : A ≤ i ≤ B, i mod K = 0 }
For example, for A = 6, B = 11 and K = 2, your function should return 3, because there are three numbers divisible by 2 within the range [6..11], namely 6, 8 and 10.

Assume that:

A and B are integers within the range [0..2,000,000,000];
K is an integer within the range [1..2,000,000,000];
A ≤ B.
Complexity:

expected worst-case time complexity is O(1);

expected worst-case space complexity is O(1)

## Francisco's Slow Version Answer: 50%
```ruby
def solution(a, b, k)
  r = []

  (a..b).each do |n|
    r << n if n % k == 0
  end

  r.size
end
```

## Francisco's Blazing Fast Version Answer: 100%
```ruby
def solution(a, b, k)
  r = ((b - a) / k).floor

  r += 1 if (b % k < a % k) || (a % k == 0)

  r
end
```

## Filib's Answer: 50%
```ruby
def solution(a, b, k)
  divisibles = 0

  [*a..b].each do |number|
    divisibles+=1 if number%k == 0
  end

  divisibles
end
```

## Ricardo's Answer: 50%
```ruby
def solution(a,b,k)
  _numbers = [*a..b]
  _numbers.keep_if{|n| n % k == 0}.size
end
```

## Sebastian's Answer: 87%
```ruby
def solution(a,b,k)
  start_at = a + (a % k)
  end_at = b - (b % k)

  ((end_at - start_at) / k) + 1
end
```
