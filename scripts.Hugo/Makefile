
$(if $(strip $(shell [ 'root' = $${USER} ] && echo 1 )),$(info you should NOT run by root)$(error xxx))

define help_text

	rg -> regen   : regen all hugo
	s  -> server  : run hugo   server to test local
	s2 -> server2 : run python server to test local

endef
export help_text

all:
	@echo "$${help_text}"

include Makefile.env

up:
	nice -n 19 git push -u origin master
e:
	vim Makefile.env
m:
	vim Makefile
gs:
	nice -n 19 git status
gc:
	nice -n 19 git commit -a
	

gd :
	nice -n 19 git diff

ga :
	nice -n 19 git add .

rg:regen
regen:
	[ -f scripts.Hugo/config.toml ] && make regenX -C scripts.Hugo || make regenX 
regenX:
	[ -d themes ] || echo "you should run : git clone https://marstool@github.com/marstool/themes.git"
	rm -fr public/*
	cp ../CNAME public/
	[ -f public/CNAME ] || ( echo ; echo "why no CNAME ? exit" ; echo ; exit 32 )
	nice -n 19 hugo

s : server
server:
	[ -d themes ] || echo "you should run : git clone https://marstool@github.com/marstool/themes.git"
	[ -f scripts.Hugo/config.toml ] && make serverX -C scripts.Hugo || make serverX 
serverX:
	nice -n 19 hugo server --disableFastRender
#	nice -n 19 hugo server

# hddps://themes.gohugo.io/
# hddps://gohugo.io/themes/

s2: server2
server2:
	[ -f scripts.Hugo/config.toml ] && make server2X -C scripts.Hugo || make server2X 
server2X:
	cd public/ && python -m SimpleHTTPServer 33221

