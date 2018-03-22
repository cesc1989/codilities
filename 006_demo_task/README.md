## MIssing Integer

Exercise: https://app.codility.com/programmers/lessons/4-counting_elements/missing_integer/

## Filib's Answer: 77%

```ruby
def solution(a)
  return 1 if a.all?{|number| number < 0}
  z = {}
  a.each do |number|
    z[number] = true
  end

  1.upto(a.max).each do |n|
    return n unless z[n]
  end

  a.size + 1
end
```

## Francisco's Answer: 22%

```ruby
def solution(a)
  return 1 if a.max < 0

  arr = [*a.min..a.max]

  if arr == a
    a.max + 1
  else
    (arr - a).min
  end
end
```

## Sebastian's Answer: 100%

```ruby
def solution(a)
  a.reject!{ |x| x <= 0}
  a.sort!

  return 1 if a.first != 1

  a.each_with_index do |num, i|
    if i < (a.size - 1)
      return num + 1 unless (a[i+1] - num).between?(0,1)
    else
      return a.last + 1
    end
  end
end
```

## Ricardo's Answer: 33%

```ruby
def solution(a)
  _max_number = a.max
  _min_number = a.min

  _sequence = [*_min_number.._max_number]
  _result = (_sequence - a)

  _cont = _result.blank? ? (_max_number + 1) : _result.min

  return _max_number < 0 ? 1 : _cont
end
```

## Iris' Answer:

```java

```
