# makefile of GigE SDK
#

include ../ARCH

NAME	= libImagelib.a

## some flags
#FLAGS	= -fPIC -fexceptions -fno-stack-protector -I/usr/include $(DFLAGS)
FLAGS	= -fPIC -fexceptions -I/usr/include $(DFLAGS)

## few locations
SRC_DIR = ./tiff-src
IST_DIR = ../../lib-pc/$(CPU)/$(CVER)

##
LIB	= -Bdynamic $(SOLIB) 
CFLAGS	= $(OPT) $(FLAGS) -Wall -I$(INC_DIR) -D_REENTRANT $(EXTRA)

## OBJS
OBJS	= $(OBJ_DIR)/ImageLibTiff.o\
	  $(OBJ_DIR)/fax3sm_winnt.o\
	  $(OBJ_DIR)/tif_aux.o\
	  $(OBJ_DIR)/tif_close.o\
	  $(OBJ_DIR)/tif_codec.o\
	  $(OBJ_DIR)/tif_compress.o\
	  $(OBJ_DIR)/tif_dir.o\
	  $(OBJ_DIR)/tif_dirinfo.o\
	  $(OBJ_DIR)/tif_dirread.o\
	  $(OBJ_DIR)/tif_dirwrite.o\
	  $(OBJ_DIR)/tif_dumpmode.o\
	  $(OBJ_DIR)/tif_error.o\
	  $(OBJ_DIR)/tif_fax3.o\
	  $(OBJ_DIR)/tif_flush.o\
	  $(OBJ_DIR)/tif_getimage.o\
	  $(OBJ_DIR)/tif_luv.o\
	  $(OBJ_DIR)/tif_lzw.o\
	  $(OBJ_DIR)/tif_open.o\
	  $(OBJ_DIR)/tif_packbits.o\
	  $(OBJ_DIR)/tif_pixarlog.o\
	  $(OBJ_DIR)/tif_predict.o\
	  $(OBJ_DIR)/tif_print.o\
	  $(OBJ_DIR)/tif_read.o\
	  $(OBJ_DIR)/tif_strip.o\
	  $(OBJ_DIR)/tif_swab.o\
	  $(OBJ_DIR)/tif_thunder.o\
	  $(OBJ_DIR)/tif_tile.o\
	  $(OBJ_DIR)/tif_unix.o\
	  $(OBJ_DIR)/tif_version.o\
	  $(OBJ_DIR)/tif_warning.o\
	  $(OBJ_DIR)/tif_write.o\
	  $(OBJ_DIR)/tif_zip.o		

##
$(OBJ_DIR)/%.o : $(SRC_DIR)/%.cpp
	$(CC) $(TARGET) $(CFLAGS) $(VERSION) -c $< -o $@

$(OBJ_DIR)/%.o : $(SRC_DIR)/%.c
	$(CC) $(TARGET) $(CFLAGS) $(VERSION) -c $< -o $@

clean: 
	rm $(OBJS)

lib : $(OBJS)
	$(AR) -r $(NAME) $(OBJS)

install:
	cp -f $(NAME) $(IST_DIR)
