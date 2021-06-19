**Ipcheck**

```bash
dotnet new console --name ipcheck . --framework netcoreapp3.1
```



Type "az" to use Azure CLI
Type "help" to learn about Cloud Shell

**fernando@Azure:~$ az --version**

azure-cli                         2.24.2

core                              2.24.2
telemetry                          1.0.6

Extensions:
ai-examples                        0.2.5
ssh                                0.1.5

Python location '/opt/az/bin/python3'
Extensions directory '/home/fernando/.azure/cliextensions'
Extensions system directory '/opt/az/lib/python3.6/site-packages/azure-cli-extensions'

Python (Linux) 3.6.10 (default, Jun  2 2021, 06:55:09)
[GCC 8.3.0]

Legal docs and information: aka.ms/AzureCliLegal

Your CLI is up-to-date.

**fernando@Azure:~$ az --help**

Group
    az

Subgroups:
    account                                   : Manage Azure subscription information.
    acr                                       : Manage private registries with Azure Container
                                                Registries.
    ad                                        : Manage Azure Active Directory Graph entities needed
                                                for Role Based Access Control.
    advisor                                   : Manage Azure Advisor.
    afd                             [Preview]
    ai-examples                     [Preview] : Add AI powered examples to help content.
    aks                                       : Manage Azure Kubernetes Services.
    ams                                       : Manage Azure Media Services resources.
    apim                                      : Manage Azure API Management services.
    appconfig                                 : Manage App Configurations.
    appservice                                : Manage App Service plans.
    aro                                       : Manage Azure Red Hat OpenShift clusters.
    backup                          [Preview] : Manage Azure Backups.
    batch                                     : Manage Azure Batch.
    bicep                                     : Bicep CLI command group.
    billing                                   : Manage Azure Billing.
    bot                                       : Manage Microsoft Azure Bot Service.
    cache                                     : Commands to manage CLI objects cached using the
                                                `--defer` argument.
    cdn                                       : Manage Azure Content Delivery Networks (CDNs).
    cloud                                     : Manage registered Azure clouds.
    cognitiveservices                         : Manage Azure Cognitive Services accounts.
    config                     [Experimental] : Manage Azure CLI configuration.
    consumption                     [Preview] : Manage consumption of Azure resources.
    container                                 : Manage Azure Container Instances.
    cosmosdb                                  : Manage Azure Cosmos DB database accounts.
    databoxedge                     [Preview] : Support data box edge device and
                                                management.
    deployment                                : Manage Azure Resource Manager template deployment at
                                                subscription scope.
    deployment-scripts                        : Manage deployment scripts at subscription or
                                                resource group scope.
    deploymentmanager               [Preview] : Create and manage rollouts for your
                                                service.
    disk                                      : Manage Azure Managed Disks.
    disk-access                               : Manage disk access resources.
    disk-encryption-set                       : Disk Encryption Set resource.
    dla                             [Preview] : Manage Data Lake Analytics accounts, jobs,
                                                and catalogs.
    dls                             [Preview] : Manage Data Lake Store accounts and
                                                filesystems.
    dms                                       : Manage Azure Data Migration Service (DMS) instances.
    eventgrid                                 : Manage Azure Event Grid topics, domains, domain
                                                topics, system topics partner topics, event
                                                subscriptions, system topic event subscriptions and
                                                partner topic event subscriptions.
    eventhubs                                 : Manage Azure Event Hubs namespaces, eventhubs,
                                                consumergroups and geo recovery configurations -
                                                Alias.
    extension                                 : Manage and update CLI extensions.
    feature                                   : Manage resource provider features.
    functionapp                               : Manage function apps. To install the Azure Functions
                                                Core tools see https://github.com/Azure/azure-
                                                functions-core-tools.
    group                                     : Manage resource groups and template deployments.
    hdinsight                                 : Manage HDInsight resources.
    identity                                  : Managed Service Identities.
    image                                     : Manage custom virtual machine images.
    iot                                       : Manage Internet of Things (IoT) assets.
    keyvault                                  : Manage KeyVault keys, secrets, and certificates.
    kusto                                     : Manage Azure Kusto resources.
    lab                             [Preview] : Manage Azure DevTest Labs.
    local-context [Deprecated] [Experimental] : Manage Local Context.
    lock                                      : Manage Azure locks.
    managedapp                                : Manage template solutions provided and maintained by
                                                Independent Software Vendors (ISVs).
    managedservices                           : Manage the registration assignments and definitions
                                                in Azure.
    maps                                      : Manage Azure Maps.
    mariadb                                   : Manage Azure Database for MariaDB servers.
    monitor                                   : Manage the Azure Monitor Service.
    mysql                                     : Manage Azure Database for MySQL servers.
    netappfiles                               : Manage Azure NetApp Files (ANF) Resources.
    network                                   : Manage Azure Network resources.
    policy                                    : Manage resource policies.
    postgres                                  : Manage Azure Database for PostgreSQL servers.
    ppg                                       : Manage Proximity Placement Groups.
    provider                                  : Manage resource providers.
    redis                                     : Manage dedicated Redis caches for your Azure
                                                applications.
    relay                                     : Manage Azure Relay Service namespaces, WCF relays,
                                                hybrid connections, and rules.
    reservations                    [Preview] : Manage Azure Reservations.
    resource                                  : Manage Azure resources.
    role                                      : Manage user roles for access control with Azure
                                                Active Directory and service principals.
    search                                    : Manage Azure Search services, admin keys and query
                                                keys.
    security                        [Preview] : Manage your security posture with Azure
                                                Security Center.
    servicebus                                : Manage Azure Service Bus namespaces, queues, topics,
                                                subscriptions, rules and geo-disaster recovery
                                                configuration alias.
    sf                                        : Manage and administer Azure Service Fabric clusters.
    sig                                       : Manage shared image gallery.
    signalr                                   : Manage Azure SignalR Service.
    snapshot                                  : Manage point-in-time copies of managed disks, native
                                                blobs, or other snapshots.
    sql                                       : Manage Azure SQL Databases and Data Warehouses.
    ssh                                       : SSH into resources (Azure VMs, etc) using AAD issued
                                                openssh certificates.
    sshkey                                    : Manage ssh public key with vm.
    staticwebapp                    [Preview] : Manage static apps.
    storage                                   : Manage Azure Cloud Storage resources.
    synapse                         [Preview] : Manage and operate Synapse Workspace, Spark
                                                Pool, SQL Pool.
    tag                                       : Tag Management on a resource.
    term                       [Experimental] : Manage marketplace agreement with
                                                marketplaceordering.
    ts                              [Preview] : Manage template specs at subscription or
                                                resource group scope.
    vm                                        : Manage Linux or Windows virtual machines.
    vmss                                      : Manage groupings of virtual machines in an Azure
                                                Virtual Machine Scale Set (VMSS).
    webapp                                    : Manage web apps.

