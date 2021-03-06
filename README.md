# grace-data

Scripts to download L1B and L2 data of the Gravity Recovery and Climate Experiment satellites from `podaac-ftp.jpl.nasa.gov`.

The file `email.txt` must be created in the same dir as the rest of the scripts, containing a single line with the email that is used as password for the anonymous FTP login.

The data is placed in `L1B/Year/Month/Day/` or `L2/[CSR|GFZ\JPL]/RELEASE/`.

The following scripts are included:
- `cat-l1b.sh`: show the contents of the L1B data (one day and product at a time):
```
./cat-l1b.sh <date> <product> [ <satellite> ]
Need at least two input arguments:
- <date> in YYYYMMDD
- <product> name: ACC1B, AHK1B, GNV1B, KBR1B
Optional argument:
- GRACE <satellite>: A or B (default is 'A')
NOTICE:
 - if <product> is KBR1B, the third input argument is ignored (effectively replaced with 'X')
 ``` 
- `download-l1b.sh`: download the L1B data (one day at a time);
```
./download-l1b.sh <date>
Need at one input argument: <date> in YYYYMMDD
```
- `download-l2.sh`: download the L2 data (all data for one institute and release version);
```
./download-l2.sh <source> <version>
Need at least two input arguments:
- the <source> can be CSR, GFZ or JPL
- the <version> can be (the 'RL' part is added internally), as of 10/2018:
  - CSR: 05, 05_mean_field, 06
  - GFZ: 05, 05_WEEKLY, 06
  - JPL: 05, 05.1, 06
```
- `gunzip-l2.sh`: decompress L2 data (called from `download-l2.sh` and sharing the same input arguments);
- `software/update.sh`: download and compile the `Bin2AsciiLevel1` utility needed to read the binary L1B data (no arguments).
