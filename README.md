                           ┌──────────────────────────┐
                           │          START           │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │ Import libraries & setup │
                           │ (device, warnings, etc.) │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │ Define network & replay  │
                           │ buffer classes           │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │ Parse arguments (mode,   │
                           │ env, steps, buffer type) │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │ Initialize environment   │
                           │ (single or vectorized)   │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │ Create policy network    │
                           │ & optimizer              │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │ Initialize replay buffer │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │ Start profiling (time &  │
                           │ memory tracking)         │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                 ┌───────────────────────────────────────────┐
                 │             TRAINING LOOP                 │
                 └─────────────┬─────────────────────────────┘
                               │
                               ▼
        ┌──────────────────────────────────────────────────────┐
        │ - Get state / observations                           │
        │ - Select action from policy                          │
        │ - Step environment → next state, reward, done        │
        │ - Store transition in replay buffer                  │
        │ - If enough samples: sample batch → update network   │
        │ - Log episode reward if done                         │
        │ - Record timings & memory usage                      │
        └──────────────────────────────────────────────────────┘
                               │
                               ▼
                           ┌──────────────────────────┐
                           │ End training: close envs │
                           │ stop profiling, save CSV │
                           └─────────────┬────────────┘
                                         │
                                         ▼
                           ┌──────────────────────────┐
                           │           END            │
                           └──────────────────────────┘

