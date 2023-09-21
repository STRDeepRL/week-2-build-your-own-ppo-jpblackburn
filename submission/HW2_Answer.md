# Homework 2 Answers

## Task 1

### Q.1 From the command line outputs, can you report the values for the following parameters from the command line outputs? Additionally, please describe the role of each parameter in the training loop and explain how these values influence training in a sentence or two. This exercise can help you grasp the fundamentals of Sample Efficiency and understand the tradeoffs when scaling your training process in a parallel fashion.

* __num_envs__: 4 - The number of environments to run in parallel.  A larger number will make training go faster, but will take more CPU and memory resources.
* __batch_size__: 512 - Total number of timesteps of data collected in a single rollout.  This is not a free parameter, but is computed as `num_envs * num_steps`.  This determines how much data is available in the random sampling of the policy optimization.  
* __num_minibatches__: 4 - The number of minibatches used.  As a free parameter, this is just useful in computing the minibatch size from the batch size.  
* __minibatch_size__: 128 - This is not a free parameter, but is computed as `batch_size // num_minibatches`.  This is the fundamental size over which the optimization of the loss function is performed.  
* __total_timesteps__: 10,000,000 - Total number of agent timesteps during training.  
* __num_updates__: 19,531 - The number of times the policy is updated during the training process.  This is not a free parameter, but is computed as `total_timesteps // batch_size`.  
* __num_steps__: 128 - The number of steps to run in each environment for each policy update.
* __update_epochs__: 4 - The number of times subsets of the same collected data are used for optimization of the policy.  

## Task 2

### Q.1 Utilizing your baseline codebase tagged v2.1, please pinpoint the Rollout Phase and the Learning Phase within the codebase, indicating specific line numbers.

* __Rollout Phase__:  Lines 500-528
* __Learning Phase__: Lines 620-717