Commands:
    configure                                 : Manage Azure CLI configuration. This command is
                                                interactive.
    feedback                                  : Send feedback to the Azure CLI Team.
    find                                      : I'm an AI robot, my advice is based on our Azure
                                                documentation as well as the usage patterns of Azure
                                                CLI and Azure ARM users. Using me improves Azure
                                                products and documentation.
    interactive                     [Preview] : Start interactive mode. Installs the
                                                Interactive extension if not installed already.
    login                                     : Log in to Azure.
    logout                                    : Log out to remove access to Azure subscriptions.
    rest                                      : Invoke a custom request.
    upgrade                         [Preview] : Upgrade Azure CLI and extensions.
    version                                   : Show the versions of Azure CLI modules and
                                                extensions in JSON format by default or format
                                                configured by --output.

For more specific examples, use: az find "az "

Please let us know how we are doing: https://aka.ms/azureclihats
and let us know if you're interested in trying out our newest features: https://aka.ms/CLIUXstudy

**fernando@Azure:~$ az vm --help**

Group
    az vm : Manage Linux or Windows virtual machines.

Subgroups:
    availability-set       : Group resources into availability sets.
    boot-diagnostics       : Troubleshoot the startup of an Azure Virtual Machine.
    diagnostics            : Configure the Azure Virtual Machine diagnostics extension.
    disk                   : Manage the managed data disks attached to a VM.
    encryption             : Manage encryption of VM disks.
    extension              : Manage extensions on VMs.
    host                   : Manage Dedicated Hosts for Virtual Machines.
    identity               : Manage service identities of a VM.
    image                  : Information on available virtual machine images.
    monitor                : Manage monitor aspect for a vm.
    nic                    : Manage network interfaces. See also `az network nic`.
    run-command            : Manage run commands on a Virtual Machine.
    secret                 : Manage VM secrets.
    unmanaged-disk         : Manage the unmanaged data disks attached to a VM.
    user                   : Manage user accounts for a VM.

