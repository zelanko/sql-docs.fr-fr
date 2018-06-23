---
title: Ce que&#39;nouveauté dans Analysis Services et Business Intelligence | Documents Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 81dc5c82b8b034556ab4eb69c9f9ca377f641c43
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040466"
---
# <a name="what39s-new-in-analysis-services-and-business-intelligence"></a>Ce que&#39;nouveauté dans Analysis Services et Business Intelligence
  À l’exception du composant ajouté prenant en charge les rapports Power View sur les modèles multidimensionnels, [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] est identique à la version précédente.  
  
 Pour plus d’informations sur les autres [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] les produits et technologies qui sont différents dans cette version, consultez [Nouveautés de SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
## <a name="updates-to-design-tool-installation"></a>Mises à jour concernant l'installation de l'outil de conception  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] pour Business Intelligence (SSDT-BI), anciennement Business Intelligence Development Studio (BIDS), permet de créer des modèles Analysis Services, des rapports Reporting Services et des packages Integration Services. Téléchargez SSDT-BI à partir des emplacements suivants :  
  
-   [Télécharger SSDT-BI pour Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Télécharger SSDT-BI pour Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 Si vous avez installé une version antérieure de SSDT-BI ou BIDS sur votre ordinateur, la version plus récente est installée côte à côte à la version antérieure. Il est habituel d'exécuter des versions précédentes et plus récentes des outils de conception sur une même station de travail afin de pouvoir modifier les projets et les solutions liés à des versions spécifiques du serveur.  
  
> [!NOTE]  
>  Il existe plusieurs sites de téléchargement de la version Visual Studio 2012 et Visual Studio 2013 de SSDT. La plupart ne comprennent pas les modèles de projet BI. En cliquant sur les liens ci-dessus, vous obtiendrez la version appropriée. Vous saurez que vous disposez de la version de SSDT-BI correcte si vous voyez le dossier des modèles de projet Business Intelligence. Ce dossier contient les modèles de projet pour Analysis Services, Reporting Services et Integration Services. Selon la manière dont vous avez installé SSDT-BI, vous verrez également un modèle de projet supplémentaire pour les bases de données SQL Server.  
  
 ![Modèles Nouveau projet dans SSDT](media/ssdt-biprojects.png "Modèles Nouveau projet dans SSDT")  
  
## <a name="features-recently-added-power-view-for-multidimensional-models"></a>Fonctionnalités récemment ajoutées : Power View pour les modèles multidimensionnels  
 La possibilité de créer des rapports Power View sur des modèles multidimensionnels a été initialement introduite dans la mise à jour cumulative 4 de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1. La fonctionnalité Power View pour les modèles multidimensionnels est maintenant incluse dans le cadre de [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
 **Rapport Power View pour un modèle multidimensionnel**  
  
 ![Rapport Power View](media/powerviewreport-wn.gif "rapport Power View")  
  
 Ce composant aide les entreprises à optimiser les investissements BI existants en utilisant les modèles multidimensionnels (également appelés des « cubes OLAP ») avec les derniers outils de création de rapports clients. Selon les types de données du modèle multidimensionnel, les utilisateurs peuvent facilement créer une variété de visualisations dynamiques à partir des tables et des matrices, notamment des graphiques en bulles et des cartes géographiques. Désormais, les modèles multidimensionnels prennent également en charge les requêtes utilisant des expressions DAX (Data Analysis Expressions).  
  
 Power View pour les modèles multidimensionnels nécessite la fonction intégrée de création de rapports Power View dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (en mode SharePoint). Les autres versions de Power View, notamment le complément Power View dans Excel 2013, ne prennent pas en charge les modèles multidimensionnels.  
  
 Pour en savoir plus, consultez [Power View pour les modèles multidimensionnels](http://msdn.microsoft.com/library/dn140246.aspx).  
  
  