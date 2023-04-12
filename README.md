# utl-which-is-the-best-syntax-for-SAS-WPS-arrays
Which is the best syntax for SAS/WPS arrays 
    %let pgm=utl-which-is-the-best-syntax-for-SAS-WPS-arrays;

    Which is the best syntax for SAS/WPS arrays

    I prefer solid brackets?
    I also prefer !! to ||?

    If I remember corectly the original and most prevalent syntax for arrays uses brackets [] not parens or
    squigly brackets.

    I think this was determined in when SAs was only available on IBM mainframes?

    I think brackets work on all platforms but the other forms may not?

    github
    https://tinyurl.com/389ebsky
    https://github.com/rogerjdeangelis/utl-which-is-the-best-syntax-for-SAS-WPS-arrays


    /*     _ _                      _      _                  _       _  ___
      __ _| | | __      _____  _ __| | __ (_)_ __   __      _(_)_ __ / |/ _ \
     / _` | | | \ \ /\ / / _ \| `__| |/ / | | `_ \  \ \ /\ / / | `_ \| | | | |
    | (_| | | |  \ V  V / (_) | |  |   <  | | | | |  \ V  V /| | | | | | |_| |
     \__,_|_|_|   \_/\_/ \___/|_|  |_|\_\ |_|_| |_|   \_/\_/ |_|_| |_|_|\___/

    */

    data arySyn;

      array tmpa (0:12) $ _temporary_;
      array tmpb [0:12] $ _temporary_;
      array tmpc {0:12} $ _temporary_;

      tmpa[1]='a' ;
      tmpb[1]='b' ;
      tmpc[1]='c' ;

      a=tmpa[1];
      b=tmpb[1];
      c=tmpc[1];

    run;quit;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* [] () {} all work                                                                                                      */
    /*                                                                                                                        */
    /* Up to 40 obs from last table WORK.ARYSYN total obs=1 12APR2023:08:42:27                                                */
    /*                                                                                                                        */
    /* Obs    A    B    C                                                                                                     */
    /*                                                                                                                        */
    /*  1     a    b    c                                                                                                     */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*     _             _
      __ _| |___  ___   (_)_ __   __      ___ __  ___
     / _` | / __|/ _ \  | | `_ \  \ \ /\ / / `_ \/ __|
    | (_| | \__ \ (_) | | | | | |  \ V  V /| |_) \__ \
     \__,_|_|___/\___/  |_|_| |_|   \_/\_/ | .__/|___/
                                           |_|
    */

    %utl_submit_wps64('
    data did_not_know;

      array tmpa (0:12) $ _temporary_;
      array tmpb [0:12] $ _temporary_;
      array tmpc {0:12} $ _temporary_;

      tmpa[1]="a" ;
      tmpb[1]="b" ;
      tmpc[1]="c" ;

      a=tmpa[1];
      b=tmpb[1];
      c=tmpc[1];

    run;quit;

    proc print;
    run;quit;

    ');

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* The WPS System                                                                                                         */
    /*                                                                                                                        */
    /* Obs    A    B    C                                                                                                     */
    /*                                                                                                                        */
    /*  1     a    b    c                                                                                                     */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
