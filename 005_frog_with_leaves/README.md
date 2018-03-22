## Frog with Leaves

Exercise: https://app.codility.com/programmers/lessons/4-counting_elements/frog_river_one/

## Filib's Answer: 81%

```ruby
def solution(x, a)
  return 0 if a.size == 1
  z = [*0..(a.size - 1)]
  z.each { |i| z[i] = 0 }
  a.each_with_index do |position, index|
    if(z[position] == 0)
      z[position] = 1
      x = x - 1
    end
    return index if x == 0
  end

  return -1
end
```

## Sebastian's Answer: 100%

```ruby
def solution(x, a)
  check_array = Array.new(x, false)
  aim = (x * (x + 1)) / 2
  sum = 0

  a.each_with_index do |num, i|
    unless check_array[num]
      check_array[num] = true
      sum += num
      if sum == aim
        return i
      end
    end
  end

  -1
end
```

## Ricardo's Answer: 54%

```ruby
def solution(x, a)
  _positions = [*1..x]
  a.each do |e|
    _positions.delete(e)
    return a.index(e) if _positions.empty?
  end

  return -1
end
```
