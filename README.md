# SENTINEL - Smart Environmental Nucleic-acid Tracking using Inference from Neural-networks for Early-warning Localization

> [!NOTE]
> This is an educational repository for installing ADAPT dependencies for environmental deployments. Many things in this repository have been adapted from the [Original ADAPT repository](https://github.com/broadinstitute/adapt/blob/main/).


## Table of contents

* [SENTINEL introduction](#sentinel-introduction)
* [Quick glossary](#quick-glossary)
* [Installing ADAPT](#installing-adapt-v160)
  - [Dependencies](#dependencies)
  - [Step 0. Installing Windows Linux Subsystem](#step-0-installing-windows-linux-subsystem)
  - [Step 1. Installing miniconda3 into your system](#step-1-installing-miniconda3-into-your-system)
    - [Step 1.1 Status check](#step-11-status-check)
    - [Step 1.2 Installing conda for Linux subsystem](#step-12-installing-conda-for-linux-subsystem)
    - [Step 1.3 Installing conda for macOS](#step-13-installing-conda-for-macos)
  - [Step 2. Quick basic terminal commands training](#step-2-quick-basic-terminal-commands-training)
  - [Step 3. Creating an environment](#step-3-creating-an-environment)
    - [Step 3.1 Specific environment creation](#step-31-specific-environment-creation)
    - [Step 3.2 Working directories creation](#step-32-working-directories-creation)
    - [Step 3.3 ADAPT installation](#step-33-adapt-installation)
- [Running ADAPT](#running-adapt)
  - [Step 4. ADAPT example run](#step-4-adapt-example-run)
    - [Step 4.1 Preparing example file](#step-41-preparing-example-file)
    - [Step 4.2 Running pipeline](#step-42-running-pipeline)
    - [Step 4.3 Output retrieval](#step-43-output-retrieval)
 
## SENTINEL introduction

In particular, SENTINEL is an integrated tool for CRISPR-based environmental biosurveillance (CRISPR-eBx). SENTINEL currently leverages ADAPT (Activity-informed Design with All-inclusive Patrolling of Targets) [article here](https://www.nature.com/articles/s41587-022-01213-5). ADAPT is an end-to-end trained artificial intelligence with ~19,000 guide-target pairs, ultimately providing a robust and comprehensive platform for target discovery in the environmental nucleic acid field that can accelerate environmental biosurveillance of emergent biosecurity threats or aid endangered species detection. ADAPT designs are trained to be highly sensitive and specific, with well-established command options that enable high customization for a flexible assay design for the user. ADAPT designs are also scalable and can be locally deployed.

This ADAPT platform will provide suitable ranked guide-target pairs for the given target (set of primers and a spacer sequence).

The ultimate objective of SENTINEL is to streamline and accelerate CRISPR-eBx deployments, whether from air, soil or water samples. So far, only water has been tested, but air and soil environmental samples are a promising deployment.

Most CRISPR-eBx deployments use an isothermal amplification method: RPA (recombinase polymerase amplification) and LAMP (Loop-mediated isothermal amplification). A quick illustration is shown below for RPA-CRISPR-Cas13a.

![RPA-CRISPR-Cas13a](Illustrations/SENTINEL.jpeg)


---

## Quick glossary
> [!IMPORTANT]
> Reading this glossary will enhance the overall experience when going through the workshop and the manual.

**CRISPR-eBx**, CRISPR-based environmental biosurveillance, an alternative use of CRISPR to detect target species presence from environmental samples, targeting environmental nucleic acids. This could be for various applications, including environmental viral vectors, elusive endangered species, invasive species, diseases, genetic modifications and more.

**CRISPR-Dx**, CRISPR-based diagnostics, CRISPR-Dx is the original use of CRISPR-based detection tools. However, these clinical deployments are not considered the same as an environmental deployment, i.e., CRISPR-eBx.

**eNAs**, Environmental nucleic acids, often refer to all the DNA or RNA shredded or left behind in the environment by organisms or agents. eNAs include environmental DNA (eDNA) and environmental RNA (eRNA).

**Guide-target pairs**, these are defined as the construct of primers and specific gRNAs that will detect a certain genomic region.

**gRNA**, small RNA molecules that program and guide the Cas nuclease into a specific target by nucleic acid complementarity. These are also sometimes called CRISPR RNAs (crRNAs). 

**LAMP**, Loop-mediated isothermal amplification. One of the most used isothermal amplification methods, it uses around 4 - 6 primers and runs between 60-70°C.

**RPA**, Recombinase polymerase amplification. One of the most used isothermal amplification methods uses 2 primers and can run between 25-42°C.

---

Some noteworthy deployments of CRISPR-based environmental biosurveillance are:

* **Biomonitoring of endangered fish** [Williams et al., 2019 - The application of CRISPR-Cas for single species identification from environmental DNA in _Mol. Ecol. Res._]( https://doi.org/10.1111/1755-0998.13045)
* **Biomonitoring of endangered amphibians** [Leugger et al., 2024 - Scanning amplicons with CRISPR-Dx detects endangered amphibians in environmental DNA in _Mol. Ecol. Res._](https://doi.org/10.1111/1755-0998.14009)
* **Biomonitoring of marine invasive species**
* **Quick, in-field biosurveillance** [Yang et al., 2024 - Rapid, easy, sensitive, low-­cost and on-­site detection of environmental DNA and RNA using CRISPR-­Cas13 in _Methods Ecol. Vol._](https://doi.org/10.1111/2041-210X.14369)

---

Some noteworthy reviews and perspectives on the CRISPR-based detection field are:

* **CRISPR-based diagnostics for harmful algal blooms** [Durán-Vinet et al., 2021 - Potential applications of CRISPR/Cas for next-generation biomonitoring of harmful algae blooms: A review in _Harmful Algae_](https://doi.org/10.1016/j.hal.2021.102027)
* **CRISPR-based diagnostics** [Kaminsky et al., 2021 - CRISPR-based diagnostics in _Nat. Biomed. Eng._](https://doi.org/10.1038/s41551-021-00760-7)
* **CRISPR-based diagnostics integrated with deep learning** [Durán-Vinet et al., 2023 - CRISPR-Cas-Based Biomonitoring for Marine Environments: Toward CRISPR RNA Design Optimization Via Deep Learning in _CRISPR J._](https://doi.org/10.1089/crispr.2023.0019)
* **CRISPR-base depletion** [Kardailsky et al., 2025 - Monitoring the Land and Sea: Enhancing Efficiency Through CRISPR-Cas Driven Depletion and Enrichment of Environmental DNA in _CRISPR J._](https://doi.org/10.1089/crispr.2024.0050)

---

# Installing ADAPT v1.6.0

## Dependencies

>[!IMPORTANT]
>The dependencies listed below are automatically installed via Bioconda, and they differ from the original ADAPT. These changes has been tested and do not change the results quality, but allow better compatibility across systems. If you desire to install the original package, it has to be installed via pip or by downloading the repository, but this is ONLY for advanced/dev users.

ADAPT will install:
* [Python](https://www.python.org) == 3.8.18
* [NumPy](http://www.numpy.org) == 1.24.3
* [SciPy](https://www.scipy.org) == 1.10.1
* [TensorFlow](https://www.tensorflow.org) == 2.11.0

Using the thermodynamic modules of ADAPT requires:
* [Primer3-py](https://libnano.github.io/primer3-py) == 0.6.1

To run ADAPT, you will need **conda** installed on your Windows Linux Subsystem or macOS. Please make sure you install it before installing ADAPT; a short walkthrough is included below.

---

## Step 0. Installing Windows Linux Subsystem

>[!WARNING]
>This is only for Windows users who haven't used Windows Linux Subsystem before.

If you are a Windows 10 user, please follow this [Win10 tutorial](https://www.ssl.com/how-to/enable-linux-subsystem-install-ubuntu-windows-10/)

If you are a Windows 11 user, please follow this [Win11 tutorial](https://www.howtogeek.com/744328/how-to-install-the-windows-subsystem-for-linux-on-windows-11/#:~:text=To%20do%20this%2C%20open%20your,prompted%20to%20reboot%20your%20computer)

After you have installed Ubuntu subsystem, open the terminal and go to Step 1.1

---

## Step 1. Installing miniconda3 into your system

### <ins>Step 1.1 Status check<ins>

>[!IMPORTANT]
>If you have used the terminal before, you might have conda installed already.

Please check if you already have conda installed

```bash
conda --version
```

This should provide a number (format xx.x.x). If you got a number as shown below, proceed to step 3 (Creating an environment; Linux and Mac users)

<img width="584" alt="image" src="https://github.com/user-attachments/assets/7698e0e7-f105-415b-ae5e-4626d4cc502e" />

If you got an error, conda is not installed on your computer, then proceed to step 1.2 (Linux subsystem users) or 1.3 (Mac users).

---

### <ins>Step 1.2 Installing conda for Linux subsystem<ins>

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
After this, restart your terminal. You should have a (base) before you prompt.

---

### <ins>Step 1.3 Installing conda for macOS<ins>

>[!CAUTION]
>Please make sure you install the correct conda version for Mac, as there are different MacOS architectures (amd64 and arm64); installing the incorrect one will bring downstream compiling errors.

```bash
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh
bash Miniconda3-latest-MacOSX-*.sh
```
After this, restart your terminal. You should have a (base) before you prompt as shown below:
<img width="574" alt="image" src="https://github.com/user-attachments/assets/57a8cde6-1359-4bfd-a692-ef99d06d238e" />

---

## Step 2. Quick basic terminal commands training

```bash
pwd
```
<img width="586" alt="image" src="https://github.com/user-attachments/assets/b7ad9657-b540-4251-95cd-8dd01950d524" />

'pwd' command allows you to see your current path (where you are in your terminal.

```bash
ls
```
<img width="580" alt="image" src="https://github.com/user-attachments/assets/81e17337-6583-4504-9a97-7fed93465fd3" />

'ls' command allows you to see directories in your current path.

```bash
mkdir SENTINELv1
```
<img width="595" alt="image" src="https://github.com/user-attachments/assets/3083b610-9b3f-49a0-85bc-90c5f597e140" />

'mkdir' command will create a directory in your current path that you saw with 'pwd'. You can see this new directory using 'ls'.

```bash
cd SENTINELv1/
```
<img width="587" alt="image" src="https://github.com/user-attachments/assets/ac4c5f3c-0052-4d63-8188-190771d25918" />

'cd' allows you to go into a specified directory or path. You can use TAB to autocomplete. 'ls' will show that this directory is empty.

```bash
cd ..
```
<img width="582" alt="image" src="https://github.com/user-attachments/assets/5a158d13-9110-4941-a7a1-8e7803964bf3" />

'cd..' will take you one directory back. You can check with 'pwd' your new position. You will also see that your prompt changed too.

---

## Step 3. Creating an environment

>[!NOTE]
> The steps below are for Windows Linux Subsystem, and Mac users, as the command lines are similar.

>[!TIP]
>Environments are useful tools in bioinformatics as they allow us to have a unique 'bench' for specific work; this way, we avoid creating incompatibilities in our main system files.

### <ins> Step 3.1 Specific environment creation<ins>

```bash
conda create -n SENTINELv1 python=3.8
```

<img width="583" alt="image" src="https://github.com/user-attachments/assets/b5e1f86f-520f-411c-a366-e2b48baf0152" />

This will create a specific environment that has Python version 3.8.x. It will also install other dependencies and libraries. Type y and press ENTER. This will take some minutes to run.

---

### <ins> Step 3.2 Working directories creation<ins>

```bash
mkdir SENTINELv1
cd SENTINELv1
mkdir input output
ls
```
<img width="586" alt="image" src="https://github.com/user-attachments/assets/4e9b7d68-0f36-4b55-936c-b08438a90930" />

If you have already created SENTINELv1, use the last three lines instead.

---

### <ins> Step 3.3 ADAPT installation <ins>

>[!WARNING]
> Ensure you activate the environment you created in step 3.1 before continuing.

```bash
conda activate SENTINELv1
```
<img width="583" alt="image" src="https://github.com/user-attachments/assets/42fdeb62-4dd9-41e3-a348-d636beda22c5" />

Your prompt environment should change from (base) to (SENTINELv1). If it activated correctly, you should see Python 3.8. x when using 'conda list'.

```bash
conda list
```
<img width="577" alt="image" src="https://github.com/user-attachments/assets/816283c0-f807-4668-b12f-a988987a5030" />

Proceed to install

```bash
conda install -c bioconda "adapt[thermo]"
```
Type 'y' and then ENTER. The installation can take some minutes as some dependencies are heavy (mainly TensorFlow). TensorFlow is a software library for machine learning deployments, which is the backbone of ADAPT.

Then:

```bash
pip install primer3-py==0.6.1
```

This should have ADAPT 1.6.0 ready to go. Run the command below.

```bash
design.py --help
```
<img width="579" alt="image" src="https://github.com/user-attachments/assets/2298b8ae-568d-4623-85d4-b9013fe1a55b" />

If something similar displays, then ADAPT has been successfully installed. 'design.py' calls for the workflow activation, while '--help' provides specific information to run the workflow. Check out the [Commands Explained](Useful/Commands%20explained.md) guide for more details.

---

# Running ADAPT

>[!TIP] 
>Before starting~~
>
>Always keep a log of your --seed xxx number, this will ensure reproducibility in case you might need it.
>
>You can use [Sublime Text](https://www.sublimetext.com/) for quick command changes and [Benchling](https://www.benchling.com/) to keep a trackable record of what you have ran through the terminal.
>
>ADAPT can only read .FASTA files. ADAPT will always assume that input files are aligned unless otherwise specified. It is recommended that files are aligned and examined carefully before running them through ADAPT.

## Step 4. ADAPT example run

>[!NOTE]
>You can optionally use your own FASTA file. In fact, it is encouraged so you can get a useful product from this workshop. You can follow the same instructions provided below, just make sure to use the correct file name.

### <ins> Step 4.1 Preparing example file <ins>

In this same repository, go to the Example folder and download Test.fasta

<img width="914" alt="image" src="https://github.com/user-attachments/assets/23e32b13-ee0c-4ad1-97d6-45b8589501fc" />
<img width="1108" alt="image" src="https://github.com/user-attachments/assets/5e78f315-6433-4a66-b6b0-d3dbcfe521f6" />


Move Test.fasta into your 'Input' directory that was previously created. You can do this manually in Windows or Mac.

---

### <ins> Step 4.2 Running pipeline <ins>

Then, please copy the following commands and paste them into your terminal.

>[!WARNING]
>Make sure you change your output file name before running a new ADAPT query, or it will get OVERWRITTEN, and previous results will be PERMANENTLY LOST.
>
>Long sequences may require special commands to ensure a smooth run or eventually a server. See [Commands Explained](Useful/Commands%20explained.md) for more information.
>
> Ensure you are in the SENTINELv1 folder before running the command below, or an error will occur.


```bash
design.py complete-targets fasta ./input/Test.fasta -o ./output/example-output1 --obj maximize-activity --id-m 4 --id-frac 0.01 -gl 28 -gm 0 -pl 30 -pm 5 -pp 0.98 --primer-gc-content-bounds 0.35 0.70 --maximization-algorithm random-greedy --predict-cas13a-activity-model --best-n-targets 10 --seed 001 --verbose
```
'./' fills your path till your actual location in the terminal. The above command will only work if you are in the /SENTINELv1/ folder.

This is how it will look when running

<img width="573" alt="image" src="https://github.com/user-attachments/assets/01c4c7da-3276-42f1-90c0-cb7fb47afa9c" />

---

### <ins> Step 4.3 Output retrieval <ins>

You can see your output file as follows

```bash
cd output
ls
```

<img width="593" alt="image" src="https://github.com/user-attachments/assets/5ef8ee08-e510-4d72-ad12-29f3a6ad7124" />

---

>[!TIP]
>For MacOS users:

```bash
open .
```
<img width="1360" alt="image" src="https://github.com/user-attachments/assets/52bbf924-0b26-41ce-81a2-f6fe1b5ee2bb" />

---

>[!TIP]
>For Windows Linux Subsystem users:

```bash
explore.exe .
```

---

Results will look similar to those shown below


<img width="938" alt="image" src="https://github.com/user-attachments/assets/a1210f26-9913-42ac-83ec-beb863473ed0" />


An explanation of the most important values is given in the next section.

# Understanding ADAPT output

objective-value,
target-length
right/left-primer-frac-bound
total-frac-bound-by-guides
guide-set-5th-pctile-activity
guide-expected-activities
guide-target-sequences
guide-target-sequence-positions












