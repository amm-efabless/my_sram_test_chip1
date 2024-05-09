# my_sram_test_chip1 (a Caravel User Project)

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![UPRJ_CI](https://github.com/efabless/caravel_project_example/actions/workflows/user_project_ci.yml/badge.svg)](https://github.com/efabless/caravel_project_example/actions/workflows/user_project_ci.yml) [![Caravel Build](https://github.com/efabless/caravel_project_example/actions/workflows/caravel_build.yml/badge.svg)](https://github.com/efabless/caravel_project_example/actions/workflows/caravel_build.yml)

This is an OpenLane-1.x-based example of using an Efabless Marketplace IP packge, installed using `ipm`.

Specifically, it demonstrates use of the commercial EFSRAM_01024x032_008_18 high-density SRAM IP.

This repo was made from https://github.com/efabless/caravel_user_project originally and then adapted with guidance from the similar project: https://github.com/efabless/caravel_user_sram

To build the GDS in this repo:

1.  Install IPM:
    ```bash
    cd ~
    git clone https://github.com/efabless/IPM.git
    pip install ./IPM
    # Test:
    ipm ls-remote
    ```
2.  Clone this repo:
    ```bash
    git clone https://github.com/amm-efabless/my_sram_test_chip1
    ```
3.  Setup your enviroment (installs OpenLane, PDK, etc):
    ```bash
    cd my_sram_test_chip1
    make setup
    ```
4.  Install the EFSRAM IP:
    ```
    ipm install-dep
    ```
    NOTE: At the time of writing, this might require special access to private repos for some IPs (including EFSRAM). This is expected to change as some IPs become officially published. For more info, see: https://github.com/efabless/IPM
5.  Harden the example `wishbone_sram` macro (which includes the SRAM hard IP):
    ```
    make wishbone_sram
    ```
    NOTE: At the time of writing, expect some minor linter errors about shorted ports, and 1 DRC violation.
6.  Harden the `user_project_wrapper`
    ```
    make user_project_wrapper
    ```


## Basic Caravel User Project guides

Refer to [README](docs/source/index.rst#section-quickstart) for a quickstart of how to use caravel_user_project

Refer to [README](docs/source/index.rst) for this sample project documentation. 

Refer to the following [readthedocs](https://caravel-sim-infrastructure.readthedocs.io/en/latest/index.html) for how to add cocotb tests to your project.
