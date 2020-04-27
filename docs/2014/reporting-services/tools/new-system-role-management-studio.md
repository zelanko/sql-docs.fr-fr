---
title: Nouveau rôle système (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4d9227136ba3bd1526f8ec04476d6dc5d61ca41f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66100178"
---
# <a name="new-system-role-management-studio"></a>Nouveau rôle système (Management Studio)
  Utilisez cette page pour créer une définition de rôle au niveau système. Une définition de rôle système spécifie un ensemble de tâches au niveau système qui s'appliquent à l'ensemble du serveur de rapports.  
  
> [!NOTE]  
>  Les définitions de rôles sont utilisées uniquement sur un serveur de rapports qui s'exécute en mode natif. Si le serveur de rapports est configuré pour l'intégration SharePoint, cette page n'est pas disponible.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de la définition de rôle. Un nom de définition de rôle doit être unique dans l'espace de noms du serveur de rapports. Le nom doit contenir un caractère alphanumérique au minimum. Il peut également comporter des espaces et quelques symboles. N'utilisez pas les caractères suivants dans le nom :  
  
 ; ? : \@ & = +, $/*\< >  
  
 " /  
  
 **Description**  
 Fournit une description qui explique l'utilisation du rôle et énumère les éléments pris en charge par ce dernier.  
  
 **Tâche**  
 Sélectionnez les tâches au niveau système qui peuvent être effectuées par ce rôle. Vous ne pouvez pas créer de tâches ou modifier les tâches existantes qui sont prises en charge par [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Vous ne pouvez pas choisir des tâches au niveau élément pour la définition d'un rôle système.  
  
 **Description de la tâche**  
 Affiche une description de la tâche qui énumère les opérations ou les autorisations prises en charge par cette dernière.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du serveur de rapports dans Management Studio accessible par la touche F1](report-server-in-management-studio-f1-help.md)   
 [Définitions de rôles](../security/role-definitions.md)  
  
  
