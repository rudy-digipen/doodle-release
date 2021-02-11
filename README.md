# doodle-release

Version 0.1.0

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
