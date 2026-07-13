# Phone restarts when running on Samsung SM-S948B (S26 Ultra): Details and logs attached

The exploit/POC (call it what you want) ran or appeared to have executed because:

1. I saw output on the Firefox tab when I navigated to <[https://rootme.nebusec.io/b9e3f1a4-7c82-4d6e-9a51-2f8c4b3e0d...](https://rootme.nebusec.io/b9e3f1a4-7c82-4d6e-9a51-2f8c4b3e0d17)>.
2. I saw some output from the execution of the POC.

However, after I went to <[https://rootme.nebusec.io/b9e3f1a4-7c82-4d6e-9a51-2f8c4b3e0d...](https://rootme.nebusec.io/b9e3f1a4-7c82-4d6e-9a51-2f8c4b3e0d17)> the phone froze and refused to respond to any input. The only thing that worked was restarting, which I wonder how it works given the, I think, the kernel has hung. The screen remains on with the partial output of the execution of the POC until the screen saver kicks in or when some watchdog or timer kicks in to restart the phone.

1. Can you please provide a `Dockerfile` to build the exploit?
2. Does anyone know how the kernel is able to respond to events whilst the system has hung?
3. Some more information about the execution state of the exploit saved to the phone would help in debugging issues because I cannot even save a screen recording (the file gets written but it is corrupted, it seems).

## Information and Logs

`logcat.zip` contains all the information I could capture before the phone restarted.

```sh
$ adb cat /proc/version
Linux version 6.12.69-android16-6-p8021103-abogkiS948BXXU3ZZF7-4k (kleaf@build-host) (Android (14043575, +pgo, +bolt, +lto, +mlgo, based on r536225) clang version 19.0.1 (https://android.googlesource.com/toolchain/llvm-project b3a530ec6537146650e42be89f1089e9a3588460), LLD 19.0.1) #1 SMP PREEMPT Wed Jun 10 08:48:33 UTC 2026
$ adb shell uname -a
Linux localhost 6.12.69-android16-6-p8021103-abogkiS948BXXU3ZZF7-4k #1 SMP PREEMPT Wed Jun 10 08:48:33 UTC 2026 aarch64 Toybox
$  adb shell getprop | grep "model\|version.sdk\|manufacturer\|ro.serialno\|product.name\|brand\|version.release\|build.id\|security_patch" | sed 's/ro\.//g' | tee -a getprop.txt
[ril.model_id]: [34826888]
[boot.em.model]: [SM-S948B]
[bootimage.build.id]: [CP2A.260605.016]
[bootimage.build.version.release]: [17]
[bootimage.build.version.release_or_codename]: [17]
[bootimage.build.version.sdk]: [37]
[bootimage.build.version.sdk_full]: [37.0]
[build.2ndbrand]: [false]
[build.id]: [CP2A.260605.016]
[build.version.release]: [17]
[build.version.release_or_codename]: [17]
[build.version.release_or_preview_display]: [17]
[build.version.sdk]: [37]
[build.version.sdk_full]: [37.0]
[build.version.security_patch]: [2026-06-05]
[omc.build.id]: [110749591]
[product.bootimage.brand]: [samsung]
[product.bootimage.manufacturer]: [samsung]
[product.bootimage.model]: [SM-S948B]
[product.brand]: [samsung]
[product.brand_for_attestation]: [samsung]
[product.build.id]: [CP2A.260605.016]
[product.build.version.release]: [17]
[product.build.version.release_or_codename]: [17]
[product.build.version.sdk]: [37]
[product.build.version.sdk_full]: [37.0]
[product.manufacturer]: [samsung]
[product.manufacturer_for_attestation]: [samsung]
[product.model]: [SM-S948B]
[product.model_for_attestation]: [SM-S948B]
[product.name]: [m3qxeea]
[product.name_for_attestation]: [m3qxeea]
[product.odm.brand]: [samsung]
[product.odm.manufacturer]: [samsung]
[product.odm.model]: [SM-S948B]
[product.product.brand]: [samsung]
[product.product.manufacturer]: [samsung]
[product.product.model]: [SM-S948B]
[product.product.name]: [m3qxxx]
[product.system.brand]: [samsung]
[product.system.manufacturer]: [samsung]
[product.system.model]: [SM-S948B]
[product.system_dlkm.brand]: [samsung]
[product.system_dlkm.manufacturer]: [samsung]
[product.system_dlkm.model]: [SM-S948B]
[product.system_ext.brand]: [samsung]
[product.system_ext.manufacturer]: [samsung]
[product.system_ext.model]: [SM-S948B]
[product.vendor.brand]: [samsung]
[product.vendor.manufacturer]: [samsung]
[product.vendor.model]: [SM-S948B]
[product.vendor_dlkm.brand]: [samsung]
[product.vendor_dlkm.manufacturer]: [samsung]
[product.vendor_dlkm.model]: [SM-S948B]
[serialno]: [R5GL159THBY]
[slmk.genie.model_count]: [1]
[soc.manufacturer]: [QTI]
[soc.model]: [SM8850]
[strongbox.manufacturer]: [QTI]
[strongbox.model]: [SM8850]
[system.build.id]: [CP2A.260605.016]
[system.build.version.release]: [17]
[system.build.version.release_or_codename]: [17]
[system.build.version.sdk]: [37]
[system.build.version.sdk_full]: [37.0]
[system_dlkm.build.id]: [BP2A.250605.031.A3]
[system_dlkm.build.version.release]: [16]
[system_dlkm.build.version.release_or_codename]: [16]
[system_dlkm.build.version.sdk]: [36]
[system_dlkm.build.version.sdk_full]: [36.0]
[system_ext.build.id]: [CP2A.260605.016]
[system_ext.build.version.release]: [17]
[system_ext.build.version.release_or_codename]: [17]
[system_ext.build.version.sdk]: [37]
[system_ext.build.version.sdk_full]: [37.0]
[vendor.build.id]: [BP2A.250605.031.A3]
[vendor.build.security_patch]: [2026-06-05]
[vendor.build.version.release]: [16]
[vendor.build.version.release_or_codename]: [16]
[vendor.build.version.sdk]: [36]
[vendor_dlkm.build.id]: [BP2A.250605.031.A3]
[vendor_dlkm.build.version.release]: [16]
[vendor_dlkm.build.version.release_or_codename]: [16]
[vendor_dlkm.build.version.sdk]: [36]
```

## Logs

[getprop.txt](https://github.com/user-attachments/files/29975190/getprop.txt)
[logcat-crash.txt](https://github.com/user-attachments/files/29975194/logcat-crash.txt)
[build.prop.txt](https://github.com/user-attachments/files/29975193/build.prop.txt)
[proc-version.txt](https://github.com/user-attachments/files/29975187/proc-version.txt)
[uname.txt](https://github.com/user-attachments/files/29975191/uname.txt)
[release.txt](https://github.com/user-attachments/files/29975189/release.txt)
[get-state.txt](https://github.com/user-attachments/files/29975188/get-state.txt)
[logcat-kernel.txt](https://github.com/user-attachments/files/29975192/logcat-kernel.txt)
[logcat-system.txt](https://github.com/user-attachments/files/29975210/logcat-system.txt)
[logcat.zip](https://github.com/user-attachments/files/29975263/logcat.zip)
