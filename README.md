# Optimizing Illumination with Least_Squares: A Lamp Power Distribution Problem
This repository focuses on optimizing area illumination using a set of lamps, employing the least squares method. It includes code for calculating optimal lamp powers, visualizing illumination patterns, and handling constraints like energy limits. Additional challenges involve optimizing lamp positions for improved results.

## Overview

The objective of this project is to address the problem of illuminating an area using a set of lamps. The area is divided into $\( m \)$ regions or pixels, and we aim to achieve the desired illumination pattern across these regions. The lighting level in each region is represented as $\( l_i \)$, forming an $\( m \)-vector$ $\( \mathbf{l} \)$ that represents the illumination levels across all regions. The power at which each lamp operates is denoted as $\( p_i \)$, forming an $\( n \)$-vector $\( \mathbf{p} \)$ representing the lamp powers.

To establish a relationship between the lamp powers and the illumination levels, we introduce matrix $\( \mathbf{A} \)$, an $\( m \times n \)$ matrix. The illumination level $\( \mathbf{l} \)$ can be expressed as a linear function of the lamp powers $\( \mathbf{p} \)$, i.e., 

$$
\mathbf{l} = \mathbf{A}\mathbf{p}
$$

Each column of matrix $\( \mathbf{A} \)$ represents the illumination pattern when a specific lamp is powered on, with all other lamps off. It is assumed that $\( \mathbf{A} \)$ has linearly independent columns, making it a tall matrix. Furthermore, the $\( i \)-th$ row of $\( \mathbf{A} \)$ represents the sensitivity of pixel $\( i \)$ to the lamp powers.

The goal is to find lamp powers $\( \mathbf{p} \)$ that result in a desired illumination pattern $\( \mathbf{l}_{\text{des}} \)$, such as a uniform illumination pattern where all regions have the same value (e.g., $ \( \mathbf{l}_{\text{des}} = [1,1,1,...,1] \) $). To achieve this, we utilize the method of least squares to find an estimate $\( \hat{\mathbf{p}} \)$ that minimizes the sum square deviation between $\( \mathbf{A}\mathbf{p} \)$ and $\( \mathbf{l}_{\text{des}} \)$, i.e., minimize 

$$
\| \mathbf{A}\mathbf{p} - \mathbf{l}_{\text{des}} \|^2
$$

The project aims to find the lamp powers that approximate the desired illumination pattern $\( \mathbf{l}_{\text{des}} \)$ using least squares optimization.

The specific problem considered in this project involves a scenario with $\( n = 10 \)$ lamps and an area represented by a $\( 25 \times 25 \)$ grid, resulting in $\( m = 625 \)$ pixels. Each pixel occupies an area of $\( 1 \text{ m}^2 \)$. The positions and heights above the floor for the lamps are provided as coordinates. The illumination decays according to an inverse square law, where $\( A_{ij} \)$ is proportional to the inverse square of the distance $\( d_{ij} \)$ between the center of the pixel and the lamp position. The matrix $\( \mathbf{A} \)$ is scaled such that when all lamps have power one, the average illumination level is one. The desired illumination pattern $\( \mathbf{l}_{\text{des}} \)$ is a uniform pattern with a value of 1.

### Tasks:

1. **Visualization**:
   - Create two graphs using colormaps to visualize the illumination of two patterns: one with all lamps set to a power of 1 and another pattern that minimizes the sum square deviation from the desired uniform illumination. Calculate and compare the Root Mean Squared (RMS) errors in both cases.

2. **Histogram Analysis**:
   - Generate histograms of the patch illumination values for two scenarios: when all lamp powers are set to one and when lamp powers are determined using the least squares optimization. Analyze and discuss the results obtained from the histograms.

3. **Constraint Optimization**:
   - Introduce an additional constraint to the lamp power distribution problem. The total energy consumption of the lamps is constrained to be equal to 10, and none of the lamp powers can be negative. Find the new power distribution of the lamps that ensures the least squares optimality under these constraints.

4. **Optimization Challenge**:
   - As an additional challenge, attempt to improve the RMS error obtained in the first question by exploring different random choices of lamp positions. Search for new points for the lamps, allowing them to be at any height between 4 and 6 meters within the defined area. The total energy consumption of the lamps will remain at 10, and none of the lamp powers can be negative. Present the colormap picture of the illumination and the histogram of the intensities of the pixels for this improved solution.


### Additional Information

The repository also includes a `Report.pdf` that briefly explains our approach and methodology used to solve the problem.
