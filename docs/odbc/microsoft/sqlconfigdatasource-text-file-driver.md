---
title: SQLConfigDataSource (pilote du fichier texte) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29075f897438208f4627ec2e89d2bbb476e1539d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (pilote du fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le **SQLConfigDataSource** fonction qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé| Description|  
|-------------|-----------------|  
|JEU DE CARACTÈRES|Pour le pilote de texte, OEM ou ANSI.|  
|COLNAMEHEADER|Pour le pilote de texte, indique si le premier enregistrement de données sera spécifient les noms de colonnes. La valeur TRUE ou FALSE.|  
|DEFAULTDIR|La spécification de chemin d’accès au répertoire.|  
|DESCRIPTION|Une description des données dans la source de données.<br /><br /> L’option est définie en tant que même **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|La spécification de chemin d’accès à la DLL du pilote.|  
|DRIVERID|Un ID d’entier pour le pilote. 27 (texte)|  
|EXTENSIONS|Répertorie les extensions de nom de fichier des fichiers texte sur la source de données.<br /><br /> L’option est définie en tant que même **liste d’Extensions** dans la boîte de dialogue d’installation.|  
|FIL|Type de fichier texte|  
|TYPE DE FICHIER|Type de fichier pour le pilote de texte (texte).|  
|FORMAT|Pour le pilote de texte, peuvent être FIXEDLENGTH, TABDELIMITED, CSVDELIMITED (par une virgule) ou DELIMITED() (par le caractère spécial spécifié dans les parenthèses). Le caractère spécial est un caractère et peut être au format décimal ou hexadécimal de caractère.|  
|MAXSCANROWS|Le nombre de lignes à analyser lors de la définition du type de données d’une colonne en fonction des données existantes.<br /><br /> Pour le pilote de texte, vous pouvez entrer un nombre compris entre 1 et 32 767 pour le nombre de lignes à analyser ; Toutefois, la valeur toujours par défaut est 25. (Un nombre en dehors de la limite retournera une erreur).<br /><br /> L’option est définie en tant que même **lignes à analyser** dans la boîte de dialogue d’installation.|  
|READONLY|TRUE pour rendre le fichier en lecture seule ; Valeur FALSE à rendre le fichier pas en lecture seule.<br /><br /> L’option est définie en tant que même **en lecture seule** dans la boîte de dialogue d’installation.|
