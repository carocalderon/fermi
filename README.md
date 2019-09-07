# Predicting future SAM dataset access through usage analysis with a LSTM model
This project analyzes the relationship between dataset access in Fermilab’s Sequential access 
via Metadata (SAM) system using a Long Short Term Memory neural network. In order to show a connection 
between datasets, an ordered window of 40 project definitions is used to predict a view of the next 10 
definitions. Definitions are renumbered for each new window of 40, so the model predicts the probabilities 
that any of these definitions will appear in its respective view. Our results show an identifiable connection 
between the definitions appearing in the windows and those called in the view. Some definitions are up to fifteen 
times more likely to appear in the view than others, and the model’s overall performance demonstrates significant 
improvement after training. However, the model’s best accuracy occurs in predicting which definitions would not 
show up in the view rather than which would. This study reveals that prior context of project definitions influence 
which definitions will be loaded later. Predicting dataset access is improved when recent access history is considered.

## Getting Started

For use on Google Colaboraty: Add the Python file to your Google Drive and make sure the Google Colaboratory specific libraries are uncommented.
For use on local machine: Add the Python file to your computer, and comment out the Google Colaboratory specific libraries at the top of the code.
Then, change the file-save locations in the code (in the functions load_data, load_all_batches etc. ... wherever there is an os.path.exists())
to directories on your machine.


### Prerequisites

To run this program, you need Python 2.7, Keras, and Tensorflow installed. If working on Google Colaboratory, no additional
installations are needed, just the program code. On your local machine, make sure NumPy, SciPy, and time libraries are installed.

In order to access Fermilab's SAM datasystem, your local machine needs to be connected to the fgz network. If you have a virtual server
connected to fgz available to ssh into, do so in order to load data in real-time. Otherwise, use preloaded datasets to the run the program.
This code has not been modified to allow Google Colaboratory to connect to PostgreSQL databases, so datasets must be preloaded. In order
to get these preloaded datasets, you need to first run the program on the fgz network.

## Running the tests

To run the LSTM model on the data, run the function run_lstm on the given dataset and specified epoch size, batch size etc.

Explain what these tests test and why

```
def run_lstm(host, database_name, project_id, epochs, number_of_predictions, batch_size):
#LSTM model for the 2-month window prior to project 3630559 created on 07/01/2019
output = run_lstm("sampgsdb01", "sam_nova_prd", 3630559, 25, 1, 500)
```

## Author

 **Carolina Calderon**

## Acknowledgments
This work was supported by the Jeff Metcalf Internship program at the University of Chicago and its partnership with the Fermi National Accelerator Laboratory. I would like to thank my supervisors Robert Illingworth and Marc Mengel for their assistance in this project. I would also like to thank my mentor Igor Mandrichenko for his initiative and time devoted to this work.
