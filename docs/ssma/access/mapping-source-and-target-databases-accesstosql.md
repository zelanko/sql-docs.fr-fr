---
title: Mappage des bases de données source et cible (AccessToSQL) | Microsoft Docs
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
ms.openlocfilehash: 192db2e6c074305ca258d76652351175c8a82751
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907155"
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>Mappage des bases de données source et cible (AccessToSQL)
Lorsque vous vous connectez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à ou SQL Azure, vous devez spécifier une base de données cible pour la migration. Si vous disposez de plusieurs bases de données Access, vous pouvez les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mapper à plusieurs bases de données (ou schémas) ou à plusieurs schémas sous la base de données SQL Azure connectée.  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server ou SQL Azure des schémas de base de données  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les bases de données utilisent le concept de schéma pour séparer les objets d’une base de données en groupes logiques. Par exemple, une base de données de bibliothèque peut utiliser trois schémas nommés **livres**, **audio**et **vidéo** pour séparer les objets de livre, audio et vidéo les uns des autres. Par défaut, la base de données Access est mappée à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Master** et au schéma **dbo** dans et à la base de données connectée et au schéma **dbo** dans SQL Azure.  
  
À moins que vous ne personnalisiez le mappage entre chaque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données Access et la base de données et le schéma, SSMA migre tous les schémas et données associés à la base de données Access vers la base de données par défaut mappée.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modification de la base de données et du schéma cibles  
SSMA vous permet de mapper chaque base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données Access à ou SQL Azure base de données et au schéma. La procédure suivante décrit comment personnaliser le mappage par base de données.  
  
**Pour modifier la base de données et le schéma cibles**  
  
1.  Dans le volet Explorateur de métadonnées d’accès, sélectionnez **accès-métadonnées**.  
  
    Le mappage de schéma est également disponible lorsque vous sélectionnez le nœud **bases de données** ou un nœud de base de données. La liste mappage de schéma est personnalisée pour l’objet sélectionné.  
  
2.  Dans le volet droit, cliquez sur l’onglet **mappage de schéma** .  
  
    Vous verrez une table contenant les noms des bases de données Access et son schéma ssNoVersion ou SQL Azure correspondant. Le schéma cible est indiqué dans une notation en deux parties (Database. Schema).  
  
3.  Sélectionnez la ligne qui contient le mappage que vous souhaitez personnaliser, puis cliquez sur **modifier**.  
  
4.  Dans la boîte de dialogue **choisir un schéma cible** , vous pouvez rechercher le schéma et la base de données cible disponibles, ou taper le nom de la base de données et du schéma dans la zone de texte en deux parties (Database. Schema), puis cliquer sur **OK**.  
  
**Modes de mappage**  
  
-   Mappage à SQL Server  
  
Vous pouvez mapper une base de données source à une base de données cible. Par défaut, la base de données source est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée à la base de données cible avec laquelle vous vous êtes connecté à l’aide de SSMA. Si la base de données cible mappée n’existe pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sur, vous êtes invité à entrer un message **«la base de données et/ou le schéma n’existe pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les métadonnées cibles. Il serait créé au cours de la synchronisation. Voulez-vous continuer ?»** Cliquez sur Oui. De même, vous pouvez mapper le schéma à un schéma non existant sous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la base de données cible, qui sera créé lors de la synchronisation.  
  
-   Mappage à SQL Azure  
  
Vous pouvez mapper la base de données source à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données cible connectée ou au schéma de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’importe quel schéma dans la base de données cible connectée. Si vous mappez le schéma source à un schéma non existant dans une base de données cible connectée, vous êtes invité à entrer un message **«le schéma n’existe pas dans les métadonnées cibles. Il serait créé au cours de la synchronisation. Voulez-vous continuer ? «** Cliquez sur Oui.  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>Rétablissement de la base de données et du schéma initiaux  
Si vous personnalisez le mappage entre une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Access et un ou SQL Azure base de données et un schéma, vous pouvez rétablir le mappage à la base de données que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous avez spécifiée lorsque vous vous êtes connecté à ou SQL Azure.  
  
**Pour rétablir la base de données et le schéma par défaut**  
  
1.  Sous l’onglet Mappage de schéma, sélectionnez n’importe quelle ligne et cliquez sur **rétablir les valeurs par défaut** pour rétablir la base de données et le schéma par défaut.  
  
## <a name="next-step"></a>étape suivante  
L’étape suivante du processus de migration consiste à [convertir des objets de base de données](converting-access-database-objects-accesstosql.md) .  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
