---
title: Mappage des bases de données MySQL à des schémas SQL Server (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping, Modifying target database and schema
- Mapping, reverting to default database and schema
ms.assetid: 5c6fb445-92ae-4933-b77d-80230931c024
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ba413a15f0d201ecaddadf83e353d28ee3010c50
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721947"
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>Mappage de bases de données MySQL à des schémas SQL Server (MySQLToSQL)
Par défaut, SSMA pour MySQL migre tous les objets dans un schéma de MySQL vers un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou nommé pour le schéma de la base de données SQL Azure. Toutefois, vous pouvez personnaliser le mappage entre les schémas de MySQL et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou bases de données SQL Azure.  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>MySQL et SQL Server ou SQL Azure schémas  
Le concept de MySQL d’un schéma mappe au concept d’une base de données et d’un des ses schémas SQL Server. SSMA fait référence à la combinaison de SQL Server de la base de données et le schéma en tant que schéma.  
  
Le concept de MySQL d’un schéma mappe au concept d’une base de données et d’un des ses schémas SQL Server. Par exemple, MySQL peut avoir un schéma nommé **HR**. Une instance de SQL Server peut avoir une base de données nommée **HR**, et au sein de cette base de données sont les schémas. Un schéma est le **dbo** (ou le propriétaire de la base de données) schéma. Par défaut, le schéma MySQL **HR** sera mappé à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données et le schéma **HR.dbo**. SSMA fait référence à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] combinaison de la base de données et le schéma en tant que schéma.  
  
Vous pouvez modifier le mappage entre MySQL et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou schémas Azure.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modification de la base de données cible et le schéma  
Dans SSMA, vous pouvez mapper un schéma de MySQL vers toute disponible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou schéma de SQL Azure.  
  
**Pour modifier la base de données et le schéma**  
  
1.  Dans l’Explorateur de métadonnées de MySQL, sélectionnez **schémas**.  
  
    Le **mappage de schéma** onglet est également disponible quand vous sélectionnez les schémas individuels. La liste dans le **mappage de schéma** onglet personnalisé pour l’objet sélectionné.  
  
2.  Dans le volet droit, cliquez sur le **mappage de schéma** onglet.  
  
    Vous verrez une liste de tous les schémas de MySQL, suivie d’une valeur cible. Cette cible est représentée dans une notation de deux parties (*database.schema*) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure où vos objets et les données seront migrées.  
  
3.  Sélectionnez la ligne qui contient le mappage que vous souhaitez modifier, puis cliquez sur **modifier**.  
  
    Dans le **choisir un schéma cible** boîte de dialogue, vous pouvez accéder pour la base de données cibles disponibles et de schéma ou de type de la base de données et le schéma nom dans la zone de texte dans une notation de deux parties (database.schema) puis cliquez sur **OK**.  
  
4.  La cible sont modifiées sur le **mappage de schéma** onglet.  
  
**Modes de mappage**  
  
-   Mappage vers SQL Server  
  
Vous pouvez mapper la base de données source vers une base de données cible. Par défaut la base de données source est mappée à la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données avec laquelle vous vous êtes connecté à l’aide de SSMA. Si la base de données cible qui est mappé est inexistant sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis vous serez invité avec un message **» la base de données et/ou le schéma n’existe pas dans la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] métadonnées. Il est créé pendant la synchronisation. Voulez-vous continuer ? »** Cliquez sur Oui. De même, vous pouvez mapper le schéma au schéma de non existant sous cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données qui sera créé pendant la synchronisation.  
  
-   Mappage à SQL Azure  
  
Vous pouvez mapper la base de données source vers la cible connectée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données ou à n’importe quel schéma dans la cible connectée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données. Si vous mappez la source de schéma à aucun schéma n’existent pas sous la base de données connectée cible, vous serez invité avec un message **« schéma n’existe pas dans les métadonnées de la cible. Il est créé pendant la synchronisation. Voulez-vous continuer ? »** Cliquez sur Oui.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Retour à la base de données par défaut et le schéma  
Si vous personnalisez le mappage entre un schéma de MySQL et un schéma de SQL Server, vous pouvez rétablir le mappage vers les valeurs par défaut.  
  
**Pour rétablir la base de données par défaut et le schéma**  
  
1.  Sous l’onglet mappage de schéma, sélectionnez n’importe quelle ligne, puis cliquez sur **rétablir par défaut** pour rétablir la base de données par défaut et le schéma.  
  
## <a name="next-steps"></a>Étapes suivantes  
Si vous souhaitez analyser la conversion d’objets de MySQL dans des objets SQL Server ou SQL Azure, vous pouvez [créer un rapport de conversion](assessing-mysql-databases-for-conversion-mysqltosql.md) dans le cas contraire, vous pouvez [convertir les définitions d’objets de base de données MySQL](converting-mysql-databases-mysqltosql.md) en SQL Schémas Server ou SQL Azure  
  
## <a name="see-also"></a>Voir aussi  
[Paramètres du projet &#40;Conversion&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[Connexion à la base de données SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[Bases de données de migration de MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Connexion à SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
