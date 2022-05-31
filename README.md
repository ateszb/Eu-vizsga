# Eu-vizsga
#--------------------------------------------------------
# 1.
class Eu:
    def __init__(self,sor):
        orszag, datum = sor.strip().split(";")
        self.orszag = orszag
        self.datum = datum
        self.ev = int(datum[:4])
        self.honap = int(datum[5:7])
        self.nap = int(datum[8:10])

      
print(f"1. Osztály létrehozása Eu: néven")

#--------------------------------------------------------
# 2. 
lista = []
with open("csatlakozas.txt") as f:
    for sor in f:
        lista.append(Eu(sor))
    
        
print(f"2. A 'csatlakozas.txt' fájl beolvasása, a lista 'feltöltése' adatokkal.")

#--------------------------------------------------------
# 3. A tagállamok száma 2018-ban a BREXIT előtt, tehát Az Egyesült királyság még tag.
def tagallamok_szama_2018(lista):
    return len(lista)
    
tagallamok_szama = tagallamok_szama_2018(lista)  
print(f"3. A tagállamok száma 2018-ban: {tagallamok_szama}")

#--------------------------------------------------------
# 4. 
def csatlakozasok_szama_az_evben(lista, ev):
    szamlalo = 0
    for sor in lista:
        if ev == sor.ev:
            szamlalo += 1
    return szamlalo
    
csatlakozasok_2007 = csatlakozasok_szama_az_evben(lista, 2007)
print(f"4. Csatlakozások száma 2007-ben: {csatlakozasok_2007} ")

#--------------------------------------------------------
# 5.
def csatlakozasok_szama_a_honapban(lista, honap):
    szamlalo = 0
    for sor in lista:
        if honap == sor.honap:
            szamlalo += 1
    return szamlalo 

csatlakozasok_majus = csatlakozasok_szama_a_honapban(lista, 5)
print(f"5. Csatlakozások száma májusban: {csatlakozasok_majus} ")

#--------------------------------------------------------
# 6. 
def orszag_csatlakozasi_datuma(lista, orszag):
    for sor in lista:
        if sor.orszag == orszag:
            return sor.datum

magyarorszag_datuma = orszag_csatlakozasi_datuma(lista, 'Magyarország')
print(f"6. Magyarország csatlakozási dátuma: {magyarorszag_datuma}")

#--------------------------------------------------------
# 7.
def utoljara_csatlakozott_orszag(lista):
    return max(lista, key=lambda x:x.datum).orszag 
    
print(f"7. Utoljára csatlakozott ország neve: {utoljara_csatlakozott_orszag(lista)} ")

#--------------------------------------------------------
# 8.
def legtobb_csatlakozas_honapja(lista):
    return min(lista, key=lambda x:x.honap).honap
    
print(f"8. A legtöbb ország a következő hónapban csatlakozott: {legtobb_csatlakozas_honapja(lista)}")

#--------------------------------------------------------
# 9.
def tagallamok_szama_az_adott_evben(lista, ev):
    szamlalo = 0
    for sor in lista:
        if sor.ev <= ev:
            szamlalo += 1
    return szamlalo
            
print(f"9. A tagállamok száma 2000-ben: {tagallamok_szama_az_adott_evben(lista, 2000)}")
