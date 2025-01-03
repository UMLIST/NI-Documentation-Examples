# NI-Documentation-Examples
Documentation and Examples for using the lab's NI Hardware 

working for eric's PC and the lab Lenovo

# Hardware
## Chassis
- how many PXIe vs PXI slots do we have?
- PXIe-1082
## Controller
- PXIe-810
## Modules (separate by function? use case?)
- PXIe-6361
    - Multifunction
- PXIe-6124
    - multifunction, less channels, higher rate
- PXIe-4330
    - Bridge
- PXI-4110 (2x)
    - Power Supply
    - working! need to manually enter name, not found in device searchm
    - Currently DCPOWER0 but can be renamed in max
- PXI-6255
    - Multifunction, M-series, 40 diff channels
    - https://www.ni.com/docs/en-US/bundle/pci-pxi-usb-6255-specs/page/specs.html?srsltid=AfmBOoq-5YzM1bHs9xQWJFWIWizD94z_7dbEns4KCNUG1NWEAg1sSLXY
- PXIe-4322
    - AO
- PXI-5402
    - FGEN
    - working! Named FGEN0 and needs to be manually typed in FGEN resource control -- can rename in max
- PXI-7854R
    - RIO
    - Per this chart, need compactrio versions 15.0 and later and R series Support installed on host
    - works with NI-RIO 21.9 with COmpactRIO support 21.0, R Series Multifunction RIO support 21.3!


add FGPA and FGEN to chassis

# Software
Best case is LabVIEW. Can also use C, .NET, Python

should also keep list of configuration of pxi software

### Accessories

## Notes
- Remote PXI devices will not be seen in Instrument Studio
- https://www.ni.com/en/support/documentation/bugs/21/ni-dcpower-21-0-known-issues.html for dcpower 

