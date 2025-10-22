# Tyler and Brian Lab 5 Measurements and Calculations

# Activity 1
# sleep.c  
Statistics:
T = 199.9988 ms
f = 5.00002 Hz
Dty+ = 50%

Jitter = 199.9988 ms - 200 ms = -1.2 microseconds

there are an expected 18000 200ms-periods in one hour
18000 cycles/hr * 199.9988 ms/cycle = 3599978.4 ms/hr
3600000 (expected) - 3599978.4 (measured) = 21.6 ms

Calculated Drift over 1 hour period = 0.108 cycles = 21.6 ms faster than expected with a 5Hz clk
This means that our timing method completes and extra 0.108 cycles in a 1-hour duration of time

Statistics after a delay of 100,000 nop instructions:
T = 208.0028 ms
f = 4.80766 Hz
Dty+ = 50%

We noticed about an 8 ms increase in our period, as expected


# timer.c  
Statistics:
T = 199.9988 ms
f = 5.00002 Hz
d_c = 50%

Jitter = 199.9988 ms - 200 ms = -1.2 microseconds

Calculated Drift over 1 hour period = 0.108 cycles = 21.6 ms faster than expected with a 5Hz clk
This means that our timing method completes and extra 0.108 cycles in a 1-hour duration of time

Statistics after a delay of 100,000 nop instructions immediately after the gpio_put() function call:
T = 199.9988 ms
f = 5.00002 Hz
d_c = 50%

We noticed no change when we had the nop instruction loop immediately after the gpio_put() function call. This is because the way the timing mechanism is structured: The gpio output logic is contained within a callback function that runs every 200ms due to a an interrupt of a hardware timer. As a result, a nop loop delay does not affect the output because the timing logic is done by hardware and not in the callback function. This means that this timing method is more resistant to undesirable/unexpected delays.


# task_delay.c
Statistics:
T = 199.9988 ms
f = 5.00002 Hz
Dty+ = 50%

Jitter = 199.9988 ms - 200 ms = -1.2 microseconds

Calculated Drift over 1 hour period = 0.108 cycles = 21.6 ms faster than expected with a 5Hz clk
This means that our timing method completes and extra 0.108 cycles in a 1-hour duration of time

Statistics after a delay of 100,000 nop instructions:
T = 208.0028 ms
f = 4.80766 Hz
Dty+ = 50%

We noticed about an 8 ms increase in our period, as expected


# Signal Generator
Statistics:
T_min = 199.9988 ms
T_max = 200.008 ms
T_mean = 199.9988 ms
T_stdDev = 3.404 microseconds

f_min = 4.99992 Hz
f_max = 5.00002 Hz
f_mean = 4.99997 Hz
f_stdDev = 23 microHz

Dty+_min = 50.17%
Dty+_max = 50.18%
Dty+_mean = 50.17%
Dty+_stdDev = 0.0%

Jitter = T_mean - T_expected = 199.9988 ms - 200 ms = -1.2 microseconds
NOTE: We used the mean period statistic to calculate our jitter. This resulted in the same calculation as above. But interestingly, the signal generator had a lot more variation in its timing compared to the ones produced by the Pico.

# Activity 2: Measure the latency of an interrupt handler
Statistics (Sync Output):
T_min = 199.9988 ms
T_max = 200.008 ms
T_mean = 199.9988 ms
T_stdDev = 3.68 microseconds

f_min = 4.99992 Hz
f_max = 5.00002 Hz
f_mean = 4.99997 Hz
f_stdDev = 20.24 microHz

Dty+_min = 50.17%
Dty+_max = 50.18%
Dty+_mean = 50.17%
Dty+_stdDev = 0.0%

Statistics (Pico Output):
T_min = 199.9988 ms
T_max = 200.008 ms
T_mean = 199.9988 ms
T_stdDev = 3.956 microseconds

f_min = 4.99992 Hz
f_max = 5.00002 Hz
f_mean = 4.99997 Hz
f_stdDev = 20.24 microHz

Dty+_min = 50.17%
Dty+_max = 50.18%
Dty+_mean = 50.17%
Dty+_stdDev = 0.0%

Measure the delay between the sync signal and the output from the board:
1.7 microseconds is the delay

Using a busy loop with 100,000 nop instructions, we increased the delay from 1.7 microseconds to approx 4 ms
