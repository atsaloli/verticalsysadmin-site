---
title: "Graphing within psql"
date: 2016-08-14
---

I mentioned this [on HN](https://news.ycombinator.com/item?id=5215040) years ago but it's nifty so add it here.

You can graph SQL output with [gnuplot](http://www.gnuplot.info/) without leaving the [psql](http://postgresguide.com/utilities/psql.html) (Postgres client) command-line.

Because @fusiongyro commented "This is incredible! I only wish it were a little easier to do on the fly," I inquired on the amazingly helpful [pgsql-general](https://www.postgresql.org/list/pgsql-general/) list.

There are two approaches: client-side and server-side.

- Ian Barwick [explained](https://www.postgresql.org/message-id/CAB8KJ=j5J8w22=SY1FgRWgkREizYEjAOsK5j+K20iS49+gS5_Q@mail.gmail.com) how to put all the prep stuff into a psql script, define your query and invoke the script.
    
    ```
    
    barwick@localhost:~$ psql -U postgres testdb
      psql (9.2.3)
      Type "help" for help.
    
      testdb=# set plot_query 'SELECT * FROM plot'
      testdb=# i tmp/plot.psql
    
    
                                        My Graph
    
        4 ++---------+-----------+----------+----------+-----------+---------**
          +          +           +          +          +           +     **** +
          |                                                          ****     |
      3.5 ++                                                     ****        ++
          |                                                  ****             |
          |                                              ****                 |
        3 ++                                         ****                    ++
          |                                      ****                         |
      2.5 ++                                *****                            ++
          |                             ****                                  |
          |                         ****                                      |
        2 ++                    ****                                         ++
          |                 ****                                              |
          |             ****                                                  |
      1.5 ++        ****                                                     ++
          |     ****                                                          |
          + ****     +           +          +          +           +          +
        1 **---------+-----------+----------+----------+-----------+---------++
          1         1.5          2         2.5         3          3.5         4
                                         Servers
    
      testdb=#
    ```
    
- [Sergey Konoplev explained](https://www.postgresql.org/message-id/CAL_0b1t9D4K5iATcmAxUAaL_6L_BF3Ccik%2BRCzDMqK_oE8DQ-w%40mail.gmail.com) how to do it with a server-side function - you need gnuplot installed on the db server and then you can use
    

`select just_for_fun_graph('select ... from ...', 'My Graph', 78, 24, ...)`
