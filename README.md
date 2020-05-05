# tinyhttpd

This software is released over 20 years ago, but now, I am going to make it work on my machine, so here is the problems I found:

I am using WSL in Windows 1909, my Linux environment is Ubuntu 18.04.

1. /usr/bin/ld: cannot find -lsocket 

change Makefile, delete it

2. In file included from httpd.c:25:0:
/usr/include/pthread.h:234:12: note: expected ‘void * restrict’ but argument is of type ‘int’
 extern int pthread_create (pthread_t *__restrict __newthread,
            ^~~~~~~~~~~~~~
/tmp/ccJbLhAF.o: In function `main':
httpd.c:(.text+0x1a46): undefined reference to `pthread_create'

change Makefile, put -lpthread in the end of the line

----------------------------------------------------------------------------

  This software is copyright 1999 by J. David Blackstone.  Permission
is granted to redistribute and modify this software under the terms of
the GNU General Public License, available at http://www.gnu.org/ .

  If you use this software or examine the code, I would appreciate
knowing and would be overjoyed to hear about it at
jdavidb@sourceforge.net .

  This software is not production quality.  It comes with no warranty
of any kind, not even an implied warranty of fitness for a particular
purpose.  I am not responsible for the damage that will likely result
if you use this software on your computer system.

  I wrote this webserver for an assignment in my networking class in
1999.  We were told that at a bare minimum the server had to serve
pages, and told that we would get extra credit for doing "extras."
Perl had introduced me to a whole lot of UNIX functionality (I learned
sockets and fork from Perl!), and O'Reilly's lion book on UNIX system
calls plus O'Reilly's books on CGI and writing web clients in Perl got
me thinking and I realized I could make my webserver support CGI with
little trouble.

  Now, if you're a member of the Apache core group, you might not be
impressed.  But my professor was blown over.  Try the color.cgi sample
script and type in "chartreuse."  Made me seem smarter than I am, at
any rate. :)

  Apache it's not.  But I do hope that this program is a good
educational tool for those interested in http/socket programming, as
well as UNIX system calls.  (There's some textbook uses of pipes,
environment variables, forks, and so on.)

  One last thing: if you look at my webserver or (are you out of
mind?!?) use it, I would just be overjoyed to hear about it.  Please
email me.  I probably won't really be releasing major updates, but if
I help you learn something, I'd love to know!

  Happy hacking!

                                   J. David Blackstone
