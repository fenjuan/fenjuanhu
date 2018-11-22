# Methodology
Modulized calibration:<br/>
1. Group state variables according to different variables(modified AN's script to output all the state variables) <br/>
2. Test the sensitivity of each module by just add 10x/100x exchange rates in each module to see the response<br/>
3.






#Parameter tracking
fabm.yaml file modification
### abiotic_water module:
```
abiotic_water:
  long_name: abiotic_process_in_water
  model: au/pclake/abiotic_water
  use: true
  initialization:
    sNH4W: 0.05
    # Amonia in water (g m-3)
    sNO3W: 0.42
    # Nitrates in water (g m-3)
    sPO4W: 0.25
    # Phosphate in water (g m-3)
    sPAIMW: 0.0
    # Absorbed_P in water (g m-3)
    sSiO2W: 1.2
    # Silica dioxide in water (g m-3)
    sO2W: 10.6
    # oxygen in water (g m-3)
    sDIMW: 5.0
    # Inorg. matter in water (g m-3)
    sDDetW: 2.5
    # detritus dry-weight in water (g m-3)
    sPDetW: 0.00625
    # detritus phosphrus in water (g m-3)
    sNDetW: 0.0625
    # detritus nitrogen in water (g m-3)
    sSiDetW: 0.025
    # detritus silica in water (g m-3)
  parameters:
    cCPerDW: 0.4
    #C content of organic matter (gC/gDW), default = 0.4
    cExtSpDet: 0.15
    #specific extinction detritus (m2/gDW), default = 0.15
    cKPAdsOx: 0.6
    # P adsorption affinity at oxidized conditions (m3/gP), default = 0.6
    cRelPAdsAl: 0.134
    # max. P adsorption per g Al (gP/gAl), default = 0.134
    cRelPAdsD: 3e-05
    # max. P adsorption per g DW (gP/gD), default = 3e-05
    cRelPAdsFe: 0.065
    # max. P adsorption per g Fe (gP/gFe), default = 0.065
    cThetaAer: 1.024
    # temperature coeff. for reaeration (1/e^oC), default = 1.024
    cThetaMinW: 1.07
    # expon. temp. constant of mineralization in water ([-]), default = 1.07
    cThetaNitr: 1.08
    # temperature coefficient for nitrification ([-]), default = 1.08
    cVSetDet: -0.25
    # max. sedimentation velocity of detritus (m/day), default = -0.25
    cVSetIM: -1.0
    # max. sedimentation velocity of inert org. matter (m/day), default = -1.0
    fAlDIM: 0.01
    # Al content of inorg. matter (gAl/gD), default = 0.01
    fFeDIM: 0.01
    # Fe content of inorg. matter (gFe/gD), default = 0.01
    fRedMax: 0.9
    # max. reduction factor of P adsorption affinity ([-]), default = 0.9
    hNO3Denit: 2.0
    # quadratic half-sat. NO3 conc. for denitrification (mgN/l), default = 2.0
    hO2BOD: 1.0
    # half-sat. oxygen conc. for BOD (mgO2/l), default = 1.0
    hO2Nitr: 2.0
    # half sat.oxygen conc. for for nitrogen (mgO2/l), default = 2.0
    kDMinDetW: 0.01
    # decomposition constant of detritus (day-1), default = 0.01
    kNitrW: 0.1
    # nitrification rate constant in water (day-1), default = 0.1
    kPSorp: 0.05
    # P sorption rate constant not too high -> model speed day (day-1), default = 0.05
    NO3PerC: 0.8
    # denitrified per mol C mineralised (molNO3), default = 0.8
    O2PerNH4: 2.0
    # used per mol NH4+ nitrified (molO2), default = 2.0
```
###Abiotic_sediment:
```
abiotic_sediment:
  long_name: abiotic_process_in_sediment
  model: au/pclake/abiotic_sediment
  use: true
  initialization:
    sNH4S: 0.02
    # Sediment Amonia (g m-2)
    sNO3S: 0.002
    # Sediment Nitrates (g m-2)
    sPO4S: 0.181703
    # Sediment Phosphate (g m-2)
    sPAIMS: 0.053618
    # SED_Absorbed Phosphate (g m-2)
    sDIMS: 10409.5
    # sediment inorg.Matter (g m-2)
    sDDetS: 81.27206
    # sediment detritus DW (g m-2)
    sNDetS: 2.031802
    # sediment detritus N (g m-2)
    sPDetS: 0.20318
    # sediment detritus P (g m-2)
    sSiDetS: 0.812721
    # sediment detritus Si (g m-2)
    sDHumS: 1544.169
    # sediment Humus DW (g m-2)
    sNHumS: 77.20846
    # sediment Humus N (g m-2)
    sPHumS: 7.720846
    # sediment Humus P (g m-2)
  parameters:
    cDepthS: 0.1
    # sediment depth (m), default = 0.1
    fRefrDetS: 0.15
    # nutrient diffusion distance as fraction of sediment depth ([-]), default = 0.15
    kDMinDetS: 0.002
    # decomposition constant of sediment detritus (d-1), default = 0.002
    cThetaMinS: 1.07
    # expon. temp. constant of sediment mineralization ([-]), default = 1.07
    cCPerDW: 0.4
    # C content of organic matter (gC/gDW), default = 0.4
    O2PerNH4: 2.0
    # O2 used per mol NH4+ nitrified (mol), default = 2.0
    kNitrS: 1.0
    # nitrification rate constant in sediment (d-1), default = 1.0
    cThetaNitr: 1.08
    # temperature coefficient for nitrification ([-]), default = 1.08
    NO3PerC: 0.8
    # NO3 denitrified per mol C mineralised ([-]), default = 0.8
    hNO3Denit: 2.0
    # quadratic half-sat. NO3 conc. for denitrification (mgN/l), default = 2.0
    kPSorp: 0.05
    # P sorption rate constant not too high -> model speed (d-1), default = 0.05
    cRelPAdsD: 3e-05
    # max. P adsorption per g DW (gP/gD), default = 3e-05
    cRelPAdsFe: 0.065
    # max. P adsorption per g Fe (gP/gFe), default = 0.065
    fFeDIM: 0.01
    # Fe content of inorg. matter (gFe/gD), default = 0.01
    cRelPAdsAl: 0.134
    # max. P adsorption per g Al (gP/gAl), default = 0.134
    fAlDIM: 0.01
    # Al content of inorg. matter (gAl/gD), default = 0.01
    fRedMax: 0.9
    # max. reduction factor of P adsorption affinity ([-]), default = 0.9
    cKPAdsOx: 0.6
    # P adsorption affinity at oxidized conditions (m3/gP), default = 0.6
    kPChemPO4: 0.03
    # chem. PO4 loss rate (d-1), default = 0.03
    coPO4Max: 1.0
    # max. SRP conc. in pore water (mgP/l), default = 1.0
    bPorS: 0.847947
    # sediment porosity (m3 water m-3 sediment), default = 0.847947
    cThetaDif: 1.02
    # temperature coefficient for diffusion ([-]), default = 1.02
    fDepthDifS: 0.5
    # utrient diffusion distance as fraction of sediment depth ([-]), default = 0.5
    kNDifNH4: 0.000112
    # mol. NH4 diffusion constant (m2/day), default = 0.000112
    cTurbDifNut: 5.0
    # bioturbation factor for diffusion ([-]), default = 5.0
    bPorCorS: 0.737275
    # sediment porosity, corrected for tortuosity (m3 water m-3 sediment), default = 0.737275
    kNDifNO3: 8.6e-05
    # mol. NO3 diffusion constant (m2/day), default = 8.6e-05
    kPDifPO4: 7.2e-05
    # mol. PO4 diffusion constant (m2/day), default = 7.2e-05
    kO2Dif: 2.6e-05
    # mol. O2 diffusion constant (m2/day), default = 2.6e-05
    cTurbDifO2: 5.0
    # bioturbation factor for diffusion ([-]), default = 5.0
    kDMinHum: 1e-05
    # maximum_decomposition_constant_of_humic_material_(1D-5) (d-1), default = 1e-05
  coupling:
    oxygen_pool_water: abiotic_water/sO2W                     # oxygen_pool_water (g m-3)
    SiO2_generated_by_mineralization: abiotic_water/sSiO2W    # SiO2_generated_by_mineralization (g m-3)
    NH4_diffusion_flux: abiotic_water/sNH4W                   # NH4_diffusion_flux (g m-3)
    NO3_diffusion_flux: abiotic_water/sNO3W                   # NO3_diffusion_flux (g m-3)
    PO4_diffusion_flux: abiotic_water/sPO4W                   # PO4_diffusion_flux (g m-3)
```
