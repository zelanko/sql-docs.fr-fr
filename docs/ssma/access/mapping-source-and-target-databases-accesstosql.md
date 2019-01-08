---
title: Mappage de Source et bases de données cibles (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- database schemas
- mapping, databases
- schemas, mapping to
- schemas, SQL Azure
- schemas, SQL Server
- source database
- target database
ms.assetid: 69bee937-7b2c-49ee-8866-7518c683fad4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d2be7854240a52edd8f3308ea92e3ea7eb25924f
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52407936"
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>Source de mappage et de bases de données cibles (AccessToSQL)
Lorsque vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vous devez spécifier une base de données cible pour la migration. Si vous avez plusieurs bases de données Access vous pouvez les mapper à plusieurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données (ou schémas) ou à plusieurs schémas sous la base de données SQL Azure connecté.  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server ou les schémas de base de données SQL Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données utilisent le concept de schémas pour séparer des objets au sein d’une base de données en groupes logiques. Par exemple, une base de données de bibliothèque peut utiliser trois schémas nommés **la documentation**, **audio**, et **vidéo** pour séparer des objets livres, audio et vidéo entre eux. Par défaut, la base de données access est mappée à **master** base de données et **dbo** schéma dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à la base de données connectée et **dbo** schéma dans SQL Azure.  
  
Sauf si vous personnalisez le mappage entre chaque base de données Access et la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données et de schéma, SSMA migre tous les schémas et les données associées à la base de données access à la base de données par défaut mappé.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modification de la base de données cible et le schéma  
SSMA vous permet de mapper chaque base de données Access à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de base de données SQL Azure et de schéma. La procédure suivante décrit comment personnaliser le mappage par base de données.  
  
**Pour modifier la base de données cible et le schéma**  
  
1.  Dans le volet Explorateur de métadonnées d’accès, sélectionnez **accès aux métadonnées**.  
  
    Mappage de schéma est également disponible quand vous sélectionnez le **bases de données** nœud ou n’importe quel nœud de base de données. La liste de mappage de schéma est personnalisée pour l’objet sélectionné.  
  
2.  Dans le volet droit, cliquez sur le **mappage de schéma** onglet.  
  
    Vous verrez une table contenant les accès des noms de base de données et ses ssNoVersion correspondante ou le schéma Sql Azure. Le schéma cible est indiqué dans une notation de deux parties (database.schema).  
  
3.  Sélectionnez la ligne qui contient le mappage que vous souhaitez personnaliser, puis cliquez sur **modifier**.  
  
4.  Dans le **choisir un schéma cible** boîte de dialogue, vous pouvez accéder pour la base de données cibles disponibles et de schéma ou de type de la base de données et le schéma nom dans la zone de texte dans une notation de deux parties (database.schema) puis cliquez sur **OK**.  
  
**Modes de mappage**  
  
-   Mappage vers SQL Server  
  
Vous pouvez mapper la base de données source vers une base de données cible. Par défaut la base de données source est mappée à la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données avec laquelle vous vous êtes connecté à l’aide de SSMA. Si la base de données cible en cours de mappage n’existe pas sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis vous serez invité avec un message **» la base de données et/ou le schéma n’existe pas dans la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] métadonnées. Il est créé pendant la synchronisation. Voulez-vous continuer ? »** Cliquez sur Oui. De même, vous pouvez mapper le schéma au schéma de non existant sous cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données qui sera créé pendant la synchronisation.  
  
-   Mappage à SQL Azure  
  
Vous pouvez mapper la base de données source vers la cible connectée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données ou à n’importe quel schéma dans la cible connectée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données. Si vous mappez la source de schéma à aucun schéma n’existent pas sous la base de données connectée cible, vous serez invité avec un message **« schéma n’existe pas dans les métadonnées de la cible. Il est créé pendant la synchronisation. Voulez-vous continuer ? "** Cliquez sur Oui.  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>Retour à votre base de données initiale et le schéma  
Si vous personnalisez le mappage entre une base de données Access et un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure et le schéma, vous pouvez rétablir le mappage à la base de données que vous avez spécifié lorsque vous connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure.  
  
**Pour réinitialiser au schéma et de la base de données par défaut**  
  
1.  Sous l’onglet mappage de schéma, sélectionnez n’importe quelle ligne, puis cliquez sur **rétablir par défaut** pour rétablir la base de données par défaut et le schéma.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration est [convertir des objets de base de données](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
