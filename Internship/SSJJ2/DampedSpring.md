# Damped Springs  
## Background  
In numerous games, players' motion may often create sharp, discontinuous changes in dierction, speed or even position, such as Gun Tick. To solve this problem, we should make sure the camera:

- Avoid discontinuities in motion.
- Never let player outrun the camera.
- Move exactly the same with respect to time regardless of frame rate.  

