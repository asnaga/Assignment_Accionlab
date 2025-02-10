# Assignment_Accionlab
# 7 Intersection of Sorted Arrays

#Python
class CommonElementsFinder:
    """Finds common unique elements between two sorted arrays."""

    def __init__(self, arr1, arr2):
        self.arr1 = set(arr1)  # Convert lists to sets to remove duplicates
        self.arr2 = set(arr2)

    def find_common(self):
        return list(self.arr1 & self.arr2)  # Set intersection to find common elements

# Take user input and process it
try:
    arr1 = list(map(int, input("Enter first sorted array (comma-separated): ").split(',')))
    arr2 = list(map(int, input("Enter second sorted array (comma-separated): ").split(',')))

    result = CommonElementsFinder(arr1, arr2).find_common()
    print(f"Common Elements: {result}")

except ValueError:
    print("Error: Please enter only numbers separated by commas.")


#test cases
print(intersecton_sorted_arrays([1, 2, 2, 3, 4], [2, 2, 4, 6])) #output : [2, 4]


