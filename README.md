def determineReflexivity(A, R):
   newArr = []
   for i in range(len(A)):
       for j in range(0, 2):
           newArr.append(A[i])

       if (not newArr in R):
           print(f"R is not Reflexive: {A[i]}")
           break

       newArr = []


def determineSymmetricity(A, R):
   newArr = []
   symAr = []
   detArr = []
   for i in range(len(A)):
       for j in range(2):
           if (len(A) == 1):
               break
           newArr.append(A[j])

       symAr.append(newArr[::-1] in R)

       A.pop(0)
       detArr.append(newArr)
       newArr = []

   if (not True in symAr):
       print(f"R is not Symmetric: {detArr[symAr.index(False)]}")
   else:
       print(f"R is Symmetric: {detArr[symAr.index(True)]}")


def determineTrancivity(A, R):
   counter = 0
   newArr = []
   symAr = []
   detArr = []
   for i in range(len(A)):
       for j in range(2):
           if (i < len(A)):
               newArr.append(A[i])

           i += 2

       symAr.append(newArr in R)

       detArr.append(newArr)
       newArr = []

   if (not True in symAr):
       print(f"R is not Transitive: {detArr[symAr.index(False)]}")
   else:
       print(f"R is Transitive: {detArr[symAr.index(True)]}")


# ----------- ----------#

A = [int(item) for item in input("Enter the list items for A separated by space: ").split()]
n = int(input("Enter number of lists in R"))
R = [[input("First element: "), input("Last element: ")] for _ in range(n)]

newR = set.union(*map(set, R))

set(newR)
print("R is a set")

if (newR.issubset(set(A))):
   print("R is a subset of AxA")

   determineReflexivity(A, R)
   determineSymmetricity(A, R)
   determineTrancivity(A, R)

else:
   print("R is not a relation on A")
