
## About

dcm_qa_stc is a simple DICOM to NIfTI validator script and dataset to test [slice timing correction](https://www.mccauslandcenter.sc.edu/crnl/tools/stc). There is no standard way to report slice times in the DICOM format, so different vendors have developed different methods. Note that [Philips](https://github.com/rordenlab/dcm2niix/tree/master/Philips) does not encode slice times in their DICOM data.

## GE

For details see [GE](https://github.com/rordenlab/dcm2niix/tree/master/GE) page.

* GE/TriggerTime
  * source: https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#Slice_timing_correction
  * slice timing: Trigger Time (0018,1060) "DS [187]"
  * units:
  * version: (0018,1020) LO [24\LX\MR Software release:DV24.0_R02_1607.b]

* GE/RTIA
  * source: https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#Slice_timing_correction
  * slice timing: RTIA Timer (0021,105E) "DS [4.314800]"
  * units: seconds
  * version: (0018,1020) LO [24\LX\MR Software release:DV24.0_R02_1607.b]

* GE/RTIAold
  * source: https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#Archival_MRI
  * slice timing: RTIA Timer (0021,105E) "DS [23457.000000]"
  * units: 1/10,000 second
  * note: https://github.com/rordenlab/dcm2niix/issues/286
  * version: (0018,1020) LO [14\LX\MR Software release:14.0_M4_0629.a]

## Siemens

For details see [Siemens](https://github.com/rordenlab/dcm2niix/tree/master/Siemens) page.

* Siemens/B12
  * source: https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#Archival_MRI
  * slice timing: CSA Header does not include "MosaicRefAcqTimes", slice times can be inferred from "sSliceArray.ucMode".
  * units: NONE (inferred from TR and delayTimeInTR)
  * version: (0018,1020) LO [syngo MR 2006T 4VB12T]

* Siemens/B13
  * source: https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#Archival_MRI
  * slice timing: CSA Header does not include "MosaicRefAcqTimes", slice times can be inferred from "sSliceArray.ucMode".
  * units: NONE (inferred from TR and delayTimeInTR)
  * version: (0018,1020) LO [syngo MR B13 4VB13A]

* Siemens/B15
  * source: https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#Archival_MRI
  * slice timing: CSA Header (0029,1009) "MosaicRefAcqTimes"
  * units: msec
  * version: (0018,1020) LO [syngo MR B15]

* Siemens/B17
  * source: https://www.nitrc.org/plugins/mwiki/index.php/dcm2nii:MainPage#Archival_MRI
  * slice timing: CSA Header (0029,1009) "MosaicRefAcqTimes"
  * units: msec
  * version: (0018,1020) LO [syngo MR B17]

* Siemens/D13
  * source: https://www.mccauslandcenter.sc.edu/crnl/tools/stc
  * slice timing: CSA Header (0029,1009) "MosaicRefAcqTimes"
  * units: msec
  * note: Series 2 uses default Foot->Head mosaic, Series 10 stores Head->Foot mosaic. See source page for details.
  * version: (0018,1020) LO [syngo MR D13D]

* Siemens/E11
  * source: Development scan from McCausland Center
  * slice timing: CSA Header (0029,1009) "MosaicRefAcqTimes"
  * units: msec
  * version: (0018,1020) LO [syngo MR B17]

* Siemens/XA10
  * source: https://github.com/rordenlab/dcm2niix/issues/240
  * slice timing: Time After Start (0021,1104) "DS [12.58]"
  * units: seconds
  * note: (XA11 multi-band sequences can inaccurately report single-band values in 0021,1104)[https://github.com/rordenlab/dcm2niix/issues/303]
  * slice timing: Frame Acquisition Time (0018,9074) "DT [20181022083642.635000]"
  * units: YYYYMMDDHHMMSS
  * note: (Siemens de-identification can scramble frame acquisition time)[https://github.com/rordenlab/dcm2niix/issues/240]
  * version: (0018,1020) LO [syngo MR XA10]

## UIH

For details see [UIH](https://github.com/rordenlab/dcm2niix/tree/master/UIH) page.

* UIH/R002
  * source: https://github.com/rordenlab/dcm2niix/issues/225
  * slice timing: AcquisitionTime (0008,0032) "TM [134052.312000]"
  * units: HHMMSS
  * note: must handle slice times across midnight
  * version: (0018,1020) LO [R002]
