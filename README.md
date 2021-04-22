# manim-presentation

Tool to do live presentations using [manim](https://www.manim.community/)

## Install

```
pip install -e git+https://github.com/galatolofederico/manim-presentation.git
```

## Usage

Use the class `Slide` as your scenes base class

```python
from manim_presentation import Slide

class Example(Slide):
    def construct(self):
        ...
```

call `self.pause()` when you want to pause the playback

call `self.start_loop()` and `self.stop_loop()` when you want to loop some animations

```python
from manim import *
from manim_presentation import Slide

class Example(Slide):
    def construct(self):
        circle = Circle(radius=3, color=BLUE)
        dot = Dot()

        self.play(GrowFromCenter(circle))
        self.pause()

        self.start_loop()
        self.play(MoveAlongPath(dot, circle), run_time=2, rate_func=linear)
        self.end_loop()

        self.play(dot.animate.move_to(ORIGIN))
        self.pause()

        self.wait()
```


## Default Keybindings

|  Keybinding |          Action          |
|:-----------:|:------------------------:|
| Right Arrow |    Continue/Next Slide   |
|  Left Arrow |      Previous Slide      |
|      R      | Re-Animate Current Slide |
|   Spacebar  |        Play/Pause        |
|      Q      |           Quit           |

## Run Example

```
git clone https://github.com/galatolofederico/manim-presentation.git
cd manim-presentation
virtualenv --python=python3.7 env
. ./env/bin/activate
python setup.py install
```

```
manim -ql example.py
manim_presentation Example
```


## Contributions and license

The code is released as Free Software under the [GNU/GPLv3](https://choosealicense.com/licenses/gpl-3.0/) license. Copying, adapting e republishing it is not only consent but also encouraged. 

For any further question feel free to reach me at  [federico.galatolo@ing.unipi.it](mailto:federico.galatolo@ing.unipi.it) or on Telegram  [@galatolo](https://t.me/galatolo)