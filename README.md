# Discrete-Hankel-Transform

This code is based on: Baddour, N. and Chouinard, U., 2017. Journal of Open Research Software, 5(1), p.4. doi.org/10.5334/jors.82  with a few improvments:

1. The Y matrix code is now vectorized making it ~ x20 faster. 
2. Optional zero padding input similar to Matlab's fft functionality.
3. Supports also arrays similar to Matlab's fft functionality, meaning that the Bessel zeros and Y matrix is only calculated once per run.
4. Updated bessel zeros calculation code (by Jason Nicholson).

Inputs:

   n      - the order of the Hankel Transform
  data   - the input data, a vector of size (q x 1), or a 2D array (q x n)
  q      - the grid points of vec
  N      - If the length of data is less than N, then data is padded with trailing zeros to length N.
  
 Outputs:

  F      - The transfomred vector
  Fgrid  - The transformed grid


   Ver 1 (2020-09-07)
   Adi Natan (natan@stanford.edu)

Example: generate array of signals in q range, pad zeros to N

N    = 2^8;               % zero padding

q    = eps:0.075:10;      % data grid

a    = linspace(1,20);     

data = sin(q'*a)./(q'*a); % set of data vectors

filt = sin(pi*[1:numel(q)]'./(numel(q))).^2;

data = bsxfun(@times,data, filt); % filter edges with sin^2 window

[F, Fgrid] = DHT(0.5, data, q, N);
 
 
 
  subplot(2,1,1);   imagesc(a,q,data);   xlim([a(1) a(end)]);    ylim([q(1) q(end)]);   title('data')
 
  subplot(2,1,2);   imagesc(a,Fgrid,F);   xlim([a(1) a(end)]);   ylim([a(1) a(end)]);   title('DHT(data)')
