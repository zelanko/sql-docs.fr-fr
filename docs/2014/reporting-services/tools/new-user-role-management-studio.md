---
title: Nouveau rôle d’utilisateur (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b40fa294cb682746fe1b69a5fb03bf841d8e334
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66100131"
---
# <a name="new-user-role-management-studio"></a>Nouveau rôle d'utilisateur (Management Studio)
  Utilisez cette page pour créer une définition de rôle au niveau élément. Une définition de rôle au niveau élément est une collection nommée de tâches qui énumère les tâches qu'un utilisateur peut effectuer sur des dossiers, des rapports, des modèles, des ressources et des sources de données partagées. Le rôle Visiteur prédéfini est un exemple de définition de rôle au niveau élément qui identifie les types d'actions dont un utilisateur final de rapports peut avoir besoin pour naviguer entre des dossiers et afficher des rapports.  
  
 Les définitions de rôles sont destinées à être peu nombreuses. La plupart des organisations n'en requièrent que quelques-unes. Toutefois, si les définitions de rôles prédéfinies sont insuffisantes, vous pouvez les modifier ou en créer de nouvelles.  
  
> [!NOTE]  
>  Les définitions de rôles sont utilisées uniquement sur un serveur de rapports qui s'exécute en mode natif. Si le serveur de rapports est configuré pour l'intégration SharePoint, cette page n'est pas disponible.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de la définition de rôle. Un nom de définition de rôle doit être unique dans l'espace de noms du serveur de rapports. Le nom doit contenir un caractère alphanumérique au minimum. Il peut également comporter des espaces et quelques symboles. N'utilisez pas les caractères suivants dans le nom :  
  
 ; ? : \@ & = + , $ / * \< >  
  
 " /  
  
 **Description**  
 Entrez une description qui explique l'utilisation du rôle et énumère les éléments pris en charge par ce dernier.  
  
 **Tâche**  
 Sélectionnez les tâches réalisables par ce rôle. Vous ne pouvez pas créer de tâches ou modifier les tâches existantes qui sont prises en charge par [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Seules les tâches au niveau élément peuvent être utilisées dans une définition de rôle au niveau élément.  
  
 **Description de la tâche**  
 Affiche une description de la tâche qui énumère les opérations ou les autorisations prises en charge par cette dernière.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du serveur de rapports dans Management Studio accessible par la touche F1](report-server-in-management-studio-f1-help.md)   
 [Définitions de rôles](../security/role-definitions.md)  
  
  
