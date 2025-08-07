# Pegleg README

## Outline

**Goal: PSF-corrected spatially resolved SED fitting. Use imcascade (Miller & van Dokkum 2021?) to psf-correct postage stamps. Do pixel-by-pixel SED fitting with Parrot. Ideally do this in the existing pirate environment? Release code.** 

### Steps:
1. [ ] **1.** Get Bluejay mosaics and psfs from Vanessa 

2. [ ] **2.** Download imcascade  

3. [ ] **3.** In collaboration with Vanessa, get imcascade running and validate fits on Vanessa’s same objects  
   - [ ] **i.**   Masks mask correct objects 
   - [ ] **ii.**  Background is close to zero 
   - [ ] **iii.** Model looks like object 
   - [ ] **iv.**  Residuals are generally small <20% of the flux in a given pixel 
   - [ ] **v.**   Sizes and fluxes are similar to what Chloe measured for the same objects. If not, let’s discuss, Chloe’s could also be wrong!

4. [ ] **4.** Also in collaboration with Vanessa, psf-correct each band and validate that these worked. To PSF-correct, add the residuals back to the model **not convolved with the PSF**
   - [ ] **i.**   PSF-corrected image should look roughly like original images but with more concentrated light in the center
   - [ ] **ii.**  Test the psf-correction of LW vs. SW bands to understand if there is a fractional amount of the original spatial resolution we recover. This is a key  question. If e.g. we can consistently correct to say 1/2 the original spatial resolution, we are going to get biased results. If this is the case, I think         we’ll need to PSF-match all the bands to the longest wavelength band then PSF-correct them all with that PSF. To check this, divide the psf-corrected              images and radial profiles of F150W and F444W to see if the F150W is consistently sharper in the center. We might have to do this anyways so we don’t have         weird shit in the outskirts. Fuck it maybe just do this.
   - [ ] **iii.** Check that images in different bands are registered correctly with respect to each other. 
5. [ ] **5.** Perform spatially resolved SED fitting on the psf-corrected images using the prospector emulator parrot and validate the fits. (Could also use another SED fitter like Kartheik’s?)
   - [ ] **i.**   Check that the fit residuals are small
   - [ ] **ii.**  Check that the sum of the stellar mass in the pixels is similar to the integrated stellar mass. Same with SFR. 
   - [ ] **iii.** Look at maps. Do they make sense? Mass maps should roughly peak in the center for most objects. Shouldn’t vary wildly from pixel to pixel. Same with SFR and Av maps. 
   - [ ] **iv.** Determine what SNR is required to get fits that actually give information that’s not just the prior
   - [ ] **v.**  Explore a potential binning scheme for low SNR pixels. Explore a way of extrapolating M/L_F444W to large radius to have a continuous mass profile by applying the M/L to the light
   - [ ] **vi.** Compare M, color, and light profiles. Does the M/L change fairly continuously with the color? It should.
   - [ ] **vii.** Test on an object with an IFU spectrum. Do predicted spectral features roughly match observed ones?
6. [ ] **6.** Build package and make documentation

