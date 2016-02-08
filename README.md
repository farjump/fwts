# About

An open place to share compliance results of board's firmwares with BIOS, UEFI, ACPI,
Multiboot... Anything your software (bootloader, OS...) may rely on.

Every non ad hoc operating system relies highly on standardized interfaces that
the firmware and the bootloader(s) are largely responsible for (e.g., the
physical memory mapping, EFI services). Non compliant firmwares are likely to
cause serious problems and undefined behaviours (e.g., bootloader errors, power
management issues). Since firmwares of proprietary boards cannot be replaced
with better ones, you could end up with an unusable board. So far, you can only
hope and cross your fingers to purchase a board with a firmware correctly
implementing the features your OS expects.

Every firmware developer should provide these results. Until then, feel free to share with the
community, especially if your results show important errors... Standard testing tools such as
Firmware Test Suite ([FWTS]) or Linux UEFI Validation ([LUV]) are freely available and allow you to
test your firmware with a live CD/USB very simply.

# Consulting Results

You can use http://rawgit.com/ to render html results without cloning the repository ([demo](https://cdn.rawgit.com/farjump/fwtr/master/intel/nuc/de3815tykhe/visual-bios/TYBYT10H.86A.0046.2015.1014.1057/fwts/uefi-linux/results.html)). Raw text
files are also generated by the testing tools.

# Testing your firmware

## Ubuntu's Firmware Test Suite (FWTS) - recommended

Allows to test BIOS, UEFI and ACPI interfaces.

The [Firmware Test Suite] is officially
[recommended by the UEFI Board of Directors](http://uefi.org/testtools) for ACPI Self-Certification
Test.

## Intel's Linux UEFI Validation (LUV)

Similar to [FWTS].

[Linux UEFI Validation]

# Contributing - Sharing results

This repository is meant to be very simple and as straightforward as possible. Results are
classified by vendor, board, firmware version, test suite/tool, firmware configuration variants:

```text
<vendor>/<board-tree>/<firmware>/<version>/<testing-tool>/<test-variant>/<test-outputs>
```

The `test-variant` should be named after the firmware's settings and described by its `README.md`.
These firmware settings should influence the results. For example, disabling firmware's secure boot
makes associated test suite fail. Note that tools like [FWTS] allow you to unselect test suits if
you want to disable some according to your settings. [FWTS] is also generally able to skip disabled
features.

Structure example of a (not-recommended) Intel NUC DE3815THYKE:

```text
intel
├── nuc
│   ├── de3815tykhe
│   │   ├── README.md
│   │   └── visual-bios
│   │       └── TYBYT10H.86A.0046.2015.1014.1057
│   │           ├── fwts
│   │           │   ├── uefi-linux
│   │           │   │   ├── acpidump.log
│   │           │   │   ├── cpuinfo.log
│   │           │   │   ├── dmesg.log
│   │           │   │   ├── lspci.log
│   │           │   │   ├── README.md
│   │           │   │   ├── results.html
│   │           │   │   └── results.log
│   │           │   └── uefi-windows
│   │           │       ├── acpidump.log
│   │           │       ├── cpuinfo.log
│   │           │       ├── dmesg.log
│   │           │       ├── lspci.log
│   │           │       ├── README.md
│   │           │       ├── results.html
│   │           │       └── results.log
│   │           └── luv
│   │               ├── uefi-linux
│   │               │   ├── luv.html
│   │               │   ├── README.md
│   │               │   ├── parsed
│   │               │   │   ├── bits
│   │               │   │   ├── chipsec
│   │               │   │   ├── efivarfs-test
│   │               │   │   ├── fwts
│   │               │   │   └── kernel-efi-warnings
│   │               │   └── raw
│   │               │       ├── bits
│   │               │       ├── chipsec
│   │               │       ├── efivarfs-test
│   │               │       ├── fwts
│   │               │       └── kernel-efi-warnings
│   │               └── uefi-windows
│   │                   └── README.md
│   └── README.md
└── README.md
```

[FWTS]: https://wiki.ubuntu.com/FirmwareTestSuite
[Firmware Test Suite]: https://wiki.ubuntu.com/FirmwareTestSuite
[LUV]: https://01.org/linux-uefi-validation
[Linux UEFI Validation]: https://01.org/linux-uefi-validation