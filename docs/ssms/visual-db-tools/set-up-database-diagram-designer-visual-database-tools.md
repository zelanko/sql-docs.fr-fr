---
title: Configurer le Concepteur de diagrammes de base de données
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 5b4ce43a2c19f58c44ab0319aec5f98c38dafa3d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75255110"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Configurer le Concepteur de diagrammes de base de données (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Pour pouvoir utiliser le Concepteur de diagrammes de base de données, il doit d’abord être configuré par un membre du rôle **db_owner** afin de contrôler l’accès aux diagrammes.  
  
### <a name="to-set-up-database-diagramming"></a>Pour configurer la fonctionnalité de diagrammes de base de données  
  
1.  Dans l'Explorateur d'objets, développez un nœud de base de données.  
  
2.  Développez le nœud Diagrammes de base de données sous la connexion de base de données.  
  
3.  Sélectionnez **Oui** quand vous êtes invité à spécifier si vous souhaitez installer le diagramme de base de données.  
  
    > [!NOTE]  
    > Cela entraîne la création de la table de diagramme de base de données, de procédures stockées système et d’une fonction système dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
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
[Comprendre la propriété du diagramme de base de données &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
[Mettre à niveau des diagrammes de base de données d’éditions antérieures &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
[ALTER AUTHORIZATION (Transact-SQL)](https://msdn.microsoft.com/8c805ae2-91ed-4133-96f6-9835c908f373)  
  
