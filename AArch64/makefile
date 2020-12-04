# Copyright © 2020 Jeremiah Orians
# Copyright © 2020 Sanne Wouda
# This file is part of stage0.
#
# stage0 is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# stage0 is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with stage0.  If not, see <http://www.gnu.org/licenses/>.

VPATH = bin

# Directories
bin:
	mkdir -p bin

# make the GAS pieces
hex0-gas: GAS/hex0_AArch64.S | bin
	as GAS/hex0_AArch64.S -o bin/hex0.o
	ld bin/hex0.o -o bin/hex0-gas

# make pieces from the GAS pieces
hex0: hex0-gas
	./bin/hex0-gas hex0_AArch64.hex0 hex0

all: hex0

clean:
	rm -f hex0
	rm -rf bin

test: all
	sha256sum -c SHA256SUMS

Generate_test_answers: all
	sha256sum hex0 >| SHA256SUMS