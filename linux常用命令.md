# linux常用命令：

## 很好的cat：

~~~
"依次显示相应文件的内容
cat file1.txt file2.txt file3.txt

"将显示的内容写到file4.txt里面去.(overwrite)
cat file1.txt file2.txt file3.txt > file4.txt

"将相应文件的内容按照字典序依次写入file4.txt(overwrite)
cat file1.txt file2.txt file3.txt | sort > file4.txt

将相应文件的内容加到file4.txt后面(append)
cat file5.txt >> file4.txt

"直接输入内容添加file4.txt的后面(a)
cat >> file4.txt
...//键入想输入的内容
~~~



## 压缩与解压缩gzip：

~~~apl
"压缩，生成压缩文件的同时删除原始文件。
gzip file

"keep:压缩，生成压缩文件的同时保存原始文件。
gzip -k file

"decompress:解压。
gzip -d *.gz

"force:压缩后产生的文件若存在，则强制重写。
gzip -df 

"将一个目录里的文件分别打包，同时对于子目录也进行相同的打包处理。(.gz文件里面只能打包单个文件)。
gzip -r  dir/

"将一个目录里的所有目录和文件作为一个整体打包至一个文件里面。
tar -czvf level1.tar.gz level1/

\
gzip -[1-9] file


gzip -t file
~~~



## 解压缩 1.tar：

**what tar.gz and tar.bz2 mean ?**

The `.tar` portion of the file extension stands for **t**ape **ar**chive, and is the reason that both of these file types are called tar files. 

The `.gz` or `.bz2` extension suffix indicates that the archive has been compressed, using either the `gzip` or `bzip2` compression algorithm. 

**how to extract files from  tar files**

~~~
tar -zxvf *.tar.gz
tar -jxvf *.tar.bz2
~~~

-options:

- -z:   Gzip, use gzip to decompress the tar file.

- -j:    Bzip2, use bzip2 to decompress the tar file.

- -v:   Verbose, list the files as they are being extracted.

- -x:  Extract, retrieve the files from the tar file. 

- -f:   File, the name of the tar file we want `tar` to work with. This option must be followed by the name of the tar file. 

  

**Choosing Where to Extract the Files To:**

~~~
"if  the destination directory is existed
tar -xvjf guitar_songs.tar.gz -C ~/Documents/Songs/

"if the destination directory is not existed
mkdir -p ~/Documents/Songs/Downloaded && tar -xvjf guitar_songs.tar.gz -C ~/Documents/Songs/Downloaded/
~~~



**Looking Inside Tar Files Before Extracting Them and extract a specified file：**

~~~
tar -tf ukulele_songs.tar.gz | less

tar -xvzf ukulele_songs.tar.gz "Ukulele Songs/Ramones/"
tar -xvzf ukulele_songs.tar.gz "Ukulele Songs/023 - My Babe.odt"
tar -xvz --wildcards -f ukulele_songs.tar.gz "Ukulele Songs/Possibles/B*"
~~~



** Extracting Files Without Extracting Directories:**

~~~
tar -xvzf ukulele_songs.tar.gz --strip-components=1
~~~





## 三剑客：grep,awk,sed；

## 1.grep

(据说是Ken Thompson 花了几个小时就弄出来的工具，orz)

~~~
"高亮搜索出的模式串"
alias grep='grep --colour=auto'

""
grep [options] patten file

"叛逆的反向匹配，只打印不匹配的内容"
grep -v Men geek.log

"沉默的grep options,搭配echo $?.return value 1 means the pattern is not found
,return value 0 means the pattern is found"
$home:grep -q Men geek.log
$home:echo $?

"递归地使用grep去匹配一个目录及其子目录。因此我们提供的不是一个文件名,而是一个路径名"
grep -r MEn pathname

"匹配时忽略大小写"
grep -i Men geek.log

"匹配时只会去匹配 whole pattern word(word regexp)"
grep -w -i men geek.log

""
grep -E -w -i "averge|memfree" geek.log

~~~

