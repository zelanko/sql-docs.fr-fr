---
title: Installation de Microsoft Connector 1.1 pour SAP BW | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: dc6bbbf5972615880d3852d5f56a955862c9f22b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153756"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Installation de Microsoft Connector 1.1 pour SAP BW
  Pour installer le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW et sa documentation, téléchargez et exécutez le package Windows installer à partir de la page de fonctionnalité Pack Web de SQL Server.  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
## <a name="required-sap-files"></a>Fichiers SAP requis  
 Pour utiliser le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW, vous n’avez pas à installer le logiciel frontal SAP (interface GUI SAP) sur l’ordinateur local.  
  
 Cependant, vous devez copier le fichier du connecteur SAP .NET, librfc32.dll, dans le sous-dossier système du dossier Windows. (En général, l’emplacement de ce dossier est **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Éléments à prendre en considération pour les ordinateurs 64 bits  
 Le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW prend totalement en charge la version 64 bits de [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. Sur un ordinateur 64 bits, le [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 pour SAP BW comprend les exigences supplémentaires suivantes :  
  
-   Pour exécuter les packages en mode 64 bits sur les systèmes d’exploitation Windows 64 bits, copiez la version 64 bits du fichier d’interface GUI SAP, librfc32.dll, dans le dossier **system32** du dossier Windows. (En général, l’emplacement de ce fichier est **C:\Windows\system32**.)  
  
-   Pour exécuter les packages en mode 32 bits sur les systèmes d’exploitation Windows 64 bits, copiez le fichier d’interface GUI SAP, librfc32.dll, dans le dossier **SysWow64** du dossier Windows. (En général, l’emplacement de ce dossier est **C:\Windows\SysWow64**.)  
  
  