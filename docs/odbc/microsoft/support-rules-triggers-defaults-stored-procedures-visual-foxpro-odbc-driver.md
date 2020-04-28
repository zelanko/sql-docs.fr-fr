---
title: Prise en charge des règles, des déclencheurs, des valeurs par défaut et des procédures stockées | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2fcf8e7c80b2712313cba81199489dc7cb06dce0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301136"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Prise en charge des règles, des déclencheurs, des valeurs par défaut et des procédures stockées (pilote ODBC Visual FoxPro)
Vous ne pouvez pas créer des règles, des déclencheurs, des valeurs par défaut ou des procédures stockées Visual FoxPro à l’aide du pilote ODBC Visual FoxPro. Toutefois, votre application peut interagir avec les règles, les déclencheurs, les valeurs par défaut ou les procédures stockées existants lors de l’insertion, de la mise à jour ou de la suppression de données Visual FoxPro stockées dans une base de données.  
  
 Le tableau suivant répertorie les commandes et les fonctions Visual FoxPro prises en charge par le pilote ODBC Visual FoxPro lorsque les commandes ou fonctions existent dans des règles, des déclencheurs, des valeurs par défaut ou des procédures stockées.  
  
 Si votre application interagit avec des données dont les règles, les déclencheurs, les valeurs par défaut ou les procédures stockées appellent d’autres commandes ou fonctions Visual FoxPro, le pilote génère une erreur. Pour obtenir la liste des commandes et fonctions non prises en charge par le pilote, consultez [commandes et fonctions Visual FoxPro non prises en charge](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) .  
  
> [!TIP]  
>  Si vous souhaitez insérer du code conditionnel dans vos règles, déclencheurs ou procédures stockées qui déterminent les commandes à exécuter quand il est appelé par le pilote, vous pouvez utiliser la fonction **version ()** . La fonction **version ()** retourne « * \<version *du pilote ODBC Visual FoxPro> » lorsqu’elle est appelée par le pilote.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Commandes et fonctions Visual FoxPro prises en charge dans les règles, les déclencheurs, les valeurs par défaut et les procédures stockées  
  
||||  
|-|-|-|  
|$, Opérateur|%, opérateur|Commande &|  
|Commande && |* Commande|=, Commande|  
  
## <a name="a"></a>Un  
  
