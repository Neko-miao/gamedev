# Real-Time Shadow 1  
- Recap: shadow mapping
- The math behind shadow mapping   
- Percentage closer soft shadows  
- Basic filtering teciniques  

## Shadow Mapping  

- A 2-pass Algorithm  
    - The light pass generates the SM
    - The camera pass uses the SM  

- An image-space algorithm  
    - Pro: no knowledge of scenes's geometry is required  
    - Con: causing self occlusion and aliasing issues  

### Shodw Mapping Process  
- Pass 1: Render from Light  
    - Output a depth texture from the light source  
- Pass 2 : render from Eye  
    - Render a standard image from the eye  

### Shadow Mapping Results  
good but not perfect  
problem:
- self occlusion  
    - precision of shadow map  
    - direction of light  
    - Adding a (variable) bias to reduce self occlusion, but introducing detached shadow issue  

### Issues in Shadow Mapping  
- Second-depth shadow mapping*  
    - Using the midpoint betwween first and second depths in SM  
    - Unfortunately, requeires objects to be watertight  
    - And the overhead may not worth it  



!!! RTR does not trust in COMPLEXITY  

- Aliasing  

## Math behind Shadow Mapping  
In RTR, we care more about "approximatedly equal"


## Percentage closer soft shadows  

### Percentage Closer Filtering(PCF)  
 
