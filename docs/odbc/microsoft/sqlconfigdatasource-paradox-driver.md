---
title: SQLConfigDataSource (pilote Paradox) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLConfigDataSource
ms.assetid: 59e84c4e-debe-49d7-b97b-84c736b0c793
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68e60d7ca9c37865c1b265297d24591638a44965
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283929"
---
# <a name="sqlconfigdatasource-paradox-driver"></a>SQLConfigDataSource (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Séquence dans laquelle les champs sont triés.<br /><br /> Lorsque le pilote Paradox est utilisé, la séquence peut être ASCII (par défaut), international, suédois-finnois ou norvégien-danois.<br /><br /> Cela définit la même option que la **séquence de classement** dans la boîte de dialogue de configuration.|  
|DBQ|Nom du fichier de base de données.<br /><br /> Cela définit la même option que **base de données** dans la boîte de dialogue installation.|  
|DEFAULTDIR|Spécification du chemin d’accès au répertoire.|  
|Description|Description des données dans la source de données.<br /><br /> Cela définit la même option que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|Spécification du chemin d’accès à la DLL du pilote.|  
|DRIVERID|ID d’entier du pilote.<br /><br /> 26 (Paradox 3. x)<br /><br /> 282 (Paradox 4. x)<br /><br /> 538 (Paradox 5. x)|  
|Or|Détermine si la base de données est ouverte en mode exclusif (accessible par un seul utilisateur à la fois) ou en mode partagé (accessible par plus d’un utilisateur à la fois). Peut avoir la valeur true (mode exclusif) ou false (mode partagé).<br /><br /> Cela définit la même option qu’en **mode exclusif** dans la boîte de dialogue installation.|  
|FIL|Type de fichier Paradox 3. x, Paradox 4. x ou Paradox 5. x|  
|FILETYPE|Type de fichier pour le pilote de texte (texte).|  
|PAGETIMEOUT|Spécifie la durée, en dixièmes de seconde, pendant laquelle une page (si elle n’est pas utilisée) reste dans la mémoire tampon avant d’être supprimée. La valeur par défaut est 600 dixièmes de seconde (60 secondes). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Cela définit la même option que le **délai d’attente** de la page dans la boîte de dialogue d’installation.|  
|PARADOXNETPATH|Chemin d’accès complet du répertoire contenant une base de données de verrouillage Paradox, car il contient le fichier PDOXUSRS.net (dans Paradox 4.* x*) ou le fichier Paradox.net (dans Paradox 5.* x*). Si le répertoire ne contient pas l’un de ces fichiers, le pilote Paradox en crée un. Pour plus d’informations sur ces fichiers, consultez la documentation relative à Paradox.<br /><br /> Pour pouvoir sélectionner un répertoire réseau, vous devez entrer un nom d’utilisateur Paradox.<br /><br /> Cela définit la même option que **Sélectionner le répertoire réseau** dans la boîte de dialogue d’installation.|  
|QUOI|Pour le pilote Paradox, il s’agit du style d’accès réseau à utiliser lors de l’accès aux données Paradox : « 3. x » pour Paradox 3. *x* ou « 4. x » pour Paradox 4. *x* ou 5. *x*. Peut être défini sur « 3. x » ou « 4. x » si la version est Paradox 4. *x* ou 5. *x*; Si la version est Paradox 3. *x*, le style doit être « 3. x ».<br /><br /> Cela définit la même option que le **style net** dans la boîte de dialogue d’installation.|  
|PARADOXUSERNAME|Pour le pilote Paradox, le nom d’utilisateur Paradox.<br /><br /> Cela définit la même option que le **nom d’utilisateur** dans la boîte de dialogue d’installation.|  
|PWD|Mot de passe.<br /><br /> Il s’agit d’un mot clé facultatif qui n’est jamais écrit dans le fichier par le pilote. Elle est utilisée dans un appel à **SQLDriverConnect** par rapport à des fichiers Paradox sécurisés par mot de passe. Le mot de passe utilisé est valide chaque fois qu’une table est ouverte. Si aucun mot de passe n’est transmis dans la chaîne de connexion, aucun mot de passe n’est établi pour cette table. Si les tables ont des mots de passe différents, plusieurs ne peuvent pas être ouverts au cours de la même session et les tables ne peuvent pas être jointes.|  
|READONLY|TRUE pour rendre le fichier accessible en lecture seule ; FALSe pour que le fichier ne soit pas en lecture seule.<br /><br /> Cela permet de définir la même option en **lecture seule** dans la boîte de dialogue d’installation.|  
|THÈMES|Nombre de threads d’arrière-plan à utiliser par le moteur. Cette valeur est 3 et ne peut pas être modifiée.<br /><br /> Cela définit la même option que les **Threads** dans la boîte de dialogue d’installation.|
