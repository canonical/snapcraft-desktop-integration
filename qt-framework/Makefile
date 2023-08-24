#!/usr/bin/make -f

SRC_DIR ?= .

PLATFORM_DIR         := $(DESTDIR)/qt-framework
DATA_DIR             := $(DESTDIR)/data-dir
BIN_DIR              := $(DESTDIR)/command-chain
LIB_DIR              := $(DESTDIR)/lib
DEST_LAUNCHER        := desktop-launch
DEST_CONFIGURE_HOOK  := hooks-configure-fonts

build: $(DEST_LAUNCHER) $(DEST_CONFIGURE_HOOK)

clean:
	rm -f $(DEST_LAUNCHER)
	rm -f $(DEST_CONFIGURE_HOOK)

$(DEST_LAUNCHER):
	@cat $(SRC_DIR)/init >> $(DEST_LAUNCHER)
  # tail -n +2 to remove the shebang
	@tail -n +2 $(SRC_DIR)/desktop-exports | sed -e "s/%PLATFORM_PLUG%/$${PLATFORM_PLUG:?}/" >> $(DEST_LAUNCHER)
	@tail -n +2 $(SRC_DIR)/launcher-specific >> $(DEST_LAUNCHER)
	@tail -n +2 $(SRC_DIR)/mark-and-exec >> $(DEST_LAUNCHER)

$(DEST_CONFIGURE_HOOK):
	@cat $(SRC_DIR)/fonts > $(DEST_CONFIGURE_HOOK)

install-$(DEST_LAUNCHER): $(DEST_LAUNCHER)
	install -d $(PLATFORM_DIR)
	install -d $(DATA_DIR)
	install -D -m755 $(DEST_LAUNCHER) "$(BIN_DIR)"/$(DEST_LAUNCHER)

install-$(DEST_CONFIGURE_HOOK): $(DEST_CONFIGURE_HOOK)
	install -D -m755 $(DEST_CONFIGURE_HOOK) "$(BIN_DIR)"/$(DEST_CONFIGURE_HOOK)

install: install-$(DEST_LAUNCHER) install-$(DEST_CONFIGURE_HOOK)
