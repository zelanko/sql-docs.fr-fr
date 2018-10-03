---
title: Espaces de noms SMO | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], namespaces
- namespaces [SMO]
- SQL Server Management Objects, namespaces
ms.assetid: 7bfabe4d-9f4c-4bc9-b998-93bd2b50ee8a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 717b2171b535405cc0bc075ceafd50107fb68bed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632647"
---
# <a name="smo-object-model-namespaces"></a>Espaces de noms du modèle objet SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les objets SMO ont différents espaces de noms. Les différents espaces de noms représentent différentes zones de fonctionnalités au sein de SMO.  
  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], les assemblys SMO sont situés dans le dossier C:\Program Files\Microsoft SQL Server\130\SDK\Assemblies\.  
  
## <a name="namespaces"></a>Espaces de noms  
 Les espaces de noms SMO sont les suivants :  
  
|Classe|Fonction|  
|-----------|--------------|  
|<xref:Microsoft.SqlServer.Management.Smo>|Contient des classes d’instance, les classes d’utilitaire et les énumérations qui servent à manipuler par programmation [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|<xref:Microsoft.SqlServer.Management.Common>|Contient les classes communes à RMO et SMO, comme les classes de connexion.|  
|<xref:Microsoft.SqlServer.Management.Smo.Agent>|Contient les classes qui représentent l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|<xref:Microsoft.SqlServer.Management.Smo.Wmi>|Contient les classes qui représentent le fournisseur WMI.|  
|<xref:Microsoft.SqlServer.Management.Smo.RegisteredServers>|Contient les classes qui représentent le serveur inscrit.|  
|<xref:Microsoft.SqlServer.Management.Smo.Mail>|Contient les classes qui représentent la messagerie de base de données.|  
|<xref:Microsoft.SqlServer.Management.Smo.Broker>|Contient les classes qui représentent le [!INCLUDE[ssSB](../../includes/sssb-md.md)].|  
  
  
