# ruby-space-weather

The goal of this project is to parse the data file contained at:

  ftp://ftp.swpc.noaa.gov/pub/lists/ace/ace_swepam_1m.txt

There is a copy of this file saved as solar_data.txt

This file contains 1-minute measurements of solar wind data from the ACE satellite, and looks like this:

    :Data_list: ace_swepam_1m.txt
    :Created: 2015 Jan 07 1548 UT
    # Units: Proton density p/cc
    # Units: Bulk speed km/s
    # Units: Ion tempeture degrees K
    # Status(S): 0 = nominal data, 1 to 8 = bad data record, 9 = no data
    # Missing data values: Density and Speed = -9999.9, Temp. = -1.00e+05
    # Source: ACE Satellite - Solar Wind Electron Proton Alpha Monitor
    #
    #   1-minute averaged Real-time Bulk Parameters of the Solar Wind Plasma
    # 
    #                Modified Seconds   -------------  Solar Wind  -----------
    # UT Date   Time  Julian  of the          Proton      Bulk         Ion
    # YR MO DA  HHMM    Day     Day     S    Density     Speed     Temperature
    2015 01 07  1348   57029   49680    0        6.8      414.6     2.09e+04
    2015 01 07  1409   57029   50940    0        9.7      419.2     2.81e+04
    2015 01 07  1410   57029   51000    0        1.6      401.1     1.03e+04
    2015 01 07  1411   57029   51060    1        8.6      422.2     2.23e+04
    2015 01 07  1412   57029   51120    1        8.1      420.7     2.17e+04


# Notes/tasks

  * Come up with a general design of classes to parse & eventually store this data
  * Design a SQL table to store this data.

  * Write some ruby code to parse the text file:
    * Commented lines begin with either : or #
    * Keep track of the following data:
      * Observation date/time (dd/mm/yyyy hh:mm - seconds & julian day can be skipped)
      * Whether the record is "nominal", or has missing data (see comments in file)
      * Proton density
      * Bulk speed
      * Ion Temperature is not important, so skip it
    * Bonus points for writing tests!
