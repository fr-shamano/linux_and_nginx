# linuxコマンド

## lsコマンド

ファイルやディレクトリの情報を表示するコマンド

***[] カレントディレクトリにあるファイルとサブディレクトリを表示する***

```bash
$ ls
dir_cat  dir_cd  dir_cp  dir_cpto  dir_grep  dir_less  dir_ls  dir_mv  dir_mvto  dir_rm  dir_tail
```

***[] dir_lsディレクトリ内のファイルを表示する***

```bash
$ ls ./dir_ls
file_ls1.txt
```

***[-l] カレントディレクトリにあるファイルやディレクトリの詳細な情報を表示する***

```bash
$ ls -l
total 0
drwxr-xr-x  3 root root  96 Mar 26 07:28 dir_cat
drwxr-xr-x  2 root root  64 Mar 26 07:28 dir_cd
drwxr-xr-x  6 root root 192 Mar 26 07:28 dir_cp
drwxr-xr-x  4 root root 128 Mar 26 07:28 dir_cpto
drwxr-xr-x  5 root root 160 Mar 26 07:28 dir_grep
drwxr-xr-x  2 root root  64 Mar 26 07:28 dir_less
drwxr-xr-x  3 root root  96 Mar 26 07:28 dir_ls
drwxr-xr-x 12 root root 384 Mar 26 07:28 dir_mv
drwxr-xr-x  4 root root 128 Mar 26 07:28 dir_mvto
drwxr-xr-x  4 root root 128 Mar 26 07:28 dir_rm
drwxr-xr-x  4 root root 128 Mar 26 07:28 dir_tail

# ディレクトリ内の詳細な情報表示も可能
$ ls -l ./dir_ls
total 4
-rw-r--r-- 1 root root 64 Mar 25 07:31 file_ls1.txt
```

## pwdコマンド

現在のカレントディレクトリを絶対パスで表示するコマンド

***[] 現在のカレントディレクトリの表示***

```bash
$ pwd
/var/www/app
```

## cdコマンド

カレントディレクトリを変更するコマンド

***[] dir_cdディレクトリに変更する***

```bash
$ pwd
/var/www/app

$ cd ./dir_cd

$ pwd
/var/www/app/dir_cd
```

***[] 親ディレクトリに移動する***

```bash
$ pwd
/var/www/app/dir_cd

$ cd ../

$ pwd
/var/www/app
```

***[] 現在のユーザのホームディレクトリに移動する***

```bash
$ pwd
/var/www/app

$ cd ~

$ pwd
/root
```

***[] 絶対パスで指定して変更する***

```bash
$ pwd
/root

$ cd /var/www/app

$ pwd
/var/www/app
```

## mkdirコマンド

空のディレクトリを作成するコマンド

***[] 「dir_mkdir」という名前のディレクトリを作成する***

```bash
$ ls
dir_cat  dir_cd  dir_cp  dir_cpto  dir_grep  dir_less  dir_ls  dir_mv  dir_mvto  dir_rm  dir_tail

$ mkdir dir_mkdir

$ ls
dir_cat  dir_cd  dir_cp  dir_cpto  dir_grep  dir_less  dir_ls  dir_mkdir  dir_mv  dir_mvto  dir_rm  dir_tail

$ ls -d dir_mkdir/
dir_mkdir/
```

***[-p] 「dir_mkdir」の中に「dir_child」、「dir_child/dir_grandc」、「dir_child/dir_grandc/dir_greatg」というディレクトリを作成する***

```bash
$ pwd
/var/www/app

$ ls -d ./dir_mkdir/
./dir_mkdir/

$ mkdir -p ./dir_mkdir/dir_child/dir_grandc/dir_greatg

$ ls -d ./dir_mkdir/
./dir_mkdir/

$ ls -d ./dir_mkdir/dir_child/
./dir_mkdir/dir_child/

$ ls -d ./dir_mkdir/dir_child/dir_grandc/
./dir_mkdir/dir_child/dir_grandc/

$ ls -d ./dir_mkdir/dir_child/dir_grandc/dir_greatg/
./dir_mkdir/dir_child/dir_grandc/dir_greatg/
```

## rmコマンド

