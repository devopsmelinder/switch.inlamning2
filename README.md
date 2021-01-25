# switch.inlamning2
SPEL- Switch inlamning2

package com.company;


public class Main {

    String characterName;
    String weaponName;
    int weaponDamage;
    int hp;
    static int hammerMaximumDamage = 20;
    static int hammerMinimumDamage = 10;

    static int hammer = (int) (Math.random() * ((hammerMaximumDamage - hammerMinimumDamage) + 1)) + hammerMinimumDamage;
    static int magicWandMaximumDamage = 50;
    static int magicWandMinimumDamage = 0;
    static int magicWand = (int) (Math.random() * (magicWandMaximumDamage - magicWandMinimumDamage));

    public Main(String charName, int wDamage, int health, String wName) {
        characterName = charName;
        weaponName = wName;
        weaponDamage = wDamage;
        hp = health;
    }

    public void beingAttacked(String defenderName, String attackerName, int attackerWeaponDamage, String attackerWeaponName) {
        if (hp <= 0 || attackerWeaponName == "Excalibur") {
            System.err.println("YOU CANNOT ATTACK");
        } else {
            /* System.err.println("WILD " + attackerName + " APPEARS!"); */
            System.out.println(attackerName + " STRIKES " + defenderName + " WITH A " + attackerWeaponName + " IT DOES " + attackerWeaponDamage + " DAMAGE");
            hp = (hp - attackerWeaponDamage);
            System.out.println(defenderName + " HAS " + hp + " REMAINING HEALTH! ");
            if (hp <=0) { System.out.println(defenderName + " died");}
        }
    }

    public static void searchWeapon(String weaponName) {

        String weaponHolder ="none";
        String goodGuy = "Hammer";
        String spider = "JAVA";
        String evilGuy = "Magic Wand";
        String JAVA = "spider";
        if (weaponName.equals(goodGuy)) {weaponHolder = "goodGuy";}
        if (weaponName.equals(spider)) {weaponHolder = "spider";}
        if (weaponName.equals(evilGuy)) {weaponHolder = "evilGuy";}
        if (weaponName.equals(JAVA)) {weaponHolder = "JAVA";}


        switch (weaponName) {
            case "Hammer":
                System.out.println("You searched for Hammer. The hammer is held by " + weaponHolder);
                break;
            case "Magic Wand":
                System.out.println("You searched for MagicWand. The MagicWand is held by " + weaponHolder);

                break;
            case "JAVA":
                System.out.println("You searched for JAVA. JAVA is held by " + weaponHolder);

                break;
            case "Excalibur":
                System.out.println("You searched for Excalibur. The Excalibur is held by " + weaponHolder);


            default:
                System.out.println("The weapon " +"\"" + weaponName + "\""  +" you searched for is not in our database or held by any characters please search again!!");
                break;
        }
    }


    public void changeWeapon2(String characterName, String wName) {
        weaponName = "Excalibur";
        System.out.println(characterName + " has changed weapon to " + weaponName);

    }

    public void drinkingHealingPotion() {
        int healingPotion = 20;
        hp = hp + healingPotion;
        System.out.println(characterName + " GAINED " + healingPotion + " HEALTH BY DRINKING A HEALING POTION");
        System.out.println(characterName + " NOW HAS A HEALTH OF " + hp);

    }



    public static void main(String[] args) {
        Main goodGuy = new Main("The Beast", hammer, 100, "Hammer");
        Main evilGuy = new Main("Ja'far", magicWand, 80, "Magic Wand");
        Main spider = new Main("spider",999, 999, "SATECHI");
        Main SATECHI = new Main("JAVA", 10, 20, "JAVA" );

        goodGuy.beingAttacked(goodGuy.characterName, evilGuy.characterName, evilGuy.weaponDamage, evilGuy.weaponName);
        evilGuy.beingAttacked(evilGuy.characterName, goodGuy.characterName, goodGuy.weaponDamage, goodGuy.weaponName );
        goodGuy.drinkingHealingPotion();
        evilGuy.drinkingHealingPotion();



        searchWeapon("JAVA");
        searchWeapon("Hammer");
        searchWeapon("Magic Wand");
        searchWeapon("devopsmelinder");

        SATECHI.changeWeapon2("SATECHI", "excalibur" );

  }}
