# Introduction

Welcome to Iqbal's adbot-ad-challenge repository! This repository is one of many solutions for Zindi's [Adbot Ad Engagement Forecasting Challenge](https://zindi.africa/competitions/adbot-ad-engagement-forecasting-challenge/discussions/21187). The objective of this challenge is to accurately predict the number of clicks a client’s ad receives, one and two weeks into the future (in digital marketing, clicks refer to when someone views the advert and follows one of the hyperlinks in that advert). Not only that, the challenge also requires one to find the most significant features on each prediction. Therefore, the best solution will not only produce an accurate prediction, but also the interpretation.

**NOTE**: Due to Zindi rules, I cannot include the competition datasets in this repository. I also excluded the `submission.csv` just to be safe. If you want to try the notebook, you need to download it from the Zindi website as linked above.

# Creating Environment

**IMPORTANT**: Make sure you have Conda on your local machine first! I recommend you to install Miniconda or Miniforge if you don't have Anaconda installed already (and I recommend you to switch if you bother).

In order to use the notebook, you need to build the enviornment first.

1. Download this repository as zip file and extract it, or clone it with the following command if you have git installed.

```bash
git clone https://github.com/Iqlab369/adbot-ad-challenge
```

2. Open the terminal in your OS. If you are in Windows, you can use Command Prompt or Powershell (preferably the latter).
3. Change your terminal directory to the location of the repository in your local machine. Here's an example if you're in Windows.

```bash
cd /home/iqlab369/adbot-ad-challenge
```

4. Build `adbot-env` conda environment with the following command.

```bash
conda env create -f environment.yml
```

5. Activate the environment with the following command.

```bash
conda activate adbot-env
```

# Notebook Information

The notebook directory is `src/adbot-ad-challenge/notebook.ipynb`. It takes `Train.csv` and `SampleSubmission.csv` as inputs from `input` folder and outputs `submission.csv` in `output` folder.

In order to run the notebook, you can use the following command, just make sure you have already activated the conda environment.

```bash
jupyter notebook src/adbot-ad-challenge/notebook.ipynb
```

If you find that the result you get is different from the one in the Github repo, that's normal. One of the data wrangling step in the notebook is non-deterministic for some reason, and trying to make it deterministic it just makes the accuracy by default. That is why, I cannot guarantee that you will get the same result in every run.

# Features Explanation

The list of features, after data wrangling and preprocessing, for the the machine learning pipeline is as follows:

1. ID,
2. date (converted to `int`),
3. ad_type: Most common ad type in a day for each ID (mode aggregation),
4. currency: Most common currency used for ads in a day for each ID (mode aggregation),
5. call_type: Most common call type in a day for each ID,
6. call_status: Most common call status in a day for each ID,
7. duration: Most common ad duration in a day for each ID,
8. display_location: Most common display location in a day for each ID,
9. is_holiday: Binary feature to indicate whether a date is an holiday in South Africa or not.

# Hardware Information

The notebook has been tested locally in ASUS Vivobook S14/S15 notebook with the following specification:

- OS: Windows 11 and Ubuntu 22.04 (WSL)
- CPU: AMD Ryzen 7 4700U
- GPU: AMD Radeon Integrated Graphics (unneeded)
- RAM: 8GB

The expected runtime of the notebook in this device, from loading library up until inference and sensitivity analysis, is 40 seconds at most.