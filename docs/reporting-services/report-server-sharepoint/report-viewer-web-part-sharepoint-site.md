---
title: "État du composant WebPart Visionneuse de sur un site SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a37ed5efe7c365c601deb95d9fe761d227e7021e
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a>État du composant WebPart Visionneuse de sur un site SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)])

Le composant WebPart Visionneuse de rapports est un composant WebPart personnalisé. Vous pouvez utiliser le composant WebPart pour afficher, naviguer, imprimer et exporter des rapports sur un serveur de rapports au sein d’un site SharePoint. Le composant WebPart Visionneuse de rapports est associé à des fichiers de définition (.rdl) de rapports qui sont traités par un serveur de rapports Microsoft SQL Server Reporting Services. 

Le composant WebPart Visionneuse de rapports plus récent peuvent également des rapports paginé de service déployés sur le serveur de rapports Power BI. Le composant WebPart ne fonctionne pas avec les rapports Power BI.

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>Raison pour laquelle le composant WebPart Visionneuse de rapports est réintroduit

Le composant WebPart Visionneuse de rapports n’était disponible en tant que partie du complément Reporting Services pour les produits SharePoint. Le composant WebPart a été spécifique pour les serveurs de rapports en mode intégré SharePoint. En mode intégré SharePoint a été déconseillé après SQL Server 2016.

À partir de SQL Server 2017, il existe un seul mode d’installation de Reporting Services : **en mode natif**. Vous pouvez l’incorporer tous les types de rapports à l’aide d’une partie de visionneuse de pages web à l’aide du *rs : incorporer = true* paramètre d’URL. L’incorporation des rapports dans les pages SharePoint est un scénario d’intégration demandé par les clients et le composant WebPart Visionneuse de rapports mis à jour permet ce scénario pour les rapports paginés.

Alors que le composant WebPart Visionneuse de pages suffit pour incorporer un rapport paginé dans une page SharePoint, le composant WebPart Visionneuse de rapports mis à jour offre des fonctionnalités supplémentaires.

* Afficher/masquer les boutons de barre d’outils
* Remplacer les valeurs de paramètre de rapport
* Connecter des composants WebPart filtre aux paramètres de rapport

## <a name="download-the-report-viewer-web-part-solution-package"></a>Télécharger le package de solution partie de la visionneuse de rapports web

Le composant WebPart Visionneuse de rapports est disponible sur du Microsoft Download Center.

[Télécharger le package solution du composant WebPart Visionneuse de rapports](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>Considérations et limitations

Les éléments répertoriés sont spécifiques au composant WebPart Visionneuse de rapports mis à jour.

* Le composant WebPart peut uniquement être utilisé sur *classique* pages SharePoint.
* Seuls les rapports (RDL) paginés sont pris en charge pour l’incorporation dans le composant WebPart Visionneuse de rapports. Si vous souhaitez pour incorporer des rapports Power BI ou mobiles, vous pouvez utiliser la *rs : incorporer = true* paramètre d’URL.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer à utiliser le composant WebPart Visionneuse de rapports mis à jour, consultez [déployer le composant WebPart Visionneuse de rapports sur un site SharePoint](deploy-report-viewer-web-part.md).

