---
title: Prise en charge des règles, les déclencheurs, les valeurs par défaut et les procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], stored procedures
- FoxPro ODBC driver [ODBC], commands and functions
- commands for FoxPro ODBC driver [ODBC]
- FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], triggers
- stored procedures [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], rules
- FoxPro commands and functions [ODBC]
- rules [ODBC]
- Visual FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], rules
- functions [ODBC], Visual FoxPro
- default values [ODBC]
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro ODBC driver [ODBC], triggers
- FoxPro ODBC driver [ODBC], stored procedures
- Visual FoxPro commands and functions [ODBC]
ms.assetid: e449de20-d6ca-4902-9f8e-814eb6e86650
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47795998b019df22b01852519f75f6e8d3d274dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655007"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Prise en charge des règles, des déclencheurs, des valeurs par défaut et des procédures stockées (pilote ODBC Visual FoxPro)
Impossible de créer des règles de Visual FoxPro, des déclencheurs, des valeurs par défaut ou des procédures stockées qui utilisent le pilote ODBC Visual FoxPro. Toutefois, votre application peut interagir avec les règles existantes, des déclencheurs, des valeurs par défaut ou des procédures stockées comme elle insère, met à jour ou supprime des données Visual FoxPro stockées dans une base de données.  
  
 Le tableau suivant répertorie les commandes de Visual FoxPro et les fonctions prises en charge par le pilote ODBC Visual FoxPro lorsque les fonctions ou les commandes existent dans les règles, les déclencheurs, les valeurs par défaut ou les procédures stockées.  
  
 Si votre application interagit avec les données dont les règles, les déclencheurs, les valeurs par défaut, ou d’appellent de procédures stockées toutes les autres commandes de Visual FoxPro ou fonctions, le pilote génère une erreur. Consultez [non pris en charge les commandes FoxPro Visual et fonctions](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) pour obtenir la liste des commandes et fonctions non prises en charge par le pilote.  
  
> [!TIP]  
>  Si vous souhaitez insérer du code conditionnel dans les règles, des déclencheurs ou des procédures stockées qui détermine les commandes à exécuter lorsqu’elle est appelée par le pilote, vous pouvez utiliser la **() VERSION** (fonction). Le **() VERSION** fonction retourne « pilote ODBC Visual FoxPro  *\<version >*» lorsqu’elle est appelée par le pilote.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Commandes de Visual FoxPro et fonctions pris en charge dans les règles, les déclencheurs, les valeurs par défaut et les procédures stockées  
  
