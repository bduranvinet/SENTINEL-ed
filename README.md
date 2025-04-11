# SENTINEL - Smart Environmental Nucleic-acid Tracking using Inference from Neural-networks for Early-warning Localization

> [!NOTE]
> This is an educational repository for installing ADAPT dependencies for environmental deployments. Many things in this repository have been adapted from the [Original ADAPT repository](https://github.com/broadinstitute/adapt/blob/main/).



## Table of contents

* [SENTINEL introduction](#sentinel-introduction)
* [Quick glossary](#quick-glossary)
* [Installing ADAPT](#installing-adapt-v1.6.0)
  * [Dependencies](#dependencies)
  * [Installing conda for Linux subsystem](#installing-conda-for-linux-subsystem)
  * [Installing conda for macOS](#installing-conda-for-macos)

 <br/>
 
## SENTINEL introduction

In particular, SENTINEL is an integrated tool for CRISPR-based environmental biosurveillance (CRISPR-eBx). SENTINEL currently leverages ADAPT (Activity-informed Design with All-inclusive Patrolling of Targets) [article here](https://www.nature.com/articles/s41587-022-01213-5). ADAPT is an end-to-end trained artificial intelligence with ~19,000 guide-target pairs, ultimately providing a robust and comprehensive platform for target discovery in the environmental nucleic acid field that can accelerate environmental biosurveillance of emergent biosecurity threats or aid endangered species detection. ADAPT designs are trained to be highly sensitive and specific, with well-established command options that enable high customization for a flexible assay design for the user. ADAPT designs are also scalable and can be locally deployed.

This ADAPT platform will provide suitable ranked guide-target pairs for the given target (set of primers and a spacer sequence).

The ultimate objective of SENTINEL is to streamline and accelerate CRISPR-eBx deployments, whether from air, soil or water samples. So far, only water has been tested, but air and soil environmental samples are a promising deployment.

## Quick glossary

**CRISPR-eBx**. CRISPR-based environmental biosurveillance, an alternative use of CRISPR to detect target species presence from environmental samples, targeting environmental nucleic acids. This could be for a broad range of applications including environmental viral vectors, elusive endangered species, invasive species and more.

**eNAs**, Environmental nucleic acids, often refer to all the DNA or RNA shredded or left behind in the environment by organisms or agents. eNAs includes environmental DNA (eDNA) and environmental RNA (eRNA).

**Guide-target pairs**, this is defined as the construct of primers and specific gRNA that will detect a certain genomic region.

Some noteworthy deployments of CRISPR-based environmental biosurveillance are:

* **Biomonitoring of endangered fish** [
* **Biomonitoring of endangered amphibians**
* **Biomonitoring of marine invasive species**
* **Quick, in-field biosurveillance** [Yang et al., 2024 - Rapid, easy, sensitive, low-­cost and on-­site detection of environmental DNA and RNA using CRISPR-­Cas13 in _Methods Ecol. Vol._](https://doi.org/10.1111/2041-210X.14369)

Some noteworthy reviews and perspectives on CRISPR-based environments are:

* **CRISPR-based diagnostics** [Kaminsky et al., 2021 - CRISPR-based diagnostics in _Nat. Biomed. Eng_](https://doi.org/10.1038/s41551-021-00760-7)


Most CRISPR-eBx deployments use an isothermal amplification method: RPA (recombinase polymerase amplification) and LAMP (Loop-mediated isothermal amplification). A quick illustration is shown below for RPA-CRISPR-Cas13a.

 <br/>

## Installing ADAPT v1.6.0

### Dependencies

ADAPT will install:
* [Python](https://www.python.org) == 3.8
* [NumPy](http://www.numpy.org) &gt;= 1.16.0, &lt; 1.19.0
* [SciPy](https://www.scipy.org) == 1.4.1
* [TensorFlow](https://www.tensorflow.org) == 2.3.2

Using the thermodynamic modules of ADAPT requires:
* [Primer3-py](https://libnano.github.io/primer3-py) == 0.6.1

To run ADAPT, you will need conda installed on your Windows Linux Subsystem or macOS. Please make sure you install it before installing ADAPT; a short walkthrough is included below.

### Installing conda for Linux subsystem

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
After this, restart your terminal. You should have a (base) before you prompt.

### Installing conda for macOS

>[!CAUTION]
>Please make sure you install the correct conda version for Mac, as there are different MacOS architectures (amd64 and arm64); installing the incorrect one will bring downstream compiling errors.

```bash
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh
bash Miniconda3-latest-MacOSX-*.sh
```
After this, restart your terminal. You should have a (base) before you prompt.
