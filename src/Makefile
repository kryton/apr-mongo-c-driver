VERSION=0:1
APR_CFLAGS=`apr-1-config --includes --cppflags --cflags`
APR_LIBS=`apr-1-config --link-libtool --libs --ldflags`
INSTALLDIR=/usr/local/apache2/modules
LIBTOOL=/usr/local/apache2/build/libtool
#INSTDSO=/usr/local/apache2/build/instdso.sh

all: libmongo.la

libmongo.la: bson.lo md5.lo mongo.lo numbers.lo 
	libtool --silent --mode=link gcc -o $@  ${APR_LIBS}    -version-info ${VERSION}  -rpath ${INSTALLDIR} bson.lo md5.lo mongo.lo numbers.lo

clean:
	rm -f *.o *.slo *.lo *.la
	rm -rf .libs

install: libmongo.la
	libtool --silent --mode=install cp $<  ${INSTALLDIR}

#	${INSTDSO} SH_LIBTOOL=${LIBTOOL}  $< ${INSTALLDIR}

%.lo: %.c bson.h mongo.h  
	libtool --silent --mode=compile gcc -prefer-pic  ${APR_CFLAGS}  -no-cpp-precomp -g -O2 -c -o $@ $<  


#x.o: x.c
#	gcc -g -c x.c  ${APR_CFLAGS} 
