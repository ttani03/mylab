# mylab

`mylab` is a govc wrapper for my lab.

## Requirements

- vSphere 7.0
- [govc](https://github.com/vmware/govmomi/blob/master/govc/README.md)
- fzf
- zsh
- DHCP server
- [ddns-client](https://github.com/ttani03/ddns-client)

## Preparation

1. Clone this repository to your home directory.

    ```
    git clone git@github.com:ttani03/mylab.git
    ```

2. Define the following enviroment variables in `~/.zshrc` according to your environment.

    ```
    ## govc
    export GOVC_URL=
    export GOVC_USERNAME=
    export GOVC_PASSWORD=
    export GOVC_INSECURE=true
    export GOVC_DATASTORE=
    export GOVC_RESOURCE_POOL=

    ## mylab
    export MYLAB_ROOT="$HOME/mylab"
    export PATH="$MYLAB_ROOT/bin:$PATH"
    ```

3. Create a new RSA key into `$HOME/.ssh/id_rsa_mylab.pub`

4. Upload a [ubuntu cloud image](https://cloud-images.ubuntu.com/) to content library `mylib`.

## Usage

### Deploy VMs

1. Deploy ubuntu VM `test-vm` with 2 vCPU, 4 GB memory and 128GB disk.

    ```
    mylab deploy ubuntu -n test-vm -c 2 -m 4 -d 128
    ```

2. Access to the deployed VM with user `ubuntu` and key `id_rsa_mylab`.

### Add/Delete DNS record for deployed VMs

1. Do the following command and select a VM to add or delete a DNS record

```
mylab ddns [add|delete]
```
