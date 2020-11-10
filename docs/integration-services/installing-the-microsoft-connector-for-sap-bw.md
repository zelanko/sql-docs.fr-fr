---
description: Installation de Microsoft Connector pour SAP BW
title: Installation de Microsoft Connector for SAP BW | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3244ffbd690d7f2ea79862eb1963df60607ac2d6
ms.sourcegitcommit: 49ee3d388ddb52ed9cf78d42cff7797ad6d668f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94384626"
---
# <a name="installing-the-microsoft-connector-for-sap-bw"></a>Installation de Microsoft Connector pour SAP BW

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


  Le logiciel [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW pour SQL Server 2016 est un composant de SQL Server 2016 Feature Pack. Pour installer le composant Connector pour SAP BW et sa documentation, téléchargez et exécutez le package du programme d’installation à la [page Web SQL Server 2016 Feature Pack](https://www.microsoft.com/download/details.aspx?id=56833).  

> [!IMPORTANT]
> Microsoft ne prévoit pas de fournir une version mise à jour du connecteur pour SAP BW. Microsoft ne détient pas le code source des composants SAP BW, qui ont été développés par un tiers, et ne peut donc pas les mettre à jour. Achetez les derniers composants de connectivité SAP auprès d’un ISV partenaire de Microsoft comme [Theobald Software](https://theobald-software.com/en/xtract-is-productinfo.html). Les partenaires ISV de Microsoft ont adapté leurs composants de connectivité SAP pour SSIS à l’installation dans Azure.

> [!IMPORTANT]  
>  La documentation relative à Microsoft Connector pour SAP BW suppose que vous êtes familiarisé avec l’environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
## <a name="required-sap-files"></a>Fichiers SAP requis  
 Pour utiliser [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW, vous n’avez pas besoin d’installer le logiciel frontal SAP (interface GUI SAP) sur l’ordinateur local.  
  
 Cependant, vous devez copier le fichier du connecteur SAP .NET, librfc32.dll, dans le sous-dossier système du dossier Windows. (En général, l’emplacement de ce dossier est **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Éléments à prendre en considération pour les ordinateurs 64 bits  
 Le composant [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW prend totalement en charge la version 64 bits de [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. Sur un ordinateur 64 bits, [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW exige la configuration requise supplémentaire suivante :  
  
-   Pour exécuter les packages en mode 64 bits sur les systèmes d’exploitation Windows 64 bits, copiez la version 64 bits du fichier d’interface GUI SAP, librfc32.dll, dans le dossier **system32** du dossier Windows. (En général, l’emplacement de ce fichier est **C:\Windows\system32**.)  
  
-   Pour exécuter les packages en mode 32 bits sur les systèmes d’exploitation Windows 64 bits, copiez le fichier d’interface GUI SAP, librfc32.dll, dans le dossier **SysWow64** du dossier Windows. (En général, l’emplacement de ce dossier est **C:\Windows\SysWow64**.)  
  
  
