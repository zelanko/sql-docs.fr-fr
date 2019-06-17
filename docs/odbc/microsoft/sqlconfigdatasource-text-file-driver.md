---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1635538f69b313a73a24ab1531f8793c7d98741e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62665255"
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (pilote de fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le **SQLConfigDataSource** fonction qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|CHARACTERSET|Pour le pilote de texte, OEM ou ANSI.|  
|COLNAMEHEADER|Pour le pilote de texte, indique si le premier enregistrement de données spécifie les noms de colonnes. La valeur TRUE ou FALSE.|  
|DEFAULTDIR|La spécification de chemin d’accès au répertoire.|  
|DESCRIPTION|Une description des données dans la source de données.<br /><br /> La même option est définie en tant que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|La spécification de chemin d’accès à la DLL du pilote.|  
|DRIVERID|Un ID d’entier pour le pilote. 27 (texte)|  
|EXTENSIONS|Répertorie les extensions de nom de fichier des fichiers texte sur la source de données.<br /><br /> La même option est définie en tant que **liste des Extensions** dans la boîte de dialogue d’installation.|  
|FIL|Type de fichier texte|  
|TYPE DE FICHIER|Type de fichier pour le pilote de texte (texte).|  
|FORMAT|Pour le pilote de texte, peut être FIXEDLENGTH, TABDELIMITED, CSVDELIMITED (par une virgule) ou DELIMITED() (par le caractère spécial spécifié dans les parenthèses). Le caractère spécial est un caractère et peut être au format caractère, décimal ou hexadécimal.|  
|MAXSCANROWS|Le nombre de lignes à analyser lors de la définition de type de données d’une colonne en fonction des données existantes.<br /><br /> Pour le pilote de texte, vous pouvez entrer un nombre compris entre 1 et 32 767 pour le nombre de lignes à analyser ; Toutefois, la valeur toujours par défaut 25. (Un nombre en dehors de la limite retournera une erreur).<br /><br /> La même option est définie en tant que **lignes à balayer** dans la boîte de dialogue d’installation.|  
|READONLY|TRUE pour rendre le fichier en lecture seule ; FALSE pour rendre le fichier pas en lecture seule.<br /><br /> La même option est définie en tant que **en lecture seule** dans la boîte de dialogue d’installation.|