||||  
|-|-|-|  
|Fonction ABS ()|ACOPY () (fonction)|Ajouter une TABLE, commande|  
|ADATABASES () (fonction)|ADBOBJECTS () (fonction)|AERROR () (fonction)|  
|ADEL () (fonction)|AELEMENT () (fonction)|ALEN () (fonction)|  
|AFIELDS () (fonction)|AINS () (fonction)|ALTER TABLE, commande SQL|  
|Fonction ALIAS ()|ALLTRIM () (fonction)|Ajouter à partir d’une commande de tableau|  
|Opérateur AND|Ajouter une commande|Ajouter un mémo, commande|  
|Ajouter à partir de la commande|Ajouter une commande générale|ASCAN () (fonction)|  
|Commande APPEND PROCEDUREs|ASC (), fonction|ASUBSCRIPT () (fonction)|  
|Fonction ASIN ()|Fonction ASORt ()|Fonction ATAN ()|  
|Fonction AT ()|Fonction AT_C ()|ATCLINE () (fonction)|  
|Fonction ATC ()|ATCC () (fonction)|AUSED () (fonction)|  
|ATLINE () (fonction)|Fonction ATN2 ()||  
|MOYENNE, commande|Fonction ACOS ()||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|Commande BEGIN TRANSACTION|BETWEEN () (fonction)|BITNOT () (fonction)|  
|BITCLEAR () (fonction)|BITLSHIFT () (fonction)|BITSET () (fonction)|  
|BITOR () (fonction)|BITRSHIFT () (fonction)|Commande vide|  
|Fonction BITTEst ()|BITXOR () (fonction)||  
|BOF (), fonction|BITAND () (fonction)||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|Commande CALCULATE|Fonction CANDIDATe ()|Fonction CHR ()|  
|CDX (), fonction|Fonction CEILING ()|Commandes fermer|  
|CHRTRAN () (fonction)|CHRTRANC () (fonction)|COPIER les INDEX, commande|  
|CMONTH () (fonction)|CONTINUER, commande|COPIER la STRUCTURE-commande étendue|  
|Commande de copie de procédures|COPIER la STRUCTURE, commande|COPIER dans la commande|  
|COPIER la BALIse, commande|COPIER dans le tableau, commande|CPCONVERT () (fonction)|  
|COS () (fonction)|COUNT (commande)|CTOD () (fonction)|  
|CPCURRENT () (fonction)|CPDBF () (fonction)|CURSORSETPROP () (fonction)|  
|CTOT () (fonction)|CURSORGETPROP () (fonction)||  
|Fonction COURBUREal ()|CDOW () (fonction)||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|Fonction DATE ()|Fonction DATETIME ()|Fonction DAY ()|  
|Fonction DBC ()|Fonction DBF ()|DBGETPROP () (fonction)|  
|Fonction DBUSed ()|DELETE, commande SQL|Commande DELETE|  
|DELETE TAG, commande|Fonction DELETEd ()|Fonction décroissant ()|  
|Fonction DIFFERENCE ()|DIMENSION, commande|Fonction d’insuffisant ()|  
|DMY () (fonction)|CASSE... Commande ENDCASE|Commande DO|  
|DO WHILE... Commande ENDDO|Fonction DOW ()|DTOC () (fonction)|  
|Fonction DTOR ()|Fonction DTO ()|DTOT () (fonction)|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|EMPTY (), fonction|Fonction EVALUATe ()|EXIT (commande)|  
|ERROR () (fonction)|EXP () (fonction)||  
|Commande END TRANSACTION|Fonction EOF ()||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|FCOUNT () (fonction)|FDATE () (fonction)|FIELD (), fonction|  
|Fonction FILE ()|Fonction FILTER ()|FLDLIST () (fonction)|  
|Fonction troupeau ()|FLOOR (), fonction|FLUSH (commande)|  
|POUR... Commande ENDFOR|Fonction FOR ()|Fonction FOUND ()|  
|Commande FREE TABLE|FSIZE (), fonction|FTIME () (fonction)|  
|Fonction FULLPATH ()|Commande de fonction|FV (), fonction|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|Commande GATHER|GETNEXTMODIFIED () (fonction)|Commande GO/GOTO|  
|GETFLDSTATE () (fonction)|GOMONTH () (fonction)||  
|GETCP () (fonction)|GETENV () (fonction)||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|HEADer () (fonction)|Fonction HOUR ()|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE () (fonction)|IF... Commande ENDIF|Fonction IIF ()|  
|INDBC () (fonction)|INDEX, commande|Fonction inList ()|  
|Commande INSERT-SQL|Fonction INT ()|ISALPHA () (fonction)|  
|ISBLANK () (fonction)|ISDIGIT () (fonction)|ISEXCLUSIVE () (fonction)|  
|ISLEADBYTE () (fonction)|ISLOWER () (fonction)|ISNULL () (fonction)|  
|Fonction ISREADONLY ()|ISUPPER () (fonction)||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Fonction KEY ()|Keymatch (), fonction||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|Fonction LEFT ()|LEFTC () (fonction)|LIKEC () (fonction)|  
|LENC () (fonction)|LIKE () (fonction)|LOCK () (fonction)|  
|Commande locale|Rechercher, commande|Fonction LOOKUP ()|  
|Fonction LOG ()|LOG10 (), fonction|Fonction LTRIM ()|  
|Fonction LOWER ()|Commande LPARAMETERS||  
|LUPDATE () (fonction)|LEN (), fonction||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|_MLINE variable de mémoire système|Fonction MAX ()|Fonction MDX ()|  
|MJA () (fonction)|MEMLINES () (fonction)|Fonction MESSAGE ()|  
|Fonction MIN ()|Fonction MINUTE ()|MLINE () (fonction)|  
|Fonction MOD ()|Fonction MONTH ()|MTON () (fonction)|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NDX () (fonction)|Fonction NORMALIZe ()|Opérateur NOT|  
|Remarque (commande)|NTOM () (fonction)|NVL () (fonction)|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|Fonction se produit ()|OLDVAL () (fonction)|Commande en cas d’erreur|  
|Commande ON KEY|ON () (fonction)|OUVRIR une base de données, commande|  
|Opérateur OR|ORDER () (fonction)|OS () (fonction)|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Commande PACK|Fonction Parameters ()|Fonction PAYMENT ()|  
|PARAMÈTRES, commande|Fonction principale ()|Commande privée|  
|Fonction PI ()|Fonction PROGRAM ()|Fonction NOMPROPRE ()|  
|Commande de procédure|Fonction PV ()||  
|Commande publique|Fonctions PADL () &#124; PADR () &#124; PADC ()||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|Fonction RAND ()|Fonction RAT ()|RATC () (fonction)|  
|RATLINE () (fonction)|Commande de rappel|RECCOUNT () (fonction)|  
|RECNO () (fonction)|RECSIZE () (fonction)|Commande régionale|  
|RELATION () (fonction)|Commande REMOVE TABLE|Replace, commande|  
|REMPLACER à partir d’une commande de tableau|Fonction REPLICATE ()|Nouvelle tentative, commande|  
|Return, commande|Fonction RIGHT ()|RIGHTC () (fonction)|  
|RLOCK () (fonction)|Commande ROLLBACK|Fonction ROUND ()|  
|RTOD () (fonction)|RTRIM () (fonction)||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|RECHERCHER... Commande ENDSCAN|Commande nuages de points|Fonction SEC ()|  
|Fonction SECONDS ()|Commande SEEK|Fonction SEEK ()|  
|SÉLECTIONNER une commande|SELECT () (fonction)|SELECT-commande SQL|  
|SET BLOCKSIZE, commande|SET CARRY, commande|SET CENTURY, commande|  
|SET COLLATE, commande|SET DATABASE, commande|SET DATE, commande|  
|DÉFINIR la commande par défaut|SET DELETED, commande|SET EXACT, commande|  
|SET EXCLUSIVE, commande|DÉFINIR la commande FDOW|Commande SET FIELDs|  
|DÉFINIR la commande de filtre|DÉFINIR la commande fixe|DÉFINIR la commande FULLPATH|  
|DÉFINIR la commande FWEEK|Commande SET HOURs|SET INDEX, commande|  
|SET LOCK, commande|DÉFINIR la commande de multiverrouillages|DÉFINIR la commande NEAR|  
|DÉFINIR la commande NOCPTRANS|DÉFINIR la commande NOTIFY|SET NULL, commande|  
|SET OPTIMIZE, commande|Commande SET ORDER|SET PATH, commande|  
|Commande SET PROCEDURE|DÉFINIR la RELATION, commande|SET RELATION OFF (commande)|  
|SET REPROCESS, commande|SET SKIP, commande|DÉFINIR la commande UDFPARMS|  
|SET UNIQUE, commande|SET VOLUME, commande|SET () (fonction)|  
|SETFLDSTATE () (fonction)|SIGN () (fonction)|SIN () (fonction)|  
|SKIP (commande)|Commande de tri|Fonction SPACE ()|  
|Fonction SQRT ()|Commande STORE|Fonction STR ()|  
|Fonction STRCONV ()|STRTRAN () (fonction)|Fonction STUFF ()|  
|STUFFC () (fonction)|SUBSTR () (fonction)|SUBSTRC () (fonction)|  
|SUM, commande|Fonction SYS (2011)||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TALLY variable de mémoire système|_TRIGGERLEVEL variable de mémoire système|TAGCOUNT () (fonction)|  
|TABLEUPDATE () (fonction)|TAG () (fonction)|Fonction TARGET ()|  
|TAGNO () (fonction)|TAN (), fonction|Fonction TRIM ()|  
|Fonction TIME ()|TOTAL, commande|TXNLEVEL () (fonction)|  
|TTOC () (fonction)|TTOD () (fonction)||  
|Fonction TYPE ()|TABLEREVERT () (fonction)||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Fonction UNIQUE ()|Commande UNLOCK|UTILISER la commande|  
|Commande UPDATE|Fonction UPPER ()||  
|Fonction USED ()|UPDATE, commande SQL||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|Fonction VAL ()|VERSION () (fonction)||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|Fonction WEEK ()|||  
  
## <a name="y"></a>O  
  
||||  
|-|-|-|  
|Fonction YEAR ()|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Commande ZAP|||
