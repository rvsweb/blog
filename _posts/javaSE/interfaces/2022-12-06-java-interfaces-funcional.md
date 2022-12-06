---
layout: single
title: Java - Interfaz Funcional
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
  - java-interface
page_css: 
  - /assets/css/mi-css.css
---

## Interfaces

* Especifica el código de criterios de búsqueda con una expresión lambda

* Interfaz Funcional → Cualquier interfaz que contiene solo un MÉTODO ABSTRACTO

* Interfaz Funcional → Puede contener uno o mas métodos predeterminados o métodos estáticos

* Interfaz Funcional → Contiene solo un método abstracto , puede omitir el nombre de ese método cuando lo implemente

* Para hacerlo en lugar de usar una expresión de clase anónima se usa una ``expresión lambda`` que se resalta en la siguiente invocación del método

## Ejemplo

```java
/**
 * Clase Concreta
 * 
 * @date 5 dic 2022 20:39:13
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
  * @date 5 dic 2022 20:39:29
  * 
  * @author RVS
  *
  */
 public enum Sex {
  MALE, FEMALE
 }

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
  * Metodo de Instancia
  * 
  * @return - int - calcula la edad mediante el año actual hasta el numero de
  *         años almacenados en birthday
  */
 public int getAge() {
  return birthday.until(IsoChronology.INSTANCE.dateNow()).getYears();
 }

 /**
  * Metodo de Instancia
  * 
  * Muestra los valores 'name' y la edad del objeto Person que sea instanciado en
  * ese momento
  */
 public void printPerson() {
  System.out.println(name + ", " + this.getAge());
 }

 /**
  * 
  * @return
  */
 public Sex getGender() {
  return gender;
 }

 /**
  * 
  * @return
  */
 public String getName() {
  return name;
 }

 /**
  * 
  * @return
  */
 public String getEmailAddress() {
  return emailAddress;
 }

 /**
  * 
  * @return
  */
 public LocalDate getBirthday() {
  return birthday;
 }

 /**
  * Metodo de Clase
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
  * Metodo que muestra por pantalla la edad que supere la que se le pase por
  * parametro
  * 
  * @param roster - List<Person> - Objetos de tipo lista con todos sus elementos
  * @param age    - int - Valor de una edad concreta
  */
 public static void printPersonsOlderThanBeta(List<Person> roster, int age) {
  for (Person p : roster) {
   if (p.getAge() >= age) {
    p.printPerson();
   }
  }
 }

 /**
  * Metodo que muestra por pantalla la edad que supere la que se le pase por
  * parametro dentro de un parametros establecidos por sus parametros
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
  * Metodo de Clase
  * 
  * Imprime los valores despues de comprobarlos mediante la llamada a un metodo
  * de la interface 'CheckPerson'
  * 
  * @param roster - List<Person> - Lista de objetos de tipo Persona
  * @param tester - Interface CheckPerson - Implementa el metodo test con un
  *               objeto Persona
  */
 public static void printPersons(List<Person> roster, CheckPerson tester) {
  for (Person p : roster) {
// tester.test(p) → Metodo de la interface - Devuelve si el objeto es de tipo Person o no
   if (tester.test(p)) {
    p.printPerson();
   }
  }
 }

 /**
  * Metodo de Clase
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

```java
  Person.printPersons(Person.createRoster(),
    (Person p) -> p.getGender() == Person.Sex.MALE 
    && p.getAge() >= 18 
    && p.getAge() <= 25);
```