Commands:
    assess-patches         : Assess patches on a VM.
    auto-shutdown          : Manage auto-shutdown for VM.
    capture                : Capture information for a stopped VM.
    convert                : Convert a VM with unmanaged disks to use managed disks.
    create                 : Create an Azure Virtual Machine.
    deallocate             : Deallocate a VM.
    delete                 : Delete a VM.
    generalize             : Mark a VM as generalized, allowing it to be imaged for multiple
                             deployments.
    get-instance-view      : Get instance information about a VM.
    install-patches        : Install patches on a VM.
    list                   : List details of Virtual Machines.
    list-ip-addresses      : List IP addresses associated with a VM.
    list-sizes             : List available sizes for VMs.
    list-skus              : Get details for compute-related resource SKUs.
    list-usage             : List available usage resources for VMs.
    list-vm-resize-options : List available resizing options for VMs.
    open-port              : Opens a VM to inbound traffic on specified ports.
    perform-maintenance    : The operation to perform maintenance on a virtual machine.
    reapply                : Reapply VMs.
    redeploy               : Redeploy an existing VM.
    resize                 : Update a VM's size.
    restart                : Restart VMs.
    show                   : Get the details of a VM.
    simulate-eviction      : Simulate the eviction of a Spot VM.
    start                  : Start a stopped VM.
    stop                   : Power off (stop) a running VM.
    update                 : Update the properties of a VM.
    wait                   : Place the CLI in a waiting state until a condition of the VM is met.

Examples
    List all VMs.
        az vm list


    Place the CLI in a waiting state until a condition of the VM is met. (autogenerated)
        az vm wait --custom {custom} --name MyVm --resource-group MyResourceGroup


    Start a stopped VM. (autogenerated)
        az vm start --name MyVm --resource-group MyResourceGroup


    Get the details of a VM. (autogenerated)
        az vm show --name MyVm --resource-group MyResourceGroup


    Power off (stop) a running VM. (autogenerated)
        az vm stop --name MyVm --resource-group MyResourceGroup


For more specific examples, use: az find "az vm"

Please let us know how we are doing: https://aka.ms/azureclihats

**fernando@Azure:~$ az vm create --help**

Command
    az vm create : Create an Azure Virtual Machine.
        For an end-to-end tutorial, see https://docs.microsoft.com/azure/virtual-
        machines/linux/quick-create-cli.

