# live-glsl

live-glsl is a very simple and lightweight tool for coding shaders. It has the ability to dynamically reload your shader, which means that any changes you make to the code will be automatically applied without needing to restart the application. Additionally, it provides on-screen error reporting, making it easy to quickly identify and fix any issues in your code. The shader inputs can also be annoted to generate GUI elements from a simple syntax, allowing you to experiment with different value tweaks and see the results in real time.

![](http://karim.naaji.fr/images/live-glsl.webp)

## build and run

```sh
> cmake . -Bbuild && cmake --build build
```

```sh
> ./live-glsl --input fragment_shader_to_watch
```

## example

There are multiple examples available in the example folder that you can easily run to see the tool in action. To execute an example, navigate to the main directory, build the tool from sources, and then run the command `./build/live-glsl --input examples/atmosphere.frag` in your terminal. This will run the specified example file and allow you to start coding.

## builtin uniforms

live-glsl provides a set of convenient built-in uniforms that can be directly accessed from the shader. 

- `time`: a `float` value for the amount of time that has passed since the start of the application, measured in seconds. This can be useful for creating time-dependent effects or animations within your shaders.
- `resolution`: a `vec2` value for the screen resolution in pixels. This can be used to ensure that your shaders are properly scaled and displayed on different screen sizes.
- `mouse`: a `vec3` value that provides information about the current state of the mouse. The first two components of this vector represent the x and y coordinates of the mouse on the screen, measured in pixels. The third component of the vector stores the state of the mouse click, with a value of `1` indicating that the mouse button is currently pressed, and `0` indicating that it is not.
- `pixel_ratio`: a `float` value that provides the pixel ratio of the current device. This can be useful for ensuring that your shaders are properly scaled and displayed on high-resolution screens.

## GUI elements

![](images/screenshot3.png)

live-glsl enables users to easily control the inputs of their shaders with GUI elements annotations. These GUI elements are defined using a specific syntax and should be placed directly before the uniform statement that they are associated with in the shader code. These elements include: `slider1`, `slider2`, `slider3`, `slider4`, `drag1`, `drag2`, `drag3`, `drag4`, `color3`, `color4`. Sliders and drag can be used to adjust a uniform value with a visual slider and drag control and color pickers allow to select a color value for a uniform input. GUI elements should be preceded by an `@` and immediately followed by their parameters in parenthesis.

Drag types follow the syntax `drag(speed, min_value, max_value)`. For example:
```
@drag2(0.1, 0.0, 1.0)
uniform vec2 uniform_name;
```

Slider types follow the syntax `slider(min_value, max_value)`. For example:
```
@slider1(-1.0, 1.0)
uniform float uniform_name;
```

Color types do not need any parameter.
