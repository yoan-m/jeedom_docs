# Alarme DSC, connexion via carte Evaslink

## Présentation

Ce plugin permet d'obtenir l'état d'une alarme DSC

## Configuration

Il faut fournir plusieurs paramètres :

  - l'adresse de la carte Envaslink.

  - le nombre de partition (habituellement 1)

  - le nombre de zones

Un équipement sera créer pour chaque zone, chaque partition et un pour le panel

## Protocole Envaslink

Le plugin utilise les codes TPI mis à disposition par Envisalink pour lire les états et envoyer des commandes

Voici ce qui est disponible

### Zone

Pour chaque zone créée, voici les informations qu'envoie la carte Envisalink

[width="80%",cols="3,^2,^2,10",options="header"]
|=======
|TPI |Signification |Information |Valeur
|601 |Alarm Activated |alarm |1
|602 |Alarm Restored |alarm |0
|603 |Tamper |tamper |1
|604 |Tamper Restored |tamper |0
|605 |Fault |fault |1
|606 |Fault Restored |fault |0
|609 |Open |activity |1
|610 |Restored |activity |0
|=======

Il n'y a pas d'actions pour les zones

### Partition

Pour chaque partition créée, voici les informations qu'envoie la carte Envisalink

[width="80%",cols="3,^2,^2,10",options="header"]
|=======
|TPI |Signification |Information |Valeur
|650 |Ready |status |650
|651 |Not Ready |status |651
|652 |Armed |status |652
|653 |Ready - Force Arming Enabled |status |653
|654 |In Alarm |status |654
|655 |Disarmed |status |655
|656 |Exit Delay in Progress |status |656
|657 |Entry Delay in Progress |status |657
|658 |Keypad Lock-Out |status |658
|659 |Failed to Arm |status |659
|=======

Et voici les actions disponibles

[width="80%",cols="3,^2,^2,10",options="header"]
|=======
|TPI |Signification |Commande |Valeur
|030 |Arm |alarm |030
|031 |Arm - Stay Arm |alarm |031
|032 |Arm - Zero Entry |alarm |032
|033 |Arm - With Code |alarm |033
|040 |Disarm |alarm |040
|=======

### Panel

Pour le panel, voici les informations remontées par Envisalink

[width="80%",cols="3,^2,^2,10",options="header"]
|=======
|TPI |Signification |Information |Valeur
|620 |Duress Alarm |code |1
|621 |Fire Alarm |fire |1
|622 |Fire Alarm restored |fire |0
|623 |Ready - Force Arming Enabled |auxiliary |1
|624 |In Alarm |auxiliary |0
|625 |Disarmed |police |1
|626 |Exit Delay in Progress |police |1
|631 |Smoke/Aux |smoke |1
|632 |Smoke/Aux Restored |smoke |0
|800 |Panel Battery Trouble |battery |1
|801 |Panel Battery Restored |battery |0
|802 |Panel AC Trouble |acpower |1
|803 |Panel AC Restored |acpower |0
|=======

Les actions suivantes sont possible également pour le panel

[width="80%",cols="3,^2,^2,10",options="header"]
|=======
|TPI |Signification |Commande |Valeur
|060 |Trigger Panic Alarm |trigger |030
|=======

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Non, le plugin appelle l'alarme DSC via la carte ethernet Evaslink.
s
## Changelog

[Voir la page dédiée](changelog.md).