Arguments
    --name -n           [Required] : Name of the virtual machine.
    --resource-group -g [Required] : Name of resource group. You can configure the default group
                                     using `az configure --defaults group=<name>`.
    --availability-set             : Name or ID of an existing availability set to add the VM to.
                                     None by default.
    --boot-diagnostics-storage     : Pre-existing storage account name or its blob uri to capture
                                     boot diagnostics. Its sku should be one of Standard_GRS,
                                     Standard_LRS and Standard_RAGRS.
    --computer-name                : The host OS name of the virtual machine. Defaults to the name
                                     of the VM.
    --count              [Preview] : Number of virtual machines to create. Value range is
                                     [2, 250], inclusive. Don't specify this parameter if you want
                                     to create a normal single VM. The VMs are created in parallel.
                                     The output of this command is an array of VMs instead of one
                                     single VM. Each VM has its own public IP, NIC. VNET and NSG are
                                     shared. It is recommended that no existing public IP, NIC, VNET
                                     and NSG are in resource group. When --count is specified,
                                     --attach-data-disks, --attach-os-disk, --boot-diagnostics-
                                     storage, --computer-name, --host, --host-group, --nics, --os-
                                     disk-name, --private-ip-address, --public-ip-address, --public-
                                     ip-address-dns-name, --storage-account, --storage-container-
                                     name, --subnet, --use-unmanaged-disk, --vnet-name are not
                                     allowed.
        Argument '--count' is in preview and under development. Reference and support levels:
        https://aka.ms/CLI_refstatus
    --custom-data                  : Custom init script file or text (cloud-init, cloud-config,
                                     etc..).
    --edge-zone          [Preview] : The name of edge zone.
        Argument '--edge-zone' is in preview and under development. Reference and support
        levels: https://aka.ms/CLI_refstatus
    --enable-agent                 : Indicates whether virtual machine agent should be provisioned
                                     on the virtual machine. When this property is not specified,
                                     default behavior is to set it to true. This will ensure that VM
                                     Agent is installed on the VM so that extensions can be added to
                                     the VM later.  Allowed values: false, true.
    --enable-auto-update           : Indicate whether Automatic Updates is enabled for the Windows
                                     virtual machine.  Allowed values: false, true.
    --enable-hotpatching           : Patch VMs without requiring a reboot. --enable-agent must be
                                     set and --patch-mode must be set to AutomaticByPlatform.
                                     Allowed values: false, true.
    --enable-secure-boot           : Enable secure boot. It is part of trusted launch.  Allowed
                                     values: false, true.
    --enable-vtpm                  : Enable vTPM. It is part of trusted launch.  Allowed values:
                                     false, true.
    --eviction-policy              : The eviction policy for the Spot priority virtual machine.
                                     Default eviction policy is Deallocate for a Spot priority
                                     virtual machine.  Allowed values: Deallocate, Delete.
    --image                        : The name of the operating system image as a URN alias, URN,
                                     custom image name or ID, custom image version ID, or VHD blob
                                     URI. This parameter is required unless using `--attach-os-
                                     disk.` Valid URN format: "Publisher:Offer:Sku:Version". For
                                     more information, see https://docs.microsoft.com/azure/virtual-
                                     machines/linux/cli-ps-findimage.  Values from: az vm image
                                     list, az vm image show.
    --license-type                 : Specifies that the Windows image or disk was licensed on-
                                     premises. To enable Azure Hybrid Benefit for Windows Server,
                                     use 'Windows_Server'. To enable Multitenant Hosting Rights for
                                     Windows 10, use 'Windows_Client'. For more information see the
                                     Azure Windows VM online docs.  Allowed values: None, RHEL_BYOS,
                                     SLES_BYOS, Windows_Client, Windows_Server.
    --location -l                  : Location in which to create VM and related resources. If
                                     default location is not configured, will default to the
                                     resource group's location.
    --max-price          [Preview] : The maximum price (in US Dollars) you are willing to
                                     pay for a Spot VM/VMSS. -1 indicates that the Spot VM/VMSS
                                     should not be evicted for price reasons.
        Argument '--max-price' is in preview and under development. Reference and support
        levels: https://aka.ms/CLI_refstatus
    --no-wait                      : Do not wait for the long-running operation to finish.
    --patch-mode                   : Mode of in-guest patching to IaaS virtual machine. Allowed
                                     values for Windows VM: AutomaticByOS, AutomaticByPlatform,
                                     Manual. Allowed values for Linux VM: AutomaticByPlatform,
                                     ImageDefault. Manual - You control the application of patches
                                     to a virtual machine. You do this by applying patches manually
                                     inside the VM. In this mode, automatic updates are disabled;
                                     the paramater --enable-auto-update must be false. AutomaticByOS
                                     - The virtual machine will automatically be updated by the OS.
                                     The parameter --enable-auto-update must be true.
                                     AutomaticByPlatform - the virtual machine will automatically
                                     updated by the OS. ImageDefault - The virtual machine's default
                                     patching configuration is used. The parameter --enable-agent
                                     and --enable-auto-update must be true.  Allowed values:
                                     AutomaticByOS, AutomaticByPlatform, ImageDefault, Manual.
    --platform-fault-domain        : Specify the scale set logical fault domain into which the
                                     virtual machine will be created. By default, the virtual
                                     machine will be automatically assigned to a fault domain that
                                     best maintains balance across available fault domains. This is
                                     applicable only if the virtualMachineScaleSet property of this
                                     virtual machine is set. The virtual machine scale set that is
                                     referenced, must have platform fault domain count. This
                                     property cannot be updated once the virtual machine is created.
                                     Fault domain assignment can be viewed in the virtual machine
                                     instance view.
    --ppg                          : The name or ID of the proximity placement group the VM should
                                     be associated with.
    --priority                     : Priority. Use 'Spot' to run short-lived workloads in a cost-
                                     effective way. 'Low' enum will be deprecated in the future.
                                     Please use 'Spot' to deploy Azure spot VM and/or VMSS. Default
                                     to Regular.  Allowed values: Low, Regular, Spot.
    --secrets                      : One or many Key Vault secrets as JSON strings or files via
                                     `@{path}` containing `[{ "sourceVault": { "id": "value" },
                                     "vaultCertificates": [{ "certificateUrl": "value",
                                     "certificateStore": "cert store name (only on windows)"}] }]`.
    --security-type                : Specify if the VM is Trusted Launch enabled. See
                                     https://docs.microsoft.com/azure/virtual-machines/trusted-
                                     launch.  Allowed values: TrustedLaunch.
    --size                         : The VM size to be created. See
                                     https://azure.microsoft.com/pricing/details/virtual-machines/
                                     for size info.  Default: Standard_DS1_v2.  Values from: az vm
                                     list-sizes.
    --ssh-key-name                 : Use it as public key in virtual machine. It should be an
                                     existing SSH key resource in Azure.
    --tags                         : Space-separated tags: key[=value] [key[=value] ...]. Use '' to
                                     clear existing tags.
    --validate                     : Generate and validate the ARM template without creating any
                                     resources.
    --vmss                         : Name or ID of an existing virtual machine scale set that the
                                     virtual machine should be assigned to. None by default.
    --zone -z                      : Availability zone into which to provision the resource.
                                     Allowed values: 1, 2, 3.

