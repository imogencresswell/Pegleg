# Pegleg README

## Outline

** Goal: PSF-corrected spatially resolved SED fitting. Use imcascade (Miller & van Dokkum 2021?) to psf-correct postage stamps. Do pixel-by-pixel SED fitting with Parrot. Ideally do this in the existing pirate environment? Release code.** 

Steps:
Get Bluejay mosaics and psfs from Vanessa
Download imcascade
In collaboration with Vanessa, get imcascade running and validate fits on Vanessa’s same objects
Masks mask correct objects
Background is close to zero
Model looks like object
Residuals are generally small <20% of the flux in a given pixel
Sizes and fluxes are similar to what Chloe measured for the same objects. If not, let’s discuss, Chloe’s could also be wrong!
Also in collaboration with Vanessa, psf-correct each band and validate that these worked. To PSF-correct, add the residuals back to the model *not convolved with the PSF*
PSF-corrected image should look roughly like original images but with more concentrated light in the center
Test the psf-correction of LW vs. SW bands to understand if there is a fractional amount of the original spatial resolution we recover. This is a key question. If e.g. we can consistently correct to say 1/2 the original spatial resolution, we are going to get biased results. If this is the case, I think we’ll need to PSF-match all the bands to the longest wavelength band then PSF-correct them all with that PSF. To check this, divide the psf-corrected images and radial profiles of F150W and F444W to see if the F150W is consistently sharper in the center. We might have to do this anyways so we don’t have weird shit in the outskirts. Fuck it maybe just do this.
Check that images in different bands are registered correctly with respect to each other. 
Perform spatially resolved SED fitting on the psf-corrected images using the prospector emulator parrot and validate the fits. (Could also use another SED fitter like Kartheik’s?)
Check that the fit residuals are small
Check that the sum of the stellar mass in the pixels is similar to the integrated stellar mass. Same with SFR. 
Look at maps. Do they make sense? Mass maps should roughly peak in the center for most objects. Shouldn’t vary wildly from pixel to pixel. Same with SFR and Av maps. 
Determine what SNR is required to get fits that actually give information that’s not just the prior
Explore a potential binning scheme for low SNR pixels. Explore a way of extrapolating M/L_F444W to large radius to have a continuous mass profile by applying the M/L to the light
Compare M, color, and light profiles. Does the M/L change fairly continuously with the color? It should.
Test on an object with an IFU spectrum. Do predicted spectral features roughly match observed ones?
Build package and make documentation

