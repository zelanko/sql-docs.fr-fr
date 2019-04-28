---
title: Mappage de Sybase ASE et Types de données SQL Server (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping Sybase ASE Schemas to SQL Server Schemas
- Type Mapping Settings
ms.assetid: 784365d3-df4e-47ab-8ee0-d8392b52f510
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8e50253b7c7fb6c59b4303c528c1ef7267ccf644
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62706073"
---
# <a name="mapping-sybase-ase-and-sql-server-data-types-sybasetosql"></a>Mappage des types de données Sybase ASE et SQL Server (SybaseToSQL)
Les types de base de données Sybase Adaptive Server Enterprise (ASE) diffèrent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou types de base de données SQL Azure. Lorsque vous convertissez des objets de base de données ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou objets de SQL Azure, vous devez spécifier le mappage des types de données à partir de l’ASE à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure. Vous pouvez accepter les mappages de type de données par défaut, ou vous pouvez personnaliser les mappages comme indiqué dans les sections suivantes.  
  
## <a name="default-mappings"></a>Mappages par défaut  
SSMA a un ensemble de mappages de types de données par défaut. Pour la liste des mappages par défaut, consultez [paramètres du projet &#40;le mappage de Type&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
## <a name="type-mapping-inheritance"></a>Type de mappage de l’héritage  
Vous pouvez personnaliser les mappages de type au niveau du projet, niveau de catégorie d’objet (par exemple, toutes les procédures stockées) ou niveau de l’objet. Les paramètres sont héritées du niveau supérieur, sauf substitution à un niveau inférieur. Par exemple, si vous mappez **smallmoney** à **money** au niveau des projets, tous les objets dans le projet utilisera ce mappage, sauf si vous personnalisez le mappage à l’objet niveau catégorie ou objet.  
  
Lorsque vous affichez le **le mappage de Type** onglet SSMA, l’arrière-plan est coloré pour afficher lesquelles mappages de type sont héritées. L’arrière-plan d’un mappage de type est jaune pour tout mappage de type hérité, blanc pour tout mappage spécifié au niveau actuel.  
  
## <a name="customizing-data-type-mappings"></a>Personnalisation mappages de types de données  
La procédure suivante montre comment mapper des types de données au niveau de l’objet, base de données ou projet.  
  
**Pour mapper les types de données**  
  
1.  Pour personnaliser le mappage de type de données pour la totalité du projet, ouvrez le **paramètres du projet** boîte de dialogue :  
  
    1.  Sur le **outils** menu, sélectionnez **paramètres du projet**.  
  
    2.  Dans le volet gauche, sélectionnez **le mappage de Type**.  
  
        Le graphique de mappage de type et les boutons s’affichent dans le volet droit.  
  
    Ou, pour personnaliser le type de données mise en correspondance à la base de données, table, vue ou niveau de la procédure stockée, sélectionnez la base de données, une catégorie d’objet ou un objet dans l’Explorateur de métadonnées Sybase :  
  
    1.  Dans l’Explorateur de métadonnées de Sybase, sélectionnez le dossier ou un objet que vous souhaitez personnaliser.  
  
    2.  Dans le volet droit, cliquez sur le **le mappage de Type** onglet.  
  
2.  Pour ajouter un nouveau mappage, procédez comme suit :  
  
    1.  Cliquez sur **Ajouter**.  
  
    2.  Sous **type de Source**, sélectionnez le type de données ASE à mapper.  
  
    3.  Si le type requiert une longueur, spécifiez la longueur minimale de données pour le mappage dans le **à partir de** zone, puis spécifiez la longueur maximale des données pour le mappage dans le **à** boîte.  
  
        Cela vous permet de personnaliser le mappage de données pour les valeurs inférieures et supérieures du même type de données.  
  
    4.  Sous **type cible**, sélectionnez la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou type de données SQL Azure.  
  
        Certains types nécessitent une longueur de type de données cible. Si nécessaire, entrez la nouvelle longueur de données dans le **remplacer par** boîte.  
  
    5.  Cliquez sur **OK**.  
  
3.  Pour modifier un mappage de type de données, procédez comme suit :  
  
    1.  Cliquez sur **Modifier**.  
  
    2.  Sous **type de Source**, sélectionnez le type de données ASE à mapper.  
  
    3.  Si le type requiert une longueur, spécifiez la longueur minimale de données pour le mappage dans le **à partir de** zone, puis spécifiez la longueur maximale des données pour le mappage dans le **à** boîte.  
  
        Cela vous permet de personnaliser le mappage de données pour les valeurs inférieures et supérieures du même type de données.  
  
    4.  Sous **type cible**, sélectionnez la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou type de données SQL Azure.  
  
        Certains types nécessitent une longueur de type de données cible. Si nécessaire, entrez la nouvelle longueur de données dans le **remplacer par** , puis cliquez sur **OK**.  
  
4.  Pour supprimer un mappage de type de données personnalisé, procédez comme suit :  
  
    1.  Sélectionnez la ligne dans la liste de mappage de type qui contient le mappage de type de données à supprimer.  
  
    2.  Cliquez sur **Supprimer**.  
  
        Impossible de supprimer les mappages hérités. Toutefois, des mappages hérités sont remplacées par des mappages personnalisés sur un objet spécifique ou une catégorie d’objet.  
  
## <a name="next-steps"></a>Étapes suivantes  
L’étape suivante du processus de migration consiste à [créer un rapport d’évaluation](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) ou [objets de base de données de convertir un ASE Sybase à la syntaxe SQL Server ou SQL Azure](converting-sybase-ase-database-objects-sybasetosql.md). Si vous créez un rapport d’évaluation, les objets de Sybase ASE sont automatiquement convertis durant l’évaluation.  
  
## <a name="see-also"></a>Voir aussi  
[Migration des bases de données de Sybase ASE pour SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
