---
title: À l’aide de SQLConfigDatasource avec le pilote ODBC pour Oracle | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa5f1ecf9f3100480081e3744fc7d280a4da282b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088034"
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>Utilisation de SQLConfigDatasource avec le pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le tableau suivant répertorie valide **SQLConfigDatasource** paramètres pour le pilote Microsoft ODBC pour Oracle, version 1.0 (Msorcl10.dll) et le pilote Microsoft ODBC pour Oracle, version 2.0 (Msorcl32.dll).  
  
> [!NOTE]  
>  Le pilote Msorcl10.dll (version 1.0) prend en charge tous les paramètres à l’exception **Server**. Le pilote Msorcl32.dll (version 2.0 et versions ultérieures) prend en charge tous les paramètres.  
  
 Certains paramètres sont ignorés par le pilote, mais sont acceptés par **SQLConfigDatasource**. Y compris de ces paramètres dans la chaîne de connexion ODBC sont la seule façon, qu'ils seront acceptés au moment de l’exécution. Un paramètre ignoré n’est pas stocké dans le Registre lorsque **SQLConfigDatasource** crée la source de données.  
  
 Dans le tableau suivant, *A/N* signifie toute chaîne d’alphanumériques valide jusqu'à la longueur maximale autorisée. *Max Len* (longueur maximale) est la longueur maximale autorisée de la chaîne acceptée par le paramètre, y compris le caractère terminateur de chaîne.  
  
|Paramètre|Max Len|Valeur par défaut|Valeurs valides|Description|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65535|1 000|Jusqu'à 65 535 octets de taille de mémoire tampon d’extraction minimale|  
|CatalogCap|2|1|0 ou 1|Si 1, les identificateurs nonquoted sera converti en majuscules dans le catalogue des fonctions.|  
|ConnectString|128|""|R/N|Chaîne de connexion. Méthode nécessaire de spécifier le nom du serveur avec le pilote Msorcl10.dll.|  
|Description|256|""|R/N|Description.|  
|DSN|33|""|R/N|Nom de source de données.|  
|GuessTheColDef|4|0|R/N|Retourne une valeur différente de zéro pour les colonnes sans mise à l’échelle définie par Oracle.|  
|NumberFloat|2|""|0 ou 1|Si 0, les colonnes de type FLOAT sont traitées comme SQL_FLOAT. La valeur 1, les colonnes de type FLOAT sont traitées comme SQL_DOUBLE.|  
|PWD|30|""|R/N|Mot de passe.|  
|RDOSupport|2|""|0 ou 1|Permet de RDO appeler des procédures Oracle.|  
|Notes|2|0|0 ou 1|Inclure des notes dans les fonctions de catalogue.|  
|RowLimit|4|""|entre 0 et 99|Nombre maximal de lignes retournées par une instruction SELECT. Une chaîne de longueur zéro indique qu’aucune limite n’est appliquée.|  
|Serveur|128|""|R/N|Nom du serveur Oracle.|  
|SynonymColumns|2|1|0 ou 1|Inclure les synonymes dans SQLColumns.|  
|SystemTable|2|""|0 ou 1|Si 0, les tables système ne s’affichera pas. La valeur 1, les tables système seront affichera.|  
|TranslationDLL|33|""|R/N|Nom du fichier .dll de traduction.|  
|TranslationName|33|""|R/N|Nom de la traduction.|  
|TranslationOption|33|""|R/N|Option de traduction.|  
|TxnCap|2|""|R/N|Capable de la transaction. Si 0, le pilote indique qu’il ne prend pas en charge les transactions. Si 1, le pilote indique qu’il est capable d’effectuer des transactions.|  
|UID|30|""|R/N|Nom d’utilisateur.|
