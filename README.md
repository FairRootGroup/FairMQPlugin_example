# FairMQPlugin_example

Welcome to the FairMQPlugin example repository. It is meant to provide a working example and starting point to develop your own FairMQ plugin.

# Contribution

If you find bugs or want to contribute, you are welcome to open a PR against this repo.

# Issues

You are also welcome to create an issue here. Please consider opening an issue against the [FairRootGroup/FairRoot](https://github.com/FairRootGroup/FairRoot) repo, if the issue is likely not specific to the examples here.

# Compilation

```
> git clone https://github.com/FairRootGroup/FairMQPlugin_example
> cd FairMQPlugin_example
FairMQPlugin_example> mkdir build
FairMQPlugin_example/build> cmake -DFAIRROOTPATH=%PATHTOFAIRROOTINSTALLATION% \
                                  -DBOOST_ROOT=%PATHTOBOOSTINSTALLATION% ..
FairMQPlugin_example/build> cmake --build .
```

You can find the resulting Plugin in `FairMQPlugin_example/build/lib/libFairMQPlugin_example.so`.

# Integration

The `CMakeLists.txt` in this repo is only meant as a minimal and compact example. Talk to your build system responsible of your project on how to best integrate it into your project.
