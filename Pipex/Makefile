# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: diespino <diespino@student.42.fr>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2025/01/15 17:16:03 by diespino          #+#    #+#              #
#    Updated: 2025/02/18 17:47:31 by diespino         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# Output name
NAME = pipex

# ft_printf
SRC_PATH	= src
SRC		= $(SRC_PATH)/pipex.c\
		$(SRC_PATH)/utils.c

OBJS	= $(SRC:.c=.o)

DEPS 	= $(SRC:.c=.d)

INCS	= includes

# libft
LIBFT_PATH	= libft
LIBFT		= $(LIBFT_PATH)/libft.a

# Remove
RM = rm -f

# Flags (-v es para ver enlazado)
CC = gcc
CLIB = ar rcs
CFLAGS = -Wall -Wextra -Werror

all: $(LIBFT) $(NAME)

$(LIBFT):
	make -C $(LIBFT_PATH)
#	cp $(LIBFT) $(NAME)

$(NAME): $(OBJS) $(LIBFT) $(INCS)
	$(CC) $(CFLAGS) $(OBJS) $(LIBFT) -o $(NAME)

# Compila cada .c en un .o y genera un .d  
%.o: %.c Makefile
	$(CC) $(CFLAGS) -I $(INCS) -MMD -MP -c $< -o $@

# Incluye los .d (files for dependencies)
-include $(DEPS)

clean:
	$(RM) $(OBJS)
	$(RM) $(DEPS)
	make clean -C $(LIBFT_PATH)
	
fclean: clean
	$(RM) $(NAME)
	$(RM) $(LIBFT)
	
re: fclean all

.PHONY: all clean fclean re
