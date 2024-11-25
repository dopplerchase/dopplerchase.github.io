---
permalink: /current-research/
title: "Current Research"
---

![DataDrivenModels](/assets/images/AI4NWP_Dalle3.jpeg) 

My current research centers on using machine learning for various meteorology tasks. I work on three primary projects: Satellite-based 3D global cloud field analysis ([OVERCAST](https://overcast.cira.colostate.edu/overcast-news)) sponsored by the Office of Naval Research; INvestigation of Convective UpdraftS ([INCUS](https://incus.colostate.edu/)) sponsored by NASA; and a NOAA sponsored project working on AI weather forecast models. 

**TL;DR:** I use the latest machine learning techniques to enhance satellite, radar and weather forecast tools. 


<h1> OVERCAST </h1> 

![OVERCASTIMAGE](https://overcast.cira.colostate.edu/overcast-static/overcastpic.png) 

OVERCAST is a project aimed at creating a global, 3D, near real-time atmospheric cloud field analysis based on existing satellite sensors operated by a variety of agencies worldwide. We have near global coverage of meteorological satellite imagery but combining these sensors into a coherent, seamless grid of 3d clouds is a non-trivial task. A large contingent at CIRA are working on creating this product. 

<h2> Diffusion Models for Nowcasting GOES Imagery </h2>

The overall OVERCAST goal is an instantaneous field of 3d clouds. This is useful but potentially more useful is a forecast of where clouds will be. There are several methods for forecasting clouds which includes: advection (based on physics models), optical flow and machine learning. I am working on the machine learning based forecasts. 

![DiffusionPNG](/assets/images/noisy_hurricane.png) 
*AI generate image of a hurricane with noise added*

In the past few years, data-driven models (i.e., models that only use AI to do the forecast) have disrupted traditional forecasting techniques (e.g., [GraphCast](https://www.science.org/doi/10.1126/science.adi2336); [GenCast](https://arxiv.org/abs/2312.15796); [CorrDiff](https://arxiv.org/abs/2309.15214); [StormCast](https://research.nvidia.com/publication/2024-08_kilometer-scale-convection-allowing-model-emulation-using-generative-diffusion)). One of my goals for OVERCAST is to bring this new technology to the satellite-cloud space. 

![DiffusionGif](/assets/images/diffusion_noise.gif) 
*GOES IR imagery of Hurricane Lee (2023) and noise being added to it*

Over the past year, I have been mastering diffusion models, which train machine learning models to remove artificial noise from an image (see image above), teaching it how to generate data it was trained on. I've successfully implemented the same diffusion method as GenCast and CorrDiff on GOES-16 imagery. So far I have been able to forecast the future hour of satellite imagery, beating a plain CNN/Unet and persistence. A comparison to HRRR will come later. A paper explaining diffusion at a more digestible level and showing off these nowcasting results is being drafted and will be submitted to AIES and arXiv in the coming months. 

![DiffusionGif2](/assets/images/DiffusionForecast_6hr.gif) 
*A diffusion model forecast of IR temperature from GOES. This 6 hour forecast only uses 2 input images (the last 20 mins) to forecast out the next 10 mins, repeated to get a 6 hour forecast. No physics is explicitly coded.*

Other researchers at CIRA have adapted the method to work with synthetic microwave imagery, in painting missing IR data, turbulence diagnosis from satellite. So far, diffusion models seem to instantly improve sharpness of machine learning images, a common issue.

<h1> INCUS </h1> 

![INCUSIMAGE](https://incus.colostate.edu/static/7a03237238052221234f3bc7d4b96703/8a89b/clean_incus_example.webp) 
*Artist rendering of the 3 INCUS spacecraft on orbit*

INCUS is a NASA mission looking to quantify the convective mass flux (i.e., how much and how fast air moves) of global thunderstorms. Our physics based global weather forecasts are beginning to simulate the atmosphere at scales that can begin to resolve thunderstorms. Since this is the first time, there are no observational constraints of the spatial distribution of convective mass flux, especially over places like central Africa where storms are frequent. INCUS will measure convective mass flux using a novel spaceborne radar concept, using time differencing of 3 radars. The general idea is to see how a storms reflectivity changes, which is related to how fast the air is moving upward. 

<h2> Multi-frequency observations of storms </h2>

![CHASE2024IMAGE](/assets/images/Chase2024_Example.png) 
*Figure 2 from Chase et al. (2024) showing an example radar sample of an MCS over the USA observed by Ku-, Ka- and W-band radars*

One outstanding question as INCUS is being built is "What can we expect to see from our Ka-band (8 mm wavelength) radars within convection?". Shorter wavelength radars (like Ka-band) tend to have added challenges with loss of signal that make retrievals from radar a bit more complicated. Unfortunately, longer wavelength radars cost more (primarily due to size), thus many missions have to choose a shorter wavelength like Ka-band or W-band (3 mm). 

To help answer the question of what Ka-band will see in convection, we leverage the large database of GPM data (a Ku-, Ka-band radar) and coincidences with CloudSat (a W-band radar). We analyze the data within storms globally and show that the Ka-band performs similarly to the longer wavelength Ku-band in many aspects. Thus, the Ka-band choice shouldn't hinder INCUS efforts when on orbit. If you want more specific details, check out our preprint [Chase et al. 2024](https://arxiv.org/abs/2406.17110).


