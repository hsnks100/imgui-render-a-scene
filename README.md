# imgui-render-a-scene

![image](https://user-images.githubusercontent.com/3623889/42198943-3d6ac8e2-7ec6-11e8-94c3-bf3c702927bb.png)

``` 
    GLubyte texture_data[width*height * 3];
    GLuint texname; //handle to a texture
    glGenTextures(1, &texname); //Gen a new texture and store the handle in texname

    //These settings stick with the texture that's bound. You only need to set them
    //once.
    glBindTexture(GL_TEXTURE_2D, texname);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_NEAREST);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST);

    for(int i=0; i<height/2; i++) {
        for(int j=0; j<width; j++) {
            texture_data[i * width * 3+ j * 3 + 0] = 0xFF;
            texture_data[i * width * 3+ j * 3 + 1] = 0x00;
            texture_data[i * width * 3+ j * 3 + 2] = 0x00;
        }
    }
    for(int i=height/2; i<height; i++) {
        for(int j=0; j<width; j++) {
            texture_data[i * width * 3+ j * 3 + 0] = 0x00;
            texture_data[i * width * 3+ j * 3 + 1] = 0xFF;
            texture_data[i * width * 3+ j * 3 + 2] = 0x00;
        }
    }
```

git clone --recursive https://github.com/hsnks100/imgui-render-a-scene.git

cd imgui-render-a-scene
cmake .
make
./imgui-demo.app



