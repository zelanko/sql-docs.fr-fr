---
title: Modifier des contraintes d’arête | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- alter edge constraints
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5b6a471156f0b1371c727ce96aac72f4f812dac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62693306"
---
# <a name="modify-edge-constraints"></a>Modifier des contraintes d’arête
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Vous pouvez modifier une contrainte d’arête dans [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous pouvez modifier la contrainte d’arête d’une table d’arêtes en modifiant l’ordre des clauses de contrainte d’arête ou en ajoutant une nouvelle clause.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour modifier une contrainte d’arête à l’aide de :**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL
 Pour modifier une contrainte d’arête à l’aide de Transact-SQL, vous devez d’abord supprimer la contrainte d’arête existante, puis la recréer avec la nouvelle définition. Pour plus d’informations, consultez [Supprimer une contrainte d’arête](../../relational-databases/tables/delete-edge-constraint.md) et [Créer des contraintes d’arête](../../relational-databases/tables/create-edge-constraints.md).    
 
