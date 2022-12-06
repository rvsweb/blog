---
layout: single
title: Java - Expresiones Lambda
date: 2022-12-06
classes: wide
toc: true
toc_label: "Tabla de contenido"
toc_icon: "clipboard-list"
header:
  teaser: /assets/images/java/logo-java-2.jpg
categories:
  - java
  - java-manual
tags:
  - java-clase
  - java-expresiones-lambda
page_css: 
  - /assets/css/mi-css.css
---

## Expresiones Lambda

* Se utilizan entre otros motivos para resolver los problemas que producían el uso las ``clases anónimas``

* La implementación de la ``clase anónima`` era simple como la creación de una ``interfaz`` que contiene ``un solo método`` lo que producía que la sintaxis de las ``clases anónimas`` pudiera parecer difícil de manejar y difícil de entender

* Antiguamente se intentaba pasar la funcionalidad de un ``método`` como ``argumento`` a otro ``método``, como la acción que se debía tomar cuando alguien por ejemplo ; hacía clic en un botón

* Las ``expresiones lambda`` le permiten tratar la funcionalidad como ``argumento de método`` o el ``código`` como ``datos``

* Las ``clases anónimas`` le muestra cómo implementar una ``clase base`` sin darle un nombre

  * Aunque esto suele ser más conciso que una ``clase con nombre`` , para las ``clases con un solo método`` , incluso una ``clase anónima`` parece un poco excesiva y engorrosa

* Las ``expresiones lambda`` le permiten expresar ``instancias de clases`` de ``método único`` de forma más compacta.

## Ejemplo de Expresión Lambda

* ``Interfaz``

  * Se usa para comprobar el tipo de ``objeto`` que recibirá el método de la ``clase`` que lo implemente

```java
public interface CheckPerson {
/**
  * Método de la interface
  * 
  * Devuelve si el objeto es de tipo Person o no
  * 
  * Se utiliza para comprobar que el parámetro que recibe el método es un objeto
  * de tipo Person y devolver un boolean
  * 
  * @param p - objeto - Objeto de la clase Person
  * @return - boolean - Devuelve true o false dependiendo del objeto que reciba
  */
boolean test(Person p);
}
```

* ``Clase Concreta`` que implementa la interface ``CheckPerson``

  * La ``clase`` implementa la ``interfaz CheckPerson`` al especificar una implementación para la prueba del ``método``

  * Este ``método`` filtra miembros que son ``elegibles`` para el ``método``  devuelve un valor ``verdadero`` si su ``parámetro Person`` es ``MAN`` y tiene **entre 18 y 25 años**

```java
// Clase Concreta que implementa la interface CheckPerson para poder usarse
public class CheckPersonEligibleForSelectiveService implements CheckPerson {
/**
  * Método de instancia
  * 
  * Implementa el método 'test' de la Interface CheckPerson
  * 
  * @param - objeto - Person - Recibe un objeto person para hacer las
  *          comprobaciones
  * @return - boolean - Devuelve - Si la edad del objeto Person esta dentro de
  *         los parámetros establecidos por el objeto
  */
 @Override
  public boolean test(Person p) {
    return p.gender == Person.Sex.MALE &&
      p.getAge() >= 18 &&
      p.getAge() <= 25;
  }
}
```

* ``Clase Person``

