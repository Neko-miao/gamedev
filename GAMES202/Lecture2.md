# Recap of CG Basics 

## Graphics Pipeline  

- Vertex Processing  
- Triangle Processing  
- Rasterization  
- Fragment Processing  
- Framebuffer Operation  


## OpenGL  
- a set of APIs that call the GPU pipeline from CPU  
    - Cross platform  
    - Alternatives (DX, Vulkan, etc.)  

- Cons  
    - Fragmented:a lots of different versions  
    - C style, not easy to use  
    - Cannot debug(?)

- Important analogy: oil painting  
     A. Place objects/models  
     - Model specification  
     - Model transformation  
     B. Set position of an easel
     - View transformation  
     - Create / use a framebuffer    
     C. Attach a canvas to the easel  
      
     D. Paint to the canvas  
     E. (Attach other canvases to the easel and continue painting)  
     F. (Use previous paintings for reference  )


## OpenGL Shading Languages(GLSL)  


## Shader Setup  
- Initializing  
    - Cetate shader (vertex and fragment)  
    - Compile shader  
    - Attach shader to program  
    - Link program  
    - Use program  
- Shader source is just sequence of string  
- Similar steps to compile a normal program  


## The Rendering Equation  
