@startuml
skinparam style strictuml
skinparam backgroundcolor transparent
scale 1
hide empty members

class Joueur {
  id : String
  nom : String
  argent : int
  deck : Deck
  amis[] : Joueur[]
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

class Carte {
  id : String
  effet : String
  rarete : intS
}

class Duel{
  joueur1 : Joueur
  joueur2 : Joueur
}
class Deck{
  deck[] : Carte[]
}
class magasin{
  bosters[] : booster[]
}
class booster{
  id : String
  cartes[] : Carte[]
}
class Bot{
  id : String
  nom : String
  deck : Deck
  niveau : ?
}


Magie "1" --> "*" Carte : est une >
Piege "1" --> "*" Carte : est une >
Monstre "1" --> "*" Carte : est une >
magasin "*" -- "1" booster : contient >
Joueur "*" -- "1" magasin : achete des cartes au >
Deck "1" -- "*" Carte : contient des >
Joueur "1" -- "1" Deck : possede un >
Joueur "2" -- "1" Duel : participe a >
Bot "2" -- "1" Duel : participe a >


@enduml