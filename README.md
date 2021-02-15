# doodle-release

Version 0.2.4

Binaries built with Visual Studio 2019 Version **`16.8.4`**

Make sure your version is not older than this.

## Documentation

View the [0.2 Documentation here](https://rudy-digipen.github.io/doodle-release/0.2/index.html).

## Install for Visual Studio 2019

Put the `doodle_development` folder at the root of your `C:\` drive

Put the `Directory.Build.props` file at the root of all drives that you intend to use for programming with doodle.

Create a new C++ project in Visual Studio and you can start writing code with doodle.

To test you can try the following doodle program:

```c++
#include <doodle/doodle.hpp>
using namespace doodle;
int main(void)
{
    create_window(100, 100);
    set_outline_width(3.0);
    Color squareColor{100, 50, 150};
    while (!is_window_closed())
    {
        update_window();
        clear_background(255);
        no_fill();
        set_outline_color(0);
        draw_ellipse(0, 0, 80.0);
        squareColor.alpha = 128 + 128.0 * std::sin(ElapsedTime);
        set_fill_color(squareColor);
        no_outline();
        draw_rectangle(-Width / 2.0 + 13, -Height / 2.0 + 13, Width - 26.0, Height - 26.0);
    }
    return 0;
}

```

## Notable Changes

- added functionality to draw to an image rather than the window
- The doodle Image class can now be copied like normal objects. 
    * It is more flexible when it is created in a global scope, so debug builds shouldn't see any popups from OpenGL asserts.
    * Got rid of the `Image::color` type. Now there is only one color type, which is `doodle::Color`
- lib files should be more forward compatible with future versions of Visual Studio now that we are no longer using the `/GL` flag _(We turned off whole program optimization)_. See [C++ binary compatibility between Visual Studio 2015, 2017, and 2019](https://docs.microsoft.com/en-us/cpp/porting/binary-compat-2015-2017) for more related info.
- doodle internals no longer use the CS230 namespace name
    * This was causing name conflicts with the current CS230 class code
- Optimized Image loading
- Ask OpenGL implementation for smoother looking lines and polygons
- Image class is more lightweight for the most common case of simply loading an image file and drawing it without modification