ファイルやディレクトリを削除するコマンド

***[] 「dir_rm」ディレクトリにある「file_rm1.txt」ファイルを削除する***

```bash
$ ls -l ./dir_rm/
total 8
-rw-r--r-- 1 root root 88 Mar 25 07:33 file_rm1.txt
-rw-r--r-- 1 root root 90 Mar 25 07:33 file_rm2.txt

$ rm ./dir_rm/file_rm1.txt

$ ls -l ./dir_rm/
total 4
-rw-r--r-- 1 root root 90 Mar 25 07:33 file_rm2.txt
```

***[-i] 「dir_rm」ディレクトリにある「file_rm2.txt」ファイルを削除する前にユーザー確認する***

```bash
$ ls -l ./dir_rm/
total 4
-rw-r--r-- 1 root root 90 Mar 25 07:33 file_rm2.txt

$ rm -i ./dir_rm/file_rm2.txt
rm: remove regular file ‘./dir_rm/file_rm2.txt’? N
# 削除しない場合は「y」か「Y」以外を入力する。何も入力せずEnterでも可

$ ls -l ./dir_rm/
total 4
-rw-r--r-- 1 root root 90 Mar 25 07:33 file_rm2.txt

$ rm -i ./dir_rm/file_rm2.txt
rm: remove regular file ‘./dir_rm/file_rm2.txt’? Y
# 削除する場合は「y」か「Y」を入力する

$ ls -l ./dir_rm/
total 0
```

***[-r] 「dir_rm」ディレクトリを削除する***

```bash
$ ls -ld ./dir_rm
drwxr-xr-x 2 root root 64 Mar 25 07:53 ./dir_rm

$ rm -r ./dir_rm/

$ ls -ld ./dir_rm
ls: cannot access ./dir_rm: No such file or directory

$ ls -l
total 0
drwxr-xr-x  3 root root  96 Mar 26 07:28 dir_cat
drwxr-xr-x  2 root root  64 Mar 26 07:28 dir_cd
drwxr-xr-x  6 root root 192 Mar 26 07:28 dir_cp
drwxr-xr-x  4 root root 128 Mar 26 07:28 dir_cpto
drwxr-xr-x  5 root root 160 Mar 26 07:28 dir_grep
drwxr-xr-x  2 root root  64 Mar 26 07:28 dir_less
drwxr-xr-x  3 root root  96 Mar 26 07:28 dir_ls
drwxr-xr-x  3 root root  96 Mar 26 08:18 dir_mkdir
drwxr-xr-x 12 root root 384 Mar 26 07:28 dir_mv
drwxr-xr-x  4 root root 128 Mar 26 07:28 dir_mvto
drwxr-xr-x  4 root root 128 Mar 26 07:28 dir_tail
```

## cpコマンド

ファイルやディレクトリをコピーするコマンド
コピー先に同名のものがあると上書きされるので注意

***[] 「dir_cp」ディレクトリにある「file_cp1.txt」を「dir_cpto」ディレクトリにコピーする***

```bash
$ ls -l ./dir_cp
total 12
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child
-rw-r--r-- 1 root root 67 Mar 25 08:03 file_cp1.txt
-rw-r--r-- 1 root root 91 Mar 25 08:30 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ ls -l ./dir_cpto
total 0
-rwxrwxrwx 1 root root 0 Mar 25 08:30 file_cp1.txt
-rwxrwxrwx 1 root root 0 Mar 25 08:30 file_cp2.txt

$ cp ./dir_cp/file_cp1.txt ./dir_cpto/file_cp1.txt

$ ls -l ./dir_cp
total 12
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child
-rw-r--r-- 1 root root 67 Mar 25 08:03 file_cp1.txt
-rw-r--r-- 1 root root 91 Mar 25 08:30 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ ls -l ./dir_cpto
total 4
-rwxrwxrwx 1 root root 67 Mar 26 08:21 file_cp1.txt
-rwxrwxrwx 1 root root  0 Mar 25 08:30 file_cp2.txt
```

***[-i] 「dir_cp」ディレクトリにある「file_cp2.txt」を「dir_cpto」ディレクトリにコピーする前にユーザー確認する***

