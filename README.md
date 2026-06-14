# Wireless Performance Analysis of Digital Modulation Schemes over AWGN Channel

## 📌 Project Overview
This project presents a comprehensive simulation-based analysis of various digital modulation schemes operating over an **Additive White Gaussian Noise (AWGN)** channel. The simulation environment is developed in Python to evaluate and validate the fundamental trade-off between **Spectral Efficiency** (bits/symbol) and **Noise Robustness** (Bit Error Rate vs. Signal-to-Noise Ratio).

### Schemes Simulated & Analyzed:
1. **Binary Phase Shift Keying (BPSK):** 1 bit/symbol
2. **Quadrature Phase Shift Keying (QPSK):** 2 bits/symbol
3. **16-Quadrature Amplitude Modulation (16-QAM):** 4 bits/symbol
4. **64-Quadrature Amplitude Modulation (64-QAM):** 6 bits/symbol
5. **256-Quadrature Amplitude Modulation (256-QAM):** 8 bits/symbol

---

## 🛠️ Simulation Design & Mathematical Framework
The engine processes a high baseline configuration volume of **200,000 bits per simulation step** across an SNR testing vector ranging from `0 to 20 dB`. 

* **Channel Modeling:** AWGN is modeled programmatically by mapping linear Signal-to-Noise ratios and injecting zero-mean Gaussian distribution variables directly onto transmission symbols.
* **Gray Coding Alignment:** Standard bit-to-symbol allocation is coupled with Gray mapping rules to ensure adjacent constellation index selection limits channel error consequences to single-bit drops wherever possible.
* **Optimal Detection:** Receivers implement Maximum Likelihood (ML) criteria via nearest-neighbor distance metrics mapping received points back to original constellation definitions.
* **Analytical Validation:** To verify experimental telemetry accuracy, empirical results are automatically cross-checked with theoretical boundaries using complementary error function equations ($Q$-function / $\text{erfc}$).

---

## 📊 Performance Benchmarks & Insights

### 1. SNR vs. BER Sensitivity Matrix (Target: $BER = 10^{-3}$)
Through continuous discrete simulation iterations, the exact minimum SNR required to reach standard communications reliability ($10^{-3}$) was measured:
* **BPSK & QPSK:** Highly robust, achieving the target at approximately **$7\text{ dB}$**.
* **16-QAM:** Requires an elevated threshold of **$11\text{ dB}$**.
* **64-QAM:** Scales further up to **$15\text{ dB}$**.
* **256-QAM:** Requires a clean, high-power environment at **$20\text{ dB}$**.

### 2. The Core Trade-Off Insight
Higher-order modulations like **256-QAM** pack 8 times more data per symbol compared to BPSK, boosting wireless network throughput tremendously. However, their constellation points sit extremely close to each other. Because of this tight grouping, even small amounts of AWGN noise easily distort the transmission grid, requiring higher link power (SNR) to maintain data accuracy. This phenomenon explains why modern infrastructure deployments (**LTE, 5G, and Wi-Fi 6**) rely heavily on **Adaptive Modulation and Coding (AMC)** to shift dynamically across these modes based on current line conditions.

---

