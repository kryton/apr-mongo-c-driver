APR_CFLAGS=`apr-1-config --includes --cppflags --cflags`
APR_LIBS=`apr-1-config --link-libtool --libs --ldflags`

all: libmongo.la

libmongo.la: bson.lo md5.lo mongo.lo numbers.lo 
	libtool --mode=link gcc -o $@  ${APR_LIBS}   -rpath /usr/local/lib -module -avoid-version bson.lo md5.lo mongo.lo numbers.lo

#utils.lo numbers.lo mongo.lo md5.lo bson.lo mod_optin.lo

#
#	apxs -c -n mod_optin mod_optin.c bson.c md5.c mongo.c numbers.c utils.c


clean:
	rm -f *.o *.slo *.lo *.la
	rm -rf .libs


%.lo: %.c bson.h mongo.h  
	libtool --silent --mode=compile gcc -prefer-pic  ${APR_CFLAGS}  -no-cpp-precomp -g -O2 -c -o $@ $<  

#	gcc -g -prefer-pic   -DDARWIN -DSIGPROCMASK_SETS_THREAD_MASK -no-cpp-precomp  -c $< -o $@ ${APR_CFLAGS} 
#x.o: x.c
#	gcc -g -c x.c  ${APR_CFLAGS} 
