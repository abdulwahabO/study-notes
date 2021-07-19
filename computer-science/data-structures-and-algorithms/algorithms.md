## Algorithms

_Asymptotic analysis_ is used to evaluate how much more time/space an algorithm will need as its input size grows. This analysis is independent of the programming language used, the CPU power, and other hardware factors. It focus on the number of steps an algorithm takes, instead of the actual running time.

`Time complexity` is a way of computing the running time of an algorithm by considering specific input that leads to the maximum number of possible primitive operations been executed. This can be expressed as a polynomial.

E.g Given the following code:

```rust
fn do_something(x: u32, y: [u32; 45]) {
    let name: &str = "I am Ade!";
    let sites: [i32; 74] = [0; 74];
    for x in 0..y.len() {
        print!("{}", y[x]);
    }
}
```

The time complexity is the number of times each line of code is executed: `1 + 1 + 1n + 1n` => `2 + 2n`. 
By dropping all constants and all but the highest term, we arrive at the Big-O notation for this algorithm: `O(n)` i.e linear time. What matters in Big-O is the number of times each operation has to be repeated.

Big-O is a notation for representing the time complexity of an algorithm in the worst case scenario.

### General Tips

* An algorithm that halves the number of elements in the problem space with each iteration, is most likely running in logarithmic time `O(log n)`

* An algorithm that has to iterate over all the elements in the problem space is most likely running in linear time `O(n)`.

* When a algorithm uses a nested loop, it is most likely running in quadratic time `O(n^2)`

### Common Complexity Scenarios

* Simple for-loop with increment of 1 => `O(n)`
* Simple for-loop with increment of _K_ => `O(n)`
* Simple nested for-loop => `O(_nm_)` where n and m = outer and inner loop iterations.
* Nested for-loop with dependent variables = `O(n2)` (i.e n * n)
* Nested for-loop with index modification = `O(n)`
* Loop multiplies/divide the loop varible (reducing the number of iterations) = `O(log n)`


_TODO: Learn common sorting and searching algorithms with their time complexities_
