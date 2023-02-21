Disk report module
==============

Provides information on all mounted HFS volumes by running 
`diskutil list -plist` and `diskutil info -plist deviceID`

The table provides the following information per client:

* totalsize (int) Size in Bytes
* freespace (int) Size in Bytes
* percentage (int) percentage 0-100
* smartstatus (string) Verified, Unsupported or Failing
* volumetype (string) HFS+, APFS, BOOTCAMP
* media_type (string) SSD, FUSION, RAID or HDD
* busprotocol (string) PCI, SAS, SATA, USB
* internal (bool)
* mountpoint (string)
* volumename (string)
* encrypted (bool)


Remarks
---

* Sizes are rounded to .5 GB steps to prevent uploading the diskreport every time the size changes with a minimal amount.
* USB FLASH drives are reported as HDD - this should be fixed

Configuration
-------------

Disk Report Widget Thresholds

Thresholds for disk report widget. This array holds two values:

* free gigabytes below which the level is set to 'danger'
* free gigabytes below which the level is set as 'warning'

If there are more free bytes, the level is set to 'success'

```bash
DISK_REPORT_THRESHOLD_DANGER=5
DISK_REPORT_THRESHOLD_WARNING=10
```

Table Schema
---
* totalsize - Big Integer - Total size of disk in bytes
* freespace - Big Integer - Free space on disk in bytes
* percentage - Big Integer - Percentage of disk used
* smartstatus - VARCHAR(255) - SMART status
* volumetype - VARCHAR(255) - Volume filesystem (HFS+, APFS, BootCamp)
* media_type - VARCHAR(255) - Disk type (HDD, SSD, Fusion, RAID)
* busprotocol - VARCHAR(255) - Disk connection bus (PATA, SATA, PCIe, NVMe) 
* internal - Integer - Boolean of if disk is internal
* mountpoint - VARCHAR(255) - Mount point of volume
* volumename - VARCHAR(255) - Volume name
* encrypted - Integer - Boolean of if volume is encrypted

