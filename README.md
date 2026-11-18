# OpenGL Rendering Engine
This is a barebones OpenGL renderer coded using C++.

I wanted to follow a written guide so i could read and attempt to understand what i am coding and how it works.
My initial goals for this project are to learn and understand OpenGL and to build a renderer that can:
- Display basic 3D  shapes in a lit scene
- Have a camera that can move around the scene
- Textures and materials on the 3D shapes
- Display imported 3D models
- Use  materials for rendering (Normal maps, Roughness maps, Diffuse maps)
- Create a base render engine that I can use to create my own 3D games in the future.

made following the guide from [learnopengl](https://learnopengl.com/)
Image importer from [stb_image](https://github.com/nothings/stb/blob/master/stb_image.h

<img width="1920" height="1080" alt="Screenshot (10)" src="https://github.com/user-attachments/assets/4d53c544-ec60-4716-9e2f-82e99334ee32" />
I started here drawing a simple Triangle to the GPU with a fragment shader to add the gradient colour.

<img width="1920" height="1080" alt="Screenshot (11)" src="https://github.com/user-attachments/assets/7af8fd8d-44a6-483c-89dd-7b380b5d198c" />
Then I combined 2 triangles to create a rectangle with a simple brick texture.

<img width="1920" height="1080" alt="Screenshot (13)" src="https://github.com/user-attachments/assets/02f65a05-ca3e-4df3-9de1-af004ee65b87" />
After this I learned how to transform the shape, here you can see this shape would be used as the front face to a cube.

<img width="1920" height="1080" alt="Screenshot (14)" src="https://github.com/user-attachments/assets/c619b11b-e9c9-4057-bfcf-eabbb09ff3a6" />
then I added 5 more squares and transformed them to create a cube but there is an issue with depth drawing.

<img width="1920" height="1080" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/668664e0-510b-441b-a40b-260139a6e1fb" />
Which I fix here by creating a depth texture to determine draw order.

<img width="1920" height="1080" alt="Screenshot (22)" src="https://github.com/user-attachments/assets/cf5ddbac-dcc9-4903-9e12-79f02f9af9d9" />
Next I added a simple light that colours the side of the cube based on the normal direction from the light position.

<img width="1920" height="1080" alt="Screenshot (25)" src="https://github.com/user-attachments/assets/7395f1b4-1690-4c5e-b83e-ffcd453b6e04" />
And I added a specular highlight, combining ambient, diffuse and specular in phong lighting.

<img width="1920" height="1080" alt="Screenshot (35)" src="https://github.com/user-attachments/assets/0e0a2339-047f-4d40-b9b8-56140daf30f8" />
Next I added a texture to the cube, and a specular texture for more realistic lighting.

<img width="1920" height="1080" alt="Screenshot (38)" src="https://github.com/user-attachments/assets/35b85a43-bdbb-4eff-8896-3556561022c1" />
Here i added a point light which will fade with distance.

<img width="1920" height="1080" alt="Screenshot (40)" src="https://github.com/user-attachments/assets/0bba0a31-b690-45d3-bb17-6b1233a0cefd" />
After that i used assimp to import OBJ models, here i have a two barrels lit with only ambient light.

<img width="1920" height="1080" alt="Screenshot (43)" src="https://github.com/user-attachments/assets/58259eff-81b1-49d3-a0b9-09d0e5f5a413" />
Next I lit the barrels model with point lights altering my previous fragment shader and added a woodel floor for projecting shadows in the future.

<img width="1920" height="1080" alt="Screenshot (46)" src="https://github.com/user-attachments/assets/47f2c6f0-6139-449a-a837-cf57f793af17" />
For optimization i added backface-culling, which reduces draw calls and triangle count by at least 50%.

<img width="1920" height="1080" alt="Screenshot (114)" src="https://github.com/user-attachments/assets/cbcee8a9-bcc7-4e9c-99d8-3cd2b833ba40" />
I was running into issues with my normal map and point light shadows (which use a cubemap at each light to generate shadows)

<img width="1920" height="1080" alt="Screenshot (122)" src="https://github.com/user-attachments/assets/b3162dbe-f42d-436d-9a96-194497c030c2" />
I got this working after finding out the shadows, specular and normal map were using the wrong texture.

This is the finished result with shadows and a diffuse, specular and normal map. I now want to use this to create a simple game, so I will need to implement many more features like skeletal animation, collisions, particles, text rendering and much more.
