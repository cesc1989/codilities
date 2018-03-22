## Count Div

Exercise: https://app.codility.com/programmers/lessons/5-prefix_sums/count_div/

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
