# 🚀 Cache performance testing tool 🚀

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![C](https://img.shields.io/badge/language-C-blue.svg)

## 🌟 Project overview

Welcome to the cache performance testing tool 🎉! This project consists of a C application designed to measure and compare the performance of 
various memory access patterns and their effects on cache efficiency in Linux. 🧑‍💻👩‍💻

### 🎯 Key objectives

- **Measure** the performance of different memory access methods.
- **Compare** latency and efficiency across various cache usage patterns.
- **Provide** insights into how different access patterns affect cache performance under different data sizes.

## 🛠️ Features

- **Multiple memory access patterns**:
  - Atomic memory operations
  - Cache delays
  - Cache misses
  - Random memory access
  - Sequential memory access
- **Customizable data sizes**: tests with various array sizes.
- **User-friendly**: easy setup and configuration using CMake.

## ⚙️ Installation

### 🔧 Prerequisites

Ensure you have the following installed on your system:

- GCC compiler (`sudo apt install gcc`)
- CMake (`sudo apt install cmake`)
- Git (`sudo apt install git`)

### Step 1: Clone the repository

Clone the project from GitHub:

```bash
git clone https://github.com/Braun-Alex/cache-performance.git
cd cache-performance
```

### Step 2: Build the project

```bash
mkdir build
cd build
cmake ..
make
```

## 📝 Performance analysis

Below is a comparison of different memory access patterns across various array sizes. Each mode was tested under similar conditions, and the 
results are presented in terms of latency.

### 1. Array size: 1,000 elements

| Mode              | Latency (s) |
|-------------------|-------------|
| Atomic memory     | 0.00005     |
| Cache delays      | 0.000045    |
| Cache misses      | 0.000048    |
| Random memory     | 0.000055    |
| Sequential memory | 0.000046    |

### 2. Array size: 1,000,000 elements

| Mode              | Latency (s) |
|-------------------|-------------|
| Atomic memory     | 0.006068    |
| Cache delays      | 0.00395     |
| Cache misses      | 0.00105     |
| Random memory     | 0.019545    |
| Sequential memory | 0.003282    |

### 3. Array size: 1,000,000,000 elements

| Mode              | Latency (s) |
|-------------------|-------------|
| Atomic memory     | 6.22328     |
| Cache delays      | 3.086384    |
| Cache misses      | 0.965692    |
| Random memory     | 43.157195   |
| Sequential memory | 2.916325    |

## 🔍 Key findings

The performance analysis of the cache performance testing tool provides valuable insights into how different memory access patterns impact cache 
efficiency and overall execution time under various data sizes. Below are the key observations derived from the test results.

### 📌 Comparison of memory access patterns

#### 1. **Sequential memory access**

- Sequential memory access consistently exhibits low latency across all array sizes, demonstrating high performance due to spatial and temporal locality.
- The cache's ability to predict and prefetch data significantly improves performance in sequential access patterns.

#### 2. **Random memory access**

- Random memory access shows significantly higher latency, especially with larger array sizes, due to numerous cache misses.
- The lack of predictable data access patterns prevents effective cache utilization, leading to performance degradation.

#### 3. **Atomic memory operations**

- Despite the potential overhead of synchronization, atomic memory operations demonstrate high performance in single-threaded scenarios.
- Modern processors efficiently handle atomic operations, resulting in competitive latency even with large data sizes.

#### 4. **Cache delays**

- Introducing cache delays results in low execution time, but the program spends more time idling than performing active computations.
- This pattern does not provide a realistic assessment of cache efficiency, as it artificially manipulates execution timing.

#### 5. **Cache misses**

- Cache misses display the lowest execution time in some tests, which may be counterintuitive.
- Possible compiler optimizations might have excluded unused computations, leading to misleadingly low latency measurements.

### 📌 Array size impact

#### **1,000 elements**

- With small data sizes, all access patterns show minimal latency differences due to the data fitting entirely within the cache.
- The cache effectively handles all access patterns, resulting in uniformly low execution times.

#### **1,000,000 elements**

- Differences in latency become more pronounced as the array size increases.
- Sequential access maintains low latency, while random access latency increases significantly due to cache inefficiency.

#### **1,000,000,000 elements**

- At very large data sizes, the impact of cache efficiency is substantial.
- Random memory access incurs the highest latency, highlighting the critical role of access patterns in performance.
- Sequential access continues to leverage cache prefetching, resulting in much lower latency compared to random access.

### 📌 Overall insights

- Memory access patterns greatly affect cache performance, and thus overall execution time.
- Careful design of data structures and algorithms to promote sequential access can lead to significant performance gains.
- Be aware of compiler optimizations that may impact performance measurements, such as eliminating unused computations.
- Accurate performance testing should ensure that computations are meaningful and that compiler optimizations do not skew results.

## ⚠️ Important notes

- Ensure that the compiler does not optimize away critical parts of the code that are intended to measure performance.
- Understanding the memory hierarchy and cache behavior is essential for optimizing software performance.
- Random access patterns can severely degrade performance due to cache misses; designing algorithms to access memory sequentially can mitigate this.
- The size of the data structures relative to the cache size can dramatically affect performance outcomes.
- While atomic operations perform well in single-threaded tests, they may introduce contention and performance penalties in multi-threaded environments.

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file 📝 for details.