Authentication Arguments
    --admin-password               : Password for the VM if authentication type is 'Password'.
    --admin-username               : Username for the VM. Default value is current username of OS.
                                     If the default value is system reserved, then default value
                                     will be set to azureuser. Please refer to
                                     https://docs.microsoft.com/en-
                                     us/rest/api/compute/virtualmachines/createorupdate#osprofile to
                                     get a full list of reserved values.
    --authentication-type          : Type of authentication to use with the VM. Defaults to password
                                     for Windows and SSH public key for Linux. "all" enables both
                                     ssh and password authentication.  Allowed values: all,
                                     password, ssh.
    --generate-ssh-keys            : Generate SSH public and private key files if missing. The keys
                                     will be stored in the ~/.ssh directory.
    --ssh-dest-key-path            : Destination file path on the VM for the SSH key. If the file
                                     already exists, the specified key(s) are appended to the file.
                                     Destination path for SSH public keys is currently limited to
                                     its default value "/home/username/.ssh/authorized_keys" due to
                                     a known issue in Linux provisioning agent.
    --ssh-key-values               : Space-separated list of SSH public keys or public key file
                                     paths.

Dedicated Host Arguments
    --host               [Preview] : ID of the dedicated host that the VM will reside in.
                                     --host and --host-group can't be used together.
        Argument '--host' is in preview and under development. Reference and support levels:
        https://aka.ms/CLI_refstatus
    --host-group         [Preview] : Name or ID of the dedicated host group that the VM
                                     will reside in. --host and --host-group can't be used together.
        Argument '--host-group' is in preview and under development. Reference and support
        levels: https://aka.ms/CLI_refstatus

Managed Service Identity Arguments
    --assign-identity              : Accept system or user assigned identities separated by spaces.
                                     Use '[system]' to refer system assigned identity, or a resource
                                     id to refer user assigned identity. Check out help for more
                                     examples.
    --role                         : Role name or id the system assigned identity will have.
                                     Default: Contributor.
    --scope                        : Scope that the system assigned identity can access.

Marketplace Image Plan Arguments
    --plan-name                    : Plan name.
    --plan-product                 : Plan product.
    --plan-promotion-code          : Plan promotion code.
    --plan-publisher               : Plan publisher.

Monitor Arguments
    --workspace          [Preview] : Name or ID of Log Analytics Workspace. If you specify
                                     the workspace through its name, the workspace should be in the
                                     same resource group with the vm, otherwise a new workspace will
                                     be created.
        Argument '--workspace' is in preview and under development. Reference and support
        levels: https://aka.ms/CLI_refstatus

Network Arguments
    --accelerated-networking       : Enable accelerated networking. Unless specified, CLI will
                                     enable it based on machine image and size.  Allowed values:
                                     false, true.
    --asgs                         : Space-separated list of existing application security groups to
                                     associate with the VM.
    --nics                         : Names or IDs of existing NICs to attach to the VM. The first
                                     NIC will be designated as primary. If omitted, a new NIC will
                                     be created. If an existing NIC is specified, do not specify
                                     subnet, VNet, public IP or NSG.
    --nsg                          : The name to use when creating a new Network Security Group
                                     (default) or referencing an existing one. Can also reference an
                                     existing NSG by ID or specify "" for none ('""' in Azure CLI
                                     using PowerShell or --% operator).
    --nsg-rule                     : NSG rule to create when creating a new NSG. Defaults to open
                                     ports for allowing RDP on Windows and allowing SSH on Linux.
                                     NONE represents no NSG rule.  Allowed values: NONE, RDP, SSH.
    --private-ip-address           : Static private IP address (e.g. 10.0.0.5).
    --public-ip-address            : Name of the public IP address when creating one (default) or
                                     referencing an existing one. Can also reference an existing
                                     public IP by ID or specify "" for None ('""' in Azure CLI using
                                     PowerShell or --% operator).
    --public-ip-address-allocation : Allowed values: dynamic, static.
    --public-ip-address-dns-name   : Globally unique DNS name for a newly created public IP.
    --public-ip-sku                : Public IP SKU. It is set to Basic by default.  Allowed values:
                                     Basic, Standard.
    --subnet                       : The name of the subnet when creating a new VNet or referencing
                                     an existing one. Can also reference an existing subnet by ID.
                                     If both vnet-name and subnet are omitted, an appropriate VNet
                                     and subnet will be selected automatically, or a new one will be
                                     created.
    --subnet-address-prefix        : The subnet IP address prefix to use when creating a new VNet in
                                     CIDR format.  Default: 10.0.0.0/24.
    --vnet-address-prefix          : The IP address prefix to use when creating a new VNet in CIDR
                                     format.  Default: 10.0.0.0/16.
    --vnet-name                    : Name of the virtual network when creating a new one or
                                     referencing an existing one.

