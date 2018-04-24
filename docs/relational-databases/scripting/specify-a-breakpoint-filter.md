---
title: Spécifier un filtre de point d’arrêt | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.breakpt.contraints
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 40cd627b8c8a90f43d9ee9cee53f85a5c5b65782
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="specify-a-breakpoint-filter"></a>Spécifier un filtre de point d'arrêt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Un filtre de point d'arrêt limite l'action du point d'arrêt uniquement aux ordinateurs, aux processus du système d'exploitation et aux threads spécifiés. Les filtres de point d'arrêt sont utilisés en général lors du débogage d'applications parallèles.  
  
##  <a name="BKMK_ActionConsiderations"></a> Règles de filtre  
 Les filtres de point d'arrêt ne sont en général pas utilisés avec le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] parce que les scripts et les procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] ne sont pas des applications parallèles.  
  
#### <a name="to-specify-a-breakpoint-filter"></a>Pour spécifier un filtre de point d'arrêt  
  
1.  Dans la fenêtre de l’éditeur, cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Filtre** dans le menu contextuel.  
  
     -ou-  
  
     Dans la fenêtre **Points d’arrêt** , cliquez avec le bouton droit sur le glyphe du point d’arrêt, puis cliquez sur **Filtre** dans le menu contextuel.  
  
2.  Dans la boîte de dialogue **Filtres de point d’arrêt** , utilisez la zone **Filtre** pour spécifier des ordinateurs par nom, ou des processus du système d’exploitation et des threads par nom ou numéro d’ID :  
  
    -   **MachineName** est l’ordinateur qui exécute l’instance du moteur de base de données.  
  
    -   **ProcessID**et **ProcessName** correspondent au processus de système d’exploitation qui exécute l’instance du moteur de base de données.  
  
    -   **ThreadID** et **ThreadName** correspondent au thread de système d’exploitation qui exécute le lot, la procédure ou la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] dans l’instance du moteur de base de données.  
  
3.  Cliquez sur **OK** pour implémenter les modifications ou sur **Annuler** pour fermer sans appliquer les modifications.  
  
## <a name="see-also"></a> Voir aussi  
 [Spécifier une condition de point d'arrêt](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Spécifier un nombre d'accès](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Spécifier une action de point d’arrêt](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
  
  
