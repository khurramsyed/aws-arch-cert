
# EBS

## Volume Types

![alt EBS Volume Type](../images/EBSVolumeTypes.png)


![alt EBS Volume Type2](../images/EBSVolumeTypes2.png)


- `Only EBS-backed instances can be stopped and restarted`.
- Remember that an `instance store-backed instance can only be rebooted` or terminated and its data will be erased if the EC2 instance is terminated.
- If you stopped an `EBS-backed EC2 instance`, the volume is preserved but the `data in any attached Instance store` volumes will be erased. (Implies that EBS-Backed instance can have instance store volumes attached it.)
