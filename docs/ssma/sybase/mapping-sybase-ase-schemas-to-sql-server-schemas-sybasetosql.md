---
title: Mappage de schémas de Sybase ASE à schémas SQL Server (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7d0f5e75e487b17873a49df25cbf4b4b359ea82b
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393852"
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>Mappage de schémas Sybase ASE à des schémas SQL Server (SybaseToSQL)
Dans Sybase Adaptive Server Enterprise (ASE), chaque base de données a un ou plusieurs schémas. Par défaut, SSMA migre tous les objets dans une base de données et le schéma à la même base de données et le même schéma dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Toutefois, vous pouvez personnaliser le mappage entre l’ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou des bases de données SQL Azure et des schémas.  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>ASE et SQL Server ou SQL Azure schémas  
ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure à la fois spécifier les bases de données et leurs schémas à l’aide de deux partie notation en tant que *database.schema*. Par exemple, dans un environnement ASE **démonstration** de base de données, il peut y avoir un **dbo** schéma. Que la paire base de données et de schéma est spécifiées en tant que **demo.dbo**. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure a la même base de données et le schéma, la paire est également spécifiée en tant que **demo.dbo**.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modification de la base de données cible et le schéma  
Dans SSMA, vous pouvez mapper un schéma de l’ASE à toute disponible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou schéma de SQL Azure.  
  
**Pour modifier la base de données et le schéma**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, sélectionnez **bases de données**.  
  
    Le **mappage de schéma** onglet est également disponible quand vous sélectionnez une base de données, le **schémas** dossier ou les schémas individuels. La liste dans le **mappage de schéma** onglet personnalisé pour l’objet sélectionné.  
  
2.  Dans le volet droit, cliquez sur le **mappage de schéma** onglet.  
  
    Vous verrez une liste de toutes les bases de données ASE avec leurs schémas, suivies d’une valeur cible. Cette cible est représentée dans une notation de deux parties (*database.schema*) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure où vos objets et les données seront migrées.  
  
3.  Sélectionnez la ligne qui contient le mappage que vous souhaitez modifier, puis cliquez sur **modifier**.  
  
4.  Dans le **choisir un schéma cible** boîte de dialogue, vous pouvez accéder pour la base de données cibles disponibles et de schéma ou de type de la base de données et le schéma nom dans la zone de texte dans une notation de deux parties (database.schema) puis cliquez sur **OK**.  
  
5.  La cible sont modifiées sur le **mappage de schéma** onglet.  
  
**Modes de mappage**  
  
-   Mappage vers SQL Server  
  
Vous pouvez mapper la base de données source vers une base de données cible. Par défaut la base de données source est mappée à la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données avec laquelle vous vous êtes connecté à l’aide de SSMA. Si la base de données cible qui est mappé est inexistant sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis vous serez invité avec un message **» la base de données et/ou le schéma n’existe pas dans la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] métadonnées. Il est créé pendant la synchronisation. Voulez-vous continuer ? »** Cliquez sur Oui. De même, vous pouvez mapper le schéma au schéma de non existant sous cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données qui sera créé pendant la synchronisation.  
  
-   Mappage à SQL Azure  
  
Vous pouvez mapper la base de données source à la base de données SQL Azure cibles connectés ou à n’importe quel schéma dans la base de données SQL Azure cibles connectés. Si vous mappez la source de schéma à aucun schéma n’existent pas sous la base de données connectée cible, vous serez invité avec un message **« schéma n’existe pas dans les métadonnées de la cible. Il est créé pendant la synchronisation. Voulez-vous continuer ? »** Cliquez sur Oui.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Retour à la base de données par défaut et le schéma  
Si vous personnalisez le mappage entre un schéma de l’ASE et un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou schéma de SQL Azure, vous pouvez rétablir le mappage vers les valeurs par défaut.  
  
**Pour rétablir la base de données par défaut et le schéma**  
  
1.  Sous l’onglet mappage de schéma, sélectionnez n’importe quelle ligne, puis cliquez sur **rétablir par défaut** pour rétablir la base de données par défaut et le schéma.  
  
## <a name="next-steps"></a>Étapes suivantes  
Si vous souhaitez analyser la conversion des objets de Sybase ASE dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou objets de SQL Azure, vous pouvez [créer un rapport de conversion](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md). Sinon, vous pouvez [convertir les définitions d’objets de base de données ASE](converting-sybase-ase-database-objects-sybasetosql.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou définitions d’objets SQL Azure.  
  
## <a name="see-also"></a>Voir aussi  
[Migration des bases de données de Sybase ASE pour SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
