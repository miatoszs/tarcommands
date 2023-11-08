# tarcommands
összegyűjtöttem egy csomó tar parancsot, remélem ez elég lesz a palinak, de majd szombaton kidolgozzuk és megcsináljuk a prezentációt.


##     Tarball létrehozása
###### Ez a parancs létrehoz egy archivum.tar nevű tarballt, amely tartalmazza a fajlok-at.
        tar -cf archivum.tar fajlok 
###### Ez a parancs létrehoz egy gzip-pel tömörített tarballt archivum.tar.gz néven.
        tar -czf archivum.tar.gz fajlok

##     Tarball tartalmának megtekintése
###### Ez a parancs kilistázza az archivum.tar tartalmát kicsomagolás nélkül.
        tar -tf archivum.tar 

##     Fájlok kicsomagolása
######  Ez a parancs kicsomagolja az összes fájlt az archivum.tar-ból.
        tar -xf archivum.tar
###### Ez a parancs kicsomagol egy adott könyvtárba.
        tar -xf archivum.tar -C /elérési/út/mappa
###### Ez a parancs csak a .txt fájlokat csomagolja ki.
        tar -xf archivum.tar --wildcards '*.txt' 

##     Fájlok hozzáadása egy tarballhoz
###### Ez a parancs hozzáad egy ujfajl-t a meglévő archivum.tar-hoz.
        tar -rf archivum.tar ujfajl 

##     Fájlok frissítése egy tarballban
###### Ez a parancs frissíti a frissitendo fájlt az archivum.tar-ban, ha az megváltozott.
        tar -uf archivum.tar frissitendo 

##     Fájlok törlése egy tarballból
###### Ez a parancs töröl egy torlendo fájlt az archivum.tar-ból (csak nem tömörített archívumoknál működik).
        tar --delete -f archivum.tar torlendo

##     Tömörítés és kicsomagolás
###### Ez a parancs tömörít egy könyvtárat egy .gz tarballba.
        tar -czf archivum.tar.gz mappa/ 
###### Ez Tömörít bzip2-vel.
        tar -cjf archivum.tar.bz2 mappa/ 
###### Ez tömörít XZ-vel.
        tar -cJf archivum.tar.xz mappa/
###### Ez kicsomagol egy .gz tömörítésű tarballt.
        tar -xzf archivum.tar.gz 
###### Ez kicsomagol egy .bz2 tömörítésű tarballt.
        tar -xjf archivum.tar.bz2
###### Ez kicsomagol egy .xz tömörítésű tarballt.
        tar -xJf archivum.tar.xz 

##     Jogosultságok megőrzése
###### Jogosultságok megőrzése tarball létrehozásakor.
        tar -pczf archivum.tar.gz mappa/ 
###### Jogosultságok megőrzése kicsomagoláskor.

        tar -pxzf archivum.tar.gz 
##     Fájlok és könyvtárak összekombinálása
###### Ez a parancs létrehoz egy tarballt több fájllal és könyvtárral.

        tar -czf archivum.tar.gz fajl1 fajl2 mappa1/ 
##     Verbose Mód
###### Ez a parancs verbose módban hoz létre egy tarballt, megmutatva a hozzáadott fájlokat.
        tar -cvzf archivum.tar.gz fajlok 
###### Ez Verbose módban csomagol ki.
        tar -xvzf archivum.tar.gz 

##     Tar használata más parancsokkal
###### Ez a parancs létrehoz egy tarballt és átviszi SSH-n keresztül.
        tar -czf - fajlok | ssh felhasznalo@hoszt 'cat > archivum.tar.gz' 
        

##     Tar file jelszóval védése
        gpg -c --cipher-algo AES256 fajlok.tar 

##     Tar file kicsomagolása és jelszavas titkosítás megszűntetése

        gpg -d fajlok.tar.gpg | tar xvf -

