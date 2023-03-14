**Week 9 Lab Report**
---
less Command


**Sources**
---
[less Documentation](https://man7.org/linux/man-pages/man1/less.1.html)


**less -jn**
---
```
$ less -j5 written_2/travel_guides/berlitz1/HandRIbiza.txt
        Recommended Hotels
        The establishments listed below offer a cross-section of
        local restaurants, and should convince you that not everything on the
        island comes with chips (french fries).
```
```
$ less -j-6 written_2/travel_guides/berlitz1/HandRIbiza.txt
        Recommended Hotels
        The establishments listed below offer a cross-section of
        local restaurants, and should convince you that not everything on the
        island comes with chips (french fries).
        The star rating in brackets after each entry refers to the
        offfical government rating system.
```

To jump to a particular line in a file being examined in the "less" pager, use the "-jn" option in the "less" command.

You can navigate up and down the text when reading a file in "less" by using the arrow buttons. However, you can use the "-jn" option to jump straight to a specific line if you know the line number you want to go to.

**less -n**
---
```
$ less -N written_2/travel_guides/berlitz1/HandRHongKong.txt
      1 
      2   
      3   
      4     
      5         
      6         Recommended Hotels
      7         Hong Kong has some of the most luxurious hotels in the
      8         world, with representatives from all the major international chains.
      9         Hotels listed below have full air-conditioning, offer 24-hour or
     10         limited room service, and a wide range of facilities. Hong Kong hotels
     11         have excellent business services and conference facilities; many have
     12         shopping malls.
```
```
$ less -N -j15 written_2/travel_guides/berlitz1/HandRHongKong.txt
     15         arrangements, the Hong Kong Hotel Reservation Center at the
     16         International Airport will be happy to arrange accommodations for you
     17         on your arrival.
     18         As a basic guide, the symbols below have been used to
     19         indicate high-season rates in Hong Kong dollars, based on double
     20         occupancy, with bath or shower. Unless otherwise noted, hotels take all
     21         major credit cards. A 10% service charge and 5% government tax will be
     22         added to the bill.
     23         $$$$above HK$2,500
     24         $$$HK$l,600 to HK$2,500
     25         $$HK$950 to HK$1,600
     26         $below HK$950
```

When examining a file, the "less" command's "-n" option is used to show line numbers.

Line numbers are not shown in the text being read by "less" by default. However, you can use the "-n" option to show line numbers if you want to be able to refer to particular lines or keep track of your progress through a big file. This option can be used with "-jn" to specify which portion of the text the user wants to see.

**less -bn**
---
```
$ less -b160 written_2/travel_guides/berlitz1/HandRHawaii.txt
        Oahu (Including Honolulu)
        Aston Waikiki Sunset $$$ 229 Paoakalani Avenue, Honolulu, HI
        96815; Tel. (808) 922-2700 or (800) 336-5599; fax (808) 922-8785;
        <www.aston-hotels.com>. One of Aston’s many condominium resort
        properties, this modern high-rise has large rooms with complete
```
```
$ less -b-1 written_2/travel_guides/berlitz1/HandRHawaii.txt
        Oahu (Including Honolulu)
        Aston Waikiki Sunset $$$ 229 Paoakalani Avenue, Honolulu, HI
        96815; Tel. (808) 922-2700 or (800) 336-5599; fax (808) 922-8785;
        <www.aston-hotels.com>. One of Aston’s many condominium resort
        properties, this modern high-rise has large rooms with complete
```

The "less" program can be launched at a particular line number by using the "-bn" option.

The default behavior of "less" is to view files from the very beginning. However, you can begin "less" at a particular line if you know the information you want to see begins at that line by using the "-bn" option. This makes viewing large files easier, because the computer does not have to load the entirety of a large file.

**less -Dxcolor**
---
```
$ less -N -j20 --color=Nblue written_2/travel_guides/berlitz1/HandRHongKong.txt
     20         occupancy, with bath or shower. Unless otherwise noted, hotels take all
     21         major credit cards. A 10% service charge and 5% government tax will be
     22         added to the bill.
     23         $$$$above HK$2,500
     24         $$$HK$l,600 to HK$2,500
     25         $$HK$950 to HK$1,600
     26         $below HK$950
     
```
```
$ less --color=Bred written_2/travel_guides/berlitz1/HandRHawaii.txt
        Oahu (Including Honolulu)
        Aston Waikiki Sunset $$$ 229 Paoakalani Avenue, Honolulu, HI
        96815; Tel. (808) 922-2700 or (800) 336-5599; fax (808) 922-8785;
        <www.aston-hotels.com>.
```

The "less" command's "-Dxcolor" option enables syntax highlighting for a number of file formats, including source code files.

When viewing a file with "less," the text often appears as plain text without any styling or highlighting. However if you choose the "-Dxcolor" option, "less" will highlight the words in the text, which can emphasize certain words or phrases.
