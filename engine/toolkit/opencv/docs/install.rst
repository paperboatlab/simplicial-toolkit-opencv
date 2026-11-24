Install
=======

The toolkit needs OpenCV (``libopencv-dev`` or your platform's equivalent):

.. code-block:: sh

   sudo apt-get install -y libopencv-dev
   paperboat toolkit install opencv --repo https://github.com/paperboatlab/simplicial-toolkit-opencv.git

A C++ station registers it next to the builtins:

.. code-block:: cpp

   tk::Registry r = tk::builtins();
   tk::opencv::register_opencv(r);

and imports ``"opencv"`` in its ``descriptor.toml``. A station that lists the toolkit in its
``station.toml`` (``toolkits = ["opencv"]``) is checked for it by ``paperboat check``.

To work on the toolkit itself, overlay it onto a Paperboat checkout so it sits at
``engine/toolkit/opencv/`` and build the engine as usual:

.. code-block:: sh

   cp -r engine/toolkit/opencv ../paperboat/engine/toolkit/opencv
   cmake -S ../paperboat/engine -B ../paperboat/engine/build -G Ninja -DPAPERBOAT_BUILD_TESTS=ON
   cmake --build ../paperboat/engine/build
