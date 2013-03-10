# Makefile for lua libs used by jivelite
# NB - repo has modified paths which assume use of luajit2.0 from source

LIBS = cjson luaexpat luafilesystem luamd5 luasocket

all: $(LIBS)

cjson: ../lib/lua/5.1/cjson.so
luaexpat: ../lib/lua/5.1/lxp.so
luafilesystem: ../lib/lua/5.1/lfs.so
luamd5: ../lib/lua/5.1/md5.so
luasocket: ../lib/lua/5.1/socket.so

../lib/lua/5.1/cjson.so:
	cd lua-cjson-2.1.0; make
	mkdir -p ../lib/lua/5.1
	cp lua-cjson-2.1.0/cjson.so ../lib/lua/5.1/cjson.so

../lib/lua/5.1/lxp.so:
	cd luaexpat-1.2.0; make
	mkdir -p ../lib/lua/5.1
	cp luaexpat-1.2.0/src/lxp.so.1.2.0 ../lib/lua/5.1/lxp.so

../lib/lua/5.1/lfs.so:
	cd luafilesystem-1.6.2; make
	mkdir -p ../lib/lua/5.1
	cp luafilesystem-1.6.2/src/lfs.so ../lib/lua/5.1/lfs.so

../lib/lua/5.1/md5.so:
	cd luamd5; make MYNAME=sha1
	cd luamd5; make MYNAME=md5
	mkdir -p ../lib/lua/5.1
	cp luamd5/md5.so ../lib/lua/5.1/md5.so
	cp luamd5/sha1.so ../lib/lua/5.1/sha1.so

../lib/lua/5.1/socket.so:
	cd luasocket-2.0.2; make LD="gcc -shared" PLATFORM=linux
	mkdir -p ../lib/lua/5.1
	cp luasocket-2.0.2/src/socket.so.2.0.2 ../lib/lua/5.1/socket.so
	cp luasocket-2.0.2/src/mime.so.1.0.2 ../lib/lua/5.1/mime.so

clean:
	cd lua-cjson-2.1.0; make clean
	cd luaexpat-1.2.0; make clean
	cd luafilesystem-1.6.2; make clean
	cd luamd5; make MYNAME=sha1 clean
	cd luamd5; make MYNAME=md5 clean
	cd luasocket-2.0.2; make PLATFORM=linux clean
	rm ../lib/lua/5.1/cjson.so ../lib/lua/5.1/lxp.so ../lib/lua/5.1/lfs.so ../lib/lua/5.1/socket.so ../lib/lua/5.1/mime.so
