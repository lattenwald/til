# hledger

Group posting by month starting from 10th day

    % hledger -f f.ledger reg status:* Salary -r -p "every 10th day of month" -w 80 --anon
    2016/01/15-2016/02/14   5143399d:c308cd88              XXXXX.00руб  XXXXXX.00руб
    2016/02/15-2016/03/14   5143399d:c308cd88              XXXXX.13руб  XXXXXX.13руб
    2016/03/15-2016/04/14   5143399d:c308cd88              XXXXX.43руб  XXXXXX.56руб
    2016/04/15-2016/05/14   5143399d:c308cd88              XXXXX.21руб  XXXXXX.77руб
    2016/05/15-2016/06/14   5143399d:c308cd88              XXXXX.63руб  XXXXXX.40руб
    2016/06/15-2016/07/14   5143399d:c308cd88              XXXXX.14руб  XXXXXX.54руб
    2016/07/15-2016/08/14   5143399d:c308cd88              XXXXX.00руб  XXXXXX.54руб

Balance changes for all accounts by month starting from 10th day with row totals

    % hledger -f f.ledger bal -p "every 10th day of month from 2016/05/09" --depth 2 --row-total | less -S
                       ||           2016/05/10-2016/06/09  2016/06/10-2016/07/09  2016/07/10-2016/08/09
    ===================++==============================================================================
     18a2e035:2909fdfe ||                     -4038.44руб            -2210.02руб            -2296.79руб
     18a2e035:2c7cfcfa ||                               0                      0            -1801.00руб
     18a2e035:30a4ff40 ||                               0                      0                      0
     18a2e035:87823730 ||                   -170384.39руб           -80786.14руб          -130500.00руб
     94ad568d:90e4f8be ||                               0                      0                      0
     94ad568d:96c82cee ||                      1288.00руб             2248.00руб             2116.00руб
     94ad568d:9e3d1427 ||                       794.18руб             1147.77руб             1871.01руб
     94ad568d:b770cc81 ||                               0              327.59руб                      0
     94ad568d:c0e5714c ||                     14471.53руб             1260.00руб                      0
     94ad568d:cc6a0707 ||                               0                      0                      0
     94ad568d:e7cf5e10 ||                     11450.91руб  37.68USD, 12294.82руб  15.03USD, 10518.54руб
     94ad568d:e87a6fd  ||                       981.79руб                      0                      0
     94ad568d:f6484134 ||                      6251.62руб             6100.31руб             6077.01руб
    -------------------++------------------------------------------------------------------------------
                       || 6000EUR, 2000USD, -570828.00руб  37.68USD, -2500.74руб  15.03USD, -1004.93руб
