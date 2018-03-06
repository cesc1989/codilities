A zero-indexed array A consisting of N different integers is given. The array contains integers in the range [1..(N + 1)], which means that exactly one element is missing.

Your goal is to find that missing element.

Write a function:

def solution(a)

that, given a zero-indexed array A, returns the value of the missing element.

For example, given array A such that:

  A[0] = 2
  A[1] = 3
  A[2] = 1
  A[3] = 5

the function should return 4, as it is the missing element.

Assume that:

N is an integer within the range [0..100,000]; the elements of A are all distinct; each element of array A is an integer within the range [1..(N + 1)].

Complexity:

expected worst-case time complexity is O(N);
expected worst-case space complexity is O(1), beyond input storage (not counting the storage required for input arguments).
Elements of input arrays can be modified.

## Francisco's Anwser: 10%

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

## Filibs' Answer: 50%

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
