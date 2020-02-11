---
title: Traduction automatique de données caractères | Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c08a0987e11f25c3f5b535d8d26526db5bb14a38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73779170"
---
# <a name="autotranslation-of-character-data"></a>Traduction automatique de données caractères
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les données de type caractère, telles que les variables de caractères ANSI déclarées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec SQL_C_CHAR ou les données stockées dans à l’aide des types de données **char**, **varchar**ou **Text** , ne peuvent représenter qu’un nombre limité de caractères. Les données caractères stockées à l'aide d'un octet par caractère ne peuvent représenter que 256 caractères. Les valeurs stockées dans les variables SQL_C_CHAR sont interprétées à l'aide de la page de codes ANSI (ACP) de l'ordinateur client. Les valeurs stockées à l’aide des types de données **char**, **varchar**ou **Text** sur le serveur sont évaluées à l’aide de l’ACP du serveur.  
  
 Si le serveur et le client ont tous les deux le même ACP, ils n’ont aucun problème pour interpréter les valeurs stockées dans les objets SQL_C_CHAR, **char**, **varchar**ou **Text** . Si le serveur et le client ont des codes ANSI différents, SQL_C_CHAR données du client peuvent être interprétées comme un caractère différent sur le serveur s’il est utilisé dans les colonnes de **type char**, **varchar**ou **Text** , les variables ou les paramètres. Par exemple, un octet de caractère contenant la valeur 0xA5 est interprété comme le caractère Ñ sur un ordinateur à l’aide de la page de codes 437 et est interprété comme le signe yen (¥) sur un ordinateur exécutant la page de codes 1252.  
  
 Les données Unicode sont stockées à l'aide de deux octets par caractère. Tous les caractères étendus étant couverts par la spécification Unicode, tous les caractères Unicode sont interprétés de la même façon par tous les ordinateurs.  
  
 La fonctionnalité de traduction automatique du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC native client tente de réduire les problèmes de déplacement de données de caractères entre un client et un serveur qui ont des pages de codes différentes. La conversion automatique peut être définie dans la chaîne de connexion de [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), dans la chaîne de configuration de [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)ou lors de la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sources de données pour le pilote ODBC Native Client à l’aide de l’administrateur ODBC.  
  
 Lorsque la conversion automatique est définie sur « non », aucune conversion n’est effectuée sur les données déplacées entre les variables de SQL_C_CHAR sur le client et **** les colonnes de **type char**, **varchar**ou Text [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les variables ou les paramètres d’une base de données. Les modèles binaires peuvent être interprétés différemment sur les ordinateurs client et serveur si les données contiennent des caractères étendus et que les deux ordinateurs ont des pages de codes différentes. Les données seront interprétées de la même façon si les deux ordinateurs ont la même page de codes.  
  
 Lorsque la conversion automatique est définie sur « Oui », [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote ODBC Native Client utilise Unicode pour convertir les données déplacées entre les variables de SQL_C_CHAR sur le client et les colonnes de **type char**, **varchar**ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text** , les variables ou les paramètres d’une base de données :  
  
-   Lorsque des données sont envoyées à partir d’une variable de SQL_C_CHAR sur le client vers une colonne de **type char**, **varchar**ou **Text** , une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] variable ou un paramètre d’une base de données, le pilote ODBC convertit d’abord de SQL_C_CHAR en Unicode à l’aide de l’ACP du client, puis de retour Unicode en caractères à l’aide de l’ACP du serveur.  
  
-   Lorsque des données sont envoyées à partir d’une colonne de **type char**, **varchar**ou **Text** , d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] variable ou d’un paramètre d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une variable de SQL_C_CHAR sur le client, le pilote ODBC native client convertit d’abord le caractère en Unicode à l’aide de l’ACP du serveur, puis de l’Unicode à SQL_C_CHAR à l’aide de l’ACP du client.  
  
 Étant donné que toutes ces conversions sont effectuées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote ODBC Native Client qui s’exécute sur le client, le serveur ACP doit être l’une des pages de codes installées sur l’ordinateur client.  
  
 Le fait d'effectuer les conversions de caractères via Unicode garantit une conversion correcte de tous les caractères qui existent dans les deux pages de codes. Si, toutefois, un caractère existe dans une page de codes mais pas dans une autre, le caractère ne peut pas être représenté dans la page de codes cible. Par exemple, la page de codes 1252 a le symbole de marque déposée (®), tandis que la page de codes 437 ne l'a pas.  
  
 Le paramètre AutoTranslate n'a aucun effet sur ces conversions :  
  
-   Déplacement de données entre des variables de type caractère **** SQL_C_CHAR client et des colonnes, des variables ou des paramètres Unicode NCHAR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , **nvarchar**ou **ntext** dans des bases de données.  
  
-   Déplacement de données entre les variables Unicode SQL_C_WCHAR client et les colonnes de **type**Character, **varchar**ou **Text** , les variables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les paramètres dans les bases de données.  
  
 Les données doivent toujours être converties lorsqu'elles sont déplacées du type caractère vers le type Unicode.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des résultats &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
