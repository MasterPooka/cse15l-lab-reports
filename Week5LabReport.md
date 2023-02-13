**Week 5 Lab Report**
---
grep Command
---

**Sources**
---
[grep Documentation](https://www.gnu.org/software/grep/manual/grep.html)
---

**grep -w**
---
```$ grep -w "and" ch1.txt
        I also served on boards of directors and
        advisory committees for child-care centers, preschools, elementary schools, and 
```

```$ grep -w "the" ch2.txt
        In response to researchers’ queries, they frequently say that babies should be trained to be self-reliant from the
```

The -w command tells the computer to match only full words, which means that the start and end of the specified string has to be spaces. This means that the word won't be part of a larger word, like how "ring" is part of "string."

**grep -c**
---
```$ grep -c "and" ch1.txt
        143
```

```$ grep -c "the" ch2.txt
        183
```

The -c command pulls the number of occurrences of the specified string within a file, instead of printing out all lines that contain the string.

**grep -L**
---
```grep -L "alohomora" *
        CH4.txt
        ch1.txt
        ch2.txt
        ch7.txt
```

```grep -L "kombucha" *
        CH4.txt
        ch1.txt
        ch2.txt
        ch7.txt
```

The -L command shows all files that do not contain the specified string, unlike -l, which shows all files that does contain the specified string.

**grep -e**
```$ grep -e "and" -e "the" -l *
        CH4.txt
        ch1.txt
        ch2.txt
        ch7.txt
```

``` grep -e "you" -e "how" -l *
        CH4.txt
        ch1.txt
        ch2.txt
        ch7.txt
```

The -e command allows the user to filter multiple string into the grep command. When coupled with -l, it shows all files containing both specified arguments.
