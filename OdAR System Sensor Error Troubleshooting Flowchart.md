flowchart TD
    A[Sensor Error] --> B{Check error code}
    B -->|E001-E005| C[Sensor fault]
    B -->|E101-E105| D[Reading error]
    B -->|E201-E205| E[Ranging error]
    
    C --> F{Check connections}
    F -->|Loose| G[Secure cables]
    F -->|OK| H{Check temperature}
    G --> X[Restart device]
    
    H -->|Out of range| I[Wait for temp stabilization]
    H -->|OK| J{Check intake}
    
    J -->|Blocked| K[Clean intake]
    J -->|Clear| L[Run diagnostics]
    
    D --> M{Check baseline}
    M -->|Drifted| N[Zero calibration]
    M -->|OK| O{Check reference}
    
    E --> P{Check obstacles}
    P -->|Present| Q[Clear path]
    P -->|Clear| R{Check distance}
    
    R -->|>4m| S[Reduce distance]
    R -->|OK| T[Calibrate ranging]
    
    I --> X
    K --> X
    N --> X
    Q --> X
    S --> X
    T --> X
    
    X --> Y{Test operation}
    Y -->|Success| Z[System OK]
    Y -->|Fails| W[Contact support]
    
    L --> W
    O --> W