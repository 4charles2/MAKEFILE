#Makefile qui sélectionne tous les fichiers .c dans le répertoire#
#avec condition pour option -g pour deboggage activer par default valeur DEBUG a changer
#Makefile silencieu @ devant les lignes de commande
#demande ne pas execute les commandes silencieuse non demandé
EXEC=test
CC=gcc
DEBUG=yes
FLAGS=-W -Wall -Werror -Wextra -ansi -pedantic
LDFLAGS=#Pour les boucles for -std=c99 ou pour autre lib -lsdl -LChemin par exemple
SRC=$(wildcard *.c) #autre possibilte au lieu de la dependance ligne 29
OBJ=$(SRC:.c=.o)

ifeq ($(DEBUG),yes)
	CFLAGS= -g $(FLAGS)
else
	CFLAGS= $(FLAGS)
endif

all: $(EXEC) clean
ifeq ($(DEBUG),yes)
	@echo "Generation avec debug"
else
	@echo "Generation sans debug"
endif

$(EXEC): $(OBJ)
	@$(CC) -o $@ $^ $(LDFLAGS)

#la depandence selectionne tous les .c
$(OBJ): $(SRC)
	@$(CC) $^ -c $(CFLAGS)

#regle .PHONY avec dependance des règles qui doivent être éxecuter même si un fichier plus récent existe
.PHONY: clean fclean

clean:
	@rm -rf $(OBJ)

fclean: clean
	rm -rf $(EXEC)
#Mettre le symbole @ devant les ligne de commande afin qu'elle n'apparaise pas dans la console on dit l'echo des lignes des commandes
re: fclean all
