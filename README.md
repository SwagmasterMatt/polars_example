
# Polars Data Analysis Tutorial

This repository contains a Jupyter Notebook that demonstrates how to use the [Polars](https://www.pola.rs/) library for efficient data manipulation and analysis. The notebook provides examples of reading data from CSV files, combining dataframes, and performing various operations using both Pandas and Polars.

## Table of Contents
- [Polars Data Analysis Tutorial](#polars-data-analysis-tutorial)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Getting Started](#getting-started)
  - [Data](#data)
  - [Usage](#usage)
  - [Features](#features)
  - [Contributing](#contributing)
  - [License](#license)
    - [Example Notebook](#example-notebook)

## Introduction
Polars is a fast DataFrame library implemented in Rust and designed for high-performance data manipulation. This tutorial will guide you through the basics of using Polars, including loading data, performing transformations, and leveraging Polars' lazy evaluation for efficient computation.

## Getting Started
To get started, you'll need to install the required libraries. You can install them using pip:

\`\`\`bash
pip install polars pandas matplotlib hvplot
\`\`\`

## Data
The dataset used in this tutorial is the E.W. Brown Solar Facility dataset, available on Kaggle. It contains solar power generation data from 2016 to 2022. You can download the dataset from [this link](https://www.kaggle.com/datasets/mexwell/e-w-brown-solar-facility).

To download the dataset using the Kaggle API in Kaggle notebooks, run the following command:

\`\`\`bash
kaggle datasets download -d mexwell/e-w-brown-solar-facility
\`\`\`

## Usage
The notebook provides detailed examples of how to perform the following tasks:

1. Reading data from CSV files using Pandas.
2. Combining multiple dataframes into one.
3. Converting Pandas DataFrames to Polars DataFrames.
4. Using Polars' lazy evaluation for efficient data manipulation.
5. Filtering, selecting, and transforming data using Polars.

To run the notebook, simply open it in Jupyter and follow the instructions provided in the cells.

## Features
- Efficient data manipulation with Polars.
- Lazy evaluation for optimized computation.
- Comparison of Pandas and Polars for common data tasks.
- Handling large datasets with ease.

## Contributing
Contributions are welcome! If you have any suggestions or improvements, please open an issue or submit a pull request.

## License
This project is licensed under the MIT License.

---

### Example Notebook
The notebook demonstrates various functionalities of Polars. Below is a brief overview of the key sections:

1. **Data Loading**: Load CSV files using Pandas and combine them into a single DataFrame.
    \`\`\`python
    df_1_pd = pd.read_csv("BS_2016.csv")
    df_2_pd = pd.read_csv("BS_2017.csv")
    df_3_pd = pd.read_csv("BS_2018.csv")
    df_4_pd = pd.read_csv("BS_2019.csv")
    df_5_pd = pd.read_csv("BS_2020.csv")
    df_6_pd = pd.read_csv("BS_2021.csv")
    df_7_pd = pd.read_csv("BS_2022.csv")
    df_pd = pd.concat([df_1_pd, df_2_pd, df_3_pd, df_4_pd, df_5_pd, df_6_pd, df_7_pd])
    \`\`\`

2. **Conversion to Polars**: Convert the combined Pandas DataFrame to a Polars DataFrame.
    \`\`\`python
    polars_df = pl.from_pandas(df_pd)
    \`\`\`

3. **Lazy Evaluation**: Use Polars' lazy evaluation to efficiently filter and transform the data.
    \`\`\`python
    lazy_df = pl.LazyFrame(polars_df)
    df_2016 = lazy_df.select(filter_cols)
    df_2016 = df_2016.filter(pl.col("Year") == 2016)
    df_2016 = df_2016.filter(pl.col("Month") == 9)
    \`\`\`

4. **Data Exploration**: Explore the data using various Polars functions and visualize it with hvplot via Polars.
    \`\`\`python
    polars_df.describe()
    polars_df.plot.hist("TmpF")
    \`\`\`

For a detailed walkthrough, please refer to the `polars.ipynb` notebook in this repository.
