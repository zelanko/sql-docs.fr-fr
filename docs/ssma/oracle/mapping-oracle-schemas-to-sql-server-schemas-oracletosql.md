---
title: Mappage de schémas Oracle à des schémas SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 76e532a39a7571bf90ab2b032b86ba4c5e07da44
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981301"
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>Mappage de schémas Oracle à des schémas SQL Server (OracleToSQL)
Dans Oracle, chaque base de données a un ou plusieurs schémas. Par défaut, SSMA migre tous les objets dans un schéma Oracle pour un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nommé pour le schéma de base de données. Toutefois, vous pouvez personnaliser le mappage entre les schémas Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] bases de données.  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle et des schémas SQL Server  
Une base de données Oracle contient des schémas. Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] contient plusieurs bases de données, chacun d’eux peut avoir plusieurs schémas.  
  
Le concept d’Oracle d’un schéma est mappé à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] concept d’une base de données et d’un de ses schémas. Par exemple, Oracle peut avoir un schéma nommé **HR**. Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] peut avoir une base de données nommée **HR**, et au sein de cette base de données sont les schémas. Un schéma est le **dbo** (ou le propriétaire de la base de données) schéma. Par défaut, le schéma Oracle **HR** sera mappé à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données et le schéma **HR.dbo**. SSMA fait référence à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] combinaison de la base de données et le schéma en tant que schéma.  
  
Vous pouvez modifier le mappage entre Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schémas.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modification de la base de données cible et le schéma  
Dans SSMA, vous pouvez mapper un schéma Oracle vers toute disponible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schéma.  
  
**Pour modifier la base de données et le schéma**  
  
1.  Dans l’Explorateur de métadonnées d’Oracle, sélectionnez **schémas**.  
  
    Le **mappage de schéma** onglet est également disponible quand vous sélectionnez une base de données, le **schémas** dossier ou les schémas individuels. La liste dans le **mappage de schéma** onglet personnalisé pour l’objet sélectionné.  
  
2.  Dans le volet droit, cliquez sur le **mappage de schéma** onglet.  
  
    Vous verrez une liste de tous les schémas Oracle, suivie d’une valeur cible. Cette cible est représentée dans une notation de deux parties (*database.schema*) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] où vos objets et les données seront migrées.  
  
3.  Sélectionnez la ligne qui contient le mappage que vous souhaitez modifier, puis cliquez sur **modifier**.  
  
    Dans le **choisir un schéma cible** boîte de dialogue, vous pouvez accéder pour la base de données cibles disponibles et de schéma ou de type de la base de données et le schéma nom dans la zone de texte dans une notation de deux parties (database.schema) puis cliquez sur **OK**.  
  
4.  La cible sont modifiées sur le **mappage de schéma** onglet.  
  
**Modes de mappage**  
  
-   Mappage vers SQL Server  
  
Vous pouvez mapper la base de données source vers une base de données cible. Par défaut la base de données source est mappée à la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données avec laquelle vous vous êtes connecté à l’aide de SSMA. Si la base de données cible qui est mappé est inexistant sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], puis vous serez invité avec un message **» la base de données et/ou le schéma n’existe pas dans la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] métadonnées. Il est créé pendant la synchronisation. Voulez-vous continuer ? »** Cliquez sur Oui. De même, vous pouvez mapper le schéma au schéma de non existant sous cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données qui sera créé pendant la synchronisation.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Retour à la base de données par défaut et le schéma  
Si vous personnalisez le mappage entre un schéma Oracle et un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schéma, vous pouvez rétablir le mappage vers les valeurs par défaut.  
  
**Pour rétablir la base de données par défaut et le schéma**  
  
1.  Sous l’onglet mappage de schéma, sélectionnez n’importe quelle ligne, puis cliquez sur **rétablir par défaut** pour rétablir la base de données par défaut et le schéma.  
  
## <a name="next-steps"></a>Étapes suivantes  
Si vous souhaitez analyser la conversion des objets Oracle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] objets, vous pouvez [créer un rapport de conversion](http://msdn.microsoft.com/4de9bcf6-1346-4740-87f9-7f24a8226357). Sinon, vous pouvez [convertir les définitions d’objets de base de données Oracle](http://msdn.microsoft.com/e021182d-31da-443d-b110-937f5db27272) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] définitions d’objets.  
  
## <a name="see-also"></a>Voir aussi  
[Connexion à SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[Bases de données de migration d’Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
