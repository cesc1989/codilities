## Pairs of Cars

A non-empty zero-indexed array A consisting of N integers is given. The consecutive elements of array A represent consecutive cars on a road.

Array A contains only 0s and/or 1s:

0 represents a car traveling east,
1 represents a car traveling west.
The goal is to count passing cars. We say that a pair of cars (P, Q), where 0 ≤ P < Q < N, is passing when P is traveling to the east and Q is traveling to the west.

For example, consider array A such that:

  A[0] = 0
  A[1] = 1
  A[2] = 0
  A[3] = 1
  A[4] = 1

We have five pairs of passing cars: (0, 1), (0, 3), (0, 4), (2, 3), (2, 4).

Write a function:

def solution(a)
that, given a non-empty zero-indexed array A of N integers, returns the number of pairs of passing cars.

The function should return −1 if the number of pairs of passing cars exceeds 1,000,000,000.

For example, given:

  A[0] = 0
  A[1] = 1
  A[2] = 0
  A[3] = 1
  A[4] = 1

the function should return 5, as explained above.

Assume that:

N is an integer within the range [1..100,000];
each element of array A is an integer that can have one of the following values: 0, 1.
Complexity:

expected worst-case time complexity is O(N);

expected worst-case space complexity is O(1), beyond input storage (not counting the storage required for input arguments).

Elements of input arrays can be modified.

## Francisco's Answer: 50%

```ruby
def solution(a)
  # Learnt about Enumerable#each_cons(n)
  pairs = 0

  a.combination(2) do |comb|
    goes_east = comb.first < 1
    goes_west = comb.last == 1

    pairs += 1 if goes_east && goes_west

    return -1 if pairs > 1_000_000_000
  end

  pairs
end
```

## Filib's Answer: 100%

```ruby
def solution(a)
  total_ones = a.count(1)
  ones_count = 0
  pairs = 0

  a.each do |number|
    if number == 0
      pairs += total_ones - ones_count
    else
      ones_count += 1
    end
  end

  return -1 if pairs > 1000000000
  pairs
end
```

## Sebastian's Answer: 40%

```ruby
def solution(a)
  start_number = a.first
  passing_number = a.first == 0 ? 1 : 0

  count = 0
  a.each_with_index do |num, i|
    next if num == passing_number
    last_numbers = a.size - i
    num_of_ones = a.last(last_numbers).reduce(:+)
    sum = start_number == 0 ? num_of_ones : last_numbers - num_of_ones
    count += sum

    return -1 if count > 1_000_000_000
  end

  count
end
```

## Iris' Answer: 20%

```java
public static int pares(int[]a){
     int ip=0, iq=0;
     int sum=0;
     for (int i=0; i< a.length; i++){
       if(a[i]==0){
         ip++;
       }else{
         iq++;
       }
     }

   for (int i=0; i< ip; i++){
     int j=i;
       while (j< iq &&sum<=1000000) {
        sum++;
        j++;
     }
   }
   if(sum>1000000){
     sum=-1;
   }
     return sum;

   }
```
