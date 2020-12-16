---
description: 'Tutoriel : Utilisation du type de données hierarchyid'
title: 'Didacticiel : utilisation du type de données hierarchyid | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: quickstart
helpviewer_keywords:
- tutorials [hierarchyid]
- hierarchyid [Database Engine], tutorial
ms.assetid: 5a7f7cfd-7faf-439f-8085-8fd6bf7db355
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8aae425506ebc8a2a17aadb2fa9c2d4485fe8f85
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97426734"
---
# <a name="tutorial-using-the-hierarchyid-data-type"></a>Tutoriel : Utilisation du type de données hierarchyid
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
 Ce didacticiel s’adresse aux utilisateurs qui connaissent [!INCLUDE[tsql](../../includes/tsql-md.md)], mais qui n’ont jamais utilisé le type de données **hierarchyid**.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
Ce didacticiel est divisé en deux leçons :  
  
[Leçon 1 : Conversion d’une table en une structure hiérarchique](../../relational-databases/tables/lesson-1-converting-a-table-to-a-hierarchical-structure.md)  
Dans cette leçon, vous prenez une table d’employés existante structurée en hiérarchie parent/enfant et vous déplacez les données dans une nouvelle table qui représente la hiérarchie en utilisant le type de données **hierarchyid** . Cette leçon requiert l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
[Leçon 2 : Création et gestion de données dans une table hiérarchique](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
Dans cette leçon, vous créez une table en utilisant le type de données **hierarchyid** pour représenter la structure de hiérarchie. Vous manipulez ensuite les données dans la table en utilisant les méthodes hiérarchiques.  
  
## <a name="requirements"></a>Conditions requises  
Les programmes suivants doivent être installés sur votre système :  
  
-   Toute édition de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express.  
  
-   Internet Explorer 6 ou une version ultérieure.  
  
## <a name="see-also"></a>Voir aussi  
[Tutoriel : Bien démarrer avec le moteur de base de données](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
[Tutoriel : Écriture d’instructions Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
[Référence de méthodes de type de données hierarchyid](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)  
  
  
