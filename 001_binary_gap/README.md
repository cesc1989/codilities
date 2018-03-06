## 001 Binary Gap

A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps.

Write a function: def solution(n) that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5.

Assume that: N is an integer within the range [1..2,147,483,647].

Complexity:

expected worst-case time complexity is O(log(N));

expected worst-case space complexity is O(1).

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