```java
/**
 * Clase Concreta
 * 
 * @author RVS
 *
 */
public class Person {

 /**
  * Elemento tipo Enumerate
  * 
  * 2 opciones 'MALE' o 'FEMALE'
  * 
  * @author RVS
  *
  */
 public enum Sex {
  MALE, FEMALE
 }

// Atributos de instancia
 String name;
 LocalDate birthday;
 Sex gender;
 String emailAddress;

 /**
  * Constructor parametrizado
  * 
  * @param nameArg
  * @param birthdayArg
  * @param genderArg
  * @param emailArg
  */
 public Person(String nameArg, LocalDate birthdayArg, Sex genderArg, String emailArg) {
  name = nameArg;
  birthday = birthdayArg;
  gender = genderArg;
  emailAddress = emailArg;
 }

 /**
  * Método de Instancia
  * 
  * @return - int - calcula la edad mediante el año actual hasta el numero de
  *         años almacenados en birthday
  */
 public int getAge() {
  return birthday.until(IsoChronology.INSTANCE.dateNow()).getYears();
 }

 /**
  * Método de Instancia
  * 
  * Muestra los valores 'name' y la edad del objeto Person que sea instanciado en
  * ese momento
  */
 public void printPerson() {
  System.out.println(name + ", " + this.getAge());
 }

 /**
  * Método de Instancia
  * 
  * Obtener un objeto del tipo enum gender
  * 
  * @return - enum - tipo Sex
  */
 public Sex getGender() {
  return gender;
 }

 /**
  * Método de Instancia
  * 
  * Obtener un objeto del tipo enum getName
  * 
  * @return - String - devuelve un objeto de tipo String identificado como name
  */
 public String getName() {
  return name;
 }

 /**
  * Método de Instancia
  * 
  * Obtener un objeto del tipo String emailAddress
  * 
  * @return - String - devuelve un objeto de tipo String identificado como emailAddress
  */
 public String getEmailAddress() {
  return emailAddress;
 }

 /**
  * Método obtenemos el día del cumpleaños
  * 
  * @return - LocalDate - Objeto de tipo birthday
  */
 public LocalDate getBirthday() {
  return birthday;
 }

 /**
  * Método de Clase
  * 
  * Calcula las fechas entre 2 edades
  * 
  * @param a - Objeto clase Persona 'a'
  * @param b - Objeto clase Persona 'b'
  * @return - int - Devuelve la diferencia entre 2 edades
  */
 public static int compareByAge(Person a, Person b) {
  return a.birthday.compareTo(b.birthday);
 }

 /**
  * Método que muestra por pantalla la edad que supere la que se le pase por
  * parámetro
  * 
  * @param roster - List<Person> - Objetos de tipo lista con todos sus elementos
  * @param age    - int - Valor de una edad concreta
  */
 public static void printPersonsOlderThan(List<Person> roster, int age) {
  for (Person p : roster) {
   if (p.getAge() >= age) {
    p.printPerson();
   }
  }
 }

 /**
  * Método que muestra por pantalla la edad que supere la que se le pase por
  * parámetro dentro de un parámetros establecidos por sus parámetros
  * 
  * @param roster
  * @param low
  * @param high
  */
 public static void printPersonsWithinAgeRange(List<Person> roster, int low, int high) {
  for (Person p : roster) {
   if (low <= p.getAge() && p.getAge() < high) {
    p.printPerson();
   }
  }
 }

 /**
  * Método de Clase
  * 
  * Imprime los valores después de comprobarlos mediante la llamada a un método
  * de la interface 'CheckPerson'
  * 
  * @param roster - List<Person> - Lista de objetos de tipo Persona
  * @param tester - Interface CheckPerson - Implementa el método test con un
  *               objeto Persona
  */
 public static void printPersons(List<Person> roster, CheckPerson tester) {
  for (Person p : roster) {
// tester.test(p) → Método de la interface - Devuelve si el objeto es de tipo Person o no
   if (tester.test(p)) {
    p.printPerson();
   }
  }
 }

 /**
  * Método de Clase
  * 
  * Crea una lista de objetos de tipo Person los cuales , cada objeto almacena
  * una serie de valores predeterminados
  * 
  * @return - List<Person> - Lista de objetos Person con valores preestablecidos
  */
 public static List<Person> createRoster() {

  List<Person> roster = new ArrayList<>();
  roster.add(new Person("Fred", IsoChronology.INSTANCE.date(1980, 6, 20), Person.Sex.MALE, "fred@example.com"));
  roster.add(new Person("Jane", IsoChronology.INSTANCE.date(1990, 7, 15), Person.Sex.FEMALE, "jane@example.com"));
  roster.add(new Person("George", IsoChronology.INSTANCE.date(1991, 8, 13), Person.Sex.MALE, "george@example.com"));
  roster.add(new Person("Bob", IsoChronology.INSTANCE.date(2000, 9, 12), Person.Sex.MALE, "bob@example.com"));
  return roster;
 }
}
```

* Invocación de una ``Expresión Lambda``

```java
/**
 * Clase Main
 * 
 * @author RVS
 */
public class Main {

 public static void main(String[] args) {

// Instanciación e invocación del método 'printPersons(Objeto de tipo List<Person> , Invocación de la clase con el método test implementado)'
  Person.printPersons(Person.createRoster(), new CheckPersonEligibleForSelectiveService());

// Implementamos la "interface CheckPerson" en la propia invocación del método de la clase Person en una clase anónima y así devolviéndole al método printPersons() la nueva implementación de la funcionalidad creada dentro del bloque de código del cuerpo del método de la interface test(Person p)
//                                                    
// Con este sistema nos ahorramos crear la clase CheckPersonEligibleForSelectiveService
//                                                    
//                                               Clase Anónima
//                                                    ↓
//                                                    ↓
  Person.printPersons(Person.createRoster(), new CheckPerson() {
   /**
    * Método de la Interface
    * Implementada en la misma llamada al método desde una clase anónima
    */
   @Override
   public boolean test(Person p) {
// Implementación "in situ" del método 'test' con la condición de búsqueda
    return p.getGender() == Person.Sex.MALE && p.getAge() > 18 && p.getAge() <= 25;
   }
  });

// La misma funcionalidad usando una Expresión Lambda
// 
// Clase
//   ↓  Método de Clase
//   ↓        ↓              Método que devuelve una List<Person>
//   ↓        ↓                ↓
  Person.printPersons(Person.createRoster(),
  //      Objeto Person
  //        ↓   Objeto.Método de Instancia
  //        ↓           ↓
  //        ↓           ↓          Clase.Enum.Atributo
  //        ↓           ↓            ↓     ↓   ↓
    (Person p) -> p.getGender() == Person.Sex.MALE 
  // Condición de búsqueda
    && p.getAge() >= 18 
    && p.getAge() <= 25);
 }
}
```
