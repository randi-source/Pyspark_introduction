# Introduction to PySpark

## How to Install PySpark in Ubuntu

### Prerequisite:
* Operation system used: Ubuntu 20.04.01 LTS
* Have Anaconda IDE installed, if not, follow this instruction for debian [here](https://docs.anaconda.com/anaconda/install/linux/).
<br><br/>
1. Create and activate new Anaconda Environment 
```console
conda create -n pyspark_env python=3.9.12
```
```console
conda activate pyspark_env
```

2. Download and install java from [here](https://www.oracle.com/java/technologies/downloads/#java8). Make sure that java version you use were 1.8 or 8 for stability. Also, be prepared to register an Oracle account to download java. Alternatively, you could use your console:
```console
sudo apt install openjdk-8-jdk
```

3. Download Spark from official download link [here](https://spark.apache.org/downloads.html). AS in this installation, I use spark 3.3.1

4. Extract the tar files
```console
tar -xvzf spark-3.3.1-bin-hadoop3.tgz
```

5. Change Bash Profile setting
```console
nano ~/.bash_profile
```
copy and paste this environment variables and dont forget to edit the SPARK_HOME path
```console
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export SPARK_HOME=<path to extracted tar file>/spark-3.3.1-bin-hadoop3
export PATH=$SPARK_HOME/bin:$PATH
export PYSPARK_PYTHON=python3
```

6. Source the bash_profile file
```console
source ~/.bash_profile
```

7. Test the pyspark installation by launch Jupyter Notebook
```console
pyspark
```
8. Eliminate the warn messages when launcing spark by going to your spark installation and edit the configuration files
```console
cd <path to extracted tar file>/spark-3.3.1-bin-hadoop3/conf/
```
```console
mv spark-env.sh.template spark-env.sh
```
```console
vi spark-env.sh
```
add this config to your spark-env.sh
```console
SPARK_LOCAL_IP="<your IP address>"
```
after that, try to relaunch pyspark
```console
pyspark
```

## Additional Implementation
if you want to use jupyter notebook in VSCode as I am using one,

### Prerequisite
* Have VSCode installed, if not, follow this instruction for Ubuntu or debian [here](https://code.visualstudio.com/docs/setup/linux)
* Have installed Jupyter Notebook in VSCode, if not, follow the instruction [here](https://towardsdatascience.com/installing-jupyter-notebook-support-in-visual-studio-code-91887d644c5d). 
note: use incognito mode in chrome browser and even thou the instruction were for windows, it will be the same for Ubuntu.

9. Open new folder in vscode

10. Create files in it (ex: test.pynb) and open the file

11. Change the kernel to pyspark_env. At first, you will prompted to install the kernel with pop up message in VSCode, after that, you ccould use the kernel.

12. Install pyspark in jupyter notebook cell
```python
!pip install pyspark==3.3.1
```

13. Test your PySpark installation in Jupyter Notebook
```python
import pyspark
from pyspark.sql import SparkSession

print(pyspark.__version__)
spark = SparkSession.builder.appName("Test Spark").getOrCreate()
print("You are working with", cores, "core(s)")
spark
```
This will show you whether PySpark already installed successfully. You can also test inside jupyter notebook after step 7 with this script.

Hope this little guide can provide you with installation of PySpark on Ubuntu. Happy Learning!




Reference:
- <https://towardsdatascience.com/how-to-get-started-with-pyspark-1adc142456ec>
- <https://medium.com/analytics-vidhya/installing-and-using-pyspark-on-windows-machine-59c2d64af76e>
- https://spark.apache.org/docs/latest/
