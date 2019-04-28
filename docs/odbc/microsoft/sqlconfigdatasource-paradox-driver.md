---
title: SQLConfigDataSource (Paradox Driver) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad9c944af33da86e0d4f85769288f4ab7b6c369f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62665341"
---
# <a name="sqlconfigdatasource-paradox-driver"></a>SQLConfigDataSource (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le **SQLConfigDataSource** fonction qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La séquence dans laquelle les champs sont triés.<br /><br /> Lorsque le pilote Paradox est utilisé, la séquence peut être ASCII (par défaut), International, suédois-finnois ou Norvégien-Danois.<br /><br /> La même option est définie en tant que **séquence de classement** dans la boîte de dialogue d’installation.|  
|DBQ|Le nom du fichier de base de données.<br /><br /> La même option est définie en tant que **base de données** dans la boîte de dialogue d’installation.|  
|DEFAULTDIR|La spécification de chemin d’accès au répertoire.|  
|DESCRIPTION|Une description des données dans la source de données.<br /><br /> La même option est définie en tant que **Description** dans la boîte de dialogue d’installation.|  
|DRIVER|La spécification de chemin d’accès à la DLL du pilote.|  
|DRIVERID|Un ID d’entier pour le pilote.<br /><br /> 26 (Paradox 3.x)<br /><br /> 282 (Paradox 4.x)<br /><br /> 538 (Paradox 5.x)|  
|EXCLUSIF|Détermine si la base de données doit être ouvert en mode exclusif (accédé par un seul utilisateur à la fois) ou mode (accédé par plusieurs utilisateurs à la fois) partagé. Peut être true (mode exclusif) ou false (mode partagé).<br /><br /> La même option est définie en tant que **exclusif** dans la boîte de dialogue d’installation.|  
|FIL|Fichier de type Paradox 3.x, Paradox 4.x ou Paradox 5.x|  
|TYPE DE FICHIER|Type de fichier pour le pilote de texte (texte).|  
|PAGETIMEOUT|Spécifie la période de temps, en dixièmes de seconde, une page (si non utilisé) reste dans la mémoire tampon avant d’être supprimés. La valeur par défaut est 600 dixièmes de seconde (60 secondes). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> La même option est définie en tant que **Page Timeout** dans la boîte de dialogue d’installation.|  
|PARADOXNETPATH|Le chemin d’accès complet du répertoire contenant une base de données de verrou Paradox, car il contient le fichier PDOXUSRS.net (dans Paradox 4. *x*) ou le fichier PARADOX.net (dans Paradox 5. *x*). Si le répertoire ne contient pas un de ces fichiers, le pilote Paradox en crée un. Pour plus d’informations sur ces fichiers, consultez la documentation de Paradox.<br /><br /> Avant de sélectionner un répertoire réseau, un nom d’utilisateur Paradox doit être entré.<br /><br /> La même option est définie en tant que **sélectionner un répertoire réseau** dans la boîte de dialogue d’installation.|  
|PARADOXNETSTYLE|Pour le pilote Paradox, le réseau de style à utiliser lors de l’accès aux données Paradox accéder : « 3.x » pour Paradox 3. *x* ou « 4.x » pour Paradox 4. *x* ou 5. *x*. Peut être définie à « 3.x » ou « 4.x » si la version est Paradox 4. *x* ou 5. *x*; si la version est Paradox 3. *x*, le style doit être « 3.x ».<br /><br /> La même option est définie en tant que **Style Net** dans la boîte de dialogue d’installation.|  
|PARADOXUSERNAME|Pour le pilote Paradox, le nom d’utilisateur Paradox.<br /><br /> La même option est définie en tant que **nom d’utilisateur** dans la boîte de dialogue d’installation.|  
|PWD|Mot de passe.<br /><br /> Ce mot clé facultatif et ne sera jamais être écrites dans le fichier par le pilote. Il est utilisé dans un appel à **SQLDriverConnect** contre les fichiers de Paradox sécurisés de mot de passe. Le mot de passe utilisé sera valide à chaque ouverture d’une table. Si aucun mot de passe n’est passé dans la chaîne de connexion, aucun mot de passe n’est établi pour cette table. Si les tables ont des mots de passe différents, plusieurs ne peut pas être ouvert dans la même session, ni si les tables peuvent être jointes.|  
|READONLY|TRUE pour rendre le fichier en lecture seule ; FALSE pour rendre le fichier pas en lecture seule.<br /><br /> La même option est définie en tant que **en lecture seule** dans la boîte de dialogue d’installation.|  
|THREADS|Le nombre de threads d’arrière-plan pour le moteur à utiliser. Cette valeur est 3 et ne peut pas être modifiée.<br /><br /> La même option est définie en tant que **Threads** dans la boîte de dialogue d’installation.|
