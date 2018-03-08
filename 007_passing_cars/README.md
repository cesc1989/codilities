## Passing Cars

Exercise: https://app.codility.com/programmers/lessons/5-prefix_sums/passing_cars/

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
