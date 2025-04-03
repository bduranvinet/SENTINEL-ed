# SENTINEL - Smart Environmental Nucleic-acid Tracking using Inference from Neural-networks for Early-warning Localization

This is an educational repository for installing ADAPT dependencies for environmental deployments. Many things in this repository have been taken and adapted from the [Original ADAPT repository](https://github.com/broadinstitute/adapt/blob/main/).

## Table of contents

* [SENTINEL introduction](#sentinel-introduction)
* [Installing ADAPT](#installing-adapt)
  * [Dependencies](#dependencies)
  * [Installing conda for Linux subsystem](#installing-conda-for-linux-subsystem)
  * [Installing conda for macOS](#installing-conda-for-macOS)

 <br/>
 
### SENTINEL introduction

In particular, SENTINEL is an integrated tool for CRISPR-based environmental biosurveillance. SENTINEL currently leverages ADAPT (Activity-informed Design with All-inclusive Patrolling of Targets) [article here](https://www.nature.com/articles/s41587-022-01213-5). ADAPT is an end-to-end trained artificial intelligence with ~19,000 guide-target pairs, ultimately providing a robust and comprehensive platform for target discovery in the environmental nucleic acid field that can accelerate environmental biosurveillance of emergent biosecurity threats or aid endangered species detection. ADAPT designs are trained to be highly sensitive and specific, with well-established command options that enable high customization for a flexible assay design for the user. ADAPT designs are also scalable and can be locally deployed.

This ADAPT platform will provide you with suitable ranked guide-target pairs for the given target (set of primers and a spacer sequence).

The ultimate objective of SENTINEL is to streamline and accelerate CRISPR-based environmental biosurveillance deployments, whether this is from air, soil or water samples. So far, only water has been tested, but air and soil environmental samples are a promising deployment.

CRISPR-based environmental biosurveillance (CRISPR-eBx) is defined as the use of CRISPR for the detection of target species presence from environmental samples, targeting environmental nucleic acids, i.e., environmental DNA (eDNA) or environmental RNA (eRNA).

Some noteworthy deployments of CRISPR-based environmental biosurveillance are:

* **Biomonitoring of endangered fish**
* **Biomonitoring of endangered amphibians**
* **Biomonitoring of marine invasive species**
* **Quick, in-field biosurveillance**

Most CRISPR-eBx deployments use an isothermal amplification method: RPA (recombinase polymerase amplification) and LAMP (Loop-mediated isothermal amplification). A quick illustration is shown below for RPA-CRISPR-Cas13a.

 <br/>

 ### Installing ADAPT

### Dependencies

ADAPT requires:
* [Python](https://www.python.org) == 3.8
* [NumPy](http://www.numpy.org) &gt;= 1.16.0, &lt; 1.19.0
* [SciPy](https://www.scipy.org) == 1.4.1
* [TensorFlow](https://www.tensorflow.org) == 2.3.2

Using the thermodynamic modules of ADAPT requires:
* [Primer3-py](https://libnano.github.io/primer3-py) == 0.6.1

To run ADAPT, you will need conda installed on your Windows Linux Subsystem or macOS. Make sure you install it before installing ADAPT; there is a short walkthrough below.

### Installing conda for Linux subsystem

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
After this, restart your terminal. You should have a (base) before you prompt.

### Installing conda for macOS

```bash
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh
bash Miniconda3-latest-MacOSX-*.sh
```
After this, restart your terminal. You should have a (base) before you prompt.
