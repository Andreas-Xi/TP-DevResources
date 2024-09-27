# Practical work on the conversion of sampling rate and STFT
Group members: LI Xiquan, ZHU Chenhao

## 1. Conversion of sampling rate
### 1.1 
To transform the sampling rate from $F_s = 48kHz$ to $F_s = 32kHz$, we need to perform a resampling by a factor 2/3. To preserve more information, we can first upscale the sampling rate to $F_s = 96kHz$ and then downscale it to $F_s = 32kHz$. Thus, the processing chain contains 
1. Insertion of zeros between each sample, L = 2
2. Apply a low-pass filter $H(z)$ 
<!-- $$\begin{equation*}
    H(e^{i2\pi\nu}) =
    \begin{cases}
        L, & \text{if } |\nu| < \min(\frac{1}{2L},\frac{1}{2M})  \\
        0, & \text{if } \min(\frac{1}{2L},\frac{1}{2M}) < |\nu| < \frac12
    \end{cases}
\end{equation*}
$$ -->
$$\begin{equation*}
    H(e^{i2\pi\nu}) =
    \begin{cases}
        L, & \text{if } |\nu| < \frac16  \\
        0, & \text{if } \frac{1}{6} < |\nu| < \frac12
    \end{cases}
\end{equation*}
$$
3. Downsample the signal by a factor 3