```bash
$ ls -l ./dir_cp
total 12
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child
-rw-r--r-- 1 root root 67 Mar 25 08:03 file_cp1.txt
-rw-r--r-- 1 root root 91 Mar 25 08:30 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ ls -l ./dir_cpto
total 4
-rwxrwxrwx 1 root root 67 Mar 26 08:21 file_cp1.txt
-rwxrwxrwx 1 root root  0 Mar 25 08:30 file_cp2.txt

$ cp -i ./dir_cp/file_cp2.txt ./dir_cpto/file_cp2.txt
cp: overwrite ‘./dir_cpto/file_cp2.txt’?
# コピーしない場合は「y」か「Y」以外を入力する。何も入力せずEnterでも可

$ ls -l ./dir_cpto
total 4
-rwxrwxrwx 1 root root 67 Mar 26 08:21 file_cp1.txt
-rwxrwxrwx 1 root root  0 Mar 25 08:30 file_cp2.txt

$ cp -i ./dir_cp/file_cp2.txt ./dir_cpto/file_cp2.txt
cp: overwrite ‘./dir_cpto/file_cp2.txt’? y
# コピーする場合は「y」か「Y」を入力する

$ ls -l ./dir_cp
total 12
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child
-rw-r--r-- 1 root root 67 Mar 25 08:03 file_cp1.txt
-rw-r--r-- 1 root root 91 Mar 25 08:30 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ ls -l ./dir_cpto
total 8
-rwxrwxrwx 1 root root 67 Mar 26 08:21 file_cp1.txt
-rwxrwxrwx 1 root root 91 Mar 26 08:25 file_cp2.txt
```

***[-p] 「dir_cp」ディレクトリにある「file_cp3.txt」を「dir_cpto」ディレクトリにファイル属性を保持したままコピーする***

```bash
$ ls -l ./dir_cp
total 12
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child
-rw-r--r-- 1 root root 67 Mar 25 08:03 file_cp1.txt
-rw-r--r-- 1 root root 91 Mar 25 08:30 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ ls -l ./dir_cpto
total 8
-rwxrwxrwx 1 root root 67 Mar 26 08:21 file_cp1.txt
-rwxrwxrwx 1 root root 91 Mar 26 08:25 file_cp2.txt

$ cp -p ./dir_cp/file_cp3.txt ./dir_cpto/file_cp3.txt

$ ls -l ./dir_cp
total 12
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child
-rw-r--r-- 1 root root 67 Mar 25 08:03 file_cp1.txt
-rw-r--r-- 1 root root 91 Mar 25 08:30 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ ls -l ./dir_cpto
total 12
-rwxrwxrwx 1 root root 67 Mar 26 08:21 file_cp1.txt
-rwxrwxrwx 1 root root 91 Mar 26 08:25 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt
```

***[-r]  「dir_cp/dir_child」ディレクトリを「dir_cpto」ディレクトリにコピーする***

```bash
$ ls -l ./dir_cp
total 12
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child
-rw-r--r-- 1 root root 67 Mar 25 08:03 file_cp1.txt
-rw-r--r-- 1 root root 91 Mar 25 08:30 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ ls -l ./dir_cpto
total 12
-rwxrwxrwx 1 root root 67 Mar 26 08:21 file_cp1.txt
-rwxrwxrwx 1 root root 91 Mar 26 08:25 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ cp -r ./dir_cp/dir_child/ ./dir_cpto/dir_child/

$ ls -l ./dir_cp
total 12
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child
-rw-r--r-- 1 root root 67 Mar 25 08:03 file_cp1.txt
-rw-r--r-- 1 root root 91 Mar 25 08:30 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt

$ ls -l ./dir_cpto
total 12
drwxr-xr-x 2 root root 64 Mar 26 08:27 dir_child
-rwxrwxrwx 1 root root 67 Mar 26 08:21 file_cp1.txt
-rwxrwxrwx 1 root root 91 Mar 26 08:25 file_cp2.txt
-rw-r--r-- 1 root root 91 Mar 25 09:00 file_cp3.txt
```

## mvコマンド

