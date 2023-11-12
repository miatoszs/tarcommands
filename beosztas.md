
### Beosztás:
a beosztást próbáltam igazségosan létrehozni, ha a neved alatt több parancsot látsz mint a többieknél, az azért lehet mert a ő parancsaik bonyolultabbak.
mindenki nézze át a saját parancsait, és tanulja meg hogy melyik opció mit csinál, pl:  `tar -czf archivum.tar.gz fajlok` `c`: archívum létrehozása `z`:gzip használata a tar fájl tömörítésére (ezért lesz a vége .tar.gz) `f`: megadja az archívum fájl nevét


# igazi Andor
##     Tarball létrehozása
###### Ez a parancs létrehoz egy archivum.tar nevű tarballt, amely tartalmazza a fajlok-at.
        tar -cf archivum.tar fajlok 
######  Ez a parancs kicsomagolja az összes fájlt az archivum.tar-ból.
        tar -xf archivum.tar
### A következő parancsok nem csak .tar-nál működnek hanem ezeknél is |.tar.gz|.tar.bz2|.tar.xz| (csak természetesen más opciókat kell megadni)

###### Ez a parancs kilistázza az archivum.tar tartalmát kicsomagolás nélkül.
        tar -tf archivum.tar 
###### Ez a parancs kicsomagol egy adott könyvtárba.
        tar -xf archivum.tar -C /elérési/út/mappa
###### Ez a parancs csak a .txt fájlokat csomagolja ki.
        tar -xf archivum.tar --wildcards '*.txt' 
###### Ez a parancs hozzáad egy ujfajl-t a meglévő archivum.tar-hoz.
        tar -rf archivum.tar ujfajl 
###### Ez a parancs frissíti a frissitendo fájlt az archivum.tar-ban, ha az megváltozott.
        tar -uf archivum.tar frissitendo 
###### Ez a parancs töröl egy torlendo fájlt az archivum.tar-ból (csak nem tömörített archívumoknál működik).
        tar --delete -f archivum.tar torlendo



# szakállas Andor

###### Ez a parancs létrehoz egy gzip-pel tömörített tarballt archivum.tar.gz néven.
        tar -czf archivum.tar.gz fajlok
###### Ez kicsomagol egy .gz tömörítésű tarballt.
        tar -xzf archivum.tar.gz 
### A következő parancsok nem csak .tar.gz-nél működnek hanem ezeknél is |.tar|.tar.bz2|.tar.xz| (csak természetesen más opciókat kell megadni)
###### Jogosultságok megőrzése tarball létrehozásakor.
        tar -pczf archivum.tar.gz mappa/ 
###### Jogosultságok megőrzése kicsomagoláskor.
        tar -pxzf archivum.tar.gz 
###### Ez a parancs létrehoz egy tarballt több fájllal és könyvtárral.
        tar -czf archivum.tar.gz fajl1 fajl2 mappa1/ 
###### Ez a parancs verbose módban hoz létre egy tarballt, megmutatva a hozzáadott fájlokat.
        tar -cvzf archivum.tar.gz fajlok 
###### Ez Verbose módban csomagol ki.
        tar -xvzf archivum.tar.gz 
        
# Cao

###### Ez Tömörít bzip2-vel.
        tar -cjf archivum.tar.bz2 mappa/ file
###### Ez kicsomagol egy .bz2 tömörítésű tarballt.
        tar -xjf archivum.tar.bz2
### A következő parancsok nem csak .tar.bz2-nél működnek hanem ezeknél is |.tar.gz|.tar|.tar.xz| (csak természetesen más opciókat kell megadni)
###### Ez a parancs létrehoz egy tarballt és átviszi SSH-n keresztül.
        tar -cjf - fajlok | ssh felhasznalo@hoszt 'cat > archivum.tar.bz2' 
Cao ez egy nehéz parancs, itt van hozzá egy kis magyarázat:
`tar -cjf - fajlok`: Ez a rész egy tar archívumot hoz létre a fajlok nevű könyvtárból vagy fájlokból. A `-c` kapcsoló új archívumot hoz létre, a `-j` kapcsoló BZip2 tömörítést használ, a `-f` - pedig azt jelzi, hogy a kimenetet a standard kimenetre (stdout) írja, nem egy fizikai fájlba. `|`: Ez a csővezeték (pipe) szimbólum, ami átirányítja az első parancs kimenetét (a tar által létrehozott archívumot) a következő parancs bemenetébe. `ssh felhasznalo@hoszt 'cat > archivum.tar.bz2'`: Ez a rész egy távoli gépre (hoszt) történő SSH kapcsolatot létesít a megadott felhasznalo felhasználói névvel. A kapcsolat létrejötte után a cat > archivum.tar.bz2 parancsot hajtja végre a távoli gépen. Ez a parancs a cat programot használja arra, hogy az SSH-n keresztül érkező adatot (amit a tar és a csővezeték küld) egy archivum.tar.bz2 nevű fájlba írja a távoli gépen. Összességében ez a parancs egy helyi könyvtár vagy fájlok tömörített archívumát hozza létre, majd ezt az archívumot átküldi egy távoli gépre SSH-n keresztül, ahol egy új .tar.bz2 fájlként menti el. Ez egy hatékony módja a nagyobb fájlok vagy könyvtárak biztonságos átvitelének egyik gépről a másikra.
# Péter

