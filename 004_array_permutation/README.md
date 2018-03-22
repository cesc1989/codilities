## Permutation Check

Exercise: https://app.codility.com/programmers/lessons/4-counting_elements/perm_check/

## Filib's Answer: 100%

```ruby
def solution(a)
  a.sort!
  a.each_index do |i|
    return 0 if a[i] != i+1
  end
  return 1
end
```

## Sebastian's Answer: 70%

```ruby
def solution(a)
  n = a.size
  aim = ((n)*(n + 1)) / 2
  if (aim - a.reduce(0, :+)) == 0
    return 1
  else
    return 0
  end
end
```

## Ricardo's Answer: 100%

```ruby
def solution(array)
  _sort_sequence = [*1..array.size]
  return (_sort_sequence - array).empty? ? 1 : 0
end
```
