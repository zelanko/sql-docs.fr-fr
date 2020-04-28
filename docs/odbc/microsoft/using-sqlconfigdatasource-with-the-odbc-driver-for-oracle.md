---
title: Utilisation de SQLConfigDatasource avec ODBC Driver for Oracle | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292769"
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>Utilisation de SQLConfigDatasource avec le pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le tableau suivant répertorie les paramètres de **SQLConfigDatasource** valides pour Microsoft ODBC Driver for Oracle, version 1,0 (Msorcl10. dll) et Microsoft ODBC Driver for Oracle, version 2,0 (msorcl32. dll).  
  
> [!NOTE]  
>  Le pilote Msorcl10. dll (version 1,0) prend en charge tous les paramètres à l’exception de **Server**. Le pilote msorcl32. dll (version 2,0 et ultérieure) prend en charge tous les paramètres.  
  
 Certains paramètres sont ignorés par le pilote, mais sont acceptés par **SQLConfigDatasource**. L’inclusion de ces paramètres dans la chaîne de connexion ODBC est la seule manière dont ils seront acceptés au moment de l’exécution. Un paramètre ignoré ne sera pas stocké dans le registre lorsque **SQLConfigDatasource** crée la source de données.  
  
 Dans le tableau suivant, *A/N* représente toute chaîne alphanumérique valide jusqu’à la longueur maximale autorisée. *Max Len* (longueur maximale) est la longueur de chaîne maximale autorisée acceptée par le paramètre, y compris le caractère de fin de chaîne.  
  
|Paramètre|Longueur max.|Valeur par défaut|Valeurs valides|Description|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65535|1 000|Taille minimale de la mémoire tampon d’extraction jusqu’à 65535 octets|  
|CatalogCap|2|1|0 ou 1|Si la valeur est 1, les identificateurs sans guillemets sont convertis en majuscules dans les fonctions de catalogue.|  
|ConnectString|128|""|A/N|Chaîne de connexion. Méthode requise pour spécifier le nom du serveur avec le pilote Msorcl10. dll.|  
|Description|256|""|A/N|Description.|  
|DSN|33|""|A/N|Nom de la source de données.|  
|GuessTheColDef|4|0|A/N|Retourne une valeur différente de zéro pour les colonnes sans échelle définie par Oracle.|  
|NumberFloat|2|""|0 ou 1|Si la valeur est 0, les colonnes FLOAT sont traitées comme des SQL_FLOAT. Si la valeur est 1, les colonnes FLOAT sont traitées comme SQL_DOUBLE.|  
|PWD|30|""|A/N|Password.|  
|RDOSupport|2|""|0 ou 1|Permet à RDO d’appeler des procédures Oracle.|  
|Notes|2|0|0 ou 1|Inclure des notes dans les fonctions de catalogue.|  
|RowLimit|4|""|0 à 99|Nombre maximal de lignes retournées par une instruction SELECT. Une chaîne de longueur nulle indique qu’aucune limite n’est appliquée.|  
|Server (Serveur)|128|""|A/N|Nom du serveur Oracle.|  
|SynonymColumns|2|1|0 ou 1|Inclure des SYNONYMEs dans SQLColumns.|  
|SystemTable|2|""|0 ou 1|Si la valeur est 0, les tables système ne sont pas affichées. Si la condition est 1, les tables système sont affichées.|  
|TranslationDLL|33|""|A/N|Nom de la traduction. dll.|  
|TranslationName|33|""|A/N|Nom de la traduction.|  
|TranslationOption|33|""|A/N|Option de traduction.|  
|TxnCap|2|""|A/N|Compatibilité des transactions. Si la valeur est 0, le pilote signale qu’il ne prend pas en charge les transactions. Si la capacité est 1, le pilote signale qu’il est capable d’effectuer des transactions.|  
|Identificateur d’utilisateur|30|""|A/N|Nom d’utilisateur.|
