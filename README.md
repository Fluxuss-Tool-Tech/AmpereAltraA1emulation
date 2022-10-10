# AmpereAltraA1emulation
![image](https://user-images.githubusercontent.com/42323126/194904900-e8babd75-6f3d-4864-be26-579ee4e3185b.png)

Making Ampere Altra A1(arm based) processor for leased data center racks run IA32/64 based vms

<h6>Requirements:</h6>

<p>You need to have a graphical environment installed on your dedicated server so that it has a desktop service running and accessible via Microsoft's RDP</p>

- 1º Install Qemu-kvm to libvirt and virt-manager

```shell
sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils virtinst virt-manager
```

- 2º Check the libvirt daemon

```shell
sudo systemctl is-active libvirtd
```
<p>If the service is not active use:</p>

```shell
sudo systemctl enable --now libvirtd
```

- 3º Add your users in kvm and libvirt groups
```shell
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
```
<p>Restart your ENTIRE dedicated server (no joke).</p>

- 4º Once started, restart all services involving libvirt once more
```shell
systemctl restart libvirtd libvirt-guests.service
```

- 5º When creating your virtual machine, pay attention to the following configuration:

![image](https://user-images.githubusercontent.com/42323126/194906793-836f2a26-20ee-44a4-8146-95cab9a5778f.png)

<p>If you are running a Windows ISO (with serial generated from the azure panel), you must select the correct architecture x86_x64, otherwise if you want to run a custom Linux image that is usually arch64 or android with arm, stay Pay attention to this detail in order to make a good emulation.</p>
