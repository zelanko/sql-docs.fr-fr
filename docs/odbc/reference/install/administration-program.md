---
title: Programme d’administration (en anglais seulement) Microsoft Docs
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
ms.openlocfilehash: d8a2a8363371d6f6c3644c2b7b49aa77644d496e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306640"
---
# <a name="administration-program"></a>Programme d’administration
> [!NOTE]  
>  En commençant par Windows XP et Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous ne devez installer explicitement ODBC que sur les versions antérieures de Windows.  
  
 Un programme d’administration, l’administrateur de l’ODBC, est inclus dans le SDK Windows SDK/MDAC. Ce programme et peut être redistribué par les utilisateurs de la SDK. En outre, les développeurs peuvent écrire leurs propres programmes d’administration. En général, les développeurs n’écrivent leurs propres programmes d’administration que s’ils veulent conserver un contrôle complet sur la configuration des sources de données, ou s’ils configurent les sources de données directement à partir d’une application qui agit comme un programme d’administration. Par exemple, un programme de feuilles de calcul peut permettre aux utilisateurs d’ajouter puis d’utiliser des sources de données au moment de l’exécution.  
  
 Le programme d’administration charge d’abord l’installateur DLL. Il appelle ensuite les fonctions dans l’installateur DLL pour effectuer les tâches suivantes:  
  
-   **Ajouter, modifier ou supprimer les sources de données de manière interactive.** Le programme d’administration peut appeler **SQLManageDataSources**, **SQLCreateDataSource**, ou **SQLConfigDataSource**.  
  
     **SQLManageDataSources** affiche une boîte de dialogue avec laquelle l’utilisateur peut ajouter, modifier ou supprimer des sources de données et spécifier les options de traçage; cette fonction est appelée lorsque l’installateur DLL est invoqué directement à partir du panneau de contrôle. **SQLCreateDataSource** affiche une boîte de dialogue avec laquelle l’utilisateur ne peut ajouter que des sources de données. **SQLConfigDataSource** passe l’appel directement à la configuration du conducteur DLL.  
  
     Dans tous les cas, l’installateur DLL appelle **ConfigDSN** dans la configuration du pilote DLL pour réellement ajouter, modifier ou supprimer la source de données. La configuration du pilote DLL peut inciter l’utilisateur à obtenir des informations supplémentaires.  
  
-   **Ajouter, modifier ou supprimer silencieusement les sources de données.** Le programme d’administration appelle **SQLConfigDataSource** dans l’installateur DLL et lui passe une poignée de fenêtre nulle, le nom d’une source de données à ajouter, modifier ou supprimer, et une liste de valeurs pour le registre. L’installateur DLL appelle **ConfigDSN** dans la configuration du pilote DLL pour réellement ajouter, modifier ou supprimer la source de données.  
  
-   **Ajouter, modifier ou supprimer une source de données par défaut.** La source de données par défaut est la même que toute autre source de données, sauf que son nom est par défaut. Il est ajouté, modifié ou supprimé de la même manière que toute autre source de données.
