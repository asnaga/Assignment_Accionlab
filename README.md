# Assignment_Accionlab
#Intersection of Sorted Arrays

#Python

def intersecton_sorted_arrays(arr1, arr2):
    """ Finds the intersecton of two sorted arrays wthout duplcates"""
    i, j = 0, 0
    result = []

    while i < len(arr1) and j < len(arr2):
      if arr1[i] == arr2[j]: #if both elements match
         if not results or results[-1] != arr1[i]: # Avoid duplicates
           results.append(arr1[i])

        i += 1
        j += 1
    elif arr1[i] < arr2[j]:
      i += 1
    else:
      j += 1

  return result

#test cases
print(intersecton_sorted_arrays([1, 2, 2, 3, 4], [2, 2, 4, 6])) #output : [2, 4]
print(intersecton_sorted_arrays([1, 3, 5], [2, 4, 6])) #output []

