# Assignment_Accionlab
# 8 Decimal Digit Transformation

class PatternCalculator:
    """
    A class to compute the sum of the series: X + XX + XXX + XXXX for a given single digit X.
    """

    def __init__(self, x):
        """
        Initializes the object with a single digit X after validation.
        """
        self.x = self.validate_input(x)

    def validate_input(self, x):
        """
        Validates the input to ensure it is a single digit between 0 and 9.
        """
        if isinstance(x, int):
            x = str(x)  # Convert integer to string format
        elif not isinstance(x, str):
            raise ValueError("Error: Input must be a digit (0-9).")

        if not x.isdigit() or len(x) != 1:
            raise ValueError("Error: Input must be a single digit between 0 and 9.")

        return int(x)  # Convert back to integer for calculations

    def compute_series(self):
        """
        Computes the sum of X + XX + XXX + XXXX.
        """
        return self.x + int(str(self.x) * 2) + int(str(self.x) * 3) + int(str(self.x) * 4)


# Taking user input 
try:
    user_input = input("Enter a single digit (0-9): ")
    calculator = PatternCalculator(user_input)
    result = calculator.compute_series()
    print(f"Result: {result}")
except ValueError as e:
    print(e)

