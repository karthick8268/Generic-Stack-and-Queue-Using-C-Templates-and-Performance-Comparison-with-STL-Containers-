Matrix Operations Using Operator Overloading in C++

📌 Project Description

This C++ program demonstrates Operator Overloading using a 2×2 Matrix class.

The program performs matrix addition and multiplication by overloading the "+" and "*" operators.

It also demonstrates overloading the "[]" operator for accessing matrix elements and the "<<" operator for displaying matrices.

The program includes unit tests using assertions to verify the correctness of matrix operations.

🎯 Objectives

- Understand operator overloading in C++.
- Implement matrix addition and multiplication.
- Learn how to overload arithmetic operators.
- Understand operator overloading using member and friend functions.
- Access matrix elements using the "[]" operator.
- Verify program correctness using assertions.

🛠️ Technologies Used

- Programming Language: C++
- Concept: Object-Oriented Programming (OOP)
- Compiler: G++
- IDE: VS Code / CLion
- Testing: C++ "assert()" function

✨ Features

- Creates and initializes 2×2 matrices.
- Performs matrix addition using the overloaded "+" operator.
- Performs matrix multiplication using the overloaded "*" operator.
- Accesses matrix elements using the overloaded "[]" operator.
- Displays matrices using the overloaded "<<" operator.
- Includes assertions to verify expected results.
- Demonstrates operator overloading and encapsulation.

💻 Source Code

#include <iostream>
#include <cassert>
using namespace std;

class Matrix
{
private:
    int data[2][2];

public:
    Matrix(int a = 0, int b = 0, int c = 0, int d = 0)
    {
        data[0][0] = a;
        data[0][1] = b;
        data[1][0] = c;
        data[1][1] = d;
    }

    // Operator +
    Matrix operator+(const Matrix &m)
    {
        Matrix result;

        for (int i = 0; i < 2; i++)
            for (int j = 0; j < 2; j++)
                result.data[i][j] = data[i][j] + m.data[i][j];

        return result;
    }

    // Operator *
    Matrix operator*(const Matrix &m)
    {
        Matrix result;

        for (int i = 0; i < 2; i++)
        {
            for (int j = 0; j < 2; j++)
            {
                result.data[i][j] = 0;

                for (int k = 0; k < 2; k++)
                    result.data[i][j] += data[i][k] * m.data[k][j];
            }
        }

        return result;
    }

    // Operator []
    int* operator[](int index)
    {
        return data[index];
    }

    // Operator <<
    friend ostream& operator<<(ostream &out, const Matrix &m)
    {
        for (int i = 0; i < 2; i++)
        {
            for (int j = 0; j < 2; j++)
                out << m.data[i][j] << " ";

            out << endl;
        }

        return out;
    }
};

int main()
{
    Matrix A(1, 2, 3, 4);
    Matrix B(5, 6, 7, 8);

    Matrix sum = A + B;
    Matrix product = A * B;

    // Unit Tests
    assert(sum[0][0] == 6);
    assert(sum[1][1] == 12);

    assert(product[0][0] == 19);
    assert(product[0][1] == 22);
    assert(product[1][0] == 43);
    assert(product[1][1] == 50);

    cout << "Matrix A:" << endl;
    cout << A;

    cout << "Matrix B:" << endl;
    cout << B;

    cout << "Addition of Matrices:" << endl;
    cout << sum;

    cout << "Multiplication of Matrices:" << endl;
    cout << product;

    cout << "All unit tests passed successfully." << endl;

    return 0;
}

📤 Expected Output

Matrix A:
1 2
3 4
Matrix B:
5 6
7 8
Addition of Matrices:
6 8
10 12
Multiplication of Matrices:
19 22
43 50
All unit tests passed successfully.

⚙️ Working of the Program

Step 1: Matrix Class

A class named "Matrix" is created with a private 2×2 integer array to store matrix elements.

Step 2: Constructor

The parameterized constructor initializes the matrix elements.

Step 3: Addition Operator ("+")

The overloaded "+" operator adds corresponding elements of two matrices and returns the resulting matrix.

Step 4: Multiplication Operator ("*")

The overloaded "*" operator performs standard matrix multiplication using three nested loops.

Step 5: Subscript Operator ("[]")

The overloaded "[]" operator allows matrix elements to be accessed using expressions such as "sum[0][0]".

Step 6: Stream Insertion Operator ("<<")

The overloaded "<<" operator displays matrix elements in a readable format.

Step 7: Unit Testing

The "assert()" function checks whether the calculated matrix elements match the expected values.

If all assertions pass, the program displays a success message.

📚 OOP Concepts Used

1. Operator Overloading

Allows existing operators to perform operations on user-defined objects.

2. Encapsulation

The matrix elements are stored in a private data member.

3. Constructor

Initializes the matrix elements when an object is created.

4. Friend Function

The overloaded "<<" operator is implemented as a friend function to access private matrix data.

5. Objects and Classes

The "Matrix" class defines the structure and operations of matrix objects.

🧪 Unit Testing

The program uses the C++ "assert()" function to validate matrix addition and multiplication.

The following operations are tested:

- Matrix addition
- Matrix multiplication
- Accessing matrix elements
- Comparing actual results with expected values

All six assertions must pass for the program to display the success message.

Note: Assertions are active when the program is compiled without defining "NDEBUG".

🎓 Learning Outcome

Through this program, I learned how to implement operator overloading in C++ to perform mathematical operations on user-defined objects.

I also gained practical knowledge of constructors, friend functions, encapsulation, and basic unit testing using assertions.

👨‍💻 Author

Karthick B
Department of Computer Science and Engineering
Chennai Institute of Technology

📄 Conclusion

This project demonstrates how operator overloading improves code readability and allows matrix objects to be manipulated using familiar mathematical operators.

It provides a practical introduction to Object-Oriented Programming concepts and basic unit testing in C++.