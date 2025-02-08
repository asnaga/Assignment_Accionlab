# Assignment_Accionlab
#Sum of Even Fibonacci Numbers

def sum_even_fibonacci(n):

  """Returns the sum of the first n even Fibonacci numbers."""
  a, b = 2, 8 #First two even Fibonacci numbers
  total = a
  count = 1

  while count < n:
    total += b
    a, b = b, 4 * b + a # Formula to generate even Fibonacci numbers
    count += 1

  return total

#calculate and print the sum of the frst 100 even Fibonacci numbers
print(sum_even_fibonacci(100))
