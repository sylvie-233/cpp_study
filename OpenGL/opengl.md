# OpenGL

> Author: Sylvie233
>
> Date: 23/5/12
>
> Point: 



[TOC]

## 基础介绍

`opengl32.lib`、`glfw3.lib`、`glew32s.lib`、





基础使用

```C+=
#define GLEW_STATIC

#include <GL/glew.h>
#include <GLFW/glfw3.h>

int main() {
	glfwInit()
	glfwWindowHint()
	
	GLFWwindow* window = glfwCreateWindow()
	if (nullptr == window) {
		glfwTerminate()
	}
	
	glfwMakeContextCurrent(window)
	
	glewExperimental = true
	if (GLEW_OK != glewInit()) {
		glfwTerminate()
	}
	
	glViewPort(0, 0, 800, 600)
	
	while (!glfwWindowShouldClose(window)) {
		glfwSwapBuffers(window)
		glfwPollEvents()
	}
	
	glfwTerminate()
	
	return 0;
}
```





<img src="opengl.assets/image-20230519145100579.png" alt="image-20230519145100579" style="zoom:67%;" />

VBO、EBO、VAO、VertexShader、FragmentShader、ShaderProgram、

VAO定义了VBO中点数据的意义，EBO提供了VBO中的索引









### GLFW



### GLEW





### GLAD



### GLM

OpenGL Mathematics数学库





## 核心内容

```
<GL/glew.h>:
	glewExperimental:
	glActiveTexture():
		GL_TEXTURE0:
		GL_TEXTURE1 :
	glAttachShader():
	glBindBuffer(): 绑定VBO
		GL_ARRAY_BUFFER:
		GL_ELEMENT_ARRAY_BUFFER:
    glBindTexture():
	glBindVertexArray(): 绑定VAO
	glBufferData():
		GL_ELEMENT_ARRAY_BUFFER:
	glClear():
		GL_COLOR_BUFFER_BIT:
		GL_DEPTH_BUFFER_BIT:
	glClearColor():
	glCompileShader():
	glCreateProgram():
	glCreateShader():
		GL_VERTEX_SHADER:
	glCullFace():
		GL_BACK:
	glDeleteShader():
	glDrawArrays():
		GL_TRIANGLES:
	glDrawElements():
	glEnable:
		GL_CULL_FACE:
		GL_DEPTH_TEST: 深度测试
	glEnableVertexAttribArray():
	glewInit():
	glGenerateMipmap():
		GL_TEXTURE_2D:
	glGenBuffers(): 生成VBO点数据
	glGenTextures(): 生成纹理
	glGenVertexArrays(): 生成VAO
	glGetProgramiv():
	glGetProgramInfoLog():
	glGetShaderiv():
	glGetShaderInfoLog():
	glGetUniformLocation(): 从shader程序程序中获取uniform变量
	glLinkProgram():
	glPolygonMode():
		GL_FRONT_AND_BACK:
			GL_LINE:
	glShaderSource():
	glTexImage2D(): 根据纹理设置生成图像
		GL_RGB:
	glTexParameteri(): 设置纹理的环绕、过滤方式
		GL_TEXTURE_2D:
			GL_TEXTURE_WRAP_S:
			GL_TEXTURE_WRAP_T:
				GL_REPEAT:
			GL_TEXTURE_MIN_FILTER:
			GL_TEXTURE_MAG_FILTER:
				GL_LINEAR:
	glUniform4f(): 设置uniform变量的值
	glUniformMatrix4fv():
	glUseProgram(): 使用ShaderProgram
	glVertexAttribPointer():
	glViewport():
<GLFW/glfw3.h>:
	GLFWindow:
	glfwCreateWindow():
	glfwGetKey():
		GLFW_KEY_ESCAPE:
	glfwGetTime():
	glfwInit():
	glfwMakeContextCurrent():
	glfwPollEvents():
	glfwSetCursorPosCallback():
	glfwSetInputMode():
	glfwSetScrollCallback():
	glfwSetWindowShouldClose():
	glfwSwapBuffers():
	glfwTerminate():
	glfwWindowHint():
		GLFW_CONTEXT_VERSION_MAJOR:
		GLFW_CONTEXT_VERSION_MINOR:
		GLFW_OPENGL_PROFILE:
			GLFW_OPENGL_CORE_PROFILE:
	glfwWindowShouldClose():
<glm/glm.hpp>
<glm/gtc/matrix_transform.hpp>
<glm/gtc/type_ptr.hpp>:				glm命名空间
	mat4:
	vec3:
	vec4:
		x:
		y:
		z:
	cross():
	lookAt(): // 当前物体坐标、目标坐标、世界Up坐标
	perspective():
	radians(): 角度转弧度
	rotate():
	scale():
	translate():
	value_ptr():
```





### Shader

<img src="opengl.assets/image-20230519150538807.png" alt="image-20230519150538807" style="zoom:67%;" />



#### GLSL

类C语言



向量

<img src="opengl.assets/image-20230519150308341.png" alt="image-20230519150308341" style="zoom:67%;" />



#### VertexShader

```
#version 330 core
layout (location = 0) in vec3 aPos;
layout (location = 1) in vec3 aColor;
layout (location = 2) in vec2 aTexCoord;

out vec4 vertexColor;
out vec2 TexCoord;

void main() {
	gl_Position = vec4(aPos, 1.0);
	vertexColor = vec4(0.5, 0.0, 0.0, 1.0);
	TexCoord = aTexCoord;
}
```



layout中的location与glVertexAttribPointer()中第一个参数意义相同（0~15、最多挖16个变量到Shader中）







#### FragmentShader

```
#version 330 core
out vec4 FragColor;

in vec4 vertexColor;
in vec2 TexCoord;

uniform vec4 xxx; # 在OpenGL程序代码中设定这个变量
uniform sampler2D ourTexture;

void main() {
	FragColor = vertexColor;
	FragColor = texture(ourTexture, TexCoord); # 纹理图片取色
}
```









### Texture

uv纹理贴图

<img src="opengl.assets/image-20230519164759745.png" alt="image-20230519164759745" style="zoom:67%;" />



纹理环绕方式，`[0, 1]`范围外数据处理

纹理过滤

多级渐远纹理(Mipmap)，OpenGL会使用不同的多级渐远纹理，即最适合物体距离的那个

纹理有16个槽位(默认使用0)，切换槽位使用`glActiveTexture()`，并手动设置shader中uniform变量的值(0~15)







### Coordinate

坐标系统

<img src="opengl.assets/image-20230520100950929.png" alt="image-20230520100950929" style="zoom:67%;" />





### Transformation

位移、旋转、缩放

在Shader中通过矩阵运算修改`gl_Position`的值

缩放->旋转->位移

<img src="opengl.assets/image-20230520102124540.png" alt="image-20230520102124540" style="zoom:67%;" />



Z缓冲



### Camera

欧拉角

<img src="opengl.assets/image-20230520111211260.png" alt="image-20230520111211260" style="zoom:67%;" />



View Space、位置+3个轴的向量=4*4向量

<img src="opengl.assets/image-20230520105658693.png" alt="image-20230520105658693" style="zoom:67%;" />



Forward向量，世界Up向量，R向量、Up向量（向量叉乘求垂直向量）|利用欧拉角求Forward向量

<img src="opengl.assets/image-20230520110146857.png" alt="image-20230520110146857" style="zoom:67%;" />

通过View Matrix转换为摄像机的坐标：`glm::lookAt(eye, center, up)`





### Material





### Light















