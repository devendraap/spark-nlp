---
layout: article
title: Installation
permalink: /docs/en/install
key: docs-install
modify_date: "2020-02-20"
---

## Spark NLP Cheat Sheet

```bash
# Install Spark NLP from PyPI
$pip install spark-nlp==2.4.5

# Install Spark NLP from Anacodna/Conda
conda install -c johnsnowlabs spark-nlp

# Load Spark NLP with Spark Shell
spark-shell --packages com.johnsnowlabs.nlp:spark-nlp_2.11:2.4.5

# Load Spark NLP with PySpark
pyspark --packages com.johnsnowlabs.nlp:spark-nlp_2.11:2.4.5

# Load Spark NLP with Spark Submit
spark-submit --packages com.johnsnowlabs.nlp:spark-nlp_2.11:2.4.5

# Load Spark NLP as external JAR after comiling and bulding Spark NLP by `sbt assembly`
spark-shell --jar spark-nlp-assembly-2.4.5
```

## Python

### Setup Jupyter Notebook

While Jupyter runs code in many programming languages, Python is a
requirement (Python 3.3 or greater, or Python 2.7) for installing the
Jupyter Notebook itself.

### Installing Jupyter using Anaconda

You can install Python and Jupyter using the Anaconda Distribution
which includes Python, the Jupyter Notebook, and other commonly used
packages for scientific computing and data science.

First, download [Anaconda](https://www.anaconda.com/downloads). We
recommend downloading Anaconda’s latest Python 3 version.

Second, install the version of Anaconda which you downloaded, following
the instructions on the download page.

Congratulations, you have installed Jupyter Notebook! To run the
notebook, run the following command at the Terminal (Mac/Linux) or
Command Prompt (Windows):

```bash
jupyter notebook
```

### Installing Jupyter using pip

As an existing or experienced Python user, you may wish to install
Jupyter using Python’s package manager, pip, instead of Anaconda.

If you have Python 3 installed (which is recommended):

```bash
python3 -m pip install --upgrade pip
python3 -m pip install jupyter
```

Congratulations, you have installed Jupyter Notebook! To run the
notebook, run the following command at the Terminal (Mac/Linux) or
Command Prompt (Windows):

```bash
jupyter notebook
```

### Install Apache Spark using pyspark

**Pip package**
Be sure that you have the required python library (pyspark 2.4.4)
installed in your python environment by running:

```bash
pip list
```

If not there you can install by using:

```bash
pip install --ignore-installed pyspark==2.4.4
```

**Conda package**
You can also install pyspark 2.4.4 using conda by running in your
terminal:

```bash
conda install pyspark=2.4.4
```

### Install Spark NLP Opensource

**Pip package**
To install Spark NLP Opensource version you can just run:

```bash
pip install --ignore-installed spark-nlp==2.4.5
```

The --ignore-installed parameter is to overwrite your previous pip
package version if already installed.

**Conda package**
If you are using Anaconda/Conda for managing Python packages, you can install Spark NLP Opensource as follow:

```bash
conda install -c johnsnowlabs spark-nlp=2.4.5
```

### Start Spark NLP Session from python

The following will initialize the spark session in case you have run
the jupyter notebook directly. If you have started the notebook using
pyspark this cell is just ignored.

```python
spark = SparkSession.builder \
    .appName("Spark NLP")\
    .master("local[*]")\
    .config("spark.driver.memory","8G")\
    .config("spark.driver.maxResultSize", "2G") \
    .config("spark.jars.packages", "com.johnsnowlabs.nlp:spark-nlp_2.11:2.4.5")\
    .config("spark.kryoserializer.buffer.max", "500m")\
    .getOrCreate()
```

If using local jars, you can use `spark.jars` instead for a comma
delimited jar files. For cluster setups, of course you'll have to put
the jars in a reachable location for all driver and executor nodes.

## Scala

Our package is deployed to maven central. In order to add this package
as a dependency in your application:

### Maven

```xml
<!-- https://mvnrepository.com/artifact/com.johnsnowlabs.nlp/spark-nlp -->
<dependency>
    <groupId>com.johnsnowlabs.nlp</groupId>
    <artifactId>spark-nlp_2.11</artifactId>
    <version>2.4.5</version>
</dependency>
```

and

```xml
<!-- https://mvnrepository.com/artifact/com.johnsnowlabs.nlp/spark-nlp-gpu -->
<dependency>
    <groupId>com.johnsnowlabs.nlp</groupId>
    <artifactId>spark-nlp-gpu_2.11</artifactId>
    <version>2.4.5</version>
</dependency>
```

### SBT

```bash
// https://mvnrepository.com/artifact/com.johnsnowlabs.nlp/spark-nlp
libraryDependencies += "com.johnsnowlabs.nlp" %% "spark-nlp" % "2.4.5"
```

and

```bash
// https://mvnrepository.com/artifact/com.johnsnowlabs.nlp/spark-nlp-gpu
libraryDependencies += "com.johnsnowlabs.nlp" %% "spark-nlp-gpu" % "2.4.5"
```

Maven Central: [https://mvnrepository.com/artifact/com.johnsnowlabs.nlp](https://mvnrepository.com/artifact/com.johnsnowlabs.nlp)

## Spark-NLP Databricks

### Databricks Notebooks

You can view all the Databricks notebooks from this address:

[https://johnsnowlabs.github.io/spark-nlp-workshop/databricks/index.html](https://johnsnowlabs.github.io/spark-nlp-workshop/databricks/index.html)

Note: You can import these notebooks by using their URLs.

### How to use Spark-NLP library in Databricks

1- Right-click the Workspace folder where you want to store the library.

2- Select Create > Library.

3- Select where you would like to create the library in the Workspace, and open the Create Library dialog:

![Databricks](https://databricks.com/wp-content/uploads/2015/07/create-lib.png)

4- From the Source drop-down menu, select **Maven Coordinate:**
![Databricks](https://databricks.com/wp-content/uploads/2015/07/select-maven-1024x711.png)

5- Now, all available **Spark Packages** are at your fingertips! Just search for **JohnSnowLabs:spark-nlp:version** where **version** stands for the library version such as: `2.4.5`
![Databricks](https://databricks.com/wp-content/uploads/2015/07/browser-1024x548.png)

6- Select **spark-nlp** package and we are good to go!

More info about how to use 3rd [Party Libraries in Databricks](https://databricks.com/blog/2015/07/28/using-3rd-party-libraries-in-databricks-apache-spark-packages-and-maven-libraries.html)
