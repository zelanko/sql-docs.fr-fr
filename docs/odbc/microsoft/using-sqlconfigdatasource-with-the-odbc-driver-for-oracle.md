---
title: Utilisation de SQLConfigDatasource avec le pilote ODBC pour Oracle ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], ODBC driver for Oracle
ms.assetid: e535d1ef-aff9-4ae7-a3ed-ef4ca2584289
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 718e444d63e0d4cf3821c0c03eb851732ed5b4e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292769"
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>Utilisation de SQLConfigDatasource avec le pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le tableau suivant répertorie les paramètres **SQLConfigDatasource** valides pour le pilote Microsoft ODBC pour Oracle, la version 1.0 (Msorcl10.dll) et le microsoft ODBC Driver pour Oracle, version 2.0 (Msorcl32.dll).  
  
> [!NOTE]  
>  Le pilote Msorcl10.dll (version 1.0) prend en charge tous les paramètres à l’exception **de Server**. Le pilote Msorcl32.dll (version 2.0 et plus) prend en charge tous les paramètres.  
  
 Certains réglages sont ignorés par le conducteur, mais sont acceptés par **SQLConfigDatasource**. L’inclusion de ces paramètres dans la chaîne de connexion ODBC est la seule façon qu’ils seront acceptés au moment de l’exécution. Un paramètre ignoré ne sera pas stocké dans le registre lorsque **SQLConfigDatasource** crée la source de données.  
  
 Dans le tableau suivant, *A/N* désigne toute chaîne alphanumérique valide jusqu’à la longueur maximale autorisée. *Max Len* (longueur maximale) est la longueur maximale de la chaîne autorisée acceptée par le réglage, y compris le caractère string-terminator.  
  
|Paramètre|Max Len|Valeur par défaut|Valeurs valides|Description|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65535|1 000|Taille minimale de tampon aller chercher jusqu’à 65535 octets|  
|CatalogCap (catalog en)|2|1|0 ou 1|Si 1, les identificateurs non cités seront convertis en majuscules dans les fonctions du catalogue.|  
|ConnectString (connectString)|128|""|A/N|Chaîne de connexion. Méthode requise pour spécifier le nom du serveur avec le pilote Msorcl10.dll.|  
|Description|256|""|A/N|Description.|  
|DSN|33|""|A/N|Nom de source de données.|  
|DevinezTheColDef|4|0|A/N|Retourne une valeur non nulle pour les colonnes sans échelle définie par Oracle.|  
|NumberFloat (en)|2|""|0 ou 1|Si 0, les colonnes FLOAT sont traitées comme SQL_FLOAT. Si 1, les colonnes FLOAT sont traitées comme SQL_DOUBLE.|  
|PWD|30|""|A/N|Password.|  
|RDOSupport (RDOSupport)|2|""|0 ou 1|Permet à RDO d’appeler les procédures Oracle.|  
|Notes|2|0|0 ou 1|Inclure REMARQUE dans les fonctions de catalogue.|  
|RowLimit RowLimit RowLimit RowLim|4|""|0 à 99|Nombre maximum de lignes retournées par une instruction SELECT. Une chaîne de longueur zéro indique qu’aucune limite n’est appliquée.|  
|Serveur|128|""|A/N|Nom du serveur Oracle.|  
|SynonymColumns|2|1|0 ou 1|Inclure SYNONYMs dans SQLColumns.|  
|SystemTable (en)|2|""|0 ou 1|Si 0, les tables système ne seront pas affichées. Si 1, des tables système seront affichées.|  
|TraductionDLL|33|""|A/N|Nom de traduction .dll.|  
|TranslationName (en)|33|""|A/N|Nom de traduction.|  
|TraductionOption|33|""|A/N|Option de traduction.|  
|TxnCap (TxnCap)|2|""|A/N|Transaction capable. Si 0, le conducteur signale qu’il ne prend pas en charge les transactions. Si 1, le conducteur signale qu’il est capable d’effectuer des transactions.|  
|Identificateur d’utilisateur|30|""|A/N|Nom d’utilisateur.|
