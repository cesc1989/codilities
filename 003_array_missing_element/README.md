## Permutation Missing Element

Exercise: https://app.codility.com/programmers/lessons/3-time_complexity/perm_missing_elem/

## Francisco's Answer: 10%

```ruby
def solution(a)
  missing = nil

  (a.min..a.max).each do |i|
    unless a.include?(i)
      missing = i
    end
  end

  missing
end
```

## Sebastian's Answer: 90%

```ruby
def solution(a)
  size = a.size
  aim = ((size + 1)*(size + 2)) / 2
  aim - a.reduce(:+)
end
```

## Filib's Answer: 50%

```ruby
def solution(a)
  a.sort!
  a.each do |i|
    return i+1 if a[i] != i+1
  end
end
```

### Optimal Solution

```ruby
def solution(a)
  n = a.size
  (n + 2) * (n + 1) / 2 - a.reduce(0, :+)
end
```
