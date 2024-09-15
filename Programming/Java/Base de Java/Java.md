# Java
## Table des Matières
- [Java](#java)
  - [Table des Matières](#table-des-matières)
  - [Méthodes](#méthodes)
    - [Méthodes Constructeurs](#méthodes-constructeurs)
    - [Appel d'une methode constructeur](#appel-dune-methode-constructeur)
    - [Méthode d'observation (get)](#méthode-dobservation-get)
    - [Méthodes de mutation (set)](#méthodes-de-mutation-set)
    - [Utilisation des méthodes de mutation et observation](#utilisation-des-méthodes-de-mutation-et-observation)
    - [Méthodes Statiques](#méthodes-statiques)
    - [Modificateur final et Classe final](#modificateur-final-et-classe-final)
    - [Méthode finale](#méthode-finale)
    - [Variable final](#variable-final)
    - [Méthodes de test](#méthodes-de-test)
      - [Test avec assertEquals()](#test-avec-assertequals)
  - [](#)
  - [](#-1)



## Méthodes
Méthode == fonction en Java.
### Méthodes Constructeurs
Les méthodes constructeurs servent basically a créer des objets pour les instancier plus tard dans le code.

Les prérequis sont:
- Méthodes doivent avoir le même nom que la classe (Contrairement aux autres méthodes qui commencent avec des minuscules)
- Le compilateur reconnais la methode constructeur lorsqu'il a le meme nom que la classe et qu'il ne contient aucun type dans sa definition

Exemples de constructeurs:

```java
//Notez que Employe doit etre dans la classe Employe{}
public Employe(String nom, String numero, double salaireHoraire, double nbreHeuresSemaine, int anciennete)  
{  
    this.nom = nom;  
    this.numero = numero;  
    this.salaireHoraire = salaireHoraire;  
    this.nbreHeuresSemaine = nbreHeuresSemaine;  
    this.anciennete = anciennete;  
}
```

2e exemple Constructeurs
```java
//creation de la classe EtudiantCegep
public class EtudiantCegep {
	private string matricule;
	private int note;
	//les parametres ont des noms differents des var
	//Avoir un parametre du meme nom va confondre le compilateur et donner les donnees nulles
	//l'utilisation du mot cle "this" peut aussi faire le travail 
	public EtudiantCegep(String matricule,int note) {
		this.matricule = matricule;
		this.note = note;
	}
}

//Bien sur faut tu ajoutes tes variables private en haut que j'ai pas fait.
public Refrigerateur(String nomModele,double prix,double capacite,boolean aDistributeurAGlace);
{
	this.nomModele = nomModele;
	this.prix = prix;
	this.capacite = capacite;
	this.aDistributeurAGlace = aDistributeurAGlace;
}

public Refrigerateur() 
{
	this("Frigidaire",900.00,16,false);
}
```
### Appel d'une methode constructeur

```java
EtudiantCegep ec = new EtudiantCegep("1528834",99) 
//Allocation dynamique
```

>[!NOTE]
> Précautions avec les constructeurs Java:
> > Pour accéder aux variables private a l'extérieur de sa classe d'origine, utiliser une méthode publique `get` (Par exemple, getprice ou getFunds) qui permettra d'accéder aux valeurs 
 


```java
package AbonnementGym;  
  
public class AbonnementGym {  
//Infos de l'abonnement  
    private double prix;  
    private int duree;  
    private String nomMembre;  
  
    //Personnalise (Clients VIP)  
    public AbonnementGym(double prix,int duree,String nomMembre)  
    {  
        this.prix = prix;  
        this.duree = duree;  
        this.nomMembre = nomMembre;  
    }  
    //Pour les mensuels  
    public AbonnementGym(String nomMembre)  
    {  
        //pas besoin d'ajouter this car aucun risque de confusion  
        prix = 41.25;  
        duree = 30;  
        this.nomMembre = nomMembre;  
    }  
    //Pour a la carte  
    public AbonnementGym(int duree,String nomMembre)  
    {  
        this.duree = duree;  
        prix = 8.25 * duree;  
        //prix = 8.25 * this.duree  
        /*  
  
         */        this.nomMembre = nomMembre;  
    }  
}
```

### Méthode d'observation (get)
- Permet de voir la variable privée dans une classe
Exemples de méthodes get
```java
  public int getDuree() {  
        return duree;  
    }  
  
    public double getPrix() {  
        return prix;  
    }  
  
    public String getNomMembre() {  
        return nomMembre;  
    }  
```
### Méthodes de mutation (set)
- Permettent de modifier la variable à l'extérieur de sa classe d'origine

Exemple de méthodes *set* :
```java
public void setPrix(double prix) {  
    this.prix = prix;  
}  
  
public void setDuree(int duree) {  
    this.duree = duree;  
}  
  
public void setNomMembre(String nomMembre) {  
    this.nomMembre = nomMembre;  
}
```

### Utilisation des méthodes de mutation et observation

```java

public class TestConstructeur2 {  
  
    public static void main(String[] args) {  
        AbonnementGym a1 = new AbonnementGym("Samuel Bergeron");  
        AbonnementGym a2 = new AbonnementGym(4,"Alexianne");  
        AbonnementGym a3 = new AbonnementGym(41.24,4,"Jean-Marc");  
  
  
        //Remarque qu'on utilise les methodes pour avoir l'information, 
        //car cest private a sa propre classe  
        System.out.println(a2.getDuree());  
        a2.setDuree(8);  
        System.out.println(a2.getDuree());  
  
    }  
  
}
```

### Méthodes Statiques
```java

Class EtudiantCegep
{
	Private String nom;
	Private String matricule;
	Private double revenu;
	Private char sexe;
	Private boolean aideSaide; //Demande d'aide pour le SAIDE en francais

	//La méthode calculerPretsEtBourses ne sera pas statique car le résultat dépend du contenu de la variable revenu de chaque Objet étudiant.
	
	//La méthode assignerCasier serait statique car le résultat ne dépends pas du contenu des variables d'instance de chaque objet étudiant.

	//La méthode assignerLocalExamenFrancais -> pas statique car elle dépenderais de la variable aideSaide de chaque objet.
}
```
### Modificateur final et Classe final

```java
public final class McDo //Notez le final
{}

public class Resto extends McDo //Pas possible car on ne peux pas prendre ce que McDo a dans son propre restaurant. On va se faire actionner


```
### Méthode finale
- On ne peut pas définir différemment ce comportement.
- Par exemple, dans une sous-classe.
```java
class Compte
{
	Public final double calculerInteret() //Notez le final
	{
		
	}
}
class ComptePrivilege extends Compte;
//On peut appeler la méthode CalculerInteret mais on ne peut pas la modifier ou la redéfinir.

```

### Variable final
- Synonyme d'une **_CONSTANTE_**
```java 
 Public static final double TAUX = 0.05
 ```
 Final: ne peux pas être modifié.
 Static: une seule copie pour toute la classe.

 ### Méthodes de test
On crée une nouvelle classe de test pour essayer les méthodes de la classe qu'on test

1. Créer une classe de test
2. Y ajouter ```@before``` et ```@test```
3. Ajouter une méthode setUp() pour before et initialiser l'objet a tester
4. Ajouter les méthodes de test après test
   ```java
    package packageTP1;

    import org.junit.*;
    import static org.junit.Assert.*;
    
    public class TestEmploye2
    {
        private Employe jeanPaul;
        // Cette methode sera appelé avant chaque methode de    test
        @Before
        public void setUp ()
        {
            jeanPaul = new Employe ("Jean-Paul Lachance",   "D-1234",17.75,40.0,10);
        }
        //methode de test
        @Test
        public void testEmploye ()
        {
            jeanPaul = new Employe("Jean-Paul Lachance",    "D-1234",17.75,40.0,10);
            //print debug always wins.
            System.out.println(jeanPaul.joursVacances()+" Jours     de vacances.");
            System.out.println(jeanPaul.salaireNetAvantImpot()  + " : Salaire net avant impot.");
            System.out.println(jeanPaul.salaireNetApresImpot()  + " : Salaire net après impot.");
            System.out.println(jeanPaul.impotFederal() + " :    Impot Fédéral.");
            System.out.println(jeanPaul.impotProvincial() + " :     Impot Provincial.");
            jeanPaul.heuresSup(10);
            assertEquals(50.0,jeanPaul.getNbreHeuresSemaine(),0.    02); // LINE IS GREEEEN
    
        }
    }

   ```
   En gros:
   - Tu définis la classe de test dans un nouveau fichier java.
   - Tu écris ```@before``` et tu crées une méthode 'setUp()' qui permettra d'initialiser ton objet a tester.
   - tu écris ```@test``` et tu crées une méthode pour tester de la facon tu veux.

 #### Test avec assertEquals()
Avec assertEquals(), tu lui donnes 3 parametres pour tester un double/float:
assertEquals(valeur a tester(float),méthode qui doit donner la réponse du 1er paramètre(float),delta(niveau de précision))

Si la ligne est verte, all good to go, si elle est rouge, problematic (quand tu launch a méthode sur intellij Idea)



 ##

 ##

