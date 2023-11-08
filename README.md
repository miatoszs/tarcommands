# tarcommands
összegyűjtöttem egy csomó tar parancsot, remélem ez elég lesz a palinak, de majd szombaton kidolgozzuk és megcsináljuk a prezentációt.


######     Tarball létrehozása
      `  tar -cf archivum.tar fajlok`: Létrehoz egy archivum.tar nevű tarballt, amely tartalmazza a fajlok-at.
        `tar -czf archivum.tar.gz fajlok`: Létrehoz egy gzip-pel tömörített tarballt archivum.tar.gz néven.

#####     Tarball tartalmának megtekintése
        `tar -tf archivum.tar`: Kilistázza az archivum.tar tartalmát kicsomagolás nélkül.

#####     Fájlok kicsomagolása
      `  tar -xf archivum.tar`: Kicsomagolja az összes fájlt az archivum.tar-ból.
       ` tar -xf archivum.tar -C /elérési/út/mappa`: Kicsomagol egy adott könyvtárba.
        `tar -xf archivum.tar --wildcards '*.txt'`: Csak a .txt fájlokat csomagolja ki.

#####     Fájlok hozzáadása egy tarballhoz
        `tar -rf archivum.tar ujfajl`: Hozzáad egy ujfajl-t a meglévő archivum.tar-hoz.

#####     Fájlok frissítése egy tarballban
        `tar -uf archivum.tar frissitendo`: Frissíti a frissitendo fájlt az archivum.tar-ban, ha az megváltozott.

#####     Fájlok törlése egy tarballból
        `tar --delete -f archivum.tar torlendo`: Töröl egy torlendo fájlt az archivum.tar-ból (csak nem tömörített archívumoknál működik).

#####     Tömörítés és kicsomagolás
        `tar -czf archivum.tar.gz mappa/`: Tömörít egy könyvtárat egy .gz tarballba.
        `tar -cjf archivum.tar.bz2 mappa/`: Tömörít bzip2-vel.
        `tar -cJf archivum.tar.xz mappa/`: Tömörít XZ-vel.
        `tar -xzf archivum.tar.gz:` Kicsomagol egy .gz tömörítésű tarballt.
        `tar -xjf archivum.tar.bz2:` Kicsomagol egy .bz2 tömörítésű tarballt.
        `tar -xJf archivum.tar.xz`: Kicsomagol egy .xz tömörítésű tarballt.

#####     Jogosultságok megőrzése
        `tar -pczf archivum.tar.gz mappa/`: Jogosultságok megőrzése tarball létrehozásakor.
        `tar -pxzf archivum.tar.gz:` Jogosultságok megőrzése kicsomagoláskor.

#####     Fájlok és könyvtárak összekombinálása
        `tar -czf archivum.tar.gz fajl1 fajl2 mappa1/`: Létrehoz egy tarballt több fájllal és könyvtárral.

#####     Bőbeszédű Mód
        `tar -cvzf archivum.tar.gz fajlok`: Verbózus módban hoz létre egy tarballt, megmutatva a hozzáadott fájlokat.
        tar -xvzf archivum.tar.gz: Verbózus módban csomagol ki.

#####     Tar használata más parancsokkal
        `tar -czf - fajlok | ssh felhasznalo@hoszt 'cat > archivum.tar.gz'`: Létrehoz egy tarballt és átviszi SSH-n keresztül.
