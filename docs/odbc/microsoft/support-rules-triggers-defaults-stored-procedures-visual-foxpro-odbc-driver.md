---
title: Prise en charge des règles, des déclencheurs, des valeurs par défaut et des procédures stockées . Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301136"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Prise en charge des règles, des déclencheurs, des valeurs par défaut et des procédures stockées (pilote ODBC Visual FoxPro)
Vous ne pouvez pas créer des règles, des déclencheurs, des valeurs par défaut ou des procédures stockées Visual FoxPro à l’aide du visual FoxPro ODBC Driver. Toutefois, votre application peut interagir avec les règles, les déclencheurs, les valeurs par défaut ou les procédures stockées existantes au fur et à mesure qu’elle insère, met à jour ou supprime les données Visual FoxPro stockées dans une base de données.  
  
 Le tableau suivant répertorie les commandes et les fonctions Visual FoxPro prises en charge par le visual FoxPro ODBC Driver lorsque les commandes ou les fonctions existent dans les règles, les déclencheurs, les valeurs par défaut ou les procédures stockées.  
  
 Si votre application interagit avec les données dont les règles, les déclencheurs, les valeurs par défaut ou les procédures stockées appellent toutes les autres commandes ou fonctions Visual FoxPro, le pilote génère une erreur. Consultez [les commandes et les fonctions Visual FoxPro non soutenues](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) pour une liste de commandes et de fonctions non prises en charge par le conducteur.  
  
> [!TIP]  
>  Si vous souhaitez insérer du code conditionnel dans vos règles, déclencheurs ou procédures stockées qui déterminent les commandes à exécuter lorsqu’il est appelé par le pilote, vous pouvez utiliser la fonction **VERSION( )** . La **version) )** la fonction VERSION retourne "Visual FoxPro ODBC Driver * \<version>" *lorsqu’elle est appelée par le conducteur.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Commandes et fonctions Visuelles FoxPro prises en charge dans les règles, les déclencheurs, les valeurs par défaut et les procédures stockées  
  
||||  
|-|-|-|  
|$ Opérateur|%, opérateur|Commandement &|  
|Commandement && |Commande|Commande|  
  
## <a name="a"></a>Un  
  
