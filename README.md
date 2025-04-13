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

Most CRISPR-eBx deployments use an isothermal amplification method: RPA (recombinase polymerase amplification) and LAMP (Loop-mediated isothermal amplification). A quick illustration is shown below for RPA-CRISPR-Cas13a.

![RPA-CRISPR-Cas13a](Illustrations/SENTINEL.jpeg)


---

## Quick glossary
> [!NOTE]
> Reading this glossary will enhance the overall experience when going through the workshop and the manual.

**CRISPR-eBx**, CRISPR-based environmental biosurveillance, an alternative use of CRISPR to detect target species presence from environmental samples, targeting environmental nucleic acids. This could be for a broad range of applications including environmental viral vectors, elusive endangered species, invasive species and more.

**eNAs**, Environmental nucleic acids, often refer to all the DNA or RNA shredded or left behind in the environment by organisms or agents. eNAs includes environmental DNA (eDNA) and environmental RNA (eRNA).

**Guide-target pairs**, this is defined as the construct of primers and specific gRNA that will detect a certain genomic region.

**LAMP**, Loop-mediated isothermal amplification. One of the most used isothermal amplification methods, it uses around 4 - 6 primers and runs between 60-70C.

**RPA**, Recombinase polymerase amplification. One of the most used isothermal amplification methods, it uses 2 primers, and runs between 25-42C.

---

Some noteworthy deployments of CRISPR-based environmental biosurveillance are:

* **Biomonitoring of endangered fish** [Williams et al., 2019 - The application of CRISPR-Cas for single species identification from environmental DNA in _Mol. Ecol. Res._]( https://doi.org/10.1111/1755-0998.13045)
* **Biomonitoring of endangered amphibians** [Leugger et al., 2024 - Scanning amplicons with CRISPR-Dx detects endangered amphibians in environmental DNA in _Mol. Ecol. Res._](https://doi.org/10.1111/1755-0998.14009)
* **Biomonitoring of marine invasive species**
* **Quick, in-field biosurveillance** [Yang et al., 2024 - Rapid, easy, sensitive, low-­cost and on-­site detection of environmental DNA and RNA using CRISPR-­Cas13 in _Methods Ecol. Vol._](https://doi.org/10.1111/2041-210X.14369)

---

Some noteworthy reviews and perspectives on CRISPR-based detection field are:

* **CRISPR-based diagnostics for harmful algal blooms** [Durán-Vinet et al., 2021 - Potential applications of CRISPR/Cas for next-generation biomonitoring of harmful algae blooms: A review in _Harmful Algae_](https://doi.org/10.1016/j.hal.2021.102027)
* **CRISPR-based diagnostics** [Kaminsky et al., 2021 - CRISPR-based diagnostics in _Nat. Biomed. Eng._](https://doi.org/10.1038/s41551-021-00760-7)
* **CRISPR-based diagnostics integrated with deep learning** [Durán-Vinet et al., 2023 - CRISPR-Cas-Based Biomonitoring for Marine Environments: Toward CRISPR RNA Design Optimization Via Deep Learning in _CRISPR J._](https://doi.org/10.1089/crispr.2023.0019)
* **CRISPR-base depletion** [Kardailsky et al., 2025 - Monitoring the Land and Sea: Enhancing Efficiency Through CRISPR-Cas Driven Depletion and Enrichment of Environmental DNA in _CRISPR J._](https://doi.org/10.1089/crispr.2024.0050)

 <br/>

# Installing ADAPT v1.6.0

## Dependencies

>[!IMPORTANT]
>The dependencies listed below are automatically installed via Bioconda and they differ from the original ADAPT. These changes has been tested and do not change the results quality, but allow better compatibility across systems. If you desire to install the original package, it has to be installed via pip or downloading the repository, but this is ONLY for advanced/dev users.

ADAPT will install:
* [Python](https://www.python.org) == 3.8.18
* [NumPy](http://www.numpy.org) == 1.24.3
* [SciPy](https://www.scipy.org) == 1.10.1
* [TensorFlow](https://www.tensorflow.org) == 2.11.0

Using the thermodynamic modules of ADAPT requires:
* [Primer3-py](https://libnano.github.io/primer3-py) == 0.6.1

To run ADAPT, you will need conda installed on your Windows Linux Subsystem or macOS. Please make sure you install it before installing ADAPT; a short walkthrough is included below.

## Step 1. Installing miniconda3 into your system

### <ins>Status check<ins>

>[!IMPORTANT]
>If you have used the terminal before, you might have conda installed already.

Please check if you already have conda installed

```bash
conda --version
```

This should provide a number (format xx.x.x), if you got an error, then conda is not installed in your computer. Proceed below.

If you got a number, then please proceed to step 2.

### <ins>Installing conda for Linux subsystem<ins>

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
After this, restart your terminal. You should have a (base) before you prompt.

### <ins>Installing conda for macOS<ins>

>[!CAUTION]
>Please make sure you install the correct conda version for Mac, as there are different MacOS architectures (amd64 and arm64); installing the incorrect one will bring downstream compiling errors.

```bash
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh
bash Miniconda3-latest-MacOSX-*.sh
```
After this, restart your terminal. You should have a (base) before you prompt.

## Step 2. Creating an environment


