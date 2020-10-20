Group Mass, Group Critical 200 Mass, Group Critical 500 Mass, 
Group Mean Mass 200, Group Mean Mass 500, 
Group Radius Critical 200, Group Radius TopHat 200, Group Mass TopHat 200,

 We use these to predict the following attributes that accumulate through cosmic time due to a  wide  range  of  non linear processes:  star formation rate, black hole mass, stellar mass of the galaxies, metallicity and \textit{g-r} color. 






SELECT 
    halo.GroupMass as GroupMass, 
    halo.Group_M_Crit200 as Halo200Mass, 
    halo.Group_R_Crit200 as Halo200Radius, 
    halo.Group_M_Crit500 as Halo500Mass, 
    halo.Group_R_Crit500 as Halo500Radius, 
    halo.Group_M_TopHat200 as HaloTopHatMass, 
    halo.Group_R_TopHat200 as HaloTophatRadius, 
    halo.Group_M_Mean200 as HaloMeanMass200, 
    halo.Group_R_Mean200 as HaloMeanRadius200, 
    halo.Group_M_Mean500 as HaloMeanMass500, 
    halo.Group_R_Mean500 as HaloMeanRadius500, 
    aperture.Mass_BH as massCentralBlackHole, 
    aperture.Mass_Star as stellarMass,
    aperture.Mass_Gas as gasMass, 
    gal.HalfMassRad_Star as RadiusStellar 
    
	
  
 FROM 
    RefL0100N1504_FOF as halo, 
    RefL0100N1504_SubHalo as gal, 
    RefL0100N1504_Aperture as aperture  
  
  
 WHERE 
    
    aperture.GalaxyID = gal.GalaxyID  
    AND gal.SubGroupNumber = 0
    AND gal.MassType_DM > 1.0e9
    AND aperture.ApertureSize = 30
    AND halo.GroupID = gal.GroupID
    AND halo.SnapNum = gal.SnapNum
    AND gal.SnapNum = 28
    