||||  
|-|-|-|  
|Opérateur de $|Opérateur %|& Commande|  
|& & Commande|* Commande|= Commande|  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|ABS (fonction))|ACOPY (fonction))|AJOUTER des commandes TABLE|  
|ADATABASES (fonction))|ADBOBJECTS (fonction))|À AERROR (fonction))|  
|ADEL (fonction))|AELEMENT (fonction))|ALEN (fonction))|  
|AFIELDS (fonction))|AINS (fonction))|ALTER TABLE, commande SQL|  
|ALIAS (fonction))|ALLTRIM (fonction))|AJOUTER à partir de la commande de tableau|  
|ET l’opérateur|AJOUTER des commandes|AJOUTER des commandes de mémo|  
|AJOUTER à partir de la commande|AJOUTER la commande de général|ASCAN (fonction))|  
|AJOUTER des commandes de procédures|ASC (fonction))|ASUBSCRIPT (fonction))|  
|ASIN (fonction))|ASORT (fonction))|ATAN (fonction))|  
|À la fonction de)|AT_C (fonction))|ATCLINE (fonction))|  
|ATC (fonction))|ATCC (fonction))|AUSED (fonction))|  
|ATLINE (fonction))|ATN2 (fonction))||  
|Commande moyenne|ACOS (fonction))||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|Commande BEGIN TRANSACTION|ENTRE (fonction))|BITNOT (fonction))|  
|BITCLEAR (fonction))|BITLSHIFT (fonction))|BITSET (fonction))|  
|BITOR (fonction))|BITRSHIFT (fonction))|Commande vide|  
|BITTEST (fonction))|BITXOR (fonction))||  
|BOF (fonction))|BITAND (fonction))||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|CALCULER la commande|CANDIDAT (fonction))|CHR (fonction))|  
|CDX (fonction))|CEILING, fonction)|Commandes CLOSE|  
|CHRTRAN (fonction))|CHRTRANC (fonction))|Commande de copie des index|  
|CMONTH (fonction))|Commande CONTINUE|Commande de copie STRUCTURE étendu|  
|Commande de copie de procédures|COPIER la commande STRUCTURE|COPIER dans la commande|  
|COPIER la commande de balise|Copier vers la commande de tableau|CPCONVERT (fonction))|  
|COS () de fonction|Commande COUNT|CTOD (fonction))|  
|CPCURRENT (fonction))|CPDBF (fonction))|CURSORSETPROP (fonction))|  
|CTOT (fonction))|CURSORGETPROP (fonction))||  
|Fonction CURVAL)|CDOW (fonction))||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|DATE (fonction))|DATETIME (fonction))|DAY (fonction))|  
|Od (fonction))|DBF (fonction))|DBGETPROP (fonction))|  
|DBUSED (fonction))|DELETE, commande SQL|Commande DELETE|  
|DELETE TAG, commande|Fonction supprimée)|DÉCROISSANT (fonction))|  
|DIFFÉRENCE (fonction))|Commande DIMENSION|Espace disque (fonction))|  
|DMY (fonction))|PROCÉDEZ COMME CAS... Commande ENDCASE|De commande|  
|DO WHILE... Commande ENDDO|DOW (fonction))|DTOC (fonction))|  
|DTOR (fonction))|DTO (fonction))|DTOT (fonction))|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|Fonction vide)|ÉVALUER la fonction de)|Commande Quitter|  
|ERREUR (fonction))|EXP (fonction))||  
|Commande TRANSACTION de fin|EOF (fonction))||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|FCOUNT (fonction))|FDATE (fonction))|CHAMP (fonction))|  
|FICHIER (fonction))|Fonction de filtre)|FLDLIST (fonction))|  
|TROUPEAU (fonction))|FLOOR (fonction))|Commande FLUSH|  
|FOR... Commande ENDFOR|POUR la fonction)|TROUVÉ (fonction))|  
|Commande TABLE gratuit|FSIZE (fonction))|Ftime, fonction de)|  
|FULLPATH (fonction))|Commande de fonction|VC (fonction))|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|COLLECTER la commande|GETNEXTMODIFIED (fonction))|Commande GO/GOTO|  
|GETFLDSTATE (fonction))|GOMONTH (fonction))||  
|GETCP (fonction))|GETENV (fonction))||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|EN-tête (fonction))|HEURE (fonction))|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE (fonction))|IF... Commande ENDIF|IIF (fonction))|  
|INDBC (fonction))|INDEX, commande|LISTE (fonction))|  
|Commande INSERT-SQL|INT (fonction))|ISALPHA (fonction))|  
|ISBLANK (fonction))|ISDIGIT (fonction))|ISEXCLUSIVE (fonction))|  
|ISLEADBYTE (fonction))|ISLOWER (fonction))|ISNULL (fonction))|  
|ISREADONLY (fonction))|ISUPPER (fonction))||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Fonction de la clé)|KEYMATCH (fonction))||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|Fonction gauche)|LEFTC (fonction))|LIKEC (fonction))|  
|LENC (fonction))|COMME la fonction)|LOCK (fonction))|  
|Commande locale|RECHERCHEZ la commande|LOOKUP (fonction))|  
|LOG (fonction))|LOG10 (fonction))|LTRIM (fonction))|  
|LOWER, fonction)|Commande LPARAMETERS||  
|LUPDATE (fonction))|LEN (fonction))||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|Variable de mémoire système _MLINE|MAX (fonction))|Fonction MDX)|  
|MDY (fonction))|MEMLINES (fonction))|MESSAGE (fonction))|  
|MIN (fonction))|Fonction MINUTE)|MLINE (fonction))|  
|Fonction MOD)|MOIS (fonction))|MTON (fonction))|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NDX (fonction))|NORMALISER (fonction))|PAS d’opérateur|  
|Commande de Remarque|NTOM (fonction))|NVL (fonction))|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|Se produit (fonction))|OLDVAL (fonction))|SUR la commande de l’erreur|  
|SUR la combinaison de touches|SUR la fonction)|Commande de base de données ouverte|  
|OU opérateur|Fonction d’ordre)|Système d’exploitation (fonction))|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Commande PACK|PARAMÈTRES (fonction))|PAIEMENT (fonction))|  
|Commande de paramètres|Fonction principale)|Commande de privé|  
|PI (fonction))|PROGRAMME (fonction))|Fonction appropriée)|  
|Commande de procédure|Fonction va)||  
|Commande publique|() PADL &#124; () PADR &#124; PADC () fonctions||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|Fonction RAND)|RAT (fonction))|RATC (fonction))|  
|RATLINE (fonction))|Commande de rappel|RECCOUNT (fonction))|  
|RECNO (fonction))|RECSIZE (fonction))|Commande régional|  
|RELATION (fonction))|SUPPRIMER la commande TABLE|REMPLACER, commande|  
|REMPLACER à partir de la commande de tableau|RÉPLIQUER (fonction))|Commande de nouvelle tentative|  
|RETOURNER la commande|Fonction RIGHT)|RIGHTC (fonction))|  
|RLOCK (fonction))|Commande de restauration|Fonction ROUND)|  
|RTOD (fonction))|RTRIM (fonction))||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|L’ANALYSE... Commande ENDSCAN|Commande de nuage de points|S (fonction))|  
|SECONDES (fonction))|Commande de recherche|SEEK (fonction))|  
|Sélectionnez la commande|Sélectionnez () (fonction)|Commande SELECT-SQL|  
|SET BLOCKSIZE, commande|SET CARRY, commande|SET siècle, commande|  
|SET COLLATE, commande|Commande de base de données de jeu|Commande DATE SET|  
|JEU de commandes par défaut|SET DELETED, commande|SET EXACT, commande|  
|SET EXCLUSIVE, commande|SET confronté, commande|Commande de jeu de champs|  
|Commande de filtre de jeu|SET, commande fixe|SET FULLPATH, commande|  
|SET FWEEK, commande|Commande des heures définies|INDEX de SET, commande|  
|Commande de verrouillage de jeu|SET MULTILOCKS, commande|DÉFINIR le côté de la commande|  
|SET NOCPTRANS, commande|Commande de notification de jeu|SET NULL, commande|  
|Commande d’optimisation de jeu|Commande de commande SET|SET PATH, commande|  
|Commande de procédure SET|Commande RELATION SET|RELATION de jeu de la commande de désactivation|  
|SET REPROCESS, commande|Définissez la commande Ignorer|SET UDFPARMS, commande|  
|SET UNIQUE, commande|SET VOLUME, commande|SET (fonction))|  
|SETFLDSTATE (fonction))|SIGN (fonction))|SIN (fonction))|  
|Commande Ignorer|Commande de tri|ESPACE (fonction))|  
|SQRT (fonction))|Commande de stockage|STR (fonction))|  
|STRCONV (fonction))|STRTRAN (fonction))|STUFF (fonction))|  
|STUFFC (fonction))|SUBSTR (fonction))|SUBSTRC (fonction))|  
|Commande somme|SYS(2011) (fonction)||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|Variable de mémoire système _TALLY|Variable de mémoire système _TRIGGERLEVEL|TAGCOUNT (fonction))|  
|TABLEUPDATE (fonction))|BALISE (fonction))|CIBLE (fonction))|  
|TAGNO (fonction))|Fonction TAN)|TRIM (fonction))|  
|TIME, fonction)|Commande TOTAL|TXNLEVEL (fonction))|  
|TTOC (fonction))|TTOD (fonction))||  
|TYPE (fonction))|TABLEREVERT (fonction))||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Fonction UNIQUE)|Commande UNLOCK|Utilisez la commande|  
|Commande de mise à jour|Fonction supérieure)||  
|UTILISÉ (fonction))|UPDATE, commande SQL||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VAL (fonction))|VERSION (fonction))||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|WEEK (fonction))|||  
  
## <a name="y"></a>O  
  
||||  
|-|-|-|  
|ANNÉE (fonction))|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Commande ZAP|||
