---
description: SQLConfigDataSource (pilote de fichier texte)
title: SQLConfigDataSource (pilote de fichier texte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 400b83d382140d4661b103e24449f14ecdfda43d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411865"
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (pilote de fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|CHARACTERSET|Pour le pilote de texte, OEM ou ANSI.|  
|COLNAMEHEADER|Pour le pilote de texte, indique si le premier enregistrement de données spécifie les noms de colonne. TRUE ou FALSe.|  
|DEFAULTDIR|Spécification du chemin d’accès au répertoire.|  
|Description|Description des données dans la source de données.<br /><br /> Cela définit la même option que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|Spécification du chemin d’accès à la DLL du pilote.|  
|DRIVERID|ID d’entier du pilote. 27 (texte)|  
|EXTENSIONS|Répertorie les extensions de nom de fichier des fichiers texte sur la source de données.<br /><br /> Cela définit la même option que la **liste des extensions** dans la boîte de dialogue d’installation.|  
|FIL|Texte du type de fichier|  
|FILETYPE|Type de fichier pour le pilote de texte (texte).|  
|FORMAT|Pour le pilote de texte, peut être multiple, TABDELIMITED, CSVDELIMITED (par une virgule) ou délimité () (par le caractère spécial spécifié entre parenthèses). Le caractère spécial est un caractère de longueur et peut être au format caractère, décimal ou hexadécimal.|  
|MAXSCANROWS|Nombre de lignes à analyser lors de la définition du type de données d’une colonne en fonction des données existantes.<br /><br /> Pour le pilote Text, vous pouvez entrer un nombre compris entre 1 et 32767 pour le nombre de lignes à analyser. Toutefois, la valeur par défaut sera toujours 25. (Un nombre en dehors de la limite renverra une erreur.)<br /><br /> Cela définit la même option que **lignes à analyser** dans la boîte de dialogue d’installation.|  
|READONLY|TRUE pour rendre le fichier accessible en lecture seule ; FALSe pour que le fichier ne soit pas en lecture seule.<br /><br /> Cela permet de définir la même option en **lecture seule** dans la boîte de dialogue d’installation.|
