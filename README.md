# ansible-module-xfs_quota

An ansible module to apply XFS quotas.

## Installation

Copy the xfs_quota file to your module library. This can typically be found in /etc/ansible/ansible.cfg

Or include it in the library/modules path at the base of your ansible playbook.

When applying limits to a project, you need to make sure the required project names, ids and paths are populated in `/etc/projects` and `/etc/projid`

## Usage
    - name: apply some xfs quota
      xfs_quota:
        type: user|group|project
        name: <user/group/project name>
        mountpoint: </path/to/mountpoint>
        bhard: <hard blocks limit>
        bsoft: <soft blocks limit>
        ihard: <hard inode limit>
        isoft: <soft inode limit>
        rtbhard: <hard realtime blocks limit>
        rtbsoft: <soft realtime blocks limit>
        state: absent|present

where:

- **type:** *mandatory*, xfs quota type, options: *user, group, project*
- **name:** *optional*, the name of the user, group or project to apply the quota to, if other than default
- **bhard:** *optional*, hard blocks quota limit
- **bsoft:** *optional*, soft blocks quota limit
- **ihard:** *optional*, soft inodes quota limit
- **isoft:** *optional*, hard inodes quota limit
- **rtbhard:** *optional*, hard realtime blocks quota limit
- **rtbsoft:** *optional*, soft realtime blocks quota limit
- **state:** *optional*, apply the limits or remove them, options: *absent, [present]*

When removing the limit (ie setting state to absent), all limits are set to 0, but not really removed. If you do not specify any limits, none will be modified.

## Examples

Please check out the module file for examples

---
## To Do:
- quota timers

