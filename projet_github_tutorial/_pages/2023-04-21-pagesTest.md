# Pages TEST

# Test article.

---

# C++ code

```cpp
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int PickMinerals(const vector<int>& mineralGroup, int pickType) {
    const int fatigues[3][3] = {
        {1,1,1},
        {5,1,1},
        {25,5,1}
    };

    int ret = 0;
    for (int mineralType = 0; mineralType < 3; ++mineralType) {
        for (int count = 0; count < mineralGroup[mineralType]; ++count) {
            ret += fatigues[pickType][mineralType];
        }
    }

    return ret;
}

int GetPick(vector<int>& currentPicks) {
    for (int i = 0; i < 3; ++i) {
        if (currentPicks[i] > 0) {
            --currentPicks[i];
            return i;
        }
    }

    return -1;
}

```

---

# Review

1. Use a more efficient priority queue implementation. The **`std::priority_queue`** in C++ is implemented using a binary heap, which can be slow for large inputs. You could try using a Fibonacci heap or a pairing heap instead.
2. Avoid using **`std::vector<bool>`** as it can be slower than other container types due to its specialized implementation. Instead, consider using a regular **`std::vector<int>`** with 0 or 1 representing false or true values.
3. Use **`reserve()`** to pre-allocate memory for vectors. This can reduce the overhead of memory allocation when vectors grow in size.
4. Instead of using **`INT_MAX`** as the initial value for distances, you can use a smaller value that is still larger than the maximum possible distance. This can reduce the number of comparisons in the algorithm and improve performance.
5. Consider using multi-threading to parallelize the computation if possible. The algorithm can be run for each gate in parallel.
6. Avoid unnecessary copying of data. In the **`for (const vector<int>& p : paths)`** loop, you can use **`const auto& p`** instead of **`const vector<int>& p`** to avoid copying the vector. Similarly, in the **`for (edge_t edgeToNext : A[curNode])`** loop, you can use **`const auto& edgeToNext`** instead of **`edge_t edgeToNext`** to avoid copying the struct.
7. Avoid using **`std::endl`** and use **`'\n'`** instead to flush the output buffer. **`std::endl`** is equivalent to **`'\n'`** followed by **`std::flush`**, which can be slower than just using **`'\n'`**.
8. Use **`static_cast`** instead of C-style casts for type conversions. C++ style casts are safer and can catch more errors at compile time.
9. Avoid using **`using namespace std`**. It's considered bad practice because it can lead to name collisions and make the code harder to read and maintain.
10. Consider using a profiler to identify performance bottlenecks and optimize them.

---

# Random Image

![testimage.png](/assets/img/20230420/tok.png)