Storage Arguments
    --attach-data-disks            : Attach existing data disks to the VM. Can use the name or ID of
                                     a managed disk or the URI to an unmanaged disk VHD.
    --attach-os-disk               : Attach an existing OS disk to the VM. Can use the name or ID of
                                     a managed disk or the URI to an unmanaged disk VHD.
    --data-disk-caching            : Storage caching type for data disk(s), including 'None',
                                     'ReadOnly', 'ReadWrite', etc. Use a singular value to apply on
                                     all disks, or use `<lun>=<vaule1> <lun>=<value2>` to configure
                                     individual disk.
    --data-disk-encryption-sets    : Names or IDs (space delimited) of disk encryption sets for data
                                     disks.
    --data-disk-sizes-gb           : Space-separated empty managed data disk sizes in GB to create.
    --encryption-at-host           : Enable Host Encryption for the VM or VMSS. This will enable the
                                     encryption for all the disks including Resource/Temp disk at
                                     host itself.  Allowed values: false, true.
    --ephemeral-os-disk  [Preview] : Allows you to create an OS disk directly on the host
                                     node, providing local disk performance and faster VM/VMSS
                                     reimage time.  Allowed values: false, true.
        Argument '--ephemeral-os-disk' is in preview and under development. Reference and
        support levels: https://aka.ms/CLI_refstatus
    --os-disk-caching              : Storage caching type for the VM OS disk. Default: ReadWrite.
                                     Allowed values: None, ReadOnly, ReadWrite.
    --os-disk-encryption-set       : Name or ID of disk encryption set for OS disk.
    --os-disk-name                 : The name of the new VM OS disk.
    --os-disk-size-gb              : OS disk size in GB to create.
    --os-type                      : Type of OS installed on a custom VHD. Do not use when
                                     specifying an URN or URN alias.  Allowed values: linux,
                                     windows.
    --specialized                  : Indicate whether the source image is specialized.  Allowed
                                     values: false, true.
    --storage-account              : Only applicable when used with `--use-unmanaged-disk`. The name
                                     to use when creating a new storage account or referencing an
                                     existing one. If omitted, an appropriate storage account in the
                                     same resource group and location will be used, or a new one
                                     will be created.
    --storage-container-name       : Only applicable when used with `--use-unmanaged-disk`. Name of
                                     the storage container for the VM OS disk. Default: vhds.
    --storage-sku                  : The SKU of the storage account with which to persist VM. Use a
                                     singular sku that would be applied across all disks, or specify
                                     individual disks. Usage: [--storage-sku SKU | --storage-sku
                                     ID=SKU ID=SKU ID=SKU...], where each ID is "os" or a 0-indexed
                                     lun. Allowed values: Standard_LRS, Premium_LRS,
                                     StandardSSD_LRS, UltraSSD_LRS, Premium_ZRS, StandardSSD_ZRS.
    --ultra-ssd-enabled            : Enables or disables the capability to have 1 or more managed
                                     data disks with UltraSSD_LRS storage account.  Allowed values:
                                     false, true.
    --use-unmanaged-disk           : Do not use managed disk to persist VM.

Global Arguments
    --debug                        : Increase logging verbosity to show all debug logs.
    --help -h                      : Show this help message and exit.
    --only-show-errors             : Only show errors, suppressing warnings.
    --output -o                    : Output format.  Allowed values: json, jsonc, none, table, tsv,
                                     yaml, yamlc.  Default: json.
    --query                        : JMESPath query string. See http://jmespath.org/ for more
                                     information and examples.
    --subscription                 : Name or ID of subscription. You can configure the default
                                     subscription using `az account set -s NAME_OR_ID`.
    --verbose                      : Increase logging verbosity. Use --debug for full debug logs.

