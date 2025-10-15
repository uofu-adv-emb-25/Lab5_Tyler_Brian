# Tyler and Brian Lab 5 Measurements and Calculations

# sleep.c  
Statistics:
T = 199.9988 ms
f = 5.00002 Hz
d_c = 50%

Jitter = 199.9988 ms - 200 ms = -1.2 microseconds

there are an expected 18000 200ms-periods in one hour
18000 cycles/hr * 199.9988 ms/cycle = 3599978.4 ms/hr
3600000 (expected) - 3599978.4 (measured) = 21.6 ms

Calculated Drift over 1 hour period = 0.108 cycles = 21.6 ms faster than expected with a 5Hz clk
This means that our timing method completes and extra 0.108 cycles in a 1-hour duration of time


# timer.c  
Statistics:
T = 199.9988 ms
f = 5.00002 Hz
d_c = 50%

Jitter = 199.9988 ms - 200 ms = -1.2 microseconds

Calculated Drift over 1 hour period = 0.108 cycles = 21.6 ms faster than expected with a 5Hz clk
This means that our timing method completes and extra 0.108 cycles in a 1-hour duration of time


# task_delay.c
Statistics:
T = 199.9988 ms
f = 5.00002 Hz
d_c = 50%

Jitter = 199.9988 ms - 200 ms = -1.2 microseconds

Calculated Drift over 1 hour period = 0.108 cycles = 21.6 ms faster than expected with a 5Hz clk
This means that our timing method completes and extra 0.108 cycles in a 1-hour duration of time



