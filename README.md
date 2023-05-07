Download Link: https://assignmentchef.com/product/solved-math-281-project-2
<br>






<h1>1           Question 1</h1>

In this problem, we are given <em>y </em>= sin<em>x</em>, which can be written as a Fourier series:

(1)

Using this Fourier series, the second, third, and fourth derivatives can be computed as follows:

Second derivative:

(2)

Third derivative:

(3)

Fourth derivative:

(4)

In code, these coefficients can be computed for our given function using the fft and ifft functions, as is shown in our Jupyter notebook.

We plotted the true first, second, third, and fourth derivatives of sin<em>x </em>along with the spectral derivatives we computed using our calculations of ˜<em>c<sub>n</sub></em>. The error in the two kinds of derivatives is also plotted in the same figure. These plots can be found in Figure 1.

(a) First Derivative                                                                               (b) Second Derivative

(c) Third Derivative                                                                              (d) Fourth Derivative

Figure 1: Comparing the spectral derivatives to the true derivatives. The true and spectral derivatives for each case are plotted on top of each other, and the difference between them (i.e. the error) is plotted alongside.

Additionally, we consider two different functions – sin<em>x </em>and sin10<em>x </em>(corresponding to NModes=1 and NModes=10 respectively). To our 2nd and 4th order finite difference derivative plots from Question 2 in the previous project, we add the first spectral derivatives corresponding to the two cases. Our plots are shown in Figure 2.

From Figure 2 we can see that the accuracy of the spectral derivatives is much higher than that of the method used in Project 1 , since the finite differences for the spectral derivative curves are smaller for same ∆<em>x</em>. In addition, for the NModes=1 plots (Figure 2(a)), the accuracy for the spectral derivative seems to improve with increasing ∆<em>x </em>due to the slight decrease in the finite difference error (although this could also be a machine or Python approximation error, due to the extremely small order of magnitude of the difference). So we can say that unlike the 2nd and 4th order finite difference derivatives, the spectral derivative for NModes=1 gives us a very low error which does not much depend on ∆<em>x</em>.

However, for NModes=10, this trend stops after a certain value of ∆<em>x</em>. That is, an increase in ∆<em>x </em>results in slightly smaller errors, but after a certain point the finite difference sharply increases. This suggests that when a function is oscillating slwoly (NModes=1),the value of ∆<em>x </em>does not impact the accuracy much. But when the function oscillates faster (for instance when NModes=10), we see that the error does depend on our resolution, and only smaller values of ∆<em>x </em>will give us good accuracy. After a point, higher values of ∆<em>x </em>will give us larger and somewhat constant errors, as is the case with our 2nd and 4th order finite difference derivatives.

<ul>

 <li>NModes=1</li>

 <li>NModes=10</li>

</ul>

Figure 2: Plotting the finite difference error as a function of ∆<em>x </em>for numerical 2nd and 4th order derivatives, and the 1st order spectral derivative.

<h1>2           Question 2</h1>

In this problem, we compare the physical space solutions and the power spectra for the following three functions:

<ul>

 <li><strong>Case 1: </strong><em>e</em><sup>−<em>x</em></sup><sup>2</sup><em>,x </em>∈ [−16<em>,</em>16] <strong>Case 2: </strong>tanh(5 − |<em>x</em>|)<em>,x </em>∈ [−16<em>,</em>16]</li>

 <li><strong>Case 3: </strong></li>

</ul>

The plots are shown in Figure 3.

Figure 3: Power spectra and physical-space solutions for the three functions corresponding to Cases 1, 2, and 3.

In Case 1, one notices that the physical space solution is a simple Gaussian or a bell curve centered at zero, with no overlaying oscillating function. The spectral plot corresponding to this function falls off the fastest in <em>kx </em>i.e. its rate of decrease of slope is the highest of the three functions. This makes sense, we see that higher wavenumbers do not hold a lot of power, which means that lower length scales will hold lesser power. As a side note, it is observed that for very low orders of magnitude (around 10<sup>−30</sup>), the computer is unable to approximate floating point values well, which is why the power seems to be sporadic when in reality it has probably just died out completely.

On the other hand, the cosine function in Case 3 oscillates the fastest, with the frequency of oscillation increasing with increasing magnitude of <em>x</em>. Correspondingly, one can see that up to a certain value of <em>kx</em>, the power remains constant and very high, compared to Case 1 which drops off a lot quicker. This indicates that the spatial solution for this function should be a rapidly oscillating one with small-scale spatial features dominating, which is what we observe in the physical space plot as well.

