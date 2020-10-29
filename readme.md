Implement a calculator, which can calculate simple expressions. It has one method `Evaluate()` which receives an expression as `string` and returns result as `string` (or error).

1. It can evaluate expressions on integer or floating point numbers with binary operators `+`, `-`, `*`, `/` and the negation unary operator `-`

    ```
    1 + 2        // 3
    2 * 3        // 6
    2 * - 2      // -4
    ```

2. It can evaluate expressions with parentheses `(` `)`

    ```
    2 * (1 + 2)         // 6
    2 * (-(2 + 3) * 4)  // -40
    ```

3. **Bonus point**: It can assign to a variable and use them for calculating. Variables are single upper case letter `A`, `B`, `C`, ...

    ```
    A = 10         // 10
    A + 2          // 12
    A * 3          // 30
    B = -A * A     // -100
    ```

***Note**: Sample code is written in Go, but you can use any programming language to solve this question.*

***Note 2**: The whole point of the question is that you can implement a parser and evaluator. You **must not** use `eval()`, `Function()` or similar constructs as (1) they are not available in many languages and (2) they leave a lot of security holes for being abused.*

```go
type Calculator struct {
	// TODO: implement this struct
}

func (c *Calculator) Evaluate(expr string) (string, error) {
	// TODO: implement this method
}

// Test cases

func TestCalculator(t *testing.T) {
	c := Calculator{}
	t.Run("addition", func(t *testing.T) {
		output, err := c.Evaluate("1 + 2")
		assert(t, "3", output, err)
	})
	t.Run("multiplication", func(t *testing.T) {
		output, err := c.Evaluate("2 * 3 + 4")
		assert(t, "10", output, err)
	})
	t.Run("parentheses", func(t *testing.T) {
		output, err := c.Evaluate("2 * (3 + 4)")
		assert(t, "14", output, err)
	})
	t.Run("negation", func(t *testing.T) {
		output, err := c.Evaluate("-(2 + 1)")
		assert(t, "-3", output, err)
	})
    
	// bonus point
	t.Run("assignment", func(t *testing.T) {
		output, err := c.Evaluate("A = 10 + 2")
		assert(t, "12", output, err)
	})
	t.Run("variable", func(t *testing.T) {
		output, err := c.Evaluate("A * 2")
		assert(t, "24", output, err)
	})
}

func assert(t *testing.T, expected string, actual string, err error) {
	if err != nil {
		t.Errorf("unexpected error: %v", err)
		return
	}
	if expected != actual {
		t.Errorf("expect `%v`, got `%v`", expected, actual)
	}
}
```