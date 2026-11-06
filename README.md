# SDR Signal Processing Pipeline for FM Broadcast Demodulation

A complete Software-Defined Radio (SDR) signal processing pipeline implemented in Python and deployed as custom embedded Python blocks within GNU Radio. This project demonstrates offline mathematical prototyping, linear-phase FIR filter optimization, non-linear FM demodulation, and live streaming DSP benchmarking against native GNU Radio C++ blocks.

## Key Features & Deliverables

* **Offline DSP Prototyping (SciPy/NumPy):** Read real-world SigMF complex IQ data ($f_s = 2.5\text{ MSps}$) captured from commercial FM radio (92.3 MHz).
* **FIR Filter Trade-Off Analysis:** Comparative design and frequency response evaluation of **Hamming** vs. **Kaiser** windowing schemes (mainlobe width vs. stopband attenuation and transition bandwidth).
* **Custom GNU Radio Python Blocks:**
  * `Custom FIR Filter Block`: Lowpass FIR filtering via `scipy.signal` / Direct-Form convolution.
  * `Conjugate Delay Demodulator Block`: Complex differential phase discriminator $\Delta \phi = \text{arg}(y[n] \cdot y^*[n-1])$.
  * `De-emphasis & Decimation Block`: $75\,\mu\text{s}$ IIR lowpass filter with polyphase resampling down to $48\text{ kHz}$ audio.
* **Performance Benchmarking:** Comparative execution profiling and spectral performance analysis between custom Python blocks and native GNU Radio C++ blocks (`freq_xlating_fir_filter`, `quadrature_demod`).

## Repository Structure

```text
├── data/                  # SigMF metadata and sample IQ captures
├── notebooks/             # Offline Jupyter prototyping & spectral analysis
├── grc/                   # GNU Radio Companion (.grc) flowgraphs
├── blocks/                # Embedded Python block scripts
├── results/               # Comparative PSDs, phase/magnitude plots, & audio samples
└── README.md
