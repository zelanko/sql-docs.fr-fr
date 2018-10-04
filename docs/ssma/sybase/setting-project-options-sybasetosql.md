---
title: Définition des Options de projet (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Project Options Setting
ms.assetid: 97b70fc8-1f68-4f15-8e22-db5b784ea4ec
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 08b1084f2f54a204f82bc0d1a0ee4096d207d835
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773977"
---
# <a name="setting-project-options-sybasetosql"></a>Définition des options du projet (SybaseToSQL)
Pour chaque projet SSMA, vous pouvez définir des options au niveau du projet. Ces options spécifient la conversion de l’objet, lors du chargement de l’objet, SQL azure, l’interface utilisateur et les paramètres de migration de données. Avant de convertir des objets à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure ou migrer des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vérifiez que les options de configuration sont appropriées pour le projet.  
  
SSMA vous permet de configurer les options par défaut pour tous les projets. Ces options sont appliquées à tout nouveau projet que vous créez. Vous pouvez ensuite personnaliser les options pour chaque projet.  
  
## <a name="configuration-options-and-modes"></a>Modes et les Options de configuration  
SSMA a cinq jeux de paramètres de projet :  
  
1.  Informations sur le projet  
  
2.  Général (Conversion, Migration et collecte des données)  
  
3.  Synchronization  
  
4.  INTERFACE GRAPHIQUE UTILISATEUR  
  
5.  Mappage de type  
  
Il a également quatre modes de configuration de ces paramètres :  
  
1.  Valeur par défaut  
  
2.  Optimistic  
  
3.  Complète  
  
4.  Custom  
  
Le mode par défaut est recommandé pour la plupart des utilisateurs. Le mode optimiste permet de maintenir davantage de la syntaxe de Sybase Adaptive Server Enterprise (ASE) actuelle et est plus facile à lire. Toutefois, en conservant la syntaxe actuelle peut manquer de précision. Si la syntaxe de l’ASE doit être convertie en équivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la syntaxe SQL Azure, le mode effectue une conversion terminée, mais le code résultant peut être plus difficile à lire. Dans le mode personnalisé, vous définissez les options.  
  
Les paramètres sont décrits dans la section de référence de l’Interface utilisateur de cette documentation. Pour plus d’informations sur les paramètres et la façon dont les paramètres sont appliqués dans chaque mode, consultez les rubriques suivantes :  
  
-   [Paramètres du projet &#40;Conversion&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
-   [Paramètres du projet &#40;Migration&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md)  
  
-   [Paramètres du projet &#40;synchronisation&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md)  
  
-   [Paramètres du projet &#40;GUI&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md)  
  
-   [Paramètres du projet &#40;mappage de Type&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)  
  
-   [Paramètres du projet &#40;Azure SQL DB &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md)  
  
## <a name="setting-project-options"></a>Définition des options du projet  
Dans SSMA, vous pouvez configurer les paramètres par défaut pour tous les projets. Ces paramètres sont enregistrés dans le fichier de configuration de SSMA et appliqués à tout nouveau projet que vous créez.  
  
**Pour définir les options de projet par défaut**  
  
1.  Sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**.  
  
2.  Dans le **par défaut des paramètres de projet** boîte de dialogue, utilisez une des procédures suivantes :  
  
    -   Sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de Migration** déplacer vers le bas sur général en bas du volet gauche, puis sélectionnez Conversion ou de Migration ou de SQL Azure.  
  
    -   Pour sélectionner un mode prédéfini, dans le **Mode** zone de liste déroulante, sélectionnez **par défaut**, **Optimistic**, ou **complète**.  
  
    -   Pour spécifier des paramètres personnalisés, simplement Sélectionnez ou entrez les nouveaux paramètres ou les valeurs.  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
Vous pouvez également personnaliser les paramètres pour le projet actuel. Ces paramètres sont enregistrés dans le fichier de projet actuel.  
  
**Pour personnaliser les paramètres pour le projet actuel**  
  
1.  Sur le **outils** menu, sélectionnez **paramètres du projet**.  
  
2.  Dans le **paramètres du projet** boîte de dialogue, utilisez une des procédures suivantes :  
  
    -   Pour sélectionner un mode prédéfini, dans le **Mode** zone de liste déroulante, sélectionnez **par défaut**, **Optimistic**, ou **complète**.  
  
    -   Pour spécifier un mode personnalisé, dans le **Mode** liste déroulante, sélectionnez **personnalisé**, sélectionnez une option dans le volet gauche, cliquez sur le paramètre ou une valeur dans le volet droit, puis sélectionnez ou entrez le nouveau paramètre ou la valeur.  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
## <a name="next-steps"></a>Étapes suivantes  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Si vous souhaitez personnaliser le mappage des types de données source et cible, consultez [mappage Sybase ASE et Types de données SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Sinon, vous pouvez convertir les définitions d’objets de base de données Sybase dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou définitions d’objets SQL Azure. Pour plus d’informations, consultez [convertir les objets de base de données Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Migration des bases de données de Sybase ASE pour SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
