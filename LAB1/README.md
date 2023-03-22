---
editor_options: 
  markdown: 
    wrap: 72
---

# LAB1

# Название

Лабораторная работа №1

## Цель

1.  Собрать сведения о системе

## ️Исходные данные

1.  Macbook Pro 14 2021
2.  RStudio Desktop
3.  Интерпретатор языка R 4.2.2

## План

1.  ️Выполнить команду system("sw_vers")

2.  Выполнить команду **`systeminfo`** с ключом **`/fo CSV`**

3.  Выполнить команду system("log show --predicate 'subsystem ==
    \\"com.apple.securityd\\"' --last 1m")

## Шаги

1.  Сначала выполним команду **`systeminfo`** с ключом **`/fo CSV`**,
    чтобы получить подробную информацию о системе в формате CSV:

    ``` r
    system('system_profiler SPHardwareDataType SPSoftwareDataType | awk \'/Processor|Memory|Model Identifier|Year|System Version|Kernel|Boot Volume|Time/ { $1=$1; print }\' | sed \'s/ :/:/g\'', intern = TRUE)
    ```

        [1] "Model Identifier: MacBookPro18,3"    
        [2] "Memory: 16 GB"                       
        [3] "System Version: macOS 13.2.1 (22D68)"
        [4] "Kernel Version: Darwin 22.3.0"       
        [5] "Boot Volume: Macintosh HD"           
        [6] "Secure Virtual Memory: Enabled"      
        [7] "Time since boot: 14 дней 53 минуты"  

2\. Далее команда system("sysctl -n machdep.cpu.brand_string
machdep.cpu.core_count machdep.cpu.thread_count")\
Эта команда выведет следующую информацию о процессоре:

-   **`machdep.cpu.brand_string`** - название процессора;

-   **`machdep.cpu.core_count`** - количество ядер процессора;

-   **`machdep.cpu.thread_count`** - количество потоков процессора;

``` r
# получить информацию о процессоре
system("sysctl -n machdep.cpu.brand_string machdep.cpu.core_count machdep.cpu.thread_count")
```

3\. Также выполним команду system("log show --predicate 'subsystem ==
\\"com.apple.securityd\\"' --last 1m") дя вывода записей лога системы
безопасности (securityd) за крайнюю минуту

``` r
system("log show --predicate 'subsystem == \"com.apple.securityd\"' --last 1m")
```

## Оценка результата

В результате лабораторной работы мы получили основную информацию об ОС,
процессоре и логи безопасности системы.

## ️Вывод

Таким образом, мы научились работать с базовыми командами командой
строки и получать информацию об операционной системе.
