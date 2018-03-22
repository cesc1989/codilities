## Max Counters

Exercise: https://app.codility.com/programmers/lessons/4-counting_elements/max_counters/

### Francisco's Answer: 88%

```ruby
def solution(n, a)
  return false if a.empty?

  counters = Array.new(n, 0)
  max = 0

  a.each do |element|
    if element >= 1 && element <= n
      next_value = counters[element - 1] + 1
      counters[element - 1] = next_value
      max = next_value if next_value > max
    elsif element > n
      counters = Array.new(n, max)
    end
  end

  counters
end
```
