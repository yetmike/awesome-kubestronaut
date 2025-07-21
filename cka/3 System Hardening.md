# System Hardening

## Table of Contents
1. [Minimize Host OS Footprint (Reduce Attack Surface)](#minimize-host-os-footprint-reduce-attack-surface)
2. [Using Least-Privilege Identity Access Management](#using-least-privilege-identity-access-management)
3. [Minimize External Access to the Network](#minimize-external-access-to-the-network)
4. [Appropriately Use Kernel Hardening Tools Such as AppArmor, seccomp](#appropriately-use-kernel-hardening-tools-such-as-apparmor-seccomp)

---

## Minimize Host OS Footprint (Reduce Attack Surface)

In most cases, Kubernetes is running on Linux distributions, and as time passes, new security vulnerabilities get disclosed. Therefore, you need to keep the operating system and services versions up to date, identify security risks, and disable or remove any operating system-specific functionality that exposes vulnerabilities.

### Steps to Minimize Security Risks

1. **Disable Services**:
   - Use `systemctl` to manage services. For example:
     ```bash
     systemctl list-units
     systemctl status <service>
     systemctl stop <service>
     systemctl disable <service>
     ```

2. **Remove Unwanted Packages**:
   - On Debian-based distributions, you can use:
     ```bash
     apt purge --auto-remove <package>
     ```

> **Task**:
> - List all running services on your host and disable any unnecessary ones.
> - Identify and remove unused packages from your system.

---

## Using Least-Privilege Identity Access Management

### Steps to Implement Least-Privilege Access

1. **Minimize Access to Files and Directories**:
   - Use file permissions and ownership with commands like `chown` and `chmod`. Follow the principle of least privilege.

2. **Create and Manage Users and Groups**:
   - Use commands like `useradd`, `groupadd`, `usermod`, `userdel`, and `groupdel`.

**Tips**:
- Use `cat /etc/passwd` to list users and their primary groups.
- Use `cat /etc/group` to list groups.
- Use `ps aux` to see which processes are started by which users.

### Example Task

1. **Create a New User with Restricted Access**:
   - Create a new user:
     ```bash
     sudo useradd -m restricted-user
     ```
   - Create a directory for the user to access:
     ```bash
     sudo mkdir /restricted-dir
     ```
   - Change ownership of the directory to the new user:
     ```bash
     sudo chown restricted-user:restricted-user /restricted-dir
     ```
   - Restrict access to the directory by setting appropriate permissions:
     ```bash
     sudo chmod 700 /restricted-dir
     ```
   - Verify the user can access the directory:
     ```bash
     sudo -u restricted-user ls /restricted-dir
     ```

2. **Remove Unnecessary Users and Groups**:
   - List all users:
     ```bash
     cat /etc/passwd
     ```
   - Identify and remove unnecessary users:
     ```bash
     sudo userdel <username>
     ```
   - List all groups:
     ```bash
     cat /etc/group
     ```
   - Identify and remove unnecessary groups:
     ```bash
     sudo groupdel <groupname>
     ```

> **Task**:
> - Create a new user `bob` with with home `/home/bob` directory and group `bob`, `bobfamily`
> - Remove `bob` from `bobfamily` group
> - Remove `bob` user, remove `bob`, `bobfamily` groups

---

## Minimize External Access to the Network

### Steps to Restrict Network Access

1. **Inspect Open Ports**:
   - Use `ss` or `netstat` to identify open ports:
     ```bash
     ss -tuln
     netstat -tuln
     ```

2. **Disable Services Managing Unwanted Ports**:
   - Use `systemctl` to stop or disable services managing those ports.

3. **Set Up Firewall Rules**:
   - Use `iptables` or `ufw` to restrict network access. For example:
     ```bash
     sudo ufw allow ssh
     sudo ufw default deny outgoing
     sudo ufw default deny incoming
     sudo ufw enable
     sudo ufw allow 6443
     ```

> **Task**:
> - Identify all open ports on your host and close any unnecessary ones.
> - Configure a firewall to allow only essential traffic (e.g., SSH and Kubernetes API server).

---

## Appropriately Use Kernel Hardening Tools Such as AppArmor, seccomp

Kernel hardening tools restrict what system calls can be made by processes.

### AppArmor

1. **AppArmor Profiles**:
   - AppArmor profiles define what a program can and cannot do. Profiles can be in `enforce` or `complain` mode.

   Example Profile:
   ```text
   # /etc/apparmor.d/k8s-deny-write
   #include <tunables/global>

   profile k8s-deny-write flags=(attach_disconnected) {
     #include <abstractions/base>
     file,
     deny /** w,  # Deny all file writes
   }
   ```

2. **Load the Profile**:
   ```bash
   sudo apparmor_parser /etc/apparmor.d/k8s-deny-write
   ```

3. **Use the Profile in a Pod**:
   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: apparmor-test
   spec:
     containers:
     - name: container-test
       image: busybox
       securityContext:
         appArmorProfile:
           type: Localhost
           localhostProfile: k8s-deny-write
   ```

### seccomp

1. **Default seccomp Profile**:
   ```yaml
   securityContext:
     seccompProfile:
       type: RuntimeDefault
   ```

2. **Custom seccomp Profile**:
   Example Profile:
   ```json
   {
     "defaultAction": "SCMP_ACT_ALLOW",
     "architectures": ["SCMP_ARCH_X86_64"],
     "syscalls": [
       {
         "names": ["mkdir"],
         "action": "SCMP_ACT_ERRNO"
       }
     ]
   }
   ```

3. **Use the Custom Profile in a Pod**:
   ```yaml
   securityContext:
     seccompProfile:
       type: Localhost
       localhostProfile: profiles/mkdir-violation.json
   ```

> **Task**:
> - Create an AppArmor profile to deny write access to all files and apply it to a Pod.
> - Create a custom seccomp profile to block the `mkdir` syscall and apply it to a Pod.

Refer to the [AppArmor Documentation](https://kubernetes.io/docs/tutorials/security/apparmor/) and [Seccomp Documentation](https://kubernetes.io/docs/tutorials/security/seccomp/) for more details.

