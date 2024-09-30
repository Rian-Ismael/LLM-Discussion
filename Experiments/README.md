# Run Experiments

This folder contains the scripts and configuration files necessary to run multi-agent discussions using different task types in the LLM-Discussion project. <br>
**NOTE:** The primary script to execute these experiments is `llm_discussion.py`.

## Prerequisites
Before running the `llm_discussion.py` script, ensure that the following prerequisites are met:

### 1. Config File
You need a configuration file for the agents. The default configuration file is `config_role.json`, located in the multi_agent folder. Yoou can modify or create new roles using the same format as provided in `config_role.json`. 

## Usage 

```bash
cd /LLM-Discussion/Experiments/multi_agent
python llm_discussion.py -c <path_to_config_file> -d <path_to_dataset_file> -t <task_type> [-r <rounds>] [-e <evaluate_or_not>]
```

#### For example: 
```bash
python3 llm_discussion.py -c config_role.json -d /home/chenlawrance/exp_repo/LLM-Creativity/Datasets/AUT/aut_30_test.json -r 5 -t AUT -e
```

### Arguments:
- -c, --config: Required. Path to the configuration file for agents.
- -d, --dataset: Required. Path to the dataset file.
- -t, --type: Required. Type of task to run. Choose from AUT, Scientific, Similarities, Instances.
- -r, --rounds: Number of rounds in the discussion. Default is 5.
- -e, --eval_mode: Run in evaluation mode. If specified, the script will evaluate the discussion output.
- -p, --prompt: Specifies the prompt test. Default is 1. Prompts are located in discussion.py line 9 to line 13

## Output File
The script will <ins>automatically</ins> create the necessary output folders if they do not exist. These folders will be created under the `Results/{task_type}` directory structure (`task_type` is "AUT", "Scientific", "Instances", or "Similarities") :

Subfolders for storing different types of data:
- `Results/{task_type}/chat_log`: Contains chat logs of the entire discussion.
- `Results/{task_type}/Output/multi_agent`: Contains the final discussion results.
- `Results/{task_type}/init`: Stores initial responses generated by the agents.

#### Evaluation Results: 
If running in evaluation mode (--eval_mode or -e), results will be saved in an Evaluation folder at the root of the project. For more information on the output folder of the evaluation, refer to: [Evaluation Output Section](../Evaluation/README.md#output)

## View Qualitative Results
Use `read_conversation.py` to read the entire chatlog
```bash
python3 read_conversation.py -i <path_to_chatlog_json_file>
```
**<path_to_chatlog_json_file>** are saved in `LLM-Discussion/Results/<task_type>/chat_log`