Домашнее задание к занятию «Инструменты Git»
Ялова Л.В 

Задание
В клонированном репозитории:

Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.
Ответьте на вопросы.
Какому тегу соответствует коммит 85024d3?
Сколько родителей у коммита b8d720? Напишите их хеши.
Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.
Найдите коммит, в котором была создана функция func providerSource, её определение в коде выглядит так: func providerSource(...) (вместо троеточия перечислены аргументы).
Найдите все коммиты, в которых была изменена функция globalPluginDirs.
Кто автор функции synchronizedWriters?
В качестве решения ответьте на вопросы и опишите, как были получены эти ответы.

ОТВЕТ
найдем полный хеш и коммиты

```bash
lyalov@RedFox:/mnt/d/gitlab/terraform$ git show aefea --oneline
aefead2207 Update CHANGELOG.md
diff --git a/CHANGELOG.md b/CHANGELOG.md
index 86d70e3e0d..588d807b17 100644
--- a/CHANGELOG.md
+++ b/CHANGELOG.md
@@ -27,6 +27,7 @@ BUG FIXES:
 * backend/s3: Prefer AWS shared configuration over EC2 metadata credentials by default ([#25134](https://github.com/hashicorp/terraform/issues/25134))
 * backend/s3: Prefer ECS credentials over EC2 metadata credentials by default ([#25134](https://github.com/hashicorp/terraform/issues/25134))
 * backend/s3: Remove hardcoded AWS Provider messaging ([#25134](https://github.com/hashicorp/terraform/issues/25134))
+* command: Fix bug with global `-v`/`-version`/`--version` flags introduced in 0.13.0beta2 [GH-25277]
 * command/0.13upgrade: Fix `0.13upgrade` usage help text to include options ([#25127](https://github.com/hashicorp/terraform/issues/25127))
 * command/0.13upgrade: Do not add source for builtin provider ([#25215](https://github.com/hashicorp/terraform/issues/25215))
 * command/apply: Fix bug which caused Terraform to silently exit on Windows when using absolute plan path ([#25233](https://github.com/hashicorp/terraform/issues/25233))
 ```


Какому тегу соответствует коммит 85024d3?  
   Коммит 85024d3 , полный хеш: 85024d3100126de36331c6982bfaac02cdab9e76
   Является релизным коммитом для v0.12.23
   Автор — tf-release-bot
   Меняет только CHANGELOG.md и version/version.go

 ```bash
  lyalov@RedFox:/mnt/d/gitlab/terraform$ git log --oneline -5 v0.12.23
85024d3100 (tag: v0.12.23) v0.12.23
4703cb6c1c Update CHANGELOG.md
0b4470e0d4 Cleanup after v0.12.22 release
18bfd096ba (tag: v0.12.22) v0.12.22
c66cdcf780 backend/plan: Show warnings even without changes (backport) (#24172)
lyalov@RedFox:/mnt/d/gitlab/terraform$ git show 85024d3 --stat
commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)
Author: tf-release-bot <terraform@hashicorp.com>
Date:   Thu Mar 5 20:56:10 2020 +0000

    v0.12.23

 CHANGELOG.md       | 2 +-
 version/version.go | 2 +-
 2 files changed, 2 insertions(+), 2 deletions(-)
lyalov@RedFox:/mnt/d/gitlab/terraform$ git show 85024d3 --stat
 ```

 Сколько родителей у коммита b8d720? Напишите их хеши.

