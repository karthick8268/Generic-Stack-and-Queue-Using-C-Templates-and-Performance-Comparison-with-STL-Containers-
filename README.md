Stack and Queue Performance Comparison in C++

📌 Project Description

This C++ project demonstrates the implementation of Stack and Queue data structures using Templates and compares their execution times with the built-in C++ Standard Template Library (STL) implementations.

The program performs 10,000 insertion and deletion operations on each data structure and measures execution time using the C++ "<chrono>" library.

The main objective is to understand data structures, templates, and basic performance benchmarking in C++.

🎯 Objectives

- Understand Stack and Queue data structures.
- Implement custom Stack and Queue classes.
- Learn how templates work in C++.
- Compare custom implementations with STL containers.
- Measure execution time using the "<chrono>" library.
- Understand basic performance analysis.

🛠️ Technologies Used

- Programming Language: C++
- Concepts: Data Structures, Templates, OOP
- Libraries: "<iostream>", "<stack>", "<queue>", "<chrono>"
- Compiler: G++
- IDE: VS Code / CLion

✨ Features

- Custom Stack implementation using an array.
- Custom Queue implementation using an array.
- Generic classes using C++ templates.
- Stack operations: "push()" and "pop()".
- Queue operations: "enqueue()" and "dequeue()".
- Performance comparison with STL Stack and Queue.
- Execution time measurement in microseconds.
- Benchmarking using 10,000 insertion and deletion operations.

💻 Source Code

#include <iostream>
#include <stack>
#include <queue>
#include <chrono>

using namespace std;
using namespace chrono;

template <class T>
class MyStack
{
private:
    T data[10000];
    int top;

public:
    MyStack()
    {
        top = -1;
    }

    void push(T value)
    {
        if (top < 9999)
            data[++top] = value;
    }

    void pop()
    {
        if (top >= 0)
            top--;
    }
};

template <class T>
class MyQueue
{
private:
    T data[10000];
    int front, rear;

public:
    MyQueue()
    {
        front = 0;
        rear = -1;
    }

    void enqueue(T value)
    {
        if (rear < 9999)
            data[++rear] = value;
    }

    void dequeue()
    {
        if (front <= rear)
            front++;
    }
};

int main()
{
    const int N = 10000;

    // Custom Stack Benchmark
    auto start = high_resolution_clock::now();

    MyStack<int> myStack;

    for (int i = 0; i < N; i++)
        myStack.push(i);

    for (int i = 0; i < N; i++)
        myStack.pop();

    auto end = high_resolution_clock::now();

    auto customStackTime =
        duration_cast<microseconds>(end - start);

    // STL Stack Benchmark
    start = high_resolution_clock::now();

    stack<int> stlStack;

    for (int i = 0; i < N; i++)
        stlStack.push(i);

    for (int i = 0; i < N; i++)
        stlStack.pop();

    end = high_resolution_clock::now();

    auto stlStackTime =
        duration_cast<microseconds>(end - start);

    // Custom Queue Benchmark
    start = high_resolution_clock::now();

    MyQueue<int> myQueue;

    for (int i = 0; i < N; i++)
        myQueue.enqueue(i);

    for (int i = 0; i < N; i++)
        myQueue.dequeue();

    end = high_resolution_clock::now();

    auto customQueueTime =
        duration_cast<microseconds>(end - start);

    // STL Queue Benchmark
    start = high_resolution_clock::now();

    queue<int> stlQueue;

    for (int i = 0; i < N; i++)
        stlQueue.push(i);

    for (int i = 0; i < N; i++)
        stlQueue.pop();

    end = high_resolution_clock::now();

    auto stlQueueTime =
        duration_cast<microseconds>(end - start);

    cout << "Custom Stack Time: "
         << customStackTime.count()
         << " microseconds" << endl;

    cout << "STL Stack Time: "
         << stlStackTime.count()
         << " microseconds" << endl;

    cout << "Custom Queue Time: "
         << customQueueTime.count()
         << " microseconds" << endl;

    cout << "STL Queue Time: "
         << stlQueueTime.count()
         << " microseconds" << endl;

    return 0;
}

📤 Expected Output Format

Custom Stack Time: <time> microseconds
STL Stack Time: <time> microseconds
Custom Queue Time: <time> microseconds
STL Queue Time: <time> microseconds

Note: Execution times vary depending on the computer, compiler, optimization settings, and system workload.

⚙️ Working of the Program

Step 1: Custom Stack Implementation

The "MyStack" class implements a Stack using a fixed-size array.

A Stack follows the LIFO (Last In, First Out) principle.

- "push()" inserts an element at the top.
- "pop()" removes the top element.

Step 2: Custom Queue Implementation

The "MyQueue" class implements a Queue using a fixed-size array.

A Queue follows the FIFO (First In, First Out) principle.

- "enqueue()" inserts an element at the rear.
- "dequeue()" removes an element from the front.

Step 3: STL Stack and Queue

The program uses the built-in C++ STL containers:

- "stack<int>" for Stack operations.
- "queue<int>" for Queue operations.

Step 4: Performance Measurement

The program uses "high_resolution_clock::now()" to record the starting and ending times.

The difference is calculated and converted into microseconds using "duration_cast<microseconds>()".

Step 5: Performance Comparison

Each data structure performs:

- 10,000 insertion operations.
- 10,000 deletion operations.

The program displays the execution time for each implementation.

📚 Concepts Used

1. Stack

A linear data structure that follows the Last In, First Out principle.

2. Queue

A linear data structure that follows the First In, First Out principle.

3. Templates

Templates allow the same class to work with different data types.

4. Object-Oriented Programming

Classes and objects are used to implement custom data structures.

5. Standard Template Library

STL provides ready-made implementations of common data structures.

6. Performance Benchmarking

The "<chrono>" library is used to measure execution time.

⏱️ Time Complexity

Operation| Custom Stack| Custom Queue| STL Stack| STL Queue
Insertion| O(1)| O(1)| O(1)| O(1)
Deletion| O(1)| O(1)| O(1)| O(1)

STL Stack and Queue operations have constant-time complexity for their standard underlying containers.

⚠️ Limitations

- Custom implementations use fixed-size arrays with a capacity of 10,000 elements.
- The custom Queue does not reuse previously occupied positions after dequeue operations.
- Overflow and underflow are handled silently without error messages.
- The benchmark runs only once for each implementation.
- Compiler optimizations may eliminate unused operations, affecting the measurements.
- The program does not verify the correctness of inserted or removed values.
- A single benchmark is insufficient to establish which implementation is generally faster.

For more reliable benchmarking, repeated measurements, optimized builds, and checks that prevent the compiler from eliminating the tested operations are recommended.

🎓 Learning Outcome

Through this project, I learned how to implement Stack and Queue data structures using C++ templates.

I also gained practical knowledge of STL containers, insertion and deletion operations, and execution time measurement using the "<chrono>" library.

This project helped me understand the basic differences between custom data structure implementations and standard library containers.

👨‍💻 Author

Karthick B
Department of Computer Science and Engineering
Chennai Institute of Technology

📄 Conclusion

This project demonstrates custom Stack and Queue implementations and compares their execution times with C++ STL containers.

It provides practical experience with data structures, templates, Object-Oriented Programming, and basic performance benchmarking in C++.
