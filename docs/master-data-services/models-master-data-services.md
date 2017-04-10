---
title: "Mod&#232;les (services de donn&#233;es de r&#233;f&#233;rence) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles [Master Data Services], à propos des modèles"
  - "modèles [Master Data Services]"
ms.assetid: 9f862a3d-25ab-41e9-b833-1db99959e825
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Mod&#232;les (services de donn&#233;es de r&#233;f&#233;rence)
  Les modèles constituent le niveau d'organisation des données le plus élevé dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Un modèle définit la structure des données dans votre solution de gestion des données de référence. Un modèle contient les objets suivants :  
  
-   Entités  
  
-   Attributs et groupes d'attributs  
  
-   Hiérarchies explicites et dérivées  
  
-   Collections  
  
 Les modèles organisent la structure de vos données de référence. Votre [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] implémentation peut avoir un ou plusieurs modèles que chaque groupe comme types de données. En général, les données de référence peuvent figurer dans l'une des quatre catégories suivantes : personnes, lieux, choses ou concepts. Par exemple, vous pouvez créer un modèle Product pour contenir des données relatives à un produit ou un modèle Customer pour contenir des données relatives à un client.  
  
 Vous pouvez affecter aux utilisateurs et groupes l'autorisation d'afficher et de mettre à jour des objets dans le modèle. Si vous ne donnez pas d'autorisation sur le modèle, il n'est pas affiché.  
  
 À tout moment, vous pouvez créer des copies des données de référence dans un modèle. Ces copies sont appelées versions.  
  
 Lorsque vous avez défini un modèle dans un environnement de test, vous pouvez le déployer, avec ou sans les données correspondantes, de l'environnement de test vers un environnement de production. Vous n'avez ainsi plus besoin de recréer vos modèles dans votre environnement de production.  
  
## Relations entre les modèles et les autres objets  
 Un modèle contient des entités. Les entités contiennent des attributs, des hiérarchies explicites et des collections. Les attributs peuvent être contenus dans des groupes d'attributs. Les attributs basés sur un domaine existent lorsqu'une entité sert d'attribut à une autre entité.  
  
 Cette image montre les relations entre les objets dans un modèle.  
  
 ![Objets dans un modèle Master Data Services](../master-data-services/media/mds-conc-model-circles.gif "Objets dans un modèle Master Data Services")  
  
> [!NOTE]  
>  Les hiérarchies dérivées sont également des objets de modèle, mais ils ne figurent pas dans l'image. Les hiérarchies dérivées sont dérivées des relations d'attributs basés sur un domaine qui existent entre les entités. Consultez [dérivée hiérarchies & #40 ; Master Data Services & #41 ;](../master-data-services/derived-hierarchies-master-data-services.md) Pour plus d’informations.  
  
 Les données de référence sont les données contenues dans les objets de modèle. Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les données de référence sont stockées en tant que membres dans une entité.  
  
 Objets de modèle sont conservées dans le **Administration système** zone fonctionnelle de le [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] l’interface utilisateur.  
  
## Exemple de modèle  
 Dans l'exemple suivant, les objets dans le modèle Product regroupent logiquement les données relatives au produit.  
  
 ![Exemple de modèle de produit Master Data](../master-data-services/media/mds-conc-model.gif "Exemple de modèle de produit Master Data")  
  
 D'autres modèles courants figurent ci-dessous :  
  
-   Accounts, qui peut inclure des entités, telles que les comptes de bilans, les comptes de résultats, les statistiques et le type de compte.  
  
-   Customer, qui peut inclure des entités, telles que le sexe, l'éducation, la profession et l'état civil.  
  
-   Geography, qui peut inclure des entités, telles que les codes postaux, villes, comtés, états, provinces, régions, territoires, pays et continents.  
  
## Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créer un modèle pour organiser vos données de référence.|[Créer un modèle & #40 ; Master Data Services & #41 ;](../master-data-services/create-a-model-master-data-services.md)|  
|Modifier le nom d'un modèle existant.|[Modifier le modèle & #40 ; Master Data Services & #41 ;](../master-data-services/edit-model-master-data-services.md)|  
|Supprimer un modèle existant.|[Supprimer un modèle & #40 ; Master Data Services & #41 ;](../master-data-services/delete-a-model-master-data-services.md)|  
  
## Contenu connexe  
  
-   [Vue d’ensemble de Master Data Services & #40 ; MDS & #41 ;](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Entités & #40 ; Master Data Services & #41 ;](../master-data-services/entities-master-data-services.md)  
  
-   [Attributs & #40 ; Master Data Services & #41 ;](../master-data-services/attributes-master-data-services.md)  
  
-   [Déploiement de modèles & #40 ; Master Data Services & #41 ;](../master-data-services/deploying-models-master-data-services.md)  
  
-   [Autorisations d’objet modèle & #40 ; Master Data Services & #41 ;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  