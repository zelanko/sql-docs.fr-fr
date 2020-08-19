---
description: Programme d’administration
title: Programme d’administration | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- administration program [ODBC]
- ODBC administrator [ODBC]
ms.assetid: a6c8248a-7a01-42e7-aaed-99dc94d50028
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5aef5e00fa69fd1f699228b2c0ac82b2a8041962
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429031"
---
# <a name="administration-program"></a>Programme d’administration
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 Un programme d’administration, l’administrateur ODBC, est inclus dans le kit de développement logiciel (SDK) SDK Windows/MDAC. Ce programme et peuvent être redistribués par les utilisateurs du kit de développement logiciel (SDK). En outre, les développeurs peuvent écrire leurs propres programmes d’administration. En règle générale, les développeurs écrivent leurs propres programmes d’administration uniquement s’ils souhaitent conserver un contrôle total sur la configuration de la source de données, ou s’ils configurent les sources de données directement à partir d’une application qui agit comme un programme d’administration. Par exemple, un programme de feuille de calcul peut permettre aux utilisateurs d’ajouter et d’utiliser des sources de données au moment de l’exécution.  
  
 Le programme d’administration charge d’abord la DLL du programme d’installation. Il appelle ensuite les fonctions dans la DLL du programme d’installation pour effectuer les tâches suivantes :  
  
-   **Ajoutez, modifiez ou supprimez des sources de données de manière interactive.** Le programme d’administration peut appeler **SQLManageDataSources**, **SQLCreateDataSource**ou **SQLConfigDataSource**.  
  
     **SQLManageDataSources** affiche une boîte de dialogue avec laquelle l’utilisateur peut ajouter, modifier ou supprimer des sources de données et spécifier des options de suivi. Cette fonction est appelée lorsque la DLL du programme d’installation est appelée directement à partir du panneau de configuration. **SQLCreateDataSource** affiche une boîte de dialogue avec laquelle l’utilisateur peut uniquement ajouter des sources de données. **SQLConfigDataSource** passe l’appel directement à la dll d’installation du pilote.  
  
     Dans tous les cas, la DLL du programme d’installation appelle **ConfigDSN** dans la dll d’installation du pilote pour ajouter, modifier ou supprimer la source de données. La DLL d’installation du pilote peut inviter l’utilisateur à fournir des informations supplémentaires.  
  
-   **Ajoutez, modifiez ou supprimez des sources de données en mode silencieux.** Le programme d’administration appelle **SQLConfigDataSource** dans la dll du programme d’installation et lui transmet un handle de fenêtre null, le nom d’une source de données à ajouter, modifier ou supprimer, ainsi qu’une liste de valeurs pour le registre. La DLL du programme d’installation appelle **ConfigDSN** dans la dll d’installation du pilote pour ajouter, modifier ou supprimer la source de données.  
  
-   **Ajoutez, modifiez ou supprimez une source de données par défaut.** La source de données par défaut est la même que toute autre source de données, sauf que son nom est default. Elle est ajoutée, modifiée ou supprimée de la même façon que n’importe quelle autre source de données.