Количество родителей: 2
Хеши родителей:
56cd7859e05c36c06b56d013b55a252d0bb7e158
9ea88f22fc6269854151c571162c5bcf958bee2b

 ```bash
   lyalov@RedFox:/mnt/d/gitlab/terraform$ git show --pretty=%P b8d720
56cd7859e05c36c06b56d013b55a252d0bb7e158 9ea88f22fc6269854151c571162c5bcf958bee2b

lyalov@RedFox:/mnt/d/gitlab/terraform$ git cat-file -p b8d720
tree cec002aab630c8bc701cb85bc94e55e751cd2d8f
parent 56cd7859e05c36c06b56d013b55a252d0bb7e158
parent 9ea88f22fc6269854151c571162c5bcf958bee2b
author Chris Griggs <cgriggs@hashicorp.com> 1579657548 -0800
committer GitHub <noreply@github.com> 1579657548 -0800
gpgsig -----BEGIN PGP SIGNATURE-----

 wsBcBAABCAAQBQJeJ6lMCRBK7hj4Ov3rIwAAdHIIAAWogFD+6nxgm7suNlJVqGv3
 iczwk1OySRvZiDhgJuaIEZMduudoIBnv7XStZsg5wQ7a0byh4iU6z7w6vVKPyj1e
 2KyTqwriHOYqDJ/pljIX92btLU+rXDP0DpnTg8WuMthqUJGh6q8OGorvlIHDwcdN
 DKZxKaLPaBYCD5nuYMyhuh9T6+4ayEN4zUbl5vLPN7XmvhSf4yDQ0H4UaR596qOo
 phaqODHglNLegdGwi+JaTtDSB/JO5zJNfn8OnuRgyhoplmKKlhBAEwS4muxjjkzD
 cUtFA+jkXaVpbfEh/dBRb3yB4W17jrxFDuDESjXKiU61bc8Fwa1JrfQAFlXczmY=
 =s9Hk
 -----END PGP SIGNATURE-----


Merge pull request #23916 from hashicorp/cgriggs01-stable
 ```

 Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.

 ```bash
    lyalov@RedFox:/mnt/d/gitlab/terraform$ git log v0.12.23..v0.12.24 --oneline
33ff1c03bb (tag: v0.12.24) v0.12.24
b14b74c493 [Website] vmc provider links
3f235065b9 Update CHANGELOG.md
6ae64e247b registry: Fix panic when server is unreachable
5c619ca1ba website: Remove links to the getting started guide's old location
06275647e2 Update CHANGELOG.md
d5f9411f51 command: Fix bug when using terraform login on Windows
4b6d06cc5d Update CHANGELOG.md
dd01a35078 Update CHANGELOG.md
225466bc3e Cleanup after v0.12.23 release
 ```

 Найдите коммит, в котором была создана функция func providerSource, её определение в коде выглядит так: func providerSource(...) (вместо троеточия перечислены аргументы).
 нашелся тольк один коммит   8c928e8358
 
 ```bash
lyalov@RedFox:/mnt/d/gitlab/terraform$ git log -S "func providerSource(" --oneline
8c928e8358 main: Consult local directories as potential mirrors of providers
 ```

 Найдите все коммиты, в которых была изменена функция globalPluginDirs.

 ```bash
        lyalov@RedFox:/mnt/d/gitlab/terraform$ git log -S "globalPluginDirs" --oneline
        7c4aeac5f3 stacks: load credentials from config file on startup (#35952)
        65c4ba7363 Remove terraform binary
        125eb51dc4 Remove accidentally-committed binary
        22c121df86 Bump compatibility version to 1.3.0 for terraform core release (#30988)
        7c7e5d8f0a Don't show data while input if sensitive
        35a058fb3d main: configure credentials from the CLI config file
        c0b1761096 prevent log output during init
        8364383c35 Push plugin discovery down into command package
```


  Кто автор функции synchronizedWriters?
```bash
  lyalov@RedFox:/mnt/d/gitlab/terraform$ git log -S "func synchronizedWriters(" --oneline
bdfea50cc8 remove unused
5ac311e2a9 main: synchronize writes to VT100-faker on Windows
lyalov@RedFox:/mnt/d/gitlab/terraform$ git log -S "synchronizedWriters" --oneline
bdfea50cc8 remove unused
fd4f7eb0b9 remove prefixed io
5ac311e2a9 main: synchronize writes to VT100-faker on Windows
lyalov@RedFox:/mnt/d/gitlab/terraform$ git show --format="%an <%ae>" 5ac311e2a9 --quiet
Martin Atkins <mart@degeneration.co.uk>
lyalov@RedFox:/mnt/d/gitlab/terraform$ git show 5ac311e2a9 | head -n 5
commit 5ac311e2a91e381e2f52234668b49ba670aa0fe5
Author: Martin Atkins <mart@degeneration.co.uk>
Date:   Wed May 3 16:25:41 2017 -0700

    main: synchronize writes to VT100-faker on Windows
lyalov@RedFox:/mnt/d/gitlab/terraform$ 

```