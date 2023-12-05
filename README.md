# adatb

A táblákat nem sikerült feltöltenem (meggyűlt a bajom a dockerrel) DE
A  file-ok között sorban haladva fel lehet építeni őket

- Táblák létrehozása az 1.-ben

- A táblák adattal való feltöltése a 2. pontban van

- Tárolt eljárások és a triggerek a 3.-ban

- A 4.-ben lévő eljárásokat le kell futtatni (karbantató fgvv).További bérlésre is van mock.

- Az 5.- ben van még pár select

- 6. Particionálás- > ez megtörténik, átmásolja az adatokat, de a függvények nem ehhez a táblához vannak bedrótozva -> majd V2-ben


Táblamagyarázat

AUTO
Rendszam (primary key )- Itt nincs külön ID mivel a rendszám eleve egyedi azonosító -> Praktikusabb lenne egy ID, mivel ezzel nehé dolgozni, e majd a v2-ben.
Gyarto - Az autó gyártója
Tipus - tipusa
Szervizelve - hányszor volt szervizelve az autó
Uzembe helyezve - autó korának számolásához
Foglalt = TRUE akkor aznapra nem lehet foglalni
Uzemmkepes = FALSE akkor semelyik napra
Napidij- az auto berleti dija/nap

KOLCSONZES
ID - serial - primary key
Rendszam (auto) - külső kulc
Ugyfel (ugyfel id) - külső kulcs
Szamla (szamla id) - külső kulcs
Amnt uj sor kerul a kolcsonzes táblába, a triggel készít egy új sort a számlába, majd onnan az ID-t visszamásolja a KOLCSONZES-be
Kezdes - date
Vege - date
  Működése
  Kissé nyaktekert itt a logika, mert a kolcsonzés kezdete es vege egyben a foglalo rendszer is. Ha adott időintervallumra már létezik bejegyzés, akkor nem lehet újat készíteni a tárolt eljárással.
Szamlazva - bool 
A mező átbillentésével kerül be a SZAMLA táblába a kelt és a bérlés összege

UGYFEL
id - primary
nev
utca
varos 
megye
szuletési dátum

Lehet particionálni megyék szerint


SZAMLA
ID - seral - primary
Ugyfel - külső kulcs
Kelt - amikor a szamla létre lett hozva
Teljesitve - amikor ki lett fizetve
Total - a kocsonzes osszege (napidij*napok szama)

Jelenleg 1 számlához 1 kölcsönzés tartozik. Persze ezt meg lehetne oldani egy tömbbel, hogy akár több kölcsönzés is tartozzon 1 táblához -> majd v2








