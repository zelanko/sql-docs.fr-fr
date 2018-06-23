---
title: L’octroi d’autorisations de base de données de processus | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: c309ca3781bea3594c6d7e8d1b912730371635e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152728"
---
# <a name="granting-process-database-permissions"></a>Attribution de l'autorisation de traiter la base de données
  Après avoir installé une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], tous les membres du rôle d'administrateur de serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans cette instance disposent d'autorisations sur le serveur pour exécuter n'importe quelle tâche dans l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Par défaut, aucun autre utilisateur n'est autorisé à administrer ou afficher des objets dans l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Un membre du rôle d'administrateur de serveur peut octroyer aux utilisateurs l'accès administratif sur le serveur en les faisant membres du rôle. Un membre du rôle d'administrateur de serveur peut également accorder à des utilisateurs un accès plus limité en leur octroyant des autorisations d'administration ou d'accès limitées ou complètes au niveau de la base de données. Les autorisations administratives limitées incluent les autorisations de traiter ou de lire la définition au niveau de la base de données, du cube ou de la dimension.  
  
 Dans les tâches de cette rubrique, vous allez définir le rôle de sécurité Process Database Objects, qui confère à ses membres l'autorisation de traiter tous les objets de base de données, mais ne les autorise pas à afficher des données dans la base de données.  
  
## <a name="defining-a-process-database-objects-security-role"></a>Définition du rôle de sécurité Process Database Objects  
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Rôles** , puis cliquez sur **Nouveau rôle** pour ouvrir le Concepteur de rôle.  
  
2.  Activez la case à cocher **Traiter la base de données** .  
  
3.  Dans la fenêtre Propriétés, modifiez la **nom** propriété pour ce nouveau rôle en `Process Database Objects Role`.  
  
     ![Concepteur de rôle](../../2014/tutorials/media/l10-security-1.png "Concepteur de rôle")  
  
4.  Cliquez sur l'onglet **Adhésion** du Concepteur de rôles et cliquez sur **Ajouter**.  
  
5.  Entrez les comptes d'utilisateur de domaine ou de groupe Windows qui seront membres de ce rôle. Cliquez sur **Vérifier les noms** pour vérifier les informations de compte, puis cliquez sur **OK**.  
  
6.  Cliquez sur l'onglet **Cubes** du Concepteur de rôles.  
  
     Notez que les membres de ce rôle sont autorisés à traiter cette base de données, mais n'ont pas l'autorisation d'accéder aux données du cube du didacticiel de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , ni d'accès Cube/Extraction local, comme le montre l'image suivante.  
  
     ![Onglet cubes du Concepteur de rôle](../../2014/tutorials/media/l10-security-2.png "onglet Cubes du Concepteur de rôle")  
  
7.  Cliquez sur l'onglet **Dimensions** du Concepteur de rôles.  
  
     Notez que les membres de ce rôle ont les autorisations nécessaires pour traiter tous les objets de dimension de cette base de données et, par défaut, ont les autorisations de lecture pour accéder à chaque objet de dimension dans la base de données du didacticiel de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
8.  Dans le menu **Générer** , cliquez sur **Déployer Analysis Services Tutorial**.  
  
     Au terme de cette procédure, vous avez défini et déployé le rôle de sécurité Process Database Objects. Après le déploiement d'un cube vers l'environnement de production, les administrateurs du cube déployé peuvent ajouter des utilisateurs à ce rôle, ce qui leur permet de déléguer des responsabilités de traitement à des utilisateurs spécifiques.  
  
> [!NOTE]  
>  Un projet complet pour la leçon 10 est disponible en téléchargeant et en installant les exemples mis à jour. Pour plus d’informations, consultez [Installer les exemples de données et de projets pour le didacticiel sur la modélisation multidimensionnelle Analysis Services](install-sample-data-and-projects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles et autorisations &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  