指定した場所にファイルやディレクトリを移動する
また、ファイル名やディレクトリ名を変更するコマンド
移動先に同名のものがあると上書きされるので注意

***[] 「dir_mv」ディレクトリにある「file_mv1.txt」ファイルを「dir_mvto」ディレクトリに移動する***

```bash
$ ls -l ./dir_mv
total 16
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child1
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root  85 Mar 26 06:44 file_mv1.txt
-rw-r--r-- 1 root root  88 Mar 26 06:43 file_mv2.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ ls -l ./dir_mvto
total 0
drwxrwxrwx 2 root root 64 Mar 26 07:28 dir_child3
-rwxrwxrwx 1 root root  0 Mar 26 01:58 file_mv3.txt

$ mv ./dir_mv/file_mv1.txt ./dir_mvto/

$ ls -l ./dir_mv
total 12
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child1
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 file_mv2.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ ls -l ./dir_mvto
total 4
drwxrwxrwx 2 root root 64 Mar 26 07:28 dir_child3
-rw-r--r-- 1 root root 85 Mar 26 06:44 file_mv1.txt
-rwxrwxrwx 1 root root  0 Mar 26 01:58 file_mv3.txt
```

***[] 「dir_mv/dir_child1」ディレクトリを「dir_mvto」ディレクトリに移動する***

```bash
$ ls -l ./dir_mv
total 12
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child1
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 file_mv2.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ ls -l ./dir_mvto
total 4
drwxrwxrwx 2 root root 64 Mar 26 07:28 dir_child3
-rw-r--r-- 1 root root 85 Mar 26 06:44 file_mv1.txt
-rwxrwxrwx 1 root root  0 Mar 26 01:58 file_mv3.txt

$ mv ./dir_mv/dir_child1 ./dir_mvto

$ ls -l ./dir_mv
total 12
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 file_mv2.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ ls -l ./dir_mvto
total 4
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child1
drwxrwxrwx 2 root root 64 Mar 26 07:28 dir_child3
-rw-r--r-- 1 root root 85 Mar 26 06:44 file_mv1.txt
-rwxrwxrwx 1 root root  0 Mar 26 01:58 file_mv3.txt
```

***[] 「dir_mv」ディレクトリにある「file_mv2.txt」ファイル名を「newfile_mv2.txt」に変更する***

```bash
$ ls -l ./dir_mv
total 12
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 file_mv2.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ mv ./dir_mv/file_mv2.txt ./dir_mv/newfile_mv2.txt

$ ls -l ./dir_mv
total 12
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt
```

***[] 「dir_mv/dir_child2」ディレクトリ名を「newdir_child2」に変更する***

```bash
$ ls -l ./dir_mv
total 12
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ mv ./dir_mv/dir_child2 ./dir_mv/newdir_child2

$ ls -l ./dir_mv
total 12
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt
```

***[-i] 「dir_mv」ディレクトリにある「file_mv3.txt」ファイルを「dir_mvto」ディレクトリに移動する前に移動するかどうか確認する***

```bash
$ ls -l ./dir_mv
total 12
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ ls -l ./dir_mvto
total 4
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child1
drwxrwxrwx 2 root root 64 Mar 26 07:28 dir_child3
-rw-r--r-- 1 root root 85 Mar 26 06:44 file_mv1.txt
-rwxrwxrwx 1 root root  0 Mar 26 01:58 file_mv3.txt

$ mv -i ./dir_mv/file_mv3.txt ./dir_mvto
mv: overwrite ‘./dir_mvto/file_mv3.txt’?
# コピーしない場合は「y」か「Y」以外を入力する。何も入力せずEnterでも可

$ ls -l ./dir_mvto
total 4
drwxr-xr-x 2 root root 64 Mar 26 07:28 dir_child1
drwxrwxrwx 2 root root 64 Mar 26 07:28 dir_child3
-rw-r--r-- 1 root root 85 Mar 26 06:44 file_mv1.txt
-rwxrwxrwx 1 root root  0 Mar 26 01:58 file_mv3.txt

$ mv -i ./dir_mv/file_mv3.txt ./dir_mvto
mv: overwrite ‘./dir_mvto/file_mv3.txt’? y
# コピーする場合は「y」か「Y」を入力する

$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ ls -l ./dir_mvto
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child1
drwxrwxrwx 2 root root  64 Mar 26 07:28 dir_child3
-rw-r--r-- 1 root root  85 Mar 26 06:44 file_mv1.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
```

***[-i] 「dir_mv/dir_child3」ディレクトリを「dir_mvto」ディレクトリに移動する前に移動するかどうか確認する***

```bash
$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child3
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ ls -l ./dir_mvto
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child1
drwxrwxrwx 2 root root  64 Mar 26 07:28 dir_child3
-rw-r--r-- 1 root root  85 Mar 26 06:44 file_mv1.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt

$ mv -i ./dir_mv/dir_child3 ./dir_mvto
mv: overwrite ‘./dir_mvto/dir_child3’?
# コピーしない場合は「y」か「Y」以外を入力する。何も入力せずEnterでも可

$ ls -l ./dir_mvto
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child1
drwxrwxrwx 2 root root  64 Mar 26 07:28 dir_child3
-rw-r--r-- 1 root root  85 Mar 26 06:44 file_mv1.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt

$ mv -i ./dir_mv/dir_child3 ./dir_mvto
mv: overwrite ‘./dir_mvto/dir_child3’? y
# コピーする場合は「y」か「Y」を入力する

$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ ls -l ./dir_mvto
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child1
drwxrwxrwx 3 root root  96 Mar 26 08:37 dir_child3
-rw-r--r-- 1 root root  85 Mar 26 06:44 file_mv1.txt
-rw-r--r-- 1 root root 112 Mar 26 06:47 file_mv3.txt
```

***[-i] 「dir_mv」ディレクトリにある「file_mv4.txt」ファイル名を「newfile_mv4.txt」に変更する前に変更するかどうか確認する***

```bash
$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ mv -i ./dir_mv/file_mv4.txt ./dir_mv/newfile_mv4.txt
mv: overwrite ‘./dir_mv/newfile_mv4.txt’?
# コピーしない場合は「y」か「Y」以外を入力する。何も入力せずEnterでも可

$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
-rw-r--r-- 1 root root 115 Mar 26 06:46 file_mv4.txt
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root   0 Mar 26 02:00 newfile_mv4.txt

$ mv -i ./dir_mv/file_mv4.txt ./dir_mv/newfile_mv4.txt
mv: overwrite ‘./dir_mv/newfile_mv4.txt’? y
# コピーする場合は「y」か「Y」を入力する

$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 newfile_mv4.txt
```

***[-i] 「dir_mv/dir_child4」ディレクトリ名を「newdir_child4」に変更する前に変更するかどうか確認する***

```bash
$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 dir_child4
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 newfile_mv4.txt

$ mv -i ./dir_mv/dir_child4 ./dir_mv/newdir_child4
mv: overwrite ‘./dir_mv/newdir_child4/dir_child4’?
# コピーしない場合は「y」か「Y」以外を入力する。何も入力せずEnterでも可

$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 08:42 dir_child4
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 3 root root  96 Mar 26 08:41 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 newfile_mv4.txt

$ mv -i ./dir_mv/dir_child4 ./dir_mv/newdir_child4
mv: overwrite ‘./dir_mv/newdir_child4/dir_child4’? y
# コピーする場合は「y」か「Y」を入力する

$ ls -l ./dir_mv
total 8
drwxr-xr-x 2 root root  64 Mar 26 07:28 newdir_child2
drwxr-xr-x 3 root root  96 Mar 26 08:41 newdir_child4
-rw-r--r-- 1 root root  88 Mar 26 06:43 newfile_mv2.txt
-rw-r--r-- 1 root root 115 Mar 26 06:46 newfile_mv4.txt
```

## catコマンド

ファイルの内容を表示するコマンド

***[] 「dir_cat」ディレクトリにある「file_cat1.txt」のファイル内容を表示する***