Finally, the hyperbolic tangent function in Case 2 can be considered the middle ground. At <em>x </em>= 0, it starts off at a positive value of <em>f</em>(<em>x</em>), but then slowly decreases to a negative value of <em>f</em>(<em>x</em>), ultimately flat-lining at <em>x </em>= −1. This may be considered ”half” an oscillation, if any at all, for the sake of understanding the way this problem works. This explains why the power spectrum for this case somewhat overlaps with that of a non-oscillating Gaussian, but ultimately does not dip as much as Case 1. This indicates a physical function which does not have prominent small-scale features, but is not as ”smooth” as a Gaussian, which is what we observe from the spatial plot.

<h1>3           Question 3</h1>

<h2>3.1         Part (a)</h2>

Figure 4: Physical-space solution of the given PDE plotted for various times (left), and the power spectrum plotted for various times (right).

In the physical space solution, one can see that at <em>t </em>= 0, <em>u </em>is a superposition of a sine (which oscillates fast) and a smooth Gaussian (which is consistent with the given initial condition). But as time progresses, <em>u</em>(<em>x,t</em>) tends to a simple Gaussian curve that slowly seems to die out as times increases. This behavior is also seen in the power spectrum, where for a given wavenumber, higher times correspond to lower energies.

It is also observed that since the initial condition is a superposition of a fast oscillating and a slow ”oscillating” function, the power spectra for lower times show a spike in energy at approximately <em>kx </em>= 16. However, since the physical space plots tend to a standard bell curve as time progresses, this spike disappears fast and eventually all wavenumbers lose energy past <em>kx </em>≈ 10<sup>0</sup>. Additionally, as time progresses, the rate of loss of power increases since the slopes get steeper (i.e. more negative). This is consistent with the shape of the power spectrum of a Gaussian which we obtained in Question 2 (Figure 3). As the width of the bell curve increases and its peak decreases, the faster its power spectrum drops. One also notes that similar to our observations in Question 2, as the power reaches 10<sup>−30</sup>, the computer can no longer store values accurately, hence the ragged lines at around <em>kx </em>≈ 10<sup>1</sup>.

<h2>3.2         Part (b)</h2>

Figure 5 shows the time evolution of power for different values of <em>kx</em>. To compare this with the predicted behavior, let. We plug this into the given PDE to get:

∞                                                       ∞

<em>∂</em><em>t </em>X<em>c</em><em>n</em>(<em>t</em>)<em>e</em><em>ik</em><em>n</em><em>x </em>= <em>∂</em><em>xx </em>X<em>c</em><em>n</em>(<em>t</em>)<em>e</em><em>ik</em><em>n</em><em>x</em>

−∞                                                     −∞

(5)

Figure 5: Power as a function of time, plotted for various values of <em>kx</em>.

From Equation 5, we can see that as <em>k<sub>n </sub></em>increases, <em>c<sub>n </sub></em>decreases. This is consistent with what we observe in Figure 5, because for the same value of time, higher values of <em>k<sub>n </sub></em>correspond to lower power. Additionally from Equation 5 we see that for a given value of <em>k<sub>n</sub></em>, the graph for log|<em>c<sub>n</sub></em>|<sup>2 </sup>versus time (i.e. |<em>c<sub>n</sub></em>|<sup>2 </sup>versus time in the log space) is a straight line with slope −2<em>k<sub>n</sub></em><sup>2</sup>. As we can see in Figure 5, this expected behavior is manifested in our plot as well. As <em>k<sub>n </sub></em>increases in our equation, the value of the slope becomes more negative, which is again a trend we observe in our plot. As with our earlier plots, lower orders of magnitude result in floating point errors, resulting in sporadic values of power.

<h2>3.3         Part (c)</h2>

A positive slope in the power spectrum simply means that as <em>kx </em>increases, so does the power. This means that in the physical space plot, the small-scale features are dominating i.e. the plot looks more ”jagged” due to the dominance of the high frequency component of the solution. So if our plot had a positive slope, we would see that the high-frequency sinusoidal part of solution would dominate over the Gaussian. On the other hand, a negative slope signifies that the large-scale component of the solution dominates. The more negative the slope becomes, the more our solution tends towards the low-frequency features. This is what we primarily see in our plot in Figure 4. For smaller times, we see a brief increased slope in the power spectrum due to the superpositioning of the sine and the Gaussian. As time progresses, the sine component dies out completely, leaving behind only the Gaussian. This is why we see a negative and steadily decreasing slope in the power spectra as <em>kx </em>increases for all remaining times. Also note that as time progresses, for the same value of <em>kx</em>, higher times have a more negative slope, which is consistent with our explanation that the Gaussian dominates over the sine with increasing time.

<h1>4           Question 4</h1>

<h2>4.1         Part (a)</h2>

Figure 6: Physical-space solution of the given PDE plotted for various times (left), and the power spectrum plotted for various times (right).

