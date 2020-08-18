---
description: SQLConfigDataSource (pilote dBASE)
title: SQLConfigDataSource (pilote dBASE) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], dBASE Driver
ms.assetid: 19909902-054c-4e19-9c06-a212aace13fe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 23e734c5aafc903e210eea18f002f4c5e8d7a456
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411955"
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Séquence dans laquelle les champs sont triés.<br /><br /> La séquence peut être : ASCII (valeur par défaut) ou international.<br /><br /> Cela définit la même option que la **séquence de classement** dans la boîte de dialogue de configuration.|  
|DEFAULTDIR|Spécification du chemin d’accès au répertoire.|  
|DELETED|Pour le pilote dBASE, spécifie si les lignes marquées comme supprimées peuvent être récupérées ou positionnées sur. Si la valeur est 1, les lignes supprimées ne sont pas affichées. Si la valeur est 0, les lignes supprimées sont traitées de la même façon que les lignes non supprimées.<br /><br /> Cela définit la même option que **afficher les lignes supprimées** dans la boîte de dialogue d’installation.|  
|Description|Description des données dans la source de données.<br /><br /> Cela définit la même option que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|Spécification du chemin d’accès à la DLL du pilote.|  
|DRIVERID|ID d’entier du pilote.<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5,0)|  
|FIL|Type de fichier dBase III, dBase IV ou dBase 5|  
|PAGETIMEOUT|Spécifie la durée, en dixièmes de seconde, pendant laquelle une page (si elle n’est pas utilisée) reste dans la mémoire tampon avant d’être supprimée. La valeur par défaut est 600 dixièmes de seconde (60 secondes). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Cela définit la même option que le **délai d’attente** de la page dans la boîte de dialogue d’installation.|  
|READONLY|TRUE pour rendre le fichier accessible en lecture seule ; FALSe pour que le fichier ne soit pas en lecture seule.<br /><br /> Cela permet de définir la même option en **lecture seule** dans la boîte de dialogue d’installation.|  
|STATISTICS|Pour le pilote dBASE, détermine si les statistiques sur la taille de la table sont approximatives. Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Cela définit la même option que le **nombre de lignes approximatif** dans la boîte de dialogue d’installation.|  
|THÈMES|Nombre de threads d’arrière-plan à utiliser par le moteur. Cette valeur est 3 et ne peut pas être modifiée.<br /><br /> Cela définit la même option que les **Threads** dans la boîte de dialogue d’installation.|
