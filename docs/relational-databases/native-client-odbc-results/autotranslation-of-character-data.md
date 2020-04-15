---
title: Autotranslation des données de caractères (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a8672f748af8d643fa39038be030efa5d434dc8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297879"
---
# <a name="autotranslation-of-character-data"></a>Traduction automatique de données caractères
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les données de caractère, telles que les variables de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] caractères ANSI déclarées avec des SQL_C_CHAR ou des données stockées à l’aide de **l’omble,** **du varchar**ou des types de données **textuelles,** ne peuvent représenter qu’un nombre limité de caractères. Les données caractères stockées à l'aide d'un octet par caractère ne peuvent représenter que 256 caractères. Les valeurs stockées dans les variables SQL_C_CHAR sont interprétées à l'aide de la page de codes ANSI (ACP) de l'ordinateur client. Les valeurs stockées à l’aide de types de données **char,** **varchar**ou **texte** sur le serveur sont évaluées à l’aide de l’ACP du serveur.  
  
 Si le serveur et le client ont le même ACP, alors ils n’ont aucun problème à interpréter les valeurs stockées dans SQL_C_CHAR, **char,** **varchar,** ou des objets **texte.** Si le serveur et le client ont des ACP différents, puis SQL_C_CHAR données du client peuvent être interprétées comme un personnage différent sur le serveur si elle est utilisée dans les colonnes, variables ou paramètres **de char,** **varchar**ou **texte.** Par exemple, un byte de caractère contenant la valeur 0xA5 est interprété comme le personnage sur un ordinateur à l’aide de la page de code 437 et est interprété comme le signe de yen () sur un ordinateur exécutant la page de code 1252.  
  
 Les données Unicode sont stockées à l'aide de deux octets par caractère. Tous les caractères étendus étant couverts par la spécification Unicode, tous les caractères Unicode sont interprétés de la même façon par tous les ordinateurs.  
  
 La fonction AutoTranslate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du conducteur native ODBC tente de minimiser les problèmes de déplacement des données de caractère entre un client et un serveur qui ont des pages de code différentes. AutoTranslate peut être réglé dans la chaîne de connexion de [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), dans la chaîne de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md), ou lors de la configuration des sources de données pour le pilote Native Client ODBC à l’aide de l’administrateur ODBC.  
  
 Lorsque AutoTranslate est configuré en «non», aucune conversion n’est effectuée sur les données déplacées entre SQL_C_CHAR variables sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le client et **l’omble,** **varchar**, ou des colonnes **de texte,** des variables ou des paramètres dans une base de données. Les modèles binaires peuvent être interprétés différemment sur les ordinateurs client et serveur si les données contiennent des caractères étendus et que les deux ordinateurs ont des pages de codes différentes. Les données seront interprétées de la même façon si les deux ordinateurs ont la même page de codes.  
  
 Lorsque AutoTranslate est configuré [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en «oui», le pilote Native Client ODBC utilise Unicode pour convertir les données déplacées entre SQL_C_CHAR variables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le client et **l’omble,** **varchar**, ou des colonnes **de texte,** des variables ou des paramètres dans une base de données:  
  
-   Lorsque les données sont envoyées à partir d’une variable SQL_C_CHAR sur le client à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une colonne de **char,** **varchar,** ou **texte,** variable, ou paramètre dans une base de données, le pilote ODBC convertit d’abord de SQL_C_CHAR à Unicode en utilisant l’ACP du client, puis d’Unicode de retour au personnage en utilisant l’ACP du serveur.  
  
-   Lorsque les données sont envoyées à partir d’une **colonne de char,** **varchar,** ou de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texte,** variable, ou paramètre dans une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données à une variable SQL_C_CHAR sur le client, le pilote native Client ODBC convertit d’abord de caractère à Unicode en utilisant l’ACP du serveur, puis d’Unicode de retour à SQL_C_CHAR en utilisant l’ACP du client.  
  
 Étant donné que toutes ces [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conversions sont effectuées par le chauffeur native ODBC exécutant sur le client, le serveur ACP doit être l’une des pages de code installées sur l’ordinateur client.  
  
 Le fait d'effectuer les conversions de caractères via Unicode garantit une conversion correcte de tous les caractères qui existent dans les deux pages de codes. Si, toutefois, un caractère existe dans une page de codes mais pas dans une autre, le caractère ne peut pas être représenté dans la page de codes cible. Par exemple, la page de codes 1252 a le symbole de marque déposée (®), tandis que la page de codes 437 ne l'a pas.  
  
 Le paramètre AutoTranslate n'a aucun effet sur ces conversions :  
  
-   Déplacement des données entre les variables du caractère SQL_C_CHAR client et Unicode **nchar**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **nvarchar**, ou **colonnes ntext,** variables ou paramètres dans les bases de données.  
  
-   Le déplacement des données entre Unicode SQL_C_WCHAR variables clientes et **l’omble**de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] caractère, **le varchar,** ou les colonnes de **texte,** les variables ou les paramètres dans les bases de données.  
  
 Les données doivent toujours être converties lorsqu'elles sont déplacées du type caractère vers le type Unicode.  
  
## <a name="see-also"></a>Voir aussi  
 [Résultats de traitement &#40;&#41;ODBC](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
