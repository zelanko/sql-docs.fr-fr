---
title: Installer et désinstaller le composant Source OData | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 039e8dd4f77c0593dcdceb69fbcd53138bc50b91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281325"
---
# <a name="install-and-uninstall-odata-source-component"></a>Installer et désinstaller le composant source OData
  Cette rubrique fournit des instructions pour installer ou supprimer le composant source OData sur votre ordinateur.  
  
## <a name="installation"></a>Installation  
 Le composant source OData requiert les composants suivants et sera installé sur votre ordinateur.  
  
-   SQL Server Data Tools (pour concevoir des packages)  
  
-   SQL Server Integration Services (pour exécuter des packages hors de Visual Studio)  
  
 Pour installer le composant source OData, téléchargez [SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkId=391999) et exécutez l'un des fichiers MSI suivants.  
  
-   ODataSourceForSQLServer2014-amd64.msi pour les plateformes 64 bits  
  
-   ODataSourceForSQLServer2014-x86.msi pour les plateformes 32 bits  
  
> [!IMPORTANT]  
>  Le programme d'installation 64 bits installera les versions 32 bits et 64 bits du composant source OData. Exécutez uniquement le programme d'installation 32 bits si vous utilisez un système d'exploitation 32 bits.  
  
## <a name="uninstallation"></a>Désinstallation  
 Le composant source OData peut être désinstallé à partir du menu **Programmes et fonctionnalités** . Recherchez l'entrée **Composant source OData Microsoft SQL Server SSIS (x64)** et cliquez sur **Désinstaller**.  
  
  
