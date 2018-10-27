# Offline series resistance correction
Matlab function to perform offline series resistance correction/compensation of recorded currents based on *"Traynelis SF (1998) Software-based correction of single compartment series resistance errors. J Neurosci Methods 86:25–34."* 

During whole-cell voltage-clamp experiments, the resistance across the patch pipette (series resistance) can introduce considerable errors on the amplitude and kinetics of the recorded currents. While in most cases a large portion of this error can be corrected online by the patch-clamp amplifier, the remaining Rs can lead to erroneous estimation of currents. This is especially important if the amount of uncomensated Rs changes during the recording or differs between experiments. A simple software-based solution allows for the correction of the remaining Rs after the experiment (see original publication for details).

### How to use:

#### Input arguments:

- **data:** trace of recorded currents, can be either single vector or multiple traces organized in an array or cell. When the input is an array, the function assumes that the shorter dimension represents the different trials/recordings, i.e. an array of the size 10,000x10 will be treated as 10 recordings with 10,000 data points each

- **Rs:** uncompensated series resistance during the recordings in Ohm, i.e. if an Rs of 10 MOhm during the recording was compensated 50% by the amplifier, the uncompensated Rs is 5 MOhm (= 5e6 Ohm)
- **Cm:** Membrane capacitance during the recording in Farad (e.g. 10 pF = 10e-12 F)
- **Vhold:** holding potential during the recording in Volts (e.g. -60 mV = 0.06 V)
- **Vrev:** reversal potential of the recorded current in Volts (e.g. 10 mV = 0.01 V)
- **SR:** sampling rate of the recording in Hz (e.g. 50 kHz = 50e3 Hz)
- **fraction:** fraction of the remaining Rs which should be compensated (0-1), e.g. 1 if all the remaining Rs should be compensated

#### Output:
- **dataCorrected:** data trace after Rs correction, format is identical to input (i.e. array or cell)