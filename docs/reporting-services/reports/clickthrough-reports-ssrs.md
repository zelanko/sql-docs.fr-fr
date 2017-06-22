---
title: "Les rapports générés interactifs (SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clickthrough reports
- customizing clickthrough reports
- clickthrough reports, customizing
ms.assetid: cf2c396e-b0c6-41f9-8c45-ddc8406f7e85
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 55d22d2fd64faef6e913bf226c831546d71665ca
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="clickthrough-reports-ssrs"></a>Rapports générés interactifs (SSRS)
  Dans le Générateur de rapports, un rapport généré interactif est un rapport qui fournit des informations détaillées sur les données contenues dans le rapport principal. Un rapport consultable à l'aide de clics est affiché lorsque l'utilisateur clique sur des données interactives apparaissant dans le rapport principal. Ces rapports sont automatiquement générés par le serveur de rapports. En tant que concepteur de modèle, vous déterminez ce qui est affiché dans les rapports générés interactifs en définissant les propriétés **DefaultDetailAttribute** et **DefaultAggregateAttribute** que vous affectez à une entité dans le modèle de rapport.  
  
> [!NOTE]  
>  Les rapports générés interactifs ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md). Si vous ne savez pas quelle édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est utilisée par votre organisation, contactez votre administrateur de base de données.  
  
## <a name="using-default-templates"></a>Utilisation de modèles par défaut  
 Par défaut, le serveur de rapports génère deux types de modèles générés interactifs pour chaque entité : un modèle à instance unique et un modèle à plusieurs instances. L'élément sur lequel vous cliquez détermine le modèle utilisé. Si la personne lisant le rapport clique sur un attribut scalaire, le modèle à instance unique est utilisé. Si la personne lisant le rapport clique sur un attribut d'agrégation, le modèle à plusieurs instances est utilisé.  
  
#### <a name="single-instance-templates"></a>Modèles à instance unique  
 Un modèle à instance unique affiche tous les attributs de l'entité cible et tous les attributs d'agrégation par défaut qui sont spécifiés pour les entités associées ayant une relation un-à-plusieurs à partir de l'entité cible. Un modèle à instance unique est similaire à l'illustration suivante.  
  
 ![Plusieurs à un rapport généré interactif 1. ] (../../reporting-services/reports/media/manytooneclickthrough.gif "Plusieurs à un rapport généré interactif 1.")  
  
#### <a name="multiple-instance-templates"></a>Modèles à plusieurs instances  
 Un modèle à plusieurs instances affiche uniquement les attributs de détails par défaut de l'entité cible et tous les attributs d'agrégation par défaut qui sont spécifiés pour les entités associées ayant une relation un-à-plusieurs à partir de l'entité cible. Un modèle à plusieurs instances est similaire à l'illustration suivante.  
  
 ![Plusieurs à un rapport généré interactif 1. ] (../../reporting-services/reports/media/onetomanyclickthrough.gif "Plusieurs à un rapport généré interactif 1.")  
  
## <a name="customizing-clickthrough-reports"></a>personnalisation de rapports consultables à l'aide de clics  
 Au lieu d'utiliser les modèles par défaut générés par le serveur de rapports, vous pouvez créer un rapport dans le Générateur de rapports et l'utiliser comme rapport généré interactif personnalisé. Vous pouvez ensuite lier votre rapport au modèle en tant que rapport d'extraction dans le Gestionnaire de rapports.  
  
 Pour transformer un rapport du Générateur de rapports en un rapport généré interactif, vous devez activer l’option **Activer l’extraction dans ce rapport** dans la boîte de dialogue **Propriétés** du Générateur de rapports. Une fois cette option activée, un paramètre d'extraction est ajouté au rapport et ce dernier ne peut plus être exécuté directement dans le Générateur de rapports. Le paramètre d'extraction est automatiquement calculé par le serveur de rapports lorsque le lecteur du rapport clique sur un élément dans un rapport du Générateur de rapports.  
  
> [!IMPORTANT]  
>  L'entité principale ou de base employée dans le rapport doit être celle à laquelle vous liez le rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Lier un rapport à un modèle en tant que rapport généré interactif](http://msdn.microsoft.com/library/3af42de3-67ef-41c2-bc8a-7045baec6f63)  
  
  

