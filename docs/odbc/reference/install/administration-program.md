---
title: "Programme d’administration | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administration program [ODBC]
- ODBC administrator [ODBC]
ms.assetid: a6c8248a-7a01-42e7-aaed-99dc94d50028
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d2fce2aa391f452286a15aa635e26c52ca96952
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="administration-program"></a>Programme d’administration
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Un programme d’administration, l’administrateur ODBC, est inclus dans le Kit de développement SDK/MDAC. Ce programme et peut être redistribué par les utilisateurs du SDK. En outre, les développeurs peuvent écrire leurs propres programmes d’administration. En règle générale, les développeurs écrire leurs propres programmes d’administration uniquement s’ils veulent conserver un contrôle complet sur la configuration de source de données, ou si elles sont configuration des sources de données directement à partir d’une application qui agit comme un programme d’administration. Par exemple, un programme de feuille de calcul peut-être autoriser les utilisateurs à ajouter, puis utiliser des sources de données en cours d’exécution.  
  
 Le programme d’administration du premier charge de la DLL de programme d’installation. Il appelle ensuite les fonctions dans le programme d’installation de la DLL pour effectuer les tâches suivantes :  
  
-   **Ajouter, modifier ou supprimer des sources de données de manière interactive.** Le programme d’administration peut appeler **SQLManageDataSources**, **SQLCreateDataSource**, ou **SQLConfigDataSource**.  
  
     **SQLManageDataSources** affiche une boîte de dialogue avec laquelle l’utilisateur peut ajouter, modifier, ou supprimer des sources de données et spécifiez les options de suivi ; cette fonction est appelée lorsque le programme d’installation DLL est appelée directement à partir du panneau. **SQLCreateDataSource** affiche une boîte de dialogue avec laquelle l’utilisateur peut uniquement ajouter des sources de données. **SQLConfigDataSource** passe l’appel directement à la DLL d’installation du pilote.  
  
     Dans tous les cas, le programme d’installation DLL appelle **ConfigDSN** dans le programme d’installation du pilote DLL pour ajouter, modifier ou supprimer la source de données. Le programme d’installation du pilote DLL peut inviter l’utilisateur pour plus d’informations.  
  
-   **Ajouter, modifier ou supprimer des sources de données en mode silencieux.** Le programme d’administration appelle **SQLConfigDataSource** dans le programme d’installation DLL et passe il une null handle de fenêtre, le nom d’une source de données à ajouter, modifier ou supprimer et une liste de valeurs du Registre. La DLL du programme d’installation appelle **ConfigDSN** dans le programme d’installation du pilote DLL pour ajouter, modifier ou supprimer la source de données.  
  
-   **Ajouter, modifier ou supprimer une source de données par défaut.** La source de données par défaut est le même que toute autre source de données, à ceci près que son nom est la valeur par défaut. Il est ajouté, modifié ou supprimé de la même manière que toute autre source de données.
