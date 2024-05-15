# Scheduling-Jobs-with-Crontab

# Scheduling Jobs with Crontab

## Introduction
The `crontab` command is used to schedule jobs to be executed periodically at fixed times, dates, or intervals on Unix-like operating systems. This guide will help you understand how to use `crontab` to schedule jobs and manage the `crond` service.

## Basic Commands

### Editing Crontab for a Specific User
To edit the crontab file for a specific user:
```sh
crontab -u username -e
```

Listing Crontab Entries for a Specific User

To list the crontab entries for a specific user:
```
crontab -u username -l
```
This command displays all scheduled jobs for the specified user.
Removing Crontab Entries for a Specific User

To remove all crontab entries for a specific user
```
crontab -r
```
### Crontab File Format

Each line in the crontab file follows this format:
```
* * * * * command
- - - - -
| | | | |
| | | | +---- Day of the week (0 - 7) (Sunday=0 or 7)
| | | +------ Month (1 - 12)
| | +-------- Day of the month (1 - 31)
| +---------- Hour (0 - 23)
+------------ Minute (0 - 59)
```
Example

To schedule a job that runs a script at a specific time:
```
21 19 15 5 3 touch /root/readme.txt

```
This job will create an empty file /root/readme.txt at 19:21 (7:21 PM) on May 15th, if it is a Wednesday.
Explanation

    21 = Minute (21)
    19 = Hour (19 or 7 PM)
    15 = Day of the month (15th)
    05 = Month (May)
    3 = Day of the week (Wednesday, where 0 = Sunday and 7 = Sunday)

Managing the crond Service
Restarting the crond Service

After editing the crontab file, restart the crond service to apply changes:
```
systemctl restart crond
```
Enabling the crond Service at Boot

To ensure that the crond service starts automatically at boot:
```
systemctl enable crond

```
 ### Step-by-Step Example
 1.Edit the crontab file for the root user:
 ```
crontab -u root -e

```
2.Add the following line to create a file at 19:21 on May 15th if it is a Wednesday:
```
21 19 15 5 3 touch /root/readme.txt
```
3.Save and exit the editor. For vi or vim, type ESC:wq and press Enter.
4.Restart the crond service:
```
systemctl restart crond

```
5.Enable the crond service to start at boot:
```
systemctl enable crond

```
6.Verify the scheduled jobs for root:
```
crontab -u root -l

```




