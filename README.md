# Black Scholes Model

## Description

This function calculates the price of a European call or put option using the **generalized Black-Scholes formula**, which extends the standard model to incorporate a continuous dividend yield.

---

## Usage

```r
generalized_black_scholes(TypeFlag = c("c", "p"), S, X, Time, r, b, sigma)
````

---

## Arguments

| Argument   | Description                                                                                        |
| ---------- | -------------------------------------------------------------------------------------------------- |
| `TypeFlag` | A character vector indicating the type of option: `"c"` for call options or `"p"` for put options. |
| `S`        | Current stock price *(scalar)*.                                                                    |
| `X`        | Strike price of the option *(scalar)*.                                                             |
| `Time`     | Time to expiration of the option *(in years)*.                                                     |
| `r`        | Risk-free interest rate *(annualized)*.                                                            |
| `b`        | Cost of carry rate, where \$b = r - q\$ for a dividend yield \$q\$.                                |
| `sigma`    | Volatility of the underlying asset *(annualized)*.                                                 |

---

## Details

The **generalized Black-Scholes formula** considers both the risk-free rate and a cost of carry, making it suitable for a wider range of financial instruments, including commodities and currencies with continuous yields.

The pricing formulas for **call** and **put** options are:

### Call Option

$$
C = S e^{(b - r)T} N(d_1) - X e^{-rT} N(d_2)
$$

### Put Option

$$
P = X e^{-rT} N(-d_2) - S e^{(b - r)T} N(-d_1)
$$

Where:

$$
d_1 = \frac{\ln(S/X) + (b + \sigma^2 / 2) T}{\sigma \sqrt{T}}
$$

$$
d_2 = d_1 - \sigma \sqrt{T}
$$

* \$N(\cdot)\$ is the **cumulative normal distribution function**, estimated by the `cum_normal_density` function.

---

## Value

Returns the **price** of the specified option (*call or put*).
