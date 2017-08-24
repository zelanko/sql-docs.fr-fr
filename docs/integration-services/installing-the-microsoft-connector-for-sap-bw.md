---
title: Installation de Microsoft Connector pour SAP BW | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 663ae1f9c71987729b96510157ce39868490f00b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="installing-the-microsoft-connector-for-sap-bw"></a>Installation de Microsoft Connector pour SAP BW
  Le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector pour SAP BW pour SQL Server 2016 est un composant de SQL Server 2016 Feature Pack. Pour installer le composant Connector pour SAP BW et sa documentation, téléchargez et exécutez le package du programme d’installation à la [page Web SQL Server 2016 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=746297).  
  
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
  
  
