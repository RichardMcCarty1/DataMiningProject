# Book Recommendation System

## Description

-------------------------
Includes all the requisite files for building both a Retrieval and Ranking model as outlined by the [Tensorflow Recommenders guide for developing recommendation systems](https://www.tensorflow.org/recommenders/examples/basic_retrieval)

Features both Jupyter Notebook files and Python scripts for generating, training, and displaying sample outputs from models developed from Goodreads user data.

<br>

## Installation / Running

-------------------------
After downloading and unzipping this repository, the user has the option between running the files in Jupyter Notebook or directly in the shell via python scripts

Regardless, this project is dependent on Python3 as well as a few packages:

```
pandas
tensorflow
tensorflow_recommenders
numpy
```

<br>

[Python3 can be found here](https://www.python.org/downloads/)

<br>


### Shell
______
If you wish to run it directly in shell with python installed, you can simply run
```
pip3 install numpy
pip3 install pandas
pip3 install tensorflow
pip3 install tensorflow_recommenders

python3 ret.py
python3 rank.py
```

ret.py and its mirror, ret.jpynb have incredibly long training times, so the saved index is included in saved_model which can be used to forego the training and generate results based on the indices retrieved from my training.

To utilize this index, the following is included AFTER fitting, simply remove everything after the vocabulary definitions and reinclude the shown segment to see the output of the index.

```
tf.saved_model.save(
    index,
    'saved_model/my_model',
    options=tf.saved_model.SaveOptions(namespace_whitelist=["Scann"])
)

# +
imported = tf.saved_model.load('saved_model/my_model')

# Get recommendations.
thing, titles = imported(np.array([uuidVocab.get_vocabulary()[1]]))
print(f"Top 10 for user {uuidVocab.get_vocabulary()[1]}: {titles}")
print(f"thing: {thing}")
```
<br>

### Jupyter Notebook
__________
Utilizing Jupyter Notebook requires the generation of a virtualenv which can be installed and instatiated from this folder with

```
pip install virtualenv

virtualenv virtualenv_name

source ./virtualenv_name/bin/activate
```

Next, Jupyter Notebook must be installed with

```
pip install ipykernel
pip install jupyterlab
pip install notebook
```

From here, Jupyter Notebook is ready to be ran; however, you still need to install the packages as mentioned above, except this time, within the virtualenv

```
pip install numpy
pip install pandas
pip install tensorflow
pip install tensorflow_recommenders
```

Jupyter Notebook can finally be ran and used to run the .jpynb files by running

```
jupyter notebook
```