Figure 6 shows the physical-space solution plotted alongside the power spectrum for the given PDE for various times. It is observed in the physical space plot that at <em>t </em>= 0, our curve is a Gaussian, which is consistent with the given initial condition. As time progresses, the peak decreases and shifts forward in <em>x</em>. For higher times, another smaller peak is observed at the minimum value of <em>x </em>= −10 (almost in a cyclic fashion). As for the power spectra, at <em>t </em>= 0 the spectrum is consistent with that of a Gaussian. However, for all remaining <em>t &gt; </em>0, there is an increase in the magnitude of the power compared to the <em>t </em>= 0 case. One sees that between <em>kx </em>= 10<sup>0 </sup>and <em>kx </em>≈ 10<sup>0<em>.</em>75</sup>, the power is greater for the <em>t </em>= 0 curve. However, after <em>kx </em>≈ 10<sup>0<em>.</em>75</sup>, the slope of the <em>t </em>= 0 curve becomes more and more negative, and therefore drops more sharply than the remaining curves. Now focusing on the power spectra for <em>t &gt; </em>0, one sees that for a given value of <em>kx</em>, higher times exhibit lower powers. Equivalently, the rate of decrease of slope increases as time increases, or wavenumbers lose energy with increasing time. This behavior is consistent with the physical space plots: for higher values of time, the function dies out due to viscous forces, causing a decrease in energy and consequently power.

<h2>4.2         Part (b)</h2>

As described in Question 3(c), more positive slope indicates dominance of small-scale features and more negative slope means dominance of large-scale features. At <em>t </em>= 0, we only have the large-scale feature (a Gaussian), which is why the corresponding power spectrum has a negative slope which only decreases with increasing <em>kx</em>. The fact that the slope increases at <em>t &gt; </em>0 indicates the introduction of small-scale features, which is consistent with what we observe in the physical space plots because the curve does not resemble a known large-scale function, likely due to the introduction of the viscosity term in the PDE and the shock frontier seen in the figure. However, for all <em>t &gt; </em>0, the slope is still negative (albeit less negative than that of <em>t </em>= 0), meaning the large scale features still dominate, which can we asserted by judging the ”smoothness” of the curve (i.e. no visible small-scale aberrations on top of the ”main” curve). For each curve, as <em>kx </em>increases, the slope of the power spectrum becomes more and more negative. However, as time progresses, the slope becomes more negative for a given <em>kx </em>value i.e. the rate at which the slope of the power spectrum decreases, increases as time progresses.

Had the slope of the power spectra been positive at any point, it would have meant increasing energy in the PDE i.e. instead of a dampening force (viscosity), we would have had an amplifying force (like a driving force).

<h2>4.3         Part (c)</h2>

In this question, we will compare the power spectra for the PDEs given in questions 3 and 4 i.e. the right sides of Figures 4 and 6. For convenience, we have plotted them again side by side in Figure 7.

(a) PDE from Question 3                                                              (b) PDE from Question 4

Figure 7: Power spectra for different times for the PDEs given in Questions 3 and 4. Once can see that the y-scales are identical for easier comparison.

Qualitatively, one observed that the initial condition of PDE 3 is a superposition between a sine and a Gaussian, which causes increased spikes in the power spectra for lower times. On the other hand, the physical space solution for PDE 4 does not have visible superposition, but instead of converging to a Gaussian the solution develops a shock frontier as time progresses due to the extra viscosity term in the PDE. This is reflected in the power spectrum by an increase in power after <em>t </em>= 0, followed by a gradual decline in power with increasing time.

The slow rate of decline for PDE 4 can be explained by comparing the values of the viscosity coefficients for the two systems. The viscous coefficient is 1 in PDE 3 and 0.00078 in PDE 4. This means that the physical system represented by PDE 3 dies down much faster than that of PDE 4. One can see that that is indeed the case, because in Figure 7(a) the power dies very quickly for a given <em>kx </em>value between 0 <em>&lt; t &lt; </em>1, whereas for similar values of <em>kx </em>the slope of the power spectrum decreases much more slowly for PDE 4 in Figure 7(b) for between 0 <em>&lt; t &lt; </em>500.

One also notices that as <em>kx </em>increases, both systems show a decreasing slope in the power spectra i.e. the slope becomes more negative at a given time. However, the rate at which the slope becomes more negative is considerably higher for PDE 3 as compared to PDE 4, which is evident also by the vastly different time scales on the colorbars. This is likely because PDE 3 resembles a Gaussian, with broadening bell curves and lowering peaks as time progresses. On the other hand, the shock frontiers in PDE 4 prevent the system from becoming symmetric, and instead of a gradual bell curve-like fall, the system exhibits a drastic fall.