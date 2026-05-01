---
title: "But My Password Is Correct!: Arch Faillock"
date: 2026-05-01
thumbnail: 'img/failed_attempts.png'
tags:
  - security
  -  arch
  - linux
categories:
  - Security
---


I guess you need a quick solution. If you do, here's one. 

```
su
faillock --rest

```

Okay, now the narrative.

I have run into this issue quite a number of times.
I enter the wrong password, say once or twice, but do give in the right one on the next attempts.
But then,  all recurring attempts are flagged as incorrect entries.
It makes you confused if someone changed your password or if the system is actually faulty.
Before learning it was part of how Arch secured accounts, it was confusing and at times had me considering re installing the OS.

Now I have encountered the issue before, and I solved it. But I don't know how I did. It just vanished. 
I mean the last time I did,it was after letting the system rest for a while.
It turns out the lockout is only for a while. 
Probably a security mechanism against bruteforce password cracking attempts.
But that is not the actual solution. Access to the mechanism that's responsible for this is. And that's `faillock`.

So Arch has this meachanism called the faillock that's triggered when an incorrect password is entered x consecutive times.
It works with the `pam_faillock.so` PAM module, which protects against brute-force attacks by temporarily locking user accounts after too many consecutive incorrect passwords.

## Default Behavior

Now default `faillock` configuration locks an account for **10 minutes** after **3 failed login attempts** within a **15-minute window**. Explains why after waiting for a while I was able to login. 
From my reading I also learnt that on some desktop environments like SDDM or hyprlock will show messages like "The account is locked due to 3 failed logins" or "(10 minutes left to unlock)" when this occurs.

## Viewing Failed Attempts

To check failed login records for a specific user:
```bash
faillock --user username
```

To check for the current user:
```bash
faillock --user $USER
```

## Resetting/Unlocking an Account

Now if your account gets locked, you can reset the failure counter in several ways:

**Method 1 - Using `faillock` (as root or from another logged-in session):**
```bash
sudo faillock --user username --reset
```

**Method 2 - Direct file removal:**
```bash
sudo rm /run/faillock/username
```

**Method 3 - If you have another TTY session already logged in**, you can run the reset command from there without needing root.

## Configuring `faillock`

You can modify the behavior by editing `/etc/security/faillock.conf`:

Here's a sample configuration file.

```conf
# Number of failed attempts before lock
deny = 5

# Time window for counting failures (seconds)
fail_interval = 900

# Lock duration after exceeding deny attempts (seconds)
unlock_time = 600
```

Common adjustments:

- `deny = 5` or `deny = 10` - More forgiving than the default 3 (for me at least)
- `unlock_time = 300` - Reduce lock time to 5 minutes (default as previously mentioned is 10)
- `fail_interval = 1800` - Extend counting window to 30 minutes

After editing the config file, no service restart is needed; changes take effect immediately for new authentication attempts.

## Some extra Notes

- **Tally files are stored in `/var/run/faillock/`** by default, which means they reset on reboot (since `/var/run` is typically a tmpfs).
- The `faillock` command requires root privileges (via `sudo`) unless you're checking your own user from an already-authenticated session.
- Some display managers (like older SDDM versions) may not show the unlock countdown message clearly, making a locked account appear as if the system is frozen. (Don't reinstall OS)




You can read about the command can at [the arch wiki](https://man.archlinux.org/man/faillock.8.en).

We learn something new every day. 