###### Ez tömörít XZ-vel.
        tar -cJf archivum.tar.xz mappa/
###### Ez kicsomagol egy .xz tömörítésű tarballt.
        tar -xJf archivum.tar.xz 
### A következő parancsok nem csak .tar.xz-nél működnek hanem ezeknél is |.tar.gz|.tar.bz2|.tar| (csak természetesen más opciókat kell megadni)
######     Tar file jelszóval védése
        gpg -c --cipher-algo AES256 fajlok.tar.xz

######     Tar file kicsomagolása és jelszavas titkosítás megszűntetése
        gpg --decrypt fajlok.tar.xz.gpg > fajlok.tar.xz

        gpg -d fajlok.tar.xz.gpg | tar xJf -
-------------------------------------------------------------------------------------------------        
### Opció magyarázatok
    -c: Create archive (archívum létrehozása).
    -x: Extract files from archive (fájlok kicsomagolása az archívumból).
    -t: List the contents of an archive (egy archívum tartalmának kilistázása).
    -r: Append files to the end of an archive (fájlok hozzáfűzése egy archívum végéhez).
    -u: Update files within an archive (fájlok frissítése egy archívumban).
    -d: Delete from the archive (nem tömörített archívumból való törlés).

###### A tömörítési módokat kiválasztó opciók:

    -z: Use gzip to compress the tar file (gzip használata a tar fájl tömörítésére).
    -j: Use bzip2 to compress the tar file (bzip2 használata a tar fájl tömörítésére).
    -J: Use xz to compress the tar file (xz használata a tar fájl tömörítésére).

###### További gyakran használt opciók:

    -f: Specify the filename of the archive (megadja az archívum fájl nevét).
    -v: Verbose mode; show progress (részletes mód; folyamat megjelenítése).
    -p: Preserve permissions (jogosultságok megőrzése).
    -C: Change to directory before performing any operations (műveletek előtt változtatja meg a munkakönyvtárat).

###### Speciális használatokhoz szükséges opciók:

    --wildcards: Use wildcard patterns (helyettesítő karakterek használata).
    --delete: Delete files from the archive (fájlok törlése az archívumból, csak nem tömörített archívumok esetén).


# tarcommands
összegyűjtöttem egy csomó tar parancsot, remélem ez elég lesz, de majd szombaton kidolgozzuk és megcsináljuk a prezentációt.
### Mi az a tarball:
A tarball olyan fájlok halmaza, amelyek egyetlen fájlba vannak csomagolva, majd tömörítve


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
        gpg --decrypt fajlok.tar.gpg > fajlok.tar

        gpg -d fajlok.tar.gpg | tar xvf -


###### Ezen felül a következő speciális használatok is láthatók:

    -c -f -: Az archívum létrehozása és a kimenet közvetlen átadása egy másik parancsnak (például SSH-n keresztül).
    gpg -c: GPG használata fájlok titkosítására.
    gpg -d: GPG használata titkosított fájlok dekódolására.

###### Minden egyes opciót gyakran együtt használnak, hogy megadott műveleteket hajtsanak végre a tar archívumokkal.
------------------------------------------------------------------------------------------------------------


### A .tar fájl egy archívum, amely több fájlt és könyvtárat tartalmaz egyetlen fájlban az egyszerűbb tárolás és szállítás érdekében. A .tar fájl nem tömörített, így gyorsan hozható létre és bontakoztatható ki, de nagyobb méretű lesz, mint a tömörített változatai.

- A .tar.gz egy gzip-pel tömörített tar archívum. Ez egy népszerű tömörítési forma Linux és Unix rendszerekben, mivel jól egyensúlyoz a tömörítés mértéke és a tömörítési/sebességi arány - között.

- A .tar.bz2 egy bzip2-vel tömörített tar archívum, amely általában jobb tömörítést biztosít mint a .tar.gz, de több processzoridőt igényel a tömörítéshez és a kibontáshoz, tehát lassabb lehet.

- A .tar.xz egy xz tömörítéssel rendelkező tar archívum, amely általában a legjobb tömörítési rátát biztosítja, de még több időt vehet igénybe a tömörítés és a kicsomagolás során.

Összefoglalva:

    .tar
        Előnyök: Gyors létrehozás és kicsomagolás.
        Hátrányok: Nagyobb fájlméret a tömörítetlen formátum miatt.

    .tar.gz
        Előnyök: Jobb tömörítés mint a sima tar, széles körben támogatott.
        Hátrányok: Lassabb tömörítés és kicsomagolás mint a tar.

    .tar.bz2
        Előnyök: Jobb tömörítési arány mint a .tar.gz, ami kisebb fájlokat eredményez.
        Hátrányok: Lassabb tömörítés/kicsomagolás, kisebb támogatottság.

    .tar.xz
        Előnyök: A legjobb tömörítési arány.
        Hátrányok: Leglassabb tömörítés/kicsomagolás, és nem támogatott minden platformon.

Mindegyik formátum használata során figyelembe kell venni a rendelkezésre álló erőforrásokat, a kompatibilitást, és hogy milyen gyakran kell a fájlokat tömöríteni vagy kicsomagolni.
