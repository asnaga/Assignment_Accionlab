# Assignment_Accionlab
#Decimal Digit Transformation

def compute_series(x):
#Input Valdidation

if isinstance(x, int):
  x = str(x) #convert intger to string for processing
elif not isinstance(x, str):
  return "Error: Input must be a digit (0-9)."

#Chec if Input is single digit
if not x.isdigit() or len (x) != 1:
  return " Error: Input must be a single digit between 0 and 9."

#Convert input to integer
num = int(x)

# Compute the series: X + XX + XXX + XXXX
result = num + int(x * 2) + int(x * 3) + int(x * 4)

return result

user_input = input ("Enter a single digit: ")

try:
    print(f"Result: {compute_series(user_input)}")

except ValueError as e:
    print(e)

#Use Cases:

print(compute_series(3))  #Output: 3702
