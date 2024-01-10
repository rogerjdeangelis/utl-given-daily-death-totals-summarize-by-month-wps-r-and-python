# utl-given-daily-death-totals-summarize-by-month-wps-r-and-python
Given daily death totals summarize by month wps r and python
    %let pgm=utl-given-daily-death-totals-summarize-by-month-wps-r-and-python;

    Given daily death totals summarize by month wps r and python

    %stop_submission;  /* stop immediately if you accidentially submit the entire window */

    stackoverflow r
    http://tinyurl.com/386f74z5
    https://stackoverflow.com/questions/77781257/transform-event-to-country-month-dataset

    github
    http://tinyurl.com/26ktajh2
    https://github.com/rogerjdeangelis/utl-given-daily-death-totals-summarize-by-month-wps-r-and-python

    SOLUTIONS

         1 wps sql
         2 wps r sql
         3 wps python sql
         4 line plot

    github
    https://tinyurl.com/2p8z8x7d
    https://github.com/rogerjdeangelis/utl-adding-infile-options-like-lrecl-and-recfm-to-cards-or-datalines-input

     ASSUMPTIONS (if you have added just a couple observations before 1989 and after 1993 to create 'big data',
                  there is no need, even if you had 141 countries and 50 years this would still be tiny data. )

        I Assume intermediate days without a record of civilian deaths have 0 deaths.
          Only 40 of the 200 dates have non zero civiian deaths output is just 40 observations

        2 The start and end dates are the same day in the example data.
          This solution works with different start and end dates, but applies the total to the
          first date,

        3 Sum these duplicate dates  (only dups in raw posted data)

             DAY      DEATHS

          1989-04-04       6
          1989-04-04       4   10

          1992-06-01       2
          1992-06-01       1    3

        4 I removed the these dates for presentation purposes only, easy to change.

           2017-07-31
           2021-08-26
           2021-08-28
           2021-08-29

        5  Assume this period.

           %let beg =01JAN1989
           %let end =31DEC1903

           Even if the span was 1989 - 2023 and you had a 141 countries
           the data would be be tiny for my $600 power workstation
           with 32 physical processors and 128gb ram.
           No need for optimization,
           Big data is a single table over 1tb,

        6  There are no deaths after 1993 so I drooed 1994 on


    Problem: Create the data for this graphic


                1   1   1   1   1   1   1   1   1   1   1   1   1   1   1   1   1   1
                9   9   9   9   9   9   9   9   9   9   9   9   9   9   9   9   9   9
                8   8   8   8   8   8   8   9   9   9   9   9   9   9   9   9   9   9
                9   9   9   9   9   9   9   0   0   1   1   2   2   2   2   2   3   3
                .   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .
                0   0   0   0   0   1   1   0   0   0   1   0   0   0   0   0   0   0
                2   3   4   6   9   0   2   4   7   7   0   2   4   6   8   9   1   2
              +-+---+---+---+---+---+---+---+---+---+---+---+---+---+---+---+---+---+---+
       DEATHS |                                                                         | DEATHS
              |   TIME SERIES OF TOTAL MONTHLY CIVILIAN DEATHA IN AFGANISTAN            |
              |   Intermediate months without any civilian deaths are not shown         |
          870 +   (dates with 1 death have been removed)                                + 870
              |                                                         * 870           |
              //  The 700 deaths in April 1992 agrres with documents    I               //
              //                                                        I               //
              |   From April 1992, Hezb-e Islami raided                 I               |
          850 +   Kabul with rocket attacks destroying                  I               + 850
              |   hundreds of homes and killing between                 I               |
          700 +   1,800 and 2,500 people.                       * 700   I               + 700
              |                                                 I       I               |
              //                                                I       I               //
              //                                                I       I               //
              |                                                 I       I               |
          200 +                                                 I       I               + 200
              |                                                 I       I               |
          150 +                                                 I       I               + 150
              |    Needles are annotated with                   I       I               |
              //   total civilian deaths                        I       I               //
              //                                                I       I               //
              |                                                 I       I               |
           75 +                                                 I       I           *77 +  75
              |                                                 I       I           I   |
              |                                                 I       I           I   |
              |                                                 I       I           I   |
              |                                                 I       I           I   |
           50 +                                                 I       I           I   +  50
              |                                                 I       I           I   |
              |         * 42                                    I       I           I   |
              |         I                                       I       I           I   |
              |         I                                       I       I           I   |
           25 +         I                                       I       I           I   +  25
              |         I           * 19            * 20        I       I           I   |
              |         I           I               I           I       I           I   |
              | * 12    I   *10 *11 I               I           I       I           I   |
              | I   *4  I   I   I   I   * 4 * 3     I   * 3     I       I   *6  *3  I   |
            0 + I   I   I   I   I   I   I   I I * 2 I   I   *2  I   *2  I   I   I   I   +   0
              |         I   I   I   I   I   I I I   I   I   I   I   I   I   I   I   I   |
              +-+---+---+---+---+---+---+---+---+---+---+---+---+---+---+---+---+---+---+
                1   1   1   1   1   1   1   1   1   1   1   1   1   1   1   1   1   1
                9   9   9   9   9   9   9   9   9   9   9   9   9   9   9   9   9   9
                8   8   8   8   8   8   8   9   9   9   9   9   9   9   9   9   9   9
                9   9   9   9   9   9   9   0   0   1   1   2   2   2   2   2   3   3
                .   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .
                0   0   0   0   0   1   1   0   0   0   1   0   0   0   0   0   0   0
                2   3   4   6   9   0   2   4   7   7   0   2   4   6   8   9   1   2

                           Months with Data (a Date with 1 death have been removed)
    /*_                   _
     (_)_ __  _ __  _   _| |_ ___
     | | `_ \| `_ \| | | | __/ __|
     | | | | | |_) | |_| | |_\__ \
     |_|_| |_| .__/ \__,_|\__|___/
             |_|
    */

    /*----                                                                   ----*/
    /*----  Template of days from 1989 to 1993 about  1,826 days             ----*/
    /*----                                                                   ----*/

    %let beg =01JAN1989;
    %let end =31DEC1993;

    libname sd1 "d:/sd1";

    data sd1.havAll(drop=days);
       length day 8 deaths 3 month $7;
       do days="&beg"d to "&end"d;
          day=input(put(days,yymmddn8.),8.);
          month=put(days,yymmd7.);
          deaths=0;
          output;
       end;
    run;quit;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*   SD1.HAVALL total obs=1,826                                                                                           */
    /*                                                                                                                        */
    /*   Obs       DAY      DEATHS     MONTH                                                                                  */
    /*                                                                                                                        */
    /*     1    19890101       0      1989-01                                                                                 */
    /*     2    19890102       0      1989-01                                                                                 */
    /*     3    19890103       0      1989-01                                                                                 */
    /*     4    19890104       0      1989-01                                                                                 */
    /*     5    19890105       0      1989-01                                                                                 */
    /*     6    19890106       0      1989-01                                                                                 */
    /*     7    19890107       0      1989-01                                                                                 */
    /*     8    19890108       0      1989-01                                                                                 */
    /*     9    19890109       0      1989-01                                                                                 */
    /*    10    19890110       0      1989-01                                                                                 */
    /*  ....                                                                                                                  */
    /*  1816    19931221       0      1993-12                                                                                 */
    /*  1817    19931222       0      1993-12                                                                                 */
    /*  1818    19931223       0      1993-12                                                                                 */
    /*  1819    19931224       0      1993-12                                                                                 */
    /*  1820    19931225       0      1993-12                                                                                 */
    /*  1821    19931226       0      1993-12                                                                                 */
    /*  1822    19931227       0      1993-12                                                                                 */
    /*  1823    19931228       0      1993-12                                                                                 */
    /*  1824    19931229       0      1993-12                                                                                 */
    /*  1825    19931230       0      1993-12                                                                                 */
    /*  1826    19931231       0      1993-12                                                                                 */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*----                                                                   ----*/
    /*----  Data from the stackoverflow post. Only the needed data.          ----*/
    /*----  Individual dates                                                 ----*/
    /*----  Since only 40 records have non-zero deaths, output is 40     obs ----*/
    /*----                                                                   ----*/


    filename ft15f001 clear;

    libname sd1 "d:/sd1";
    options validvarname=upcase;
    filename ft15f001 temp lrecl=88 recfm=f;
    data sd1.havPost ;
      length yyyymm $7;
      infile ft15f001 ;
      input (day deaths) (8. 3.) @@ ;
      strDte=put(day,8.);
      yyyymm=catx('-',substr(strDte,1,4),substr(strDte,5,2));
      if deaths ne 0;
      /*----                                                                 ----*/
      /*----  fix dups                                                       ----*/
      /*----                                                                 ----*/
      select;
        when (day=19890404 and deaths =  6) delete;
        when (day=19890404 and deaths =  4) deaths=10;
        when (day=19920601 and deaths =  2) delete;
        when (day=19920601 and deaths =  1) deaths=3;
        otherwise;
      end;
      if strip(scan(yyyymm,1,'-')) in ('1989','1990','1991','1992','1993')  ;
    parmcards4;
    2017073100020210826141202108280002021082901019890107000198901150001989012300019890130000
    1989013100019890204000198902080001989021000019890214005198902160071989021900019890221000
    1989022100019890221000198903080001989030800419890315000198904040061989040400419890405006
    1989040600019890415002198904190011989042000019890421002198904230021989042702019890516000
    1989053100019890601000198906010041989060300219890613001198906140001989062200219890623002
    1989081600119890822000198909050081989091100319890911000198909110001989091100019890911000
    1989092000019891027000198910270191989102800019891029000198910310001989122400419900401000
    1990040600319900711000199007130001990072000019900720002199010120001990102400019901106000
    1990110700019910317000199103260001991050700019910521000199105280001991070400019910717020
    1991081600019910816000199108160001991081700019911227000199202260021992022900019960928000
    1996092900019961005001199610050001996100800019961010000198907230001989120200019901002000
    1990100500019901010000199010100001990101800019901106000199011070001990112300019901127001
    1991021700019910420000199104220001991080100019910804000199110160001991101800319911018000
    1991102000019920418000199204210001992042200019920425000199204257001992042600019920426000
    1992042600019920428000199205040001992050400019920505000199205210001992052400019920601002
    1992060100119920623001199207020001992070400119920704000199208010011992080200019920804000
    1992080600019920808000199208090001992081000019920810000199208100001992081076619920810000
    1992081308019920815000199208190241992081900019920821000199208210001992082300019920823000
    1992082400019920828000199209010001992090100019920901000199209010001992091100619920912000
    1992100200019930102000199301020001993010200019930106000199301080031993011900019930119000
    1993011900019930119000199301190001993011900019930119000199301230001993012500019930126000
    1993012700019930127000199301300001993013000019930131000199302020001993020400019930204000
    1993020800019930212012199302120001993021800319930228062199304130001993041600019930418000
    1993050700019930512000199305120001993051200019930512000199305120001993051300019930516000
    1993051600019930518000199305190001993052100019930807000199308100001993081800019930822000
    ;;;;
    run;quit;


    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* sd1.havPost                                                                                                            */
    /*                                                                                                                        */
    /* Only dates with non-zero civilian deaths                                                                               */
    /*                                                                                                                        */
    /* Obs       DAY      DEATHS     DAY     DEATHS                                                                           */
    redo                                                                                                                      */
    /*                                                                                                                        */
    /*   1    19890214        5       23    1991-07    19910717       20     19910717                                         */
    /*   2    19890216        7       24    1992-02    19920226        2     19920226                                         */
    /*   3    19890308        4       25    1990-11    19901127        1     19901127                                         */
    /*   4    19890404       10       26    1991-10    19911018        3     19911018                                         */
    /*   5    19890405        6       27    1992-04    19920425      700     19920425                                         */
    /*   6    19890415        2       28    1992-06    19920601        3     19920601                                         */
    /*   7    19890419        1       29    1992-06    19920623        1     19920623                                         */
    /*   8    19890421        2       30    1992-07    19920704        1     19920704                                         */
    /*   9    19890423        2       31    1992-08    19920801        1     19920801                                         */
    /*  10    19890427       20       32    1992-08    19920810      766     19920810                                         */
    /*  11    19890601        4       33    1992-08    19920813       80     19920813                                         */
    /*  12    19890603        2       34    1992-08    19920819       24     19920819                                         */
    /*  13    19890613        1       35    1992-09    19920911        6     19920911                                         */
    /*  14    19890622        2       36    1993-01    19930108        3     19930108                                         */
    /*  15    19890623        2       37    1993-02    19930212       12     19930212                                         */
    /*  16    19890816        1       38    1993-02    19930218        3     19930218                                         */
    /*  17    19890905        8       39    1993-02    19930228       62     19930228                                         */
    /*  18    19890911        3                                                                                               */
    /*  19    19891027       19                                                                                               */
    /*  20    19891224        4                                                                                               */
    /*  21    19900406        3                                                                                               */
    /*  22    19900720        2                                                                                               */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*                                  _
    / | __      ___ __  ___   ___  __ _| |
    | | \ \ /\ / / `_ \/ __| / __|/ _` | |
    | |  \ V  V /| |_) \__ \ \__ \ (_| | |
    |_|   \_/\_/ | .__/|___/ |___/\__, |_|
                 |_|                 |_|
    */

    /*----                                                                   ----*/
    /*---- Although it is not necessary to call SQL twice I wanted           ----*/
    /*---- to show how to save and restore dataframes.                       ----*/
    /*----                                                                   ----*/

    proc datasets lib=sd1 nolist mt=data mt=view nodetails;delete want; run;quit;

    %utl_submit_wps64x('
    libname sd1 "d:/sd1";
    options validvarname=any;
    options missing="0";
    proc sql;
      create
        table sd1.want as
      select
        l.month
       ,sum(r.deaths)  as deaths
      from
        sd1.havall as l left join sd1.havPost as r
      on
        l.day = r.day
      group
        by l.month
    ;quit;
    proc print;
    run;quit;
    ');

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*           sd1.want obs=I349                                                                                            */
    /*                                                                                                                        */
    /*           Obs MONTH  DEATHS       Obs MONTH  DEATHS                                                                    */
    /*                                                                                                                        */
    /*            1 1989-01     0         31 1991-07    20                                                                    */
    /*            2 1989-02    12         32 1991-08     0                                                                    */
    /*            3 1989-03     4         33 1991-09     0                                                                    */
    /*            4 1989-04    43         34 1991-10     3                                                                    */
    /*            5 1989-05     0         35 1991-11     0                                                                    */
    /*            6 1989-06    11         36 1991-12     0                                                                    */
    /*            7 1989-07     0         37 1992-01     0                                                                    */
    /*            8 1989-08     1         38 1992-02     2                                                                    */
    /*            9 1989-09    11         39 1992-03     0                                                                    */
    /*           10 1989-10    19         40 1992-04   700                                                                    */
    /*           11 1989-11     0         41 1992-05     0                                                                    */
    /*           12 1989-12     4         42 1992-06     4                                                                    */
    /*           13 1990-01     0         43 1992-07     1                                                                    */
    /*           14 1990-02     0         44 1992-08   871                                                                    */
    /*           15 1990-03     0         45 1992-09     6                                                                    */
    /*           16 1990-04     3         46 1992-10     0                                                                    */
    /*           17 1990-05     0         47 1992-11     0                                                                    */
    /*           18 1990-06     0         48 1992-12     0                                                                    */
    /*           19 1990-07     2         49 1993-01     3                                                                    */
    /*           20 1990-08     0         50 1993-02    77                                                                    */
    /*           21 1990-09     0         51 1993-03     0                                                                    */
    /*           22 1990-10     0         52 1993-04     0                                                                    */
    /*           23 1990-11     1         53 1993-05     0                                                                    */
    /*           24 1990-12     0         54 1993-06     0                                                                    */
    /*           25 1991-01     0         55 1993-07     0                                                                    */
    /*           26 1991-02     0         56 1993-08     0                                                                    */
    /*           27 1991-03     0         57 1993-09     0                                                                    */
    /*           28 1991-04     0         58 1993-10     0                                                                    */
    /*           29 1991-05     0         59 1993-11     0                                                                    */
    /*           30 1991-06     0         60 1993-12     0                                                                    */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*___                                          _
    |___ \  __      ___ __  ___   _ __   ___  __ _| |
      __) | \ \ /\ / / `_ \/ __| | `__| / __|/ _` | |
     / __/   \ V  V /| |_) \__ \ | |    \__ \ (_| | |
    |_____|   \_/\_/ | .__/|___/ |_|    |___/\__, |_|
                     |_|                        |_|
    */

    proc datasets lib=sd1 nolist mt=data mt=view nodetails;delete want; run;quit;

    %utl_submit_wps64x('
    libname sd1 "d:/sd1";
    options validvarname=any;
    proc r;
    export data=sd1.havall  r=havall;
    export data=sd1.havpost r=havpost;
    submit;
    library(sqldf);
    want <- sqldf("
      select
        l.month
       ,sum(r.deaths)  as DEATHS
      from
        havall as l left join havpost as r
      on
        l.day = r.day
      group
        by l.month
    ");
    want;
    endsubmit;
    import data=sd1.want r=want;
    options missing="0";
    proc print data=sd1.want;
    run;quit;
    ');


    /*___                                          _
    |___ \  __      ___ __  ___   _ __   ___  __ _| |
      __) | \ \ /\ / / `_ \/ __| | `__| / __|/ _` | |
     / __/   \ V  V /| |_) \__ \ | |    \__ \ (_| | |
    |_____|   \_/\_/ | .__/|___/ |_|    |___/\__, |_|
                     |_|                        |_|
    */

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*           sd1.want obs=I349                                                                                            */
    /*                                                                                                                        */
    /*           Obs MONTH  DEATHS       Obs MONTH  DEATHS                                                                    */
    /*                                                                                                                        */
    /*            1 1989-01     0         31 1991-07    20                                                                    */
    /*            2 1989-02    12         32 1991-08     0                                                                    */
    /*            3 1989-03     4         33 1991-09     0                                                                    */
    /*            4 1989-04    43         34 1991-10     3                                                                    */
    /*            5 1989-05     0         35 1991-11     0                                                                    */
    /*            6 1989-06    11         36 1991-12     0                                                                    */
    /*            7 1989-07     0         37 1992-01     0                                                                    */
    /*            8 1989-08     1         38 1992-02     2                                                                    */
    /*            9 1989-09    11         39 1992-03     0                                                                    */
    /*           10 1989-10    19         40 1992-04   700                                                                    */
    /*           11 1989-11     0         41 1992-05     0                                                                    */
    /*           12 1989-12     4         42 1992-06     4                                                                    */
    /*           13 1990-01     0         43 1992-07     1                                                                    */
    /*           14 1990-02     0         44 1992-08   871                                                                    */
    /*           15 1990-03     0         45 1992-09     6                                                                    */
    /*           16 1990-04     3         46 1992-10     0                                                                    */
    /*           17 1990-05     0         47 1992-11     0                                                                    */
    /*           18 1990-06     0         48 1992-12     0                                                                    */
    /*           19 1990-07     2         49 1993-01     3                                                                    */
    /*           20 1990-08     0         50 1993-02    77                                                                    */
    /*           21 1990-09     0         51 1993-03     0                                                                    */
    /*           22 1990-10     0         52 1993-04     0                                                                    */
    /*           23 1990-11     1         53 1993-05     0                                                                    */
    /*           24 1990-12     0         54 1993-06     0                                                                    */
    /*           25 1991-01     0         55 1993-07     0                                                                    */
    /*           26 1991-02     0         56 1993-08     0                                                                    */
    /*           27 1991-03     0         57 1993-09     0                                                                    */
    /*           28 1991-04     0         58 1993-10     0                                                                    */
    /*           29 1991-05     0         59 1993-11     0                                                                    */
    /*           30 1991-06     0         60 1993-12     0                                                                    */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*____                                    _   _                             _
    |___ /  __      ___ __  ___   _ __  _   _| |_| |__   ___  _ __    ___  __ _| |
      |_ \  \ \ /\ / / `_ \/ __| | `_ \| | | | __| `_ \ / _ \| `_ \  / __|/ _` | |
     ___) |  \ V  V /| |_) \__ \ | |_) | |_| | |_| | | | (_) | | | | \__ \ (_| | |
    |____/    \_/\_/ | .__/|___/ | .__/ \__, |\__|_| |_|\___/|_| |_| |___/\__, |_|
                     |_|         |_|    |___/                                |_|
    */

    %utlfkil(d:/xpt/want.xpt);

    /*----                                                                   ----*/
    /*----  elimiate issues with datastep and view with the same name        ----*/
    /*----                                                                   ----*/

    proc datasets lib=sd1 nolist mt=data mt=view nodetails;delete want; run;quit;
    proc datasets lib=work nolist mt=data mt=view nodetails;delete want; run;quit;

    %utl_submit_wps64x("
    options validvarname=any lrecl=32756;
    libname sd1 'd:/sd1';
    proc python;
    export data=sd1.havall  python=havall;
    export data=sd1.havpost python=havpost;
    submit;
    import pyreadstat as ps;
    from os import path;
    import pandas as pd;
    import numpy as np;
    from pandasql import sqldf;
    mysql = lambda q: sqldf(q, globals());
    from pandasql import PandaSQL;
    pdsql = PandaSQL(persist=True);
    sqlite3conn = next(pdsql.conn.gen).connection.connection;
    sqlite3conn.enable_load_extension(True);
    sqlite3conn.load_extension('c:/temp/libsqlitefunctions.dll');
    mysql = lambda q: sqldf(q, globals());
    want = pdsql('''
      select
        l.month
       ,sum(r.deaths)  as DEATHS
      from
        havall as l left join havpost as r
      on
        l.day = r.day
      group
        by l.month
    ''');
    print(want);
    ps.write_xport(want,'d:\\xpt\\want.xpt',table_name='want',file_format_version=5
    ,column_labels=['MONTHS','DEATHS']);
    endsubmit;
    ");

    /*--- handles long variable names by using the label to rename the variables  ----*/

    libname xpt xport "d:/xpt/want.xpt";
    proc contents data=xpt._all_;
    run;quit;

    data want_py_long_names;
      %utl_rens(xpt.want) ;
      set want;
    run;quit;
    libname xpt clear;

    proc print data=want_py_long_names;
    run;quit;

    /**************************************************************************************************************************/
    /*                                                        |                                                               */
    /*  The WPS PYTHON Procedure                              |    WPS                                                        */
    /*                                                        |                                                               */
    /*        MONTH  DEATHS               MONTH  DEATHS       |   Obs MONTH  DEATHS       Obs MONTH  DEATHS                   */
    /*                                                        |                                                               */
    /*  0   1989-01     NaN          31  1991-08     NaN      |    1 1989-01     0         31 1991-07    20                   */
    /*  1   1989-02    12.0          32  1991-09     NaN      |    2 1989-02    12         32 1991-08     0                   */
    /*  2   1989-03     4.0          33  1991-10     3.0      |    3 1989-03     4         33 1991-09     0                   */
    /*  3   1989-04    43.0          34  1991-11     NaN      |    4 1989-04    43         34 1991-10     3                   */
    /*  4   1989-05     NaN          35  1991-12     NaN      |    5 1989-05     0         35 1991-11     0                   */
    /*  5   1989-06    11.0          36  1992-01     NaN      |    6 1989-06    11         36 1991-12     0                   */
    /*  6   1989-07     NaN          37  1992-02     2.0      |    7 1989-07     0         37 1992-01     0                   */
    /*  7   1989-08     1.0          38  1992-03     NaN      |    8 1989-08     1         38 1992-02     2                   */
    /*  8   1989-09    11.0          39  1992-04   700.0      |    9 1989-09    11         39 1992-03     0                   */
    /*  9   1989-10    19.0          40  1992-05     NaN      |   10 1989-10    19         40 1992-04   700                   */
    /*  10  1989-11     NaN          41  1992-06     4.0      |   11 1989-11     0         41 1992-05     0                   */
    /*  11  1989-12     4.0          42  1992-07     1.0      |   12 1989-12     4         42 1992-06     4                   */
    /*  12  1990-01     NaN          43  1992-08   871.0      |   13 1990-01     0         43 1992-07     1                   */
    /*  13  1990-02     NaN          44  1992-09     6.0      |   14 1990-02     0         44 1992-08   871                   */
    /*  14  1990-03     NaN          45  1992-10     NaN      |   15 1990-03     0         45 1992-09     6                   */
    /*  15  1990-04     3.0          46  1992-11     NaN      |   16 1990-04     3         46 1992-10     0                   */
    /*  16  1990-05     NaN          47  1992-12     NaN      |   17 1990-05     0         47 1992-11     0                   */
    /*  17  1990-06     NaN          48  1993-01     3.0      |   18 1990-06     0         48 1992-12     0                   */
    /*  18  1990-07     2.0          49  1993-02    77.0      |   19 1990-07     2         49 1993-01     3                   */
    /*  19  1990-08     NaN          50  1993-03     NaN      |   20 1990-08     0         50 1993-02    77                   */
    /*  20  1990-09     NaN          51  1993-04     NaN      |   21 1990-09     0         51 1993-03     0                   */
    /*  21  1990-10     NaN          52  1993-05     NaN      |   22 1990-10     0         52 1993-04     0                   */
    /*  22  1990-11     1.0          53  1993-06     NaN      |   23 1990-11     1         53 1993-05     0                   */
    /*  23  1990-12     NaN          54  1993-07     NaN      |   24 1990-12     0         54 1993-06     0                   */
    /*  24  1991-01     NaN          55  1993-08     NaN      |   25 1991-01     0         55 1993-07     0                   */
    /*  25  1991-02     NaN          56  1993-09     NaN      |   26 1991-02     0         56 1993-08     0                   */
    /*  26  1991-03     NaN          57  1993-10     NaN      |   27 1991-03     0         57 1993-09     0                   */
    /*  27  1991-04     NaN          58  1993-11     NaN      |   28 1991-04     0         58 1993-10     0                   */
    /*  28  1991-05     NaN          59  1993-12     NaN      |   29 1991-05     0         59 1993-11     0                   */
    /*  29  1991-06     NaN                                   |   30 1991-06     0         60 1993-12     0                   */
    /*  30  1991-07    20.0                                   |                                                               */
    /*                                                        |                                                               */
    /**************************************************************************************************************************/


    /*  _     _ _                    _       _
    | || |   | (_)_ __   ___   _ __ | | ___ | |_
    | || |_  | | | `_ \ / _ \ | `_ \| |/ _ \| __|
    |__   _| | | | | | |  __/ | |_) | | (_) | |_
       |_|   |_|_|_| |_|\___| | .__/|_|\___/ \__|
                              |_|
    */

    /*----                                                                   ----*/
    /*---- requires sophisticated manual editing - best in classic editor?   ----*/
    /*----                                                                   ----*/

    options ls=84 ps=54;
    proc plot  data=sd1.want (where=(deaths gt 0));
     plot deaths*month='*' $ deaths /box vaxis= 1 10 100 1000;
    run;quit;

    NOTES

    Edit this plot by hand

    Up to 40 obs from SD1.WANT total obs=60 10MAY2022:09:54:14

                     Plot of deaths*MONTH$deaths.  Symbol used is '*'.

                ---+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+---
           1000 +                                                                 +
                |                                                     * 871       |
                |                                            * 700                |
                |                                                                 |
                |                                                                 |
                |                                                                 |
                |                                                                 |
                |                                                                 |
                |                                                                 |
                |                                                                 |
                |                                                                 |
                |                                                                 |
            100 +                                                                 +
                |                                                           77 *  |
                |                                                                 |
                |                                                                 |
                |        * 43                                                     |
                |                                                                 |
         deaths |                                                                 |
                |                                                                 |
                |                                   * 20                          |
                |                    * 19                                         |
                |                                                                 |
                |  * 12                                                           |
             10 +           * 11  * 11                                            +
                |                                                                 |
                |                                                                 |
                |                                                        * 6      |
                |                                                                 |
                |     * 4               * 4                     * 4               |
                |                          * 3         * 3                  * 3   |
                |                                                                 |
                |                             * 2         * 2                     |
                |                                                                 |
                |                                                                 |
                |                                                                 |
              1 +              * 1               * 1               * 1            +
                ---+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+---
                   1  1  1  1  1  1  1  1  1  1  1  1  1  1  1  1  1  1  1  1  1
                   9  9  9  9  9  9  9  9  9  9  9  9  9  9  9  9  9  9  9  9  9
                   8  8  8  8  8  8  8  8  9  9  9  9  9  9  9  9  9  9  9  9  9
                   9  9  9  9  9  9  9  9  0  0  0  1  1  2  2  2  2  2  2  3  3
                   -  -  -  -  -  -  -  -  -  -  -  -  -  -  -  -  -  -  -  -  -
                   0  0  0  0  0  0  1  1  0  0  1  0  1  0  0  0  0  0  0  0  0
                   2  3  4  6  8  9  0  2  4  7  1  7  0  2  4  6  7  8  9  1  2

                                               MONTH
    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
