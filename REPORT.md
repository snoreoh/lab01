## Домашняя работа #1

##Задания:

- [x] 1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
- [x] 2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0
- [x] 3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
- [x] 4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
- [x] 5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
- [x] 6. Найдите полный пусть до файла any.hpp внутри библиотеки boost.
- [x] 7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
- [x] 8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.
- [x] 9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
- [x] 10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
- [x] 11. Найдите топ10 самых "тяжёлых".
- [x] 12. Составить отчет и отправить ссылку личным сообщением в **Slack**


##Выполнение:
```bash
1.Command:
   $ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```
```sh
2.Command:
  $ tar -xf boost_1_69_0.tar.gz
```

```sh
3.Command:
  $ tree -L 1 OR $ find. -maxdepth 1 -type f | wc

Result: 12;
```
```sh
4.Command:
  $ tree OR $ find.  -type f | wc 
  
Result: 61192;
```

```sh
5.For ".cpp": Result == 13774; Command: $ find. -type f -name "*.cpp" | wc
  For ".h": Result == 96; Command: $ find. -type f -name "*.h" | wc
  For !".h" and !".cpp": Result == 47122; Command: $ find. -type f -not -name "*.cpp" -not -name "*.h" | wc
```
```sh
6.Command: $ find `pwd` -name "any.hpp"
Part of the result: 
/home/snoreoh/boost_1_69_0/boost/fusion/include/any.hpp
/home/snoreoh/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/snoreoh/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/snoreoh/boost_1_69_0/boost/type_erasure/any.hpp
/home/snoreoh/boost_1_69_0/boost/hana/any.hpp
/home/snoreoh/boost_1_69_0/boost/hana/fwd/any.hpp
```
```sh
7.Command: $ grep -lR "boost::asio"
Part of the result:
boost_output/include/boost/process/io.hpp
boost_output/include/boost/process/spawn.hpp
boost_output/include/boost/process/async.hpp
boost_output/include/boost/process/system.hpp
boost_output/include/boost/process/async_pipe.hpp
boost_output/include/boost/process/detail/windows/async_in.hpp
boost_output/include/boost/process/detail/windows/async_out.hpp
boost_output/include/boost/process/detail/windows/io_context_ref.hpp
```
```sh
8.Command ./bootstrap.sh --prefix=boost_output from istruction throwed an error:
                                              -Failed to build Boost.Build engine
So it's necessary to upload 'gpp' compiler:
 $ sudo apt install build-essential
 $ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
 $ sudo apt update
```
```sh
9.Being in ~/boost_1_69_0/boost_output write:
  $ mv ~/boost-libs
```
```sh
10.Command: du -ah
Part of the result: 
460K	./lib/libboost_math_tr1.so.1.69.0
120K	./lib/libboost_math_c99l.so.1.69.0
3,1M	./lib/libboost_math_tr1l.a
76K	./lib/libboost_stacktrace_backtrace.so.1.69.0
4,7M	./lib/libboost_wave.a
104K	./lib/libboost_date_time.so.1.69.0
```
```sh
11.Command: $ du -Sah | sort -rh | head -10

Result:
54M	./lib
4,7M	./lib/libboost_wave.a
4,5M	./lib/libboost_log.a
3,5M	./lib/libboost_locale.a
3,2M	./lib/libboost_regex.a
3,1M	./lib/libboost_math_tr1l.a
3,1M	./lib/libboost_math_tr1f.a
3,1M	./lib/libboost_math_tr1.a
2,7M	./lib/libboost_log_setup.a
2,4M	./lib/libboost_unit_test_framework.a
```




  

 

  
 
 


```
Copyright (c) 2015-2020 The ISC Authors
```
