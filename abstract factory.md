# Le design pattern abstract  Factory ou Fabrique abstraite

Le design pattern Abstract Factory, ou **Fabrique abstraite** reprend le même principe que **Factory**, à l'exception que nous considérons dans ce cas un ensemble de fabrique. En effet, la **Fabrique abstraite** permet non pas d'instancier différents objets d'une même classe mère mais plusieurs objets de plusieurs classes mères.

Pour créer notre **Fabrique abstraite**, nous avons besoin des étapes suivantes :
- Une fabrique abstraite contenant toutes les méthodes de création d'objets, le client peut seulement intéragir avec.
- Les fabriques dérivant de la fabrique abstraite, permettant d'instancier les objets souhaités.
- Les classes abstraites des objets, elles contiennent les méthodes d'utilisation propre à chaque objet.
- Les classes dérivant des produits abstraits, ce sont ces produits qui seront renvoyés au client.

De la même manière que le design pattern Factory, nous détachons toutes méthodes de création des méthodes d'utilisation, afin de faciliter la maintenance et la compréhension des applications. Nous remarquons aussi que le principe DIP est démontré, ainsi qu'un nouveau principe : ISP. ISP nous dit que  **un client ne doit pas dépendre d'interfaces qui ne lui correspondent pas**, ainsi un produit A1 peut etre vu comme un simple produit A, tout en ne prenant pas les méthodes du produit B, chose qui arrivera lors de la création des objets dans les différentes fabriques.

## **Exemple de design pattern Fabrique :**

L'exemple que nous allons voir permet de créer des Ordinateur qui seront soit des PC soit des Serveurs.

**Etape 1 :**
Création de la classe abstaite  **Computer**  qui correspond à la classe mère.

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

Création des classes  **PC**  et  **Server**  les classes filles descendant de  **Computer**.

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

Création de l'interface  **ComputerAbstractFactory**  qui possède une méthode  **createComputer()**.

```java
public interface ComputerAbstractFactory {

	public Computer createComputer();

}
```

**Etape 4 :**

Création des classes d'usine  **PCFactory**  et  **ServerFactory**  qui implementent l'interface  **ComputerAbstractFactory**.

```java
public class PCFactory implements ComputerAbstractFactory {

	private String ram;
	private String hdd;
	private String cpu;
	
	public PCFactory(String ram, String hdd, String cpu){
		this.ram=ram;
		this.hdd=hdd;
		this.cpu=cpu;
	}
	@Override
	public Computer createComputer() {
		return new PC(ram,hdd,cpu);
	}

}

```

```java
public class ServerFactory implements ComputerAbstractFactory {

	private String ram;
	private String hdd;
	private String cpu;
	
	public ServerFactory(String ram, String hdd, String cpu){
		this.ram=ram;
		this.hdd=hdd;
		this.cpu=cpu;
	}
	
	@Override
	public Computer createComputer() {
		return new Server(ram,hdd,cpu);
	}

}

```

**Etape 5 :**

Création de la classe  **ComputerFactory**  qui possède une méthode abstraite  **getComputer()**  prenant en paramètre une  **ComputerAbstractFactory**.

```java
public class ComputerFactory {

	public static Computer getComputer(ComputerAbstractFactory factory){
		return factory.createComputer();
	}
}

```

**Etape 6 :**

Création d'une classe **TestFactory** qui utilise l'implémentation du modèle de conception ci-dessus.

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

  

interface  ComputerAbstractFactory { //autofold

  

public  Computer  createComputer();

  

}

  

class  PCFactory  implements  ComputerAbstractFactory { //autofold

  

private  String  ram;

private  String  hdd;

private  String  cpu;

public  PCFactory(String  ram, String  hdd, String  cpu){

this.ram=ram;

this.hdd=hdd;

this.cpu=cpu;

}

@Override

public  Computer  createComputer() {

return  new  PC(ram,hdd,cpu);

}

  

}

  

class  ServerFactory  implements  ComputerAbstractFactory { //autofold

  

private  String  ram;

private  String  hdd;

private  String  cpu;

public  ServerFactory(String  ram, String  hdd, String  cpu){

this.ram=ram;

this.hdd=hdd;

this.cpu=cpu;

}

@Override

public  Computer  createComputer() {

return  new  Server(ram,hdd,cpu);

}

  

}

  

class  ComputerFactory { //autofold

  

public  static  Computer  getComputer(ComputerAbstractFactory  factory){

return  factory.createComputer();

}

}

  

class  Main {

  

public  static  void  main(String[] args) {

Computer  pc = ComputerFactory.getComputer(new  PCFactory("2 GB","500 GB","2.4 GHz"));

Computer  server = ComputerFactory.getComputer(new  ServerFactory("16 GB","1 TB","2.9 GHz"));

System.out.println("AbstractFactory PC Config::"+pc);

System.out.println("AbstractFactory Server Config::"+server);

}

}
```
