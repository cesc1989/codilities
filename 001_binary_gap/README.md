## 001 Binary Gap

Exercise: https://app.codility.com/programmers/lessons/1-iterations/binary_gap/

### Francisco's Answer

Incomplete

```ruby
def solution(n)
  bin = ("%b" % n)

  return 0 if bin.count("0") == 0

  bin.each_char do |char|
    #if char == '1'

    #end
    puts char.inspect
  end

  #bin.each_char.map{ |c| c if c == '0'  }
end
```

### Sebastian's Answer

```ruby
def solution(n)
  string_binary = '%0*b' % [33, n]

  count = 0
  highest = 0
  start_counting = false

  string_binary.each_char do |char|
    if char == '1'
      highest = count if count > highest
      count = 0
      start_counting = true
    elsif start_counting
      count += 1
    end
  end

  highest
end
```

### Filib's Answer

```ruby
def solution(n)
  x = n.to_s(2).split('')
  is_one = false
  count = 0
  zeros = []

  x.each do |i|
    if(i == "1" && is_one == false)
      is_one = true
    elsif(i == "0" && is_one)
      count = count + 1
    elsif(i == "1" && is_one)
      zeros << count
      count = 0
    end
  end

  zeros.max
end
```

### Optimal Solution

```ruby
def solution(n)
  s = '%b' % n
  zeroes = s.split('1')
  zeroes.pop if n % 2 == 0
  return 0 if zeroes.empty?
  zeroes.map { |zeroes| zeroes.length }.max
end
```
