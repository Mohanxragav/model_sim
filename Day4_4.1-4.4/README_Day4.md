# Day 4 – Five-Stage Pipelined RISC-V CPU

## Goal
Implement pipeline hazard handling, verify branch/jump flushing, compare CPU performance, and organize the project in Git.

## Activities

### 4.1 Data Hazard Handling
Implement:
- EX/MEM-to-EX forwarding
- MEM/WB-to-EX forwarding
- One-cycle stall for a load-use dependency
- Bubble insertion into the pipeline when a stall is detected

Test with back-to-back dependent instructions and a load followed by an instruction that uses the loaded value.

### 4.2 Control Hazard Handling
Resolve branches/jumps and flush incorrect instructions when control flow changes.

Test:
- Taken branch
- Not-taken branch
- JAL instruction

Capture a waveform showing the flush and PC redirection.

### 4.3 Performance Comparison
Run Program 1 (sum 1 to N) and Program 3 (maximum of 8 words) on both CPUs.

Record:
- Instruction count
- Total clock cycles
- CPI = total cycles / instruction count
- Clock period (if measured)
- Execution time = cycles × clock period

Compare the single-cycle and pipelined results and write a five-line conclusion. Do not assume the pipeline always has CPI = 1; stalls and flushes affect CPI.

### 4.4 Git Submission
Push the project to one Git repository with a clear directory structure and README files.

## Files
- `pipeline/pipeline_cpu.v`
- `pipeline/pipeline_tb.v`
- Day 3 single-cycle CPU and program files used for comparison

## Simulation (Icarus Verilog)
From the project root:
```bash
iverilog -g2012 -o day4_sim pipeline/*.v
vvp day4_sim
```

For ModelSim, add the pipeline source files, compile them, set `pipeline_tb` as the simulation top, and run the simulation.

## Expected Deliverables
- Updated pipeline CPU source
- Forwarding and hazard-handling logic
- Hazard test program and testbench results
- Branch/jump test program and annotated waveform
- Performance comparison table and conclusion
- Git repository link

## Notes
The provided pipeline is an educational implementation and requires validation for all hazard combinations and control-flow cases. Confirm the testbench results and inspect waveforms before submission.
