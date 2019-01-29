# License

RLAssist is available under the Apache License, version 2.0. Please see the LICENSE file for details.

# Reference

Rahul Gupta, Aditya Kanade, Shirish Shevade. "Deep Reinforcement Learning for Syntactic Error Repair in Student Programs", AAAI 2019.

# Running the tool

If you are using Ubuntu 16.04.5 LTS (not tested on other distributions) and have conda installed, you can run `source init.sh` which creates a new virtual environment called `rlassist` and installs all the dependcies in it.
Furthermore, it downloads, extracts, and preprocesses the student submission data for you into the required directory structure.
Otherwise, run `source init.sh` and manually fix any failing steps.

To start training on one of the folds with default hyper-parameters, you could run the following.

`python -O neural_net/agent.py data/network_inputs/RLAssist-seed-1189/bin_0/ data/checkpoints/RLAssist-seed-1189/bin_0/`

To run a configuration without expert demonstrations, use `-ge 0 -sr` flags.
You can also control the number of worker threads using `-w` flag.
Please see the details of other flags in `neural_net/agent.py`.
Training script will perodically write to a log file in the `logs` directory.

To use the trained model to fix programs in the test dataset, take the value of the checkpoint from the log file (say 23495767) and run the following.

`python -O neural_net/agent.py data/network_inputs/RLAssist-seed-1189/bin_0/ data/checkpoints/RLAssist-seed-1189/bin_0/ -eval 23495767`
