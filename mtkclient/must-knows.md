# Must Knows
In this section, you will find mtkclient's operation that's useful to know.

## Bypass
Came here for bypass for SP Flash tool? You're on the right section!
Simply run the following: `./mtk payload` and voila! You can now use SP Flash tool.

## Replacement of fastboot
Fastboot is inaccessible? mtkclient to the rescue!

With mtkclient, you can flash partitions from BROM, just like SP Flash tool except that:
    - It does not depend on scatter file, this mean you can flash to any partitions, none of them will be hidden. On SP Flash tool, some partitions may be hidden depending on the scatter file.
    - Be careful since you can flash to the wrong partition and potentially hard-brick your device.

Let's move on to the guide.

**Before jumping right in: all of these operations requires your phone to be powered of and holding vol+ and vol- at the same time while running them.**

### Dumping operations
*Note: `r` stands for read.*
1. Syntax to dump a partition: `./mtk r <partitionName> <fileName>`
    - Example: `./mtk r recovery recovery.img`
2. You can also dump a few partitions at once. The partitions and filename can be separated by a comma, refer to the following example:
    - Example: `./mtk r boot,recovery boot.img,recovery.img`
3. If you want to take extra precautions before modding your device, you can even read the whole flash! Usage: `./mtk rf <fileName>` **Note that this will take around 2-3 hours, and prepare a disk space ~128GB for this**
    - Example: `./mtk rf whole_flash.bin`

### Flashing operations
*Note: `w` stands for write.*
1. Syntax to flash a partition: `./mtk w <partitionName> <fileName>`
    - Example: `./mtk w recovery recovery.img`
2. You can also flash a few partitions at once. The partitions and filename can be separated by a comma, refer to the following example:
    - Example: `./mtk w boot,recovery boot.img,recovery.img`
3. If you've backed up the whole flash, simply run `./mtk wf <fileName>` to restore it.
    - Example: `./mtk wf whole_flash.bin`

### Erasing operations
*Note: `e` stands for erase.*
1. Syntax to erase a partition: `./mtk e <partitionName>`
    - Example: `./mtk e recovery`
2. You can also erase a few partitions at once. The partitions can be separated by a comma, refer to the following example:
    - Example: `./mtk e boot,recovery`

## Unlock / lock bootloader
You saw that, bootloader can be unlocked with mtkclient!
*Note that we recommend you to unlock /lock the official way while you still can, because unlocking by mtkclient gives an unintended side effect which is dm-verity corruption.*

1. To unlock the bootloader simply run the following command:
`./mtk da seccfg unlock`
2. To lock the bootloader simply run the following command:
`./mtk da seccfg lock`
