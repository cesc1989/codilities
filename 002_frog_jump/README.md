## Frog Jump

Exercise: https://app.codility.com/programmers/lessons/3-time_complexity/frog_jmp/

## Francisco's Answer: 11%

```ruby
def solution(x, y, d)
  calc = (x..y).step(d){ |step| step }.size
  calc.fdiv(d).ceil
end
```

## Filib's Answer: 44%

```ruby
def solution(x, y, d)
  jumps = 0
  while x < y
    x = x + d
    jumps = jumps + 1
  end
  jumps
end
```

## Sebastian's Answer: 100%

```ruby
def solution(x, y, d)
  ((y - x).to_f/d.to_f).to_f.ceil
end
```

## Ricardos' Answer

A. 11%
```ruby
def jumps_while(x, y, d)
  jumps = 0
  progress = x
  begin
    progress += d
    jumps += 1
  end while progress <= y
  jumps
end
```

B. 55%
```ruby
def jumps_whitout_while(x, y, d)
  ((y.to_f - x.to_f)/d).round
end
```
