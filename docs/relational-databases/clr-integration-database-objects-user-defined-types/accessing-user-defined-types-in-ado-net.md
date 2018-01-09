---
title: "L’accès à des Types définis par l’utilisateur dans ADO.NET | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ab92bd954e06ffcb3047c77d49d1e142ff5ab861
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="accessing-user-defined-types-in-adonet"></a>Accès aux types définis par l'utilisateur dans ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Types définis par l’utilisateur (UDT) sont écrits à l’aide d’une des langues prises en charge par le [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) qui produire du code vérifiable. notamment [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Les types définis par l'utilisateur permettent de stocker des objets et des structures de données personnalisées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les données sont exposées en tant que membres publics d'une classe ou d'une structure .NET Framework, et les comportements sont définis par des méthodes de la classe ou de la structure. Un UDT peut être utilisé en tant que définition de colonne d’une table, en tant que variable dans un [!INCLUDE[tsql](../../includes/tsql-md.md)] lot, ou en tant qu’argument d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] fonction ou procédure stockée.  
  
 Dans ADO.NET, le **System.Data.SqlClient** fournisseur expose des UDT comme suit :  
  
-   Via le **System.Data.SqlClient.SqlDataReader** en tant qu’objet.  
  
-   Via le **SqlDataReader** comme octets bruts.  
  
-   En tant que paramètre d’une **System.Data.SqlClient.SqlParameter** objet.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Extraction de données UDT](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Décrit comment récupérer les données UDT et comment spécifier des paramètres.  
  
 [Mise à jour de colonnes UDT avec DataAdapters](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Décrit comment utiliser des UDT dans **DataSets** et comment mettre à jour des données UDT à l’aide de **DataAdapters**.  
  
## <a name="see-also"></a>Voir aussi  
 [Types CLR définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
