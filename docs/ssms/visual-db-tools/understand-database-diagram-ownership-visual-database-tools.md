---
title: "Comprendre la propriété du schéma de base de données (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3c807b9768da6ad563558eadf18ea8ee4544485
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Comprendre la propriété du schéma de base de données (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Pour utiliser le Concepteur de schémas de base de données, il doit d’abord être installé par un membre du rôle db_owner (rôle de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]) pour contrôler l’accès aux schémas. Chaque schéma a un seul propriétaire : l'utilisateur qui l'a créé. Pour plus d’informations sur la configuration des schémas, consultez [Configurer le Concepteur de schémas de base de données (Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md).  
  
Voici quelques points à retenir au sujet de la propriété des schémas :  
  
-   Même si tout utilisateur ayant accès à une base de données peut créer un schéma, lorsque ce dernier est créé, les seuls utilisateurs autorisés à le consulter sont son créateur et tout membre du rôle db_owner.  
  
-   La propriété de schémas ne peut être transférée qu'à des membres du rôle db_owner. Cela n'est possible que si l'ancien propriétaire du schéma a été supprimé de la base de données.  
  
-   Si le propriétaire d'un schéma a été supprimé de la base de données, le schéma reste dans la base de données jusqu'à ce qu'un membre du rôle db_owner tente de l'ouvrir. À ce stade, le membre du rôle db_owner peut choisir de prendre possession du schéma.  
  
## <a name="see-also"></a> Voir aussi  
[Utiliser des schémas de base de données (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Configurer le Concepteur de schémas de base de données (Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)  
  
