**Outlining procedural steps**

The user wants short procedures for various problems, starting with manual implementations, later using built-ins. For instance:

* \#1: Implement operators by assigning variables, applying operations, and printing results.
* \#2: Manually code if-else statements to compare values.

For later steps, such as statistical tests, loops, and regression, I'll handle manual implementations at first but rely on built-ins like `mean()`, `var()`, and others when specified. Each section will have a short, clear set of steps to follow.


Thought for 11 seconds


**Short procedural outlines**—do the first four problems **fully “by hand”** (no built‑ins beyond basic arithmetic, comparison and loops); from Problem 5 onward you may leverage R’s built‑in functions.

---

### 1. Operators (no built‑ins)

1. Read or assign two numbers, `a`, `b`.
2. Compute each operator manually:

* `sum ← a + b`
* `diff ← a - b`
* `prod ← a * b`
* `quot ← a / b`
* `pow  ← a ^ b`
* `mod  ← a %% b`
* `intdiv ← a %/% b`
  3. Compare with `==, !=, >, <, >=, <=`; combine with `&`, `|`, `!`.
  4. Print each result.

---

### 2. Conditional control (no built‑ins)

1. Read four inputs into `a,b,c,d`.
2. Use nested `if…else` to compare pairwise and carry forward the current maximum.
3. Read income `x`.
4. Use chained `if…else if…else` and the piecewise tax formula to compute `T`.

---

### 3. Iteration & distribution (no built‑ins)

1. Read vectors `x[]` and `p[]`.
2. Loop `for i in 1:length(x)` to accumulate

* `mean ← mean + x[i]*p[i]`
  3. Loop again for
* `var  ← var + p[i]*(x[i]-mean)^2`
* `sd   ← sqrt(var)`
  4. Compute `P(X≤6)` by summing `p[i]` when `x[i]≤6`; similarly for `5≤X<8`.
  5. Read three rank‑vectors; in a loop compute rank differences `d[i]`, then sum `d[i]^2` and plug into
  $\displaystyle \rho =1 - \frac{6\sum d_i^2}{n(n^2-1)}$.

---

### 4. Arrays & dice (no built‑ins)

1. Read or define your array `A[]`; loop to do sum, mean, min, max manually.
2. For two‑dice: nested loops `i=1…6`, `j=1…6`, tally counts of `i+j` in an array `cnt[s]`.
3. Compute `P[s] = cnt[s]/36`.
4. Compute expected value `E=∑ s*P[s]` and variance `Var=∑(s−E)^2*P[s]`.
5. Use formulas

$$
  E(2X-3)=2E(X)-3,\quad
  Var(2X-3)=4\,Var(X).
$$

---

### 5–14. Using built‑in R functions from here on

5. **Matrices**

   * `A + B`, `A - B`, `t(A)`, `A %*% B`

6. **Data frame & Iris**

   * `data(iris)`; then
     `dim()`, `str()`, `summary()`, `var()`,
     `hist()`, `pie()`, `barplot()`, `plot()`,
     `cov()`, `cor()`

7. **Central tendency**

   * `mean(x)`, `median(x)`, custom `mode` via `table()`

8. **Graphs**

   * `plot()`, `barplot()`, `pie()`, `hist()`

9. **Distribution stats**

   * `sum(x*p)`, `sum(p*(x-mean(x))^2)`, `sqrt(var)`, logical indexing

10. **Poisson fit**

    * `lambda <- sum(x*f)/sum(f)`
      `dpois(x, lambda) * sum(f)`

11. **Z‑ and t‑tests**

    * Z: manual formula + `pnorm()`
    * t: `t.test(x, mu=…, alternative=…)`

12. **F‑ and χ²‑tests**

    * F: `var.test(x,y)`
    * Chi‑sq: `chisq.test(obs, p=…)`

13. **Regression**

    * Simple: `lm(y ~ x)`
    * Multiple: `lm(y ~ x1 + x2 + …)`

14. **S3 & S4 Objects**

    * S3: `class<-`, write `print.ClassName`
    * S4: `setClass()`, `new()`