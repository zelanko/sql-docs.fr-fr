---
description: Comprendre la propriété du diagramme de base de données (Visual Database Tools)
title: Présentation de la propriété du diagramme de base de données
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: d3da1122dcb61b50db189ec798f091496621cbfc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88312685"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Comprendre la propriété du diagramme de base de données (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Pour utiliser le Concepteur de diagrammes de base de données, il doit d’abord être installé par un membre du rôle db_owner (rôle de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) pour contrôler l’accès aux diagrammes. Chaque schéma a un seul propriétaire : l'utilisateur qui l'a créé. Pour plus d’informations sur la configuration des diagrammes, consultez [Configurer le Concepteur de diagrammes de base de données(../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md).  
  
Voici quelques points à retenir au sujet de la propriété des schémas :  
  
-   Même si tout utilisateur ayant accès à une base de données peut créer un schéma, lorsque ce dernier est créé, les seuls utilisateurs autorisés à le consulter sont son créateur et tout membre du rôle db_owner.  
  
-   La propriété de schémas ne peut être transférée qu'à des membres du rôle db_owner. Cela n'est possible que si l'ancien propriétaire du schéma a été supprimé de la base de données.  
  
-   Si le propriétaire d'un schéma a été supprimé de la base de données, le schéma reste dans la base de données jusqu'à ce qu'un membre du rôle db_owner tente de l'ouvrir. À ce stade, le membre du rôle db_owner peut choisir de prendre possession du schéma.  
  
## <a name="see-also"></a>Voir aussi

[Utiliser des diagrammes de base de données](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Configurer le Concepteur de diagrammes de base de données](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)