||||  
|-|-|-|  
|ABS( ) Fonction|ACOPY( ) Fonction|Commande ADD TABLE|  
|ADATABASES( ) Fonction|ADBOBJECTS( ) Fonction|AERROR( ) Fonction|  
|ADEL( ) Fonction|AELEMENT( ) Fonction|ALEN( ) Fonction|  
|AFIELDS( ) Fonction|AINS( ) Fonction|ALTER TABLE, commande SQL|  
|ALIAS( ) Fonction|ALLTRIM) ) Fonction|APPEND DE ARRAY Command|  
|ET Opérateur|Commandement APPEND|AppEND MEMO Commande|  
|APPEND DE Commande|Commandement GENERAL APPEND|ASCAN) ) Fonction|  
|AppEND PROCEDURES Commande|ASC( ) Fonction|ASUBSCRIPT( ) Fonction|  
|ASIN( ) Fonction|ASORT( ) Fonction|ATAN( ) Fonction|  
|AT( ) Fonction|AT_C) Fonction|ATCLINE( ) Fonction|  
|ATC( ) Fonction|ATCC( ) Fonction|AUSED) ) Fonction|  
|ATLINE( ) Fonction|ATN2) ) Fonction||  
|Commande AVERAGE|ACOS( ) Fonction||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|Commande BEGIN TRANSACTION|BETWEEN( ) Fonction|BITNOT( ) Fonction|  
|BITCLEAR( ) Fonction|BITLSHIFT( ) Fonction|BITSET( ) Fonction|  
|BITOR( ) Fonction|BITRSHIFT( ) Fonction|Commande BLANK|  
|BITTEST( ) Fonction|BITXOR( ) Fonction||  
|BOF) ) Fonction|BITAND( ) Fonction||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|Commande CALCULATE|CANDIDATE( ) Fonction|CHR) ) Fonction|  
|CDX( ) Fonction|CEILING( ) Fonction|Commandes CLOSE|  
|CHRTRAN( ) Fonction|CHRTRANC( ) Fonction|Copy INDEXES Commande|  
|CMONTH( ) Fonction|Commandement CONTINUE|COPY STRUCTURE EXTENDED Command|  
|Copy PROCEDURES Commande|Commande COPY STRUCTURE|COPY TO Commande|  
|Copy TAG Commande|COPY TO ARRAY Command|CPCONVERT( ) Fonction|  
|COS) ) Fonction|Commande COUNT|CTOD( ) Fonction|  
|CPCURRENT( ) Fonction|CPDBF( ) Fonction|CURSORSETPROP( ) Fonction|  
|CTOT) ) Fonction|CURSORGETPROP( ) Fonction||  
|CURVAL( ) Fonction|CDOW( ) Fonction||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|DATE( ) Fonction|DATETIME( ) Fonction|JOUR( ) Fonction|  
|DBC) ) Fonction|DBF) ) Fonction|DBGETPROP( ) Fonction|  
|DBUSED( ) Fonction|DELETE, commande SQL|Commande SUPPRIMER|  
|DELETE TAG, commande|DELETED) ) Fonction|DESCENDING( ) Fonction|  
|DIFFERENCE( ) Fonction|Commande DIMENSION|DISKSPACE( ) Fonction|  
|DMY) ) Fonction|DO CAS ... Commandement ENDCASE|Do Commande|  
|FAITES ALORS ... Commande ENDDO|DOW) ) Fonction|DTOC( ) Fonction|  
|DTOR( ) Fonction|DTOS( ) Fonction|DTOT( ) Fonction|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|FONCTION VIDE( )|ASSESS( ) Fonction|Commande EXIT|  
|ERROR( ) Fonction|EXP) ) Fonction||  
|Commande END TRANSACTION|EOF( ) Fonction||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|FCOUNT( ) Fonction|FDATE( ) Fonction|FIELD( ) Fonction|  
|FILE( ) Fonction|FILTER( ) Fonction|FLDLIST( ) Fonction|  
|FLOCK( ) Fonction|FLOOR( ) Fonction|Commande FLUSH|  
|Pour... Commandement ENDFOR|FOR( ) Fonction|FOUND( ) Fonction|  
|Commande TABLE GRATUITE|FSIZE( ) Fonction|FTIME( ) Fonction|  
|FULLPATH( ) Fonction|Commande FUNCTION|FV) ) Fonction|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|Commande GATHER|GETNEXTMODIFIED( ) Fonction|Commande GO/GOTO|  
|GETFLDSTATE( ) Fonction|GOMONTH( ) Fonction||  
|GETCP) ) Fonction|GETENV) ) Fonction||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|HEADER( ) Fonction|HEURE( ) Fonction|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE( ) Fonction|Si... Commande ENDIF|IIF) ) Fonction|  
|INDBC( ) Fonction|INDEX, commande|INLIST( ) Fonction|  
|INSERT-SQL Command|INT( ) Fonction|ISALPHA( ) Fonction|  
|ISBLANK( ) Fonction|ISDIGIT( ) Fonction|ISEXCLUSIVE( ) Fonction|  
|ISLEADBYTE( ) Fonction|ISLOWER( ) Fonction|ISNULL( ) Fonction|  
|ISREADONLY( ) Fonction|ISUPPER( ) Fonction||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|KEY( ) Fonction|KEYMATCH( ) Fonction||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|LEFT( ) Fonction|LEFTC( ) Fonction|LIKEC) ) Fonction|  
|LENC) ) Fonction|LIKE( ) Fonction|LOCK( ) Fonction|  
|Commandement LOCAL|Commande LOCATE|LOOKUP( ) Fonction|  
|LOG( ) Fonction|LOG10( ) Fonction|LTRIM) ) Fonction|  
|LOWER( ) Fonction|Commandement LPARAMETERS||  
|Fonction LUPDATE( )|LEN) ) Fonction||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|_MLINE Variable de mémoire du système|MAX( ) Fonction|MDX) ) Fonction|  
|MDY( ) Fonction|MEMLINES( ) Fonction|MESSAGE( ) Fonction|  
|MIN( ) Fonction|MINUTE( ) Fonction|MLINE( ) Fonction|  
|MOD( ) Fonction|MONTH( ) Fonction|MTON( ) Fonction|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NDX) ) Fonction|NORMALIZE( ) Fonction|PAS Opérateur|  
|Commande NOTE|NTOM( ) Fonction|NVL) ) Fonction|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OCCURS( ) Fonction|OLDVAL( ) Fonction|Sur LA commande d’ERREUR|  
|Sur LE COMMANDEMENT KEY|ON( ) Fonction|Open DATABASE Commande|  
|OPÉRATEUR OU|ORDER( ) Fonction|OS( ) Fonction|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Commande PACK|PARAMETERS( ) Fonction|PAYMENT( ) Fonction|  
|Commande PARAMETERS|PRIMARY( ) Fonction|Commandement PRIVATE|  
|IP( ) Fonction|PROGRAM( ) Fonction|PROPER( ) Fonction|  
|Commande PROCEDURE|PV) ) Fonction||  
|Commandement PUBLIC|PADL( ) &#124; PADR( ) &#124; PADC) ) Fonctions||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|RAND( ) Fonction|RAT( ) Fonction|RATC( ) Fonction|  
|RATLINE( ) Fonction|Commande RECALL|RECCOUNT( ) Fonction|  
|RECNO( ) Fonction|RECSIZE( ) Fonction|Commandement REGIONAL|  
|RELATION( ) Fonction|Commande DE TABLE REMOVE|Commande REPLACE|  
|REPLACE FROM ARRAY Command|REPLICATE( ) Fonction|Commande RETRY|  
|Commande RETURN|RIGHT( ) Fonction|RIGHTC( ) Fonction|  
|RLOCK) ) Fonction|Commande ROLLBACK|ROUND( ) Fonction|  
|RTOD) ) Fonction|RTRIM) ) Fonction||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|numériser... Commandement ENDSCAN|Commande SCATTER|SEC( ) Fonction|  
|SECONDS( ) Fonction|Commande SEEK|SEEK( ) Fonction|  
|Commande SELECT|SELECT( ) Fonction|Commandement SELECT-SQL|  
|SET BLOCKSIZE, commande|Set CARRY Commande|Set CENTURY Commande|  
|SET COLLATE, commande|Set DATABASE Commande|Set DATE Commande|  
|SET DEFAULT Command|SET DELETED, commande|SET EXACT, commande|  
|SET EXCLUSIVE, commande|Set FDOW Commande|Commande SET FIELDS|  
|SET FILTER Commande|Set FIXED Commande|Set FULLPATH Commande|  
|Set FWEEK Commande|Set HOURS Commande|Set INDEX Commande|  
|Set LOCK Commande|Set MULTILOCKS Commande|Set NEAR Commande|  
|SET NOCPTRANS Commande|SET NOTIFY Commande|SET NULL, commande|  
|Set OPTIMIZE Commande|Set ORDER Commande|SET PATH, commande|  
|Set PROCEDURE Commande|Set RELATION Commande|SET RELATION OFF Commande|  
|SET REPROCESS, commande|Set SKIP Commande|SET UDFPARMS Command|  
|SET UNIQUE, commande|Set VOLUME Commande|SET( ) Fonction|  
|SETFLDSTATE( ) Fonction|SIGN ( ) Fonction|SIN( ) Fonction|  
|Commande SKIP|Commande SORT|SPACE( ) Fonction|  
|SQRT( ) Fonction|Commande STORE|STR( ) Fonction|  
|STRCONV) ) Fonction|STRTRAN( ) Fonction|STUFF( ) Fonction|  
|STUFFC( ) Fonction|SUBSTR( ) Fonction|SUBSTRC( ) Fonction|  
|Commande SUM|Fonction SYS(2011)||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TALLY Variable de mémoire du système|_TRIGGERLEVEL variable de mémoire du système|TAGCOUNT( ) Fonction|  
|TABLEUPDATE( ) Fonction|TAG( ) Fonction|TARGET( ) Fonction|  
|TAGNO) ) Fonction|TAN( ) Fonction|TRIM( ) Fonction|  
|TEMPS( ) Fonction|Commande TOTAL|TXNLEVEL( ) Fonction|  
|TTOC) ) Fonction|TTOD( ) Fonction||  
|TYPE( ) Fonction|TABLEREVERT( ) Fonction||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|UNIQUE( ) Fonction|Commande UNLOCK|Commande USE|  
|Mise À JOUR Commande|UPPER( ) Fonction||  
|USED( ) Fonction|UPDATE, commande SQL||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VAL( ) Fonction|VERSION( ) Fonction||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|SEMAINE( ) Fonction|||  
  
## <a name="y"></a>O  
  
||||  
|-|-|-|  
|ANNÉE( ) Fonction|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Commandement ZAP|||
