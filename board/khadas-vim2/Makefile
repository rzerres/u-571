
.PHONY: all clean install

all: bundle.uEnv

clean:
	rm -f bundle.uEnv

bundle.uEnv: board_init.env
	cat $< | tr -s '\t' | tr '\t' '=' > $@
	(cd ../../macro; make macro.ext4.uEnv)
	cat ../../macro/macro.ext4.uEnv >> $@
	(cd ../../macro; make clean)

install:
	cat *.env | sudo fw_setenv -s -
	(cd ../../macro; make install.ext4; make clean)
