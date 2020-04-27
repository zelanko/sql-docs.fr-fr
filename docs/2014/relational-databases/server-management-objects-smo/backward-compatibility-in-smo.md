---
title: Compatibilité descendante dans SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9432d9ae69ff9802d41e376c06d86ebbd2d594b0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63184451"
---
# <a name="backward-compatibility-in-smo"></a>Compatibilité descendante dans SMO
  Les applications SMO écrites dans une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être recompilées à l'aide de SMO dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="migrating-smo-applications"></a>Migration d'applications SMO  
 Les références aux DLL SMO dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent être supprimées et celles aux nouvelles DLL SMO fournies avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] doivent être incluses.  
  
 Vous devez au minimum faire référence aux éléments suivants :  
  
-   Microsoft.SqlServer.ConnectionInfo  
  
-   Microsoft.SqlServer.Smo  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc  
  
 Ces fichiers sont requis pour les classes de connexion, les classes utilitaires SMO et les classes de base.  
  
> [!NOTE]  
>  SmoEnum.dll ayant été supprimé, les références à ce fichier doivent être supprimées du projet SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
 Les espaces de noms ayant également changé, vous pouvez utiliser les éléments suivants :  
  
##### <a name="for-visual-c"></a>Pour Visual C#  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a>Pour Visual Basic  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 Si votre code utilise une fonction Urn, telle que `Server.GetSqlSmoObject(Urn)`, vous devez établir un lien avec l'espace de noms Microsoft.SqlServer.Management.Sdk.Sfc.  
  
 Si votre code utilise directement l'objet de transfert, vous devrez établir un lien avec l'espace de noms Microsoft.SqlServer.Management.SmoExtended.  
  
 Lors de la migration du code, il est possible que vous deviez le modifier. En effet, plusieurs fonctionnalités [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ont été déconseillées dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations sur les fonctionnalités déconseillées, consultez [fonctionnalités déconseillées de moteur de base de données dans SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) dans la documentation en ligne de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
  
