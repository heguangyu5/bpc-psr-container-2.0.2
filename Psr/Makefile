FILES = ContainerExceptionInterface.php \
        ContainerInterface.php          \
        NotFoundExceptionInterface.php

BPCPHP_FILES = $(patsubst %,Container/%,$(FILES))

libpsr-container.so:
	rm -rf Container
	mkdir Container
	for i in $(FILES); do phptobpc ../src/$$i > Container/$$i; done
	bpc -v \
		-c bpc.conf  \
		-l psr-container \
		placeholder-container.php \
		$(BPCPHP_FILES)

install-libpsr-container:
	bpc -l psr-container --install
