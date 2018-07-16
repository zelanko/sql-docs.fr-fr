---
title: Configurer le Concepteur de schémas de base de données (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eda956d955756b9617a609b9954e0ad1881b6b1b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232439"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Configurer le Concepteur de schémas de base de données (Visual Database Tools)
  Pour pouvoir utiliser le Concepteur de schémas de base de données, il doit d’abord être configuré par un membre du rôle **db_owner** afin de contrôler l’accès aux schémas.  
  
### <a name="to-set-up-database-diagramming"></a>Pour configurer la fonctionnalité de schémas de base de données  
  
1.  Dans l'Explorateur d'objets, développez un nœud de base de données.  
  
2.  Développez le nœud Schémas de base de données sous la connexion de base de données.  
  
3.  Sélectionnez **Oui** quand vous êtes invité à spécifier si vous souhaitez installer le schéma de base de données.  
  
    > [!NOTE]  
    >  Cela entraîne la création de la table de schéma de base de données, de procédures stockées système et d'une fonction système dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  Visual Studio créera les objets suivants sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    1.  Table sysdiagrams  
  
    2.  Procédure stockée sp_alterdiagram  
  
    3.  Procédure stockée sp_creatediagram  
  
    4.  Procédure stockée sp_dropdiagram  
  
    5.  Procédure stockée sp_renamediagram  
  
    6.  Fonction fn_diagramobjects  
  
    7.  Procédure stockée sp_helpdiagrams  
  
    8.  Procédure stockée sp_helpdiagramsdefinition  
  
    9. Procédure stockée sp_upgraddiagrams  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre la propriété du schéma de base de données &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Mettre à niveau des schémas de base de données d’éditions antérieures &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  
