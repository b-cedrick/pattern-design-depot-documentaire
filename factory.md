# Le design pattern Factory ou Fabrique

Le design pattern Factory, ou **Fabrique** est un design pattern permettant de séparer la création d'objets dérivant d'une classe mère de leur utilisation. De ce fait, on a alors la possibilité de créer plusieurs objets issue d'une même classe mère.

Pour créer notre **Fabrique**, nous avons besoin de 4 éléments :
1.  Une fabrique générique : Elle contient toutes les méthodes nécessaires à la création d'un produit
2.  Une fabrique : Elle va créer le produit souhaité
3.  Un produit : Le produit créé par la fabrique, dérivant du produit générique
4.  Un produit générique : Le produit d'origine, contenant toutes les méthodes permettant de réaliser les actions associées

Ainsi, nous détachons la création des objets de l'utilisation, ce qui permet d'éviter une certaine redondance au niveau de la programmation.
Nous pouvons voir aussi que le fait de passer par des classes filles pour créer différents objets permet de répondre au **principe d'inversion des dépendances** ou DIP (Dependency Inversion **Principle**), qui consiste à dire que  **les objets de forte valeur métier ne doivent pas dépendre des objets de faible valeur métier**

## **Exemple de design pattern Fabrique :**

L'exemple que nous allons voir permet de créer des Ordinateur qui seront soit des PC soit des Serveurs.
**Etape 1 :**

Création de la classe abstraite  **Computer**  (la classe mère).

```java
public abstract class Computer {
	
	public abstract String getRAM();
	public abstract String getHDD();
	public abstract String getCPU();
	
	@Override
	public String toString(){
		return "RAM= "+this.getRAM()+", HDD="+this.getHDD()+", CPU="+this.getCPU();
	}
}
```

**Etape 2 :**

Création des classes  **PC**  et  **Server**  (les classe filles extraite de la classe  **Computer**  ci-dessous).

```java
public class PC extends Computer {

	private String ram;
	private String hdd;
	private String cpu;
	
	public PC(String ram, String hdd, String cpu){
		this.ram=ram;
		this.hdd=hdd;
		this.cpu=cpu;
	}
	@Override
	public String getRAM() {
		return this.ram;
	}

	@Override
	public String getHDD() {
		return this.hdd;
	}

	@Override
	public String getCPU() {
		return this.cpu;
	}

}

```

```java
public class Server extends Computer {

	private String ram;
	private String hdd;
	private String cpu;
	
	public Server(String ram, String hdd, String cpu){
		this.ram=ram;
		this.hdd=hdd;
		this.cpu=cpu;
	}
	@Override
	public String getRAM() {
		return this.ram;
	}

	@Override
	public String getHDD() {
		return this.hdd;
	}

	@Override
	public String getCPU() {
		return this.cpu;
	}

}

```

**Etape 3 :**

Création de la classe  **ComputerFactory**  qui contient les méthodes nécessaires à la création d'un  **Computer**.

```java
public class ComputerFactory {

	public static Computer getComputer(String type, String ram, String hdd, String cpu){
		if("PC".equalsIgnoreCase(type)) return new PC(ram, hdd, cpu);
		else if("Server".equalsIgnoreCase(type)) return new Server(ram, hdd, cpu);
		
		return null;
	}
}

```

**Etape 4 :**

Création d'une classe **Main** qui utilise l'implémentation du modèle de conception ci-dessus.

```java
  

abstract  class  Computer { //autofold

	public  abstract  String  getRAM();

	public  abstract  String  getHDD();

	public  abstract  String  getCPU();

	@Override

	public  String  toString(){

	return  "RAM= "+this.getRAM()+", HDD="+this.getHDD()+", CPU="+this.getCPU();
	}
}

class  PC  extends  Computer { //autofold
	private  String  ram;
	private  String  hdd;
	private  String  cpu;
	public  PC(String  ram, String  hdd, String  cpu){
		this.ram=ram;
		this.hdd=hdd;
		this.cpu=cpu;
	}

	@Override
	public  String  getRAM() {
		return  this.ram;
	}

	@Override
	public  String  getHDD() {
		return  this.hdd;
	}

	@Override
	public  String  getCPU() {
		return  this.cpu;
	}
}

class  Server  extends  Computer { //autofold
	private  String  ram;
	private  String  hdd;
	private  String  cpu;
	public  Server(String  ram, String  hdd, String  cpu){
		this.ram=ram;
		this.hdd=hdd;
		this.cpu=cpu;
	}

	@Override
	public  String  getRAM() {
		return  this.ram;
	}

	@Override
	public  String  getHDD() {
		return  this.hdd;
	}

	@Override
	public  String  getCPU() {
		return  this.cpu;
	}
}

class  ComputerFactory { //autofold
	public  static  Computer  getComputer(String  type, String  ram, String  hdd, String  cpu){
		if("PC".equalsIgnoreCase(type)) return  new  PC(ram, hdd, cpu);
		else  if("Server".equalsIgnoreCase(type)) return  new  Server(ram, hdd, cpu);
		return  null;
	}
}

class  Main {
	public  static  void  main(String[] args) {
	Computer  pc = ComputerFactory.getComputer("pc","2GB","500GB","2.4GHz");

	Computer  server = ComputerFactory.getComputer("server","16GB","1TB","2.9GHz");

	System.out.println("Factory PC Configuration : " + pc);

	System.out.println("Factory Server Configuration : " + server);

	}
}
```
