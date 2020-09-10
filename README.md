# Discrete-Hankel-Transform

The code follows the path as the Discrete Fourier transform, including properties such as orthogonality and invertibility, as well as the typical discrete shift, modulation, multiplication and convolution rules, unlike past DHT definitions that approximated the continuous integral transform without the properties mentioned.

This code is based on: Baddour, N. and Chouinard, U., 2017. Journal of Open Research Software, 5(1), p.4. [doi.org/10.5334/jors.82](https://doi.org/10.5334/jors.82)
 with a few improvements: The Y matrix code is now vectorized making it ~ x20 faster, there is and optional zero padding input and arrays input similar to Matlab's fft functionality, meaning that the Bessel zeros and Y matrix are only calculated once. The Bessel zeros calculation code s the updated version by Jason Nicholson.
 
