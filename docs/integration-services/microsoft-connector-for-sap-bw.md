---
title: Microsoft Connector for SAP BW | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5281f080-53d5-4679-aa26-f4cd4ac7a2df
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 22dd86257529f3e872ec2a42c4439ba4518cb7ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65720119"
---
# <a name="microsoft-connector-for-sap-bw"></a>Microsoft Connector pour SAP BW

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW comprend un jeu de trois composants qui vous permettent d’extraire ou de charger des données dans un système SAP Netweaver BW version 7.  
  
 Le logiciel [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW pour SQL Server 2016 est un composant de SQL Server 2016 Feature Pack. Pour installer le composant Connector pour SAP BW et sa documentation, téléchargez et exécutez le package du programme d’installation à la [page Web SQL Server 2016 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=746297).  

> [!IMPORTANT]
> Microsoft ne prévoit pas de fournir une version mise à jour du connecteur pour SAP BW. Microsoft ne détient pas le code source des composants SAP BW, qui ont été développés par un tiers, et ne peut donc pas les mettre à jour. Achetez les derniers composants de connectivité SAP auprès d’un ISV partenaire de Microsoft comme [Theobald Software](https://theobald-software.com/en/xtract-is-productinfo.html). Les partenaires ISV de Microsoft ont adapté leurs composants de connectivité SAP pour SSIS à l’installation dans Azure.
 
> [!IMPORTANT]  
>  La documentation relative à Microsoft Connector pour SAP BW suppose que vous êtes familiarisé avec l’environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
## <a name="components"></a>Components  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW comprend les éléments suivants :  
  
-   **Source SAP BW** : la source SAP BW est un composant source de flux de données qui vous permet d’extraire des données d’un système SAP Netweaver BW version 7.  
  
-   **Destination SAP BW** : la destination SAP BW est un composant de destination de flux de données qui vous permet de charger des données dans un système SAP Netweaver BW version 7.  
  
-   **Gestionnaire de connexions SAP BW** : le gestionnaire de connexions SAP BW connecte une source SAP BW ou une destination SAP BW à un système SAP Netweaver BW version 7.  
  
 Pour obtenir la procédure pas à pas qui montre comment configurer et utiliser le gestionnaire de connexions, la source et la destination SAP BW, consultez le livre blanc [Utilisation de SQL Server Integration Services avec SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkId=301897). Ce livre blanc explique également comment configurer les objets nécessaires dans SAP BW.  
  
## <a name="documentation"></a>Documentation  
 Ce fichier d’aide de [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW contient les rubriques et sections suivantes :  
  
 [Installation de Microsoft Connector pour SAP BW](../integration-services/installing-the-microsoft-connector-for-sap-bw.md)  
 Décrit la configuration requise pour l’installation de [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW.  
  
 [Composants Microsoft Connector 1.1 pour SAP BW](../integration-services/microsoft-connector-for-sap-bw-components.md)  
 Décrit chaque composant de [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW.  
  
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
 Décrit l’interface utilisateur de chaque composant de [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW.  
  
  
