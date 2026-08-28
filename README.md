# Exp 01 Matrix Multiplication using MapReduce

**Date:**

## AIM:
To implement Matrix Vector Multiplication using the MapReduce programming model.
## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create a Python/Java project in the preferred IDE (Eclipse/IntelliJ IDEA/VS Code).

### Step 3:
Create the Python/Java program for Matrix Vector Multiplication using the MapReduce concept.

### Step 4:
Implement the **Mapper** phase to generate intermediate key-value pairs from the input matrices.

### Step 5:
Implement the **Shuffle and Sort** phase to group intermediate values based on common keys.

### Step 6:
Implement the **Reducer** phase to compute the final matrix vector multiplication results.

### Step 7:
Compile and execute the program.

### Step 8:
Verify and display the resulting product matrix.

## PROGRAM:

```
# Matrix Multiplication using MapReduce

# Matrix A
A = [
    [1, 2],
    [3, 4]
]

# Matrix B
B = [
    [5, 6],
    [7, 8]
]

# Mapper Phase
def mapper(A, B):
    intermediate = []

    for i in range(len(A)):
        for j in range(len(B[0])):
            for k in range(len(B)):
                intermediate.append(((i, j), A[i][k] * B[k][j]))

    return intermediate


# Shuffle and Sort Phase
def shuffle(intermediate):
    grouped = {}

    for key, value in intermediate:
        if key not in grouped:
            grouped[key] = []
        grouped[key].append(value)

    return grouped


# Reducer Phase
def reducer(grouped):
    result = {}

    for key, values in grouped.items():
        result[key] = sum(values)

    return result


# Execute MapReduce
intermediate = mapper(A, B)
grouped = shuffle(intermediate)
result = reducer(grouped)


# Display Result
print("Matrix A:")
for row in A:
    print(row)

print("\nMatrix B:")
for row in B:
    print(row)

print("\nResultant Matrix (A x B):")

for i in range(len(A)):
    row = []
    for j in range(len(B[0])):
        row.append(result[(i, j)])
    print(row)

```

## OUTPUT:

*(<img width="1920" height="1080" alt="Screenshot (134)" src="https://github.com/user-attachments/assets/90a1ec34-a6a3-4be3-a41c-600417fa2a89" /)*

## RESULT:

The Matrix Multiplication using the MapReduce programming model was implemented successfully, and the resultant matrix was computed correctly.
