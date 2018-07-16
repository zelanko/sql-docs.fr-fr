---
title: Installation de Microsoft Connector 1.1 pour SAP BW | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff4176fabb78aede03ca04fdf64fc52085431c9b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248796"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Installation de Microsoft Connector 1.1 pour SAP BW
  Pour installer le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW et sa documentation, téléchargez et exécutez le package de programme d’installation de Windows à partir de la page Web de Pack de fonctionnalité de serveur SQL.  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
## <a name="required-sap-files"></a>Fichiers SAP requis  
 Pour utiliser le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW, il est inutile d’installer le logiciel frontal SAP (interface GUI SAP) sur l’ordinateur local.  
  
 Cependant, vous devez copier le fichier du connecteur SAP .NET, librfc32.dll, dans le sous-dossier système du dossier Windows. (En général, l’emplacement de ce dossier est **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Éléments à prendre en considération pour les ordinateurs 64 bits  
 Le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW prend totalement en charge la version 64 bits de [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. Sur un ordinateur 64 bits, le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW comprend les exigences supplémentaires suivantes :  
  
-   Pour exécuter les packages en mode 64 bits sur les systèmes d’exploitation Windows 64 bits, copiez la version 64 bits du fichier d’interface GUI SAP, librfc32.dll, dans le dossier **system32** du dossier Windows. (En général, l’emplacement de ce fichier est **C:\Windows\system32**.)  
  
-   Pour exécuter les packages en mode 32 bits sur les systèmes d’exploitation Windows 64 bits, copiez le fichier d’interface GUI SAP, librfc32.dll, dans le dossier **SysWow64** du dossier Windows. (En général, l’emplacement de ce dossier est **C:\Windows\SysWow64**.)  
  
  
