
# Astrocyte ion dynamics - glutamate model replication

     ```markdown
     [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1UKbpOCXTUBWOHiykV6zH264pMnAiy0o_?usp=sharing)
     ```

Learning replication of Ullah lab astrocyte ion homeostasis models (Thapaliya et al., 2023; Meyer et al., 2025), implemented from scratch in Python as a single-compartment astrocyte model (and subsequently subcompartments).

This project is a small computational neuroscience lab exercise where I learned how to read existing models and build a single-compartment astrocyte model of ion homeostasis using Python and Google Colab.

The model is based on biophysical fluxes and parameters from Ullah lab work on astrocytic ion dynamics. I used these papers (and their associated code) as references for the flux equations, parameter choices, and modeling assumptions. However, all code in this repository is written and organized by me as a personal learning and replication exercise.

This repo is *not* the official code for those papers; any mistakes are my own.

**References**

1. Thapaliya et al. (2023). *Modeling the heterogeneity of sodium and calcium homeostasis between cortical and hippocampal astrocytes and its impact on bioenergetics.*  
   DOI: <https://doi.org/10.3389/fncel.2023.1035553>

2. Meyer et al. (2025). *Local differences in baseline sodium shape astrocytic potassium uptake by the NKA.*  
   DOI: <https://doi.org/10.1101/2025.11.18.687951>

---

## Project context

- **Type of project:** Personal learning / mini research project in computational neuroscience  
- **Focus:** Astrocyte ion homeostasis and glutamate-dependent Na⁺/K⁺ dynamics  
- **Motivation:** Build a mechanistic model of how astrocytes maintain ionic balance and support glutamate uptake, as a foundation for future work on neuron–glia interactions and memory-related network stability.  
- **Lab:** Ghanim Ullah Biophysics Lab, University of South Florida  
- **Timeframe:** Fall 2025  
- **Goal:** Learn basic skills in mechanistic modeling and good coding practices; simulate ion dynamics related to glutamate flux in a single-compartment astrocyte model, then extend to sub-compartments using real neuromorphological data.

---

## What the notebook does (current v1)

The current notebook `astrocyte_ion_homeostasis_replication_v1.ipynb`:

1. **Defines biophysical parameters**  
   - Ionic concentrations (Na⁺, K⁺, Cl⁻) inside and outside an astrocyte  
   - Conductances for leak channels and cotransporters  
   - Na⁺/K⁺-ATPase strength and affinities  
   - Volume and conversion factors  

2. **Implements ion fluxes as functions**  
   - Na⁺ and K⁺ leak currents  
   - Cl⁻ leak current  
   - Na⁺/K⁺-ATPase (NKA) pump  
   - NKCC and KCC1 cotransport  
   - Na⁺-bicarbonate cotransporter (NBC)  
   - Na⁺/H⁺ exchanger (NHE)  
   - Na⁺/Ca²⁺ exchanger (NCX)  
   - Na⁺-dependent glutamate transporter (EAAT-like)

3. **Formulates a system of coupled ODEs**  
   - Time derivatives for intracellular Na⁺, K⁺, Cl⁻  
   - Membrane potential dynamics based on the total transmembrane current  

4. **Runs time-domain simulations**  
   - Baseline simulations to check whether ion concentrations drift or reach a steady state  
   - Visualizations of ion trajectories and steady-state behavior  

5. **Plots and interprets outcomes**  
   - Time courses of ion concentrations and membrane potential  
   - How changes in Na⁺ driving force impact glutamate transport and K⁺ uptake via the NKA  

---

## Methods and tools

- **Language:** Python (Google Colab)  
- **Key libraries:**
  - `NumPy` for numerical calculations  
  - `SciPy` (`odeint`) for solving ordinary differential equations  
  - `matplotlib` for visualization  
- **Model type:**
  - Single-compartment astrocyte  
  - Mechanistic flux-based ODE system (each term corresponds to a specific channel or transporter)

Biophysically, each term in the ODEs is grounded in Ullah lab astrocyte models and represents a specific transporter or channel flux.

---

## Why this project matters

Astrocytes are key regulators of extracellular K⁺, glutamate clearance, and metabolic support for neurons. Their Na⁺ gradient powers many of these processes. Modeling astrocytic ion dynamics is an important step toward:

- Understanding neuron–glia interactions in realistic networks  
- Connecting ionic homeostasis to synaptic transmission and memory stability  
- Building multiscale models that link single-cell biophysics to cognitive-level phenomena  

This repo is my starting point for that line of work—a first step toward more advanced projects in neural modeling and memory research.

---

## Future directions

**Next goals to be implemented soon**

- Parameter sweeps for various ions (especially Na⁺)  
- Add explicit Ca²⁺ dynamics  
- Add NMDA and AMPA receptor fluxes to represent glutamate-evoked Na⁺ and Ca²⁺ entry more completely  
- Introduce astrocytic sub-compartments (soma and processes) to study local Na⁺ microdomains and their impact on glutamate uptake  
- Incorporate real neuromorphological data for astrocyte geometry and distances  
- Explore how distance between soma and processes and differences in local Na⁺ affect glutamate flux and K⁺ uptake  

**Longer-term ideas**

- Embed the astrocyte model into simple neural networks to study how astrocytic ion homeostasis contributes to memory-related network function and stability  
- Analyze additional datasets from experimental labs and compare model predictions to data  

---

## How to run the notebook

1. Click on `astrocyte_ion_homeostasis_replication_v1.ipynb` in this repo.  
2. Download the notebook and upload it into your own Google Colab environment.  
3. In Colab, install any missing packages (for example):

   ```python
   !pip install numpy scipy matplotlib