```bash
$ ls -l ./dir_cat/
total 4
-rw-r--r-- 1 root root 574 Mar 26 07:20 file_cat1.txt

$ cat ./dir_cat/file_cat1.txt
linuxコマンド確認

catコマンドでの確認ファイル

catとは・・・

cat（キャット）はUNIXの標準コマンドであり

ファイルを連結させたり表示したりするのに用いる。

catは連結することを意味する「catenate」の略である。

出典: フリー百科事典『ウィキペディア（Wikipedia）』


cat ファイル名
と入力するとこのようにファイルの内容が表示されます。

CUIでとっさにファイル内容を確認する時には非常に役立ちます。
```

## tailコマンド

ファイル内容の末尾部分を表示するコマンド

***[] 「dir_tail」ディレクトリにある「file_tail1.txt」のファイル内容の末尾部分を表示する***

```bash
$ ls -l ./dir_tail/
total 8
-rw-r--r-- 1 root root 607 Mar 26 07:03 file_tail1.txt
-rw-r--r-- 1 root root 631 Mar 26 07:07 file_tail2.txt

$ tail ./dir_tail/file_tail1.txt

Coreutils の一部。

出典: フリー百科事典『ウィキペディア（Wikipedia）』

tail ファイル名
と入力すると最終行から10行分の内容が表示されます。

オプションを使えばファイルの監視ができるようになる。
業務で使用することも多々あります


# オプション無しだと最終行から10行が表示される
```

***[-n] 「dir_tail」ディレクトリにある「file_tail2.txt」のファイル内容を末尾から指定した行数分を表示する***

```bash
$ ls -l ./dir_tail/
total 8
-rw-r--r-- 1 root root 607 Mar 26 07:03 file_tail1.txt
-rw-r--r-- 1 root root 631 Mar 26 07:07 file_tail2.txt

$ tail -n 15 ./dir_tail/file_tail2.txt
tailとは・・・

tail（テール）はUNIXおよびUnix系のシステムで

テキストファイルやパイプ上のデータの末尾から数行を表示するプログラムである。

Coreutils の一部。

出典: フリー百科事典『ウィキペディア（Wikipedia）』

tail -n 15 ファイル名
と入力すると最終行から15行分の内容が表示されます。

オプションを使えばファイルの監視ができるようになる。
業務で使用することも多々あります
```

***[-f] 「dir_tail」ディレクトリにある「file_tail3.txt」のファイルの末尾に追加された行を表示し続ける***

```bash
TODO: 今回ログを流せるようなものがない。バックグラウンドで実行するshを自作した方が良いか？
xxxxxxxx
```

## lessコマンド（コマンドを使用するにはインストールが必要）

ファイルを1画面ずつ表示するコマンド

***[オプション1] 実施した時の挙動***

```bash
xxxxxxxx
```

***[オプション2] 実施した時の挙動***

```bash
xxxxxxxx
```

## grepコマンド

ファイルの中で文字列が含まれている行を表示するコマンド

***[] 「dir_grep」ディレクトリにある「file_grep1.txt」から「grep確認」が含まれる行を表示する***

```bash
$ ls -l ./dir_grep/
total 12
-rw-r--r-- 1 root root 674 Mar 26 07:20 file_grep1.txt
-rw-r--r-- 1 root root 692 Mar 26 07:21 file_grep2.txt
-rw-r--r-- 1 root root 692 Mar 26 07:21 file_grep3.txt

$ cat ./dir_grep/file_grep1.txt
linuxコマンド確認

grepコマンドでの確認ファイル

grep確認
GREP確認

grepとは・・・

grep（グレップ、グレプ）は、UNIXおよびUnixオペレーティングシステムにおけるコマンド。

テキストファイル中から

正規表現に一致する行を検索して出力する。

出典: フリー百科事典『ウィキペディア（Wikipedia）』

grep 調べたい文字 ファイル名
と入力するとファイルの中から調べたい文字を含む行が表示されます。

catだとすべて表示されますが、これなら特定の行のみを表示することも可能です。

$ grep "grep確認" ./dir_grep/file_grep1.txt
grep確認
```

***[-i] 「dir_grep」ディレクトリにある「file_grep2.txt」から「grep確認」（英字の大文字小文字を区別せず）が含まれる行を表示する***

