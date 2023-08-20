# Ansible Playbook: Windows In-Place Upgrade

This playbook provides a procedure to automatically perform an in-place upgrade of Windows servers managed via vCenter. It leverages VMware functionalities to retrieve VM info, mount the upgrade ISO, and manage the VM's power state. Post-ISO mounting, the Windows setup process is initiated to perform the in-place upgrade.

## Overview of Steps:

1. **VM and ISO Management:** Verify if the Windows VMs exist in the inventory and then mount the specified Windows upgrade ISO.
2. **Pre-upgrade Preparations:** Gracefully shut down the VMs, wait for them to be fully powered off, and take VM snapshots.
3. **In-Place Upgrade:** Power on the VMs, identify the drive letter of the mounted ISO, and initiate the Windows upgrade process.
4. **Post-upgrade Activities:** Confirm that the upgrade to Windows Server 2016 was successful and then apply any outstanding Windows updates.

## Configuration Files:

1. **vars.yml:** Contains all the necessary variables, including vCenter connection details.
2. **serverlist.yml:** List of servers on which the in-place upgrade needs to be performed.

## Usage:

1. Modify the `vars.yml` and `serverlist.yml` to fit your environment.
2. Ensure that Ansible is appropriately configured to connect to your vCenter and Windows servers.
3. Run the playbook:
   ```
   ansible-playbook <path-to-your-playbook.yml>
   ```

## Notes:

- Ensure the provided ISO path in the playbook points to a valid Windows Server 2016 ISO.
- Make sure to adjust the Ansible inventory to align with the `hosts` directives in the playbook.
- While the playbook is automated, always test on a non-production server first to verify behavior.
- It's highly recommended to monitor the servers during the in-place upgrade process, especially during production rollouts.

---

Feel free to make further edits or adjustments to this README to better align it with your specific requirements or organizational standards!


---

**Plugins You Will Need:**
To run this playbook effectively, ensure the following plugins are installed:

```
sudo pip3 install pyvmomi
sudo pip3 install aiohttp
```

---
