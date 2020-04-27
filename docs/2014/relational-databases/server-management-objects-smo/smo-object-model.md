---
title: Modèle objet SMO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 637c60fd6d7ba53087a145135d7152066983b644
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63130615"
---
# <a name="smo-object-model"></a>Modèle objet SMO
  Le modèle objet SMO est composé d'une hiérarchie d'objets. L'objet <xref:Microsoft.SqlServer.Management.Smo.Server> est l'objet de niveau supérieur et tous les objets de classe d'instance résident sous l'objet <xref:Microsoft.SqlServer.Management.Smo.Server>.  
  
 La classe <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> est une classe de niveau supérieur avec une hiérarchie d'objets distincte. L' <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> objet représente [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les services et les paramètres réseau disponibles via le fournisseur WMI.  
  
 Outre les objets <xref:Microsoft.SqlServer.Management.Smo.Server> et <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>, il existe plusieurs classes utilitaires qui représentent des tâches ou des opérations, telles que <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> ou <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
 Le modèle objet SMO est composé de plusieurs espaces de noms. Pour plus d’informations, consultez [Espaces de noms SMO](smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Diagramme du modèle objet SMO](smo-object-model-diagram.md)   
 [Espaces de noms SMO](smo-object-model-namespaces.md)   
 [Fournisseur WMI pour les concepts de gestion de configuration](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
