@startuml
skinparam style strictuml
skinparam backgroundcolor transparent
scale 1
hide empty members

class Joueur {
  id : String
  nom : String
}
class Carte {
  id : String
  effet : String
  rarete : intS
}

class Magie{
  type : Magie
  carte : Carte
}
class Piege{
  type : Piege
  carte : Carte
}
class Monstre{
  type : Monstre
  carte : Carte
}
class duelliste{}
class Duel{}
class Deck{}
class magasin{}
class booster{}


PR "1" *-- "42" Pays : Contient >
PR "1" *-- "6" Continent : Est-\ndivisé-\nen >
Continent "1" *-- "4, 6,\n7, 9,\n12" Pays : Groupe >
Pays "1" -- "1..*" Pays : Est-voisin-de >
JeuRisk "1" -l- "1" PR : Est-joué-sur >
JeuRisk "1" -d- "5" Dé : Inclut >
Joueur "   2:6" -l- "1" JeuRisk : Joue >
Joueur "1" -- "1..*" Pays : Contrôle >
(Joueur, Pays) .. Occupation
Pays "1" -l- "1..*" Attaque : Lance >
Pays "1" -- "1..*\n" Attaque : Défend-contre >
Joueur "1" -- "1,2,3" Dé : Jette >
@enduml