Examples
    Create an Azure Virtual Machine. (autogenerated)
        az vm create --admin-username deploy --generate-ssh-keys --image Centos --name MyVm
        --resource-group MyResourceGroup


    Create a default Ubuntu VM with automatic SSH authentication.
        az vm create --name MyVm --resource-group MyResourceGroup --image UbuntuLTS


    Create a VM by attaching to a managed operating system disk.
        az vm create --resource-group MyResourceGroup --name MyVm --attach-os-disk MyOsDisk --os-
        type linux


    Create an Ubuntu Linux VM using a cloud-init script for configuration. See:
    https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-using-cloud-init.
        az vm create --resource-group MyResourceGroup --name MyVm --image debian --custom-data
        MyCloudInitScript.yml


    Create a default Windows Server VM with a private IP address.
        az vm create --name MyVm --resource-group MyResourceGroup --public-ip-address "" --image
        Win2012R2Datacenter


For more specific examples, use: az find "az vm create"

Please let us know how we are doing: https://aka.ms/azureclihats
fernando@Azure:~$

**az vm create --resource-group ContainerCompute --name quickvm --image Debian --admin-username student --admin-password StudentPa55w.rd**

{
  "fqdns": "",
  "id": "/subscriptions/72f1bde0-238c-477c-b89f-cdc8b883d0cc/resourceGroups/ContainerCompute/providers/Microsoft.Compute/virtualMachines/quickvm",
  "location": "francecentral",
  "macAddress": "00-0D-3A-89-D4-A6",
  "powerState": "VM running",
  "privateIpAddress": "10.0.0.4",
  "publicIpAddress": "51.103.74.115",
  "resourceGroup": "ContainerCompute",
  "zones": ""
}

**az vm show --resource-group ContainerCompute --name quickvm**

