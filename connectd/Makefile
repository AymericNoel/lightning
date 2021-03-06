#! /usr/bin/make

CONNECTD_HEADERS := connectd/connectd_wiregen.h		\
	connectd/connectd_gossipd_wiregen.h		\
	connectd/connectd.h				\
	connectd/peer_exchange_initmsg.h		\
	connectd/handshake.h				\
	connectd/netaddress.h				\
	connectd/tor_autoservice.h			\
	connectd/tor.h

CONNECTD_SRC := $(CONNECTD_HEADERS:.h=.c) connectd/connectd.c

CONNECTD_OBJS := $(CONNECTD_SRC:.c=.o)
$(CONNECTD_OBJS): $(CONNECTD_HEADERS)

# Make sure these depend on everything.
ALL_C_SOURCES += $(CONNECTD_SRC)
ALL_C_HEADERS += $(CONNECTD_HEADERS)
ALL_PROGRAMS += lightningd/lightning_connectd

# Here's what lightningd depends on
LIGHTNINGD_CONTROL_HEADERS += connectd/connectd_wiregen.h
LIGHTNINGD_CONTROL_OBJS += connectd/connectd_wiregen.o

# Common source we use.
CONNECTD_COMMON_OBJS :=				\
	common/amount.o				\
	common/base32.o				\
	common/base64.o				\
	common/bech32.o				\
	common/bech32_util.o			\
	common/bigsize.o			\
	common/bip32.o				\
	common/channel_id.o			\
	common/crypto_state.o			\
	common/cryptomsg.o			\
	common/daemon.o				\
	common/daemon_conn.o			\
	common/derive_basepoints.o		\
	common/dev_disconnect.o			\
	common/ecdh_hsmd.o			\
	common/features.o			\
	common/status_wiregen.o			\
	common/gossip_rcvd_filter.o		\
	common/key_derive.o			\
	common/memleak.o			\
	common/msg_queue.o			\
	common/node_id.o			\
	common/onionreply.o			\
	common/per_peer_state.o			\
	common/psbt_open.o			\
	common/pseudorand.o			\
	common/setup.o				\
	common/status.o				\
	common/status_wire.o			\
	common/subdaemon.o			\
	common/timeout.o			\
	common/type_to_string.o			\
	common/utils.o				\
	common/utxo.o				\
	common/version.o			\
	common/wireaddr.o			\
	common/wire_error.o			\
	gossipd/gossipd_wiregen.o		\
	lightningd/gossip_msg.o			\
	wire/onion$(EXP)_wiregen.o

lightningd/lightning_connectd: $(CONNECTD_OBJS) $(CONNECTD_COMMON_OBJS) $(BITCOIN_OBJS) $(WIRE_OBJS) $(HSMD_CLIENT_OBJS)

include connectd/test/Makefile
