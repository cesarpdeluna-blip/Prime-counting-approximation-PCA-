# Prime-counting-approximation-PCA-
High-Precision Approximation for the Prime-Counting Function π(x)
# High-Precision Approximation for the Prime-Counting Function $\pi(x)$

This project presents a highly accurate, novel formula for approximating the prime-counting function $\pi(x)$. This formula achieves remarkable precision by using a dynamic adjustment variable $a$ and a high-precision correction factor $K$.

## The Mathematical Model

The approximation is structured using a primary function and a secondary adjustment variable **$a$**.

### Core Formula
$$\pi(x) \approx \left( \frac{x}{\ln(x) - a} \right) \cdot (1 + K)$$

Where:
* **$x$**: The input value.
* **$K$**: $1.6702623205 \times 10^{-6}$ (Precision Correction Factor).
* **$a$**: A variable adjustment term defined as:

$$a = 1 + \frac{\pi^2}{24 \log_{10} x} + \frac{11}{8 (\log_{10} x)^2} - \frac{2\pi}{(\log_{10} x)^3}$$

### Final Expanded Form
By substituting **$a$** into the denominator, the complete expression for calculation is:

$$\pi(x) \approx \frac{x}{\ln x - 1 - \frac{\pi^2}{24 \log_{10} x} - \frac{11}{8 (\log_{10} x)^2} + \frac{2\pi}{(\log_{10} x)^3}} \cdot (1 + 1.6702623205 \times 10^{-6})$$

---

## Verified Results and Comparison

The following table contains the full set of calculations verified using WolframAlpha. It compares the **Prime-Counting-Approximation (PCA)** against the real value of $\pi(x)$ and the classical $Li(x)$ function.

| x | $\pi(x)$ | prime-counting-approximation (pca) | $Li(x)$ | relative error pca | relative error $Li(x)$ |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 10 | 4 | 1.72 | 6.165 | 56.89% | -54.13% |
| 1.00E+02 | 25 | 26.03 | 30.126 | -4.13% | -20.50% |
| 1.00E+03 | 168 | 170.92 | 177.609 | -1.740% | -5.720% |
| 1.00E+04 | 1229 | 1231.56 | 1246.137 | -0.209% | -1.394% |
| 1.00E+05 | 9592 | 9591.47 | 9629.809 | 0.0054898525% | -0.3941722269% |
| 1.00E+06 | 78498 | 78506.22 | 78627.549 | -0.0104674603% | -0.1650347780% |
| 1.00E+07 | 664579 | 664470.37 | 664918.405 | 0.0163453899% | -0.0510706778% |
| 1.00E+08 | 5761455 | 5760357.04 | 5762209.375 | 0.0190569905% | -0.0130934807% |
| 1.00E+09 | 5.084753400E+07 | 5.084095006E+07 | 5.084923496E+07 | 0.0129484027% | -0.0033452104% |
| 1.00E+10 | 4.550525110E+08 | 4.550165196E+08 | 4.550556146E+08 | 0.0079092886% | -0.0006820281% |
| 1E+11 | 4.118054813E+09 | 4.117875401E+09 | 4.118066401E+09 | 0.0043567283% | -0.0002813858% |
| 1E+12 | 3.760791202E+10 | 3.760699934E+10 | 3.760795028E+10 | 0.0024268260% | -0.0001017414% |
| 1E+13 | 3.460655368E+11 | 3.460608948E+11 | 3.460656458E+11 | 0.0013413786% | -0.0000314886% |
| 1E+14 | 3.204941751E+12 | 3.204918668E+12 | 3.204942066E+12 | 0.0007202143% | -0.0000098251% |
| 1E+15 | 2.984457042E+13 | 2.984446073E+13 | 2.984457148E+13 | 0.0003675572% | -0.0000035270% |
| 1E+16 | 2.792383410E+14 | 2.792378624E+14 | 2.792383442E+14 | 0.0001714023% | -0.0000011512% |
| 1E+17 | 2.623557158E+15 | 2.623555437E+15 | 2.623557166E+15 | 0.0000655750% | -0.0000003033% |
| 1E+18 | 2.473995429E+16 | 2.473995133E+16 | 2.473995431E+16 | 0.0000119709% | -0.0000000887% |
| 1E+19 | 2.340576673E+17 | 2.340576943E+17 | 2.340576674E+17 | -0.0000115301% | -0.0000000427% |
| 1E+20 | 2.220819603E+18 | 2.220820003E+18 | 2.220819603E+18 | -0.0000180196% | -0.0000000100% |
| 1E+21 | 2.1112726949E+19 | 2.1112727273E+19 | 2.1112726949E+19 | -0.0000153341% | -0.0000000028% |
| 1E+22 | 2.014672867E+20 | 2.014673030E+20 | 2.014672867E+20 | -0.0000080791% | -0.0000000010% |
| 1E+23 | 1.925320392E+21 | 1.925320372E+21 | 1.925320392E+21 | 0.0000010356% | -0.0000000004% |

---

## Python Implementation

Implementation in Python:

To check that the calculations made with PCA are correct, you can run the following Python code.

Checking calculations in Python ensures accuracy according to the required need, since a standard calculation platform like Excel is limited to 15 decimals, and Python can handle as many decimals as memory allows, configuring its precision with getcontext().prec.

To run the code in a practical and simple way, follow these instructions:


1. Click on the following online Python link: https://www.online-python.com/
2. Delete the lines of code written in the main.py tab.
3. Copy and paste the following code in that same main.py tab:

from decimal import Decimal, getcontext

# Absolute precision for high-magnitude verification
getcontext().prec = 50

def calculate_pi_discovery(exponent):
    """
    Computes pi(x) approximation for x = 10^exponent.
    Implements dynamic factor a(x) and proportional scaling.
    """
    x = Decimal('10')**exponent
    ln_x = x.ln()
    log10_x = Decimal(exponent)
    pi_ref = Decimal('3.1415926535897932384626433832795028841971')
   
    # 1. Dynamic factor a(x)
    term1 = pi_ref**2 / (Decimal('24') * log10_x)
    term2 = Decimal('11') / (Decimal('8') * log10_x**2)
    term3 = (Decimal('2') * pi_ref) / (log10_x**3)
   
    a = Decimal('1') + term1 + term2 - term3
   
    # 2. Base term calculation
    base_term = x / (ln_x - a)
   
    # 3. Scale correction (epsilon)
    epsilon = Decimal('1.6702623205e-6')
   
    return base_term * (Decimal('1') + epsilon)

if __name__ == "__main__":
    print("-" * 65)
    print(f"{'Exp':<5} | {'Approximation Result':<35} | {'Note'}")
    print("-" * 65)
   
    # Generate all 23 results without omission
    for exp in range(1, 24):
        result = calculate_pi_discovery(exp)
        note = "High Precision Range" if exp >= 9 else "Low Range"
        print(f"10^{exp:<2} | {result:<35.6f} | {note}")
   
    print("-" * 65)

4. Click on Run and that's it, we can see the results and analyze the information. The code is specified for a precision of 50 decimals.