```bash
$ ls -l ./dir_grep/
total 12
-rw-r--r-- 1 root root 674 Mar 26 07:20 file_grep1.txt
-rw-r--r-- 1 root root 692 Mar 26 07:21 file_grep2.txt
-rw-r--r-- 1 root root 692 Mar 26 07:21 file_grep3.txt

$ cat ./dir_grep/file_grep2.txt
linuxコマンド確認

grepコマンド -iオプションでの確認ファイル

grep確認
GREP確認

grepとは・・・

grep（グレップ、グレプ）は、UNIXおよびUnixオペレーティングシステムにおけるコマンド。

テキストファイル中から

正規表現に一致する行を検索して出力する。

出典: フリー百科事典『ウィキペディア（Wikipedia）』

grep 調べたい文字 ファイル名
と入力するとファイルの中から調べたい文字を含む行が表示されます。

catだとすべて表示されますが、これなら特定の行のみを表示することも可能です。

$ grep -i "grep確認" ./dir_grep/file_grep2.txt
grep確認
GREP確認
```

***[-v] 「dir_grep」ディレクトリにある「file_grep3.txt」から「grep確認」が含まれない行を表示する***

```bash
$ ls -l ./dir_grep/
total 12
-rw-r--r-- 1 root root 674 Mar 26 07:20 file_grep1.txt
-rw-r--r-- 1 root root 692 Mar 26 07:21 file_grep2.txt
-rw-r--r-- 1 root root 692 Mar 26 07:21 file_grep3.txt

$ cat ./dir_grep/file_grep3.txt
linuxコマンド確認

grepコマンド -vオプションでの確認ファイル

grep確認
GREP確認

grepとは・・・

grep（グレップ、グレプ）は、UNIXおよびUnixオペレーティングシステムにおけるコマンド。

テキストファイル中から

正規表現に一致する行を検索して出力する。

出典: フリー百科事典『ウィキペディア（Wikipedia）』

grep 調べたい文字 ファイル名
と入力するとファイルの中から調べたい文字を含む行が表示されます。

catだとすべて表示されますが、これなら特定の行のみを表示することも可能です。

$ grep -v "grep確認" ./dir_grep/file_grep3.txt
linuxコマンド確認

grepコマンド -vオプションでの確認ファイル

GREP確認

grepとは・・・

grep（グレップ、グレプ）は、UNIXおよびUnixオペレーティングシステムにおけるコマンド。

テキストファイル中から

正規表現に一致する行を検索して出力する。

出典: フリー百科事典『ウィキペディア（Wikipedia）』

grep 調べたい文字 ファイル名
と入力するとファイルの中から調べたい文字を含む行が表示されます。

catだとすべて表示されますが、これなら特定の行のみを表示することも可能です。
```

***TODO: パイプを使用した利用したコマンド***

```bash
xxxxxxxx
```

### historyコマンド

コマンドの実行履歴が順に表示されるコマンド

***[] コマンドの実行履歴を表示する***

```bash
$ history
    1  ls
    2  ls ./dir_ls
    3  ls -l
    4  ls -l ./dir_ls
    5  pwd
    6  pwd
    7  cd ./dir_cd
    8  pwd
    9  cd ../
   10  pwd
   11  ls
   12  mkdir dir_mkdir
   13  ls

    ~

  100  grep ./dir_grep/file_grep1.txt | grep grep確認
  101  grep ./dir_grep/file_grep1.txt | grep "grep確認"
  102  grep "grep確認" ./dir_grep/file_grep1.txt
  103  cat ./dir_grep/file_grep1.txt
  104  cat ./dir_grep/file_grep2.txt
  105  grep -i "GREP確認" ./dir_grep/file_grep2.txt
  106  grep -i "grep確認" ./dir_grep/file_grep2.txt
  107  cat ./dir_grep/file_grep3.txt
  108  grep -v "grep確認" ./dir_grep/file_grep3.txt
  109  history
```

***[] コマンドの実行履歴にある10番目のコマンドを実行する***

```bash
$ !10
pwd
/var/www/app

# 上記の一覧からだと「pwd」が実行されます。
```

## TODO: パイプを利用したコマンド実行

説明

***[オプション1] 実施した時の挙動***

```bash
xxxxxxxx
```

***[オプション2] 実施した時の挙動***

```bash
xxxxxxxx
```