{
  "additionalCapabilities": null,
  "availabilitySet": null,
  "billingProfile": null,
  "diagnosticsProfile": null,
  "evictionPolicy": null,
  "extendedLocation": null,
  "extensionsTimeBudget": null,
  "hardwareProfile": {
    "vmSize": "Standard_DS1_v2"
  },
  "host": null,
  "hostGroup": null,
  "id": "/subscriptions/72f1bde0-238c-477c-b89f-cdc8b883d0cc/resourceGroups/ContainerCompute/providers/Microsoft.Compute/virtualMachines/quickvm",
  "identity": null,
  "instanceView": null,
  "licenseType": null,
  "location": "francecentral",
  "name": "quickvm",
  "networkProfile": {
    "networkInterfaces": [
      {
        "id": "/subscriptions/72f1bde0-238c-477c-b89f-cdc8b883d0cc/resourceGroups/ContainerCompute/providers/Microsoft.Network/networkInterfaces/quickvmVMNic",
        "primary": null,
        "resourceGroup": "ContainerCompute"
      }
    ]
  },
  "osProfile": {
    "adminPassword": null,
    "adminUsername": "student",
    "allowExtensionOperations": true,
    "computerName": "quickvm",
    "customData": null,
    "linuxConfiguration": {
      "disablePasswordAuthentication": false,
      "patchSettings": {
        "patchMode": "ImageDefault"
      },
      "provisionVmAgent": true,
      "ssh": null
    },
    "requireGuestProvisionSignal": true,
    "secrets": [],
    "windowsConfiguration": null
  },
  "plan": null,
  "platformFaultDomain": null,
  "priority": null,
  "provisioningState": "Succeeded",
  "proximityPlacementGroup": null,
  "resourceGroup": "ContainerCompute",
  "resources": null,
  "securityProfile": null,
  "storageProfile": {
    "dataDisks": [],
    "imageReference": {
      "exactVersion": "0.20210329.591",
      "id": null,
      "offer": "debian-10",
      "publisher": "Debian",
      "sku": "10",
      "version": "latest"
    },
    "osDisk": {
      "caching": "ReadWrite",
      "createOption": "FromImage",
      "diffDiskSettings": null,
      "diskSizeGb": 30,
      "encryptionSettings": null,
      "image": null,
      "managedDisk": {
        "diskEncryptionSet": null,
        "id": "/subscriptions/72f1bde0-238c-477c-b89f-cdc8b883d0cc/resourceGroups/ContainerCompute/providers/Microsoft.Compute/disks/quickvm_OsDisk_1_21aba24fe09a41a2a0bdc74a6cc1bdca",
        "resourceGroup": "ContainerCompute",
        "storageAccountType": "Premium_LRS"
      },
      "name": "quickvm_OsDisk_1_21aba24fe09a41a2a0bdc74a6cc1bdca",
      "osType": "Linux",
      "vhd": null,
      "writeAcceleratorEnabled": null
    }
  },
  "tags": {},
  "type": "Microsoft.Compute/virtualMachines",
  "virtualMachineScaleSet": null,
  "vmId": "e1911056-960d-418d-92d0-e5ce05314640",
  "zones": null





**az vm list-ip-addresses --resource-group ContainerCompute --name quickvm**

[
  {
    "virtualMachine": {
      "name": "quickvm",
      "network": {
        "privateIpAddresses": [
          "10.0.0.4"
        ],
        "publicIpAddresses": [
          {
            "id": "/subscriptions/72f1bde0-238c-477c-b89f-cdc8b883d0cc/resourceGroups/ContainerCompute/providers/Microsoft.Network/publicIPAddresses/quickvmPublicIP",
            "ipAddress": "51.103.74.115",
            "ipAllocationMethod": "Dynamic",
            "name": "quickvmPublicIP",
            "resourceGroup": "ContainerCompute"
          }
        ]
      },
      "resourceGroup": "ContainerCompute"
    }
  }
]

**az vm list-ip-addresses --resource-group ContainerCompute --name quickvm --query '[].{ip:virtualMachine.network.publicIpAddresses[0].ipAddress}' --output tsv**

51.103.74.115

**ipAddress=$(az vm list-ip-addresses --resource-group ContainerCompute --name quickvm --query '[].{ip:virtualMachine.network.publicIpAddresses[0].ipAddress}' --output tsv)**

**echo $ipAddress**

51.103.74.115

**ssh student@$ipAddress**

yes

**StudentPa55w.rd**

**uname -a**

cd ~/clouddrive

mkdir ipcheck

cd ~/clouddrive/ipcheck

dotnet new console --output . --name ipcheck

touch Dockerfile

code .

**public class Program {    public static void Main(string[] args)    {                // Check if network is available        if (System.Net.NetworkInformation.NetworkInterface.GetIsNetworkAvailable())        {            System.Console.WriteLine("Current IP Addresses:");             // Get host entry for current hostname            string hostname = System.Net.Dns.GetHostName();            System.Net.IPHostEntry host = System.Net.Dns.GetHostEntry(hostname);                            // Iterate over each IP address and render their values            foreach(System.Net.IPAddress address in host.AddressList)            {                System.Console.WriteLine($"\t{address}");            }        }        else        {            System.Console.WriteLine("No Network Connection");        }    } }**



dotnet run

\# Start using the .NET Core 3.1 SDK container image FROM mcr.microsoft.com/dotnet/sdk:3.1-alpine AS build # Change current working directory WORKDIR /app # Copy existing files from host machine COPY . ./ # Publish application to the "out" folder RUN dotnet publish --configuration Release --output out # Start container by running application DLL ENTRYPOINT ["dotnet", "out/ipcheck.dll"]



**ContainerCompute**

Containerfpm

az acr list

az acr list --query "max_by([], &creationDate).name" --output tsv

acrName=$(az acr list --query "max_by([], &creationDate).name" --output tsv)

echo $acrName

cd ~/clouddrive/ipcheck

dir



az acr build --registry $acrName --image ipcheck:latest .



docker pull containerfpm.azurecr.io/ipcheck:latest

1. In the **Container name** text box, enter **managedcompute**.
2. Leave the **Container image** text box set to its default value.
3. In the **OS type** section, select **Linux**.
4. Leave the **Subscription** text box set to its default value.
5. In the **Resource group** drop-down list, select **ContainerCompute**.
6. In the **Location** drop-down list, select **East US**.
7. In the **Number of cores** drop-down list, select **2**.
8. In the **Memory (GB)** text box, enter **4**.
9. In the **Public IP address** section, select **No**.
10. Select **OK**.



1. From the **Basics** tab, perform the following actions:

   1. Leave the **Subscription** text box set to its default value.
   2. In the **Resource group** drop-down list, select **ContainerCompute**.
   3. In the **Container name** text box, enter **manualcompute**.
   4. In the **Region** drop-down list, select **(US) East US**.
   5. In the **Image source** section, select **Azure Container Registry**.
   6. In the **Registry** drop-down list, select the **Azure Container Registry** resource that you created earlier in this lab.
   7. In the **Image** drop-down list, select **ipcheck**.
   8. In the **Image tag** drop-down list, select **latest**.
   9. Select **Review + Create**.

2. From the **Review + Create** tab, review the selected options.

3. Select **Create** to create the container instance by using your specified configuration.

   > 

az group delete --name ContainerCompute --no-wait --yes
