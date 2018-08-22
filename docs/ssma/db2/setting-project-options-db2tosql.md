---
title: Définition des Options de projet (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f325a606-97ac-48bc-b344-b55f5e086a48
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e3974057f6b975a5c8abc7cc99f886360be15aa8
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40392979"
---
# <a name="setting-project-options-db2tosql"></a>Définition des Options de projet (DB2ToSQL)
Pour chaque projet SSMA, vous pouvez définir les options de niveau projet. Ces options spécifient la conversion de l’objet, le chargement d’objet, paramètres de migration des données et d’interface utilisateur. Avant de convertir des objets à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou migrer des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que les options de configuration sont appropriées pour le projet.  
  
SSMA vous permet de configurer les options par défaut pour tous les projets. Ces options sont appliquées à tout nouveau projet que vous créez. Vous pouvez ensuite personnaliser les options pour chaque projet.  
  
## <a name="configuration-options-and-modes"></a>Modes et les Options de configuration  
SSMA a cinq jeux de paramètres de projet :  
  
-   Informations sur le projet  
  
-   Général (Conversion, Migration, le chargement d’objets)  
  
-   Synchronization  
  
-   INTERFACE GRAPHIQUE UTILISATEUR  
  
-   Mappage de type  
  
Il a également quatre modes de configuration de ces paramètres :  
  
-   Valeur par défaut  
  
-   Optimistic  
  
-   Complète  
  
-   Custom  
  
Le mode par défaut est recommandé pour la plupart des utilisateurs. Le mode optimiste permet de maintenir davantage de la syntaxe de DB2 actuelle et est plus facile à lire. Toutefois, en conservant la syntaxe actuelle peut manquer de précision. Si la syntaxe de DB2 doit être convertie en équivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe, le mode effectue la conversion la plus complète, mais le code résultant peut être plus difficile à lire. Dans le mode personnalisé, vous définissez les options.  
  
Pour plus d’informations sur les paramètres et la façon dont les paramètres sont appliqués dans chaque mode, consultez les rubriques suivantes :  
  
-   [Paramètres du projet &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)  
  
-   [Paramètres du projet &#40;Migration&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md)  
  
-   [Paramètres du projet&#40;synchronisation&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)  
  
-   [Paramètres du projet &#40;GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md)  
  
-   [Paramètres du projet &#40;mappage de Type&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)  
  
## <a name="setting-project-options"></a>Définition des options du projet  
Dans SSMA, vous pouvez configurer les paramètres par défaut pour tous les projets. Ces paramètres sont enregistrés dans le fichier de configuration de SSMA et appliqués à tout nouveau projet que vous créez.  
  
**Pour définir les options de projet par défaut**  
  
1.  Sur le **outils** menu, cliquez sur **par défaut des paramètres de projet**.  
  
2.  Dans le **par défaut des paramètres de projet** boîte de dialogue, utilisez une des procédures suivantes :  
  
    -   Sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de Migration** déroulante cliquez **général** en bas du volet gauche, puis sélectionnez Conversion ou Migration.  
  
    -   Pour sélectionner un mode prédéfini, dans le **Mode** zone de liste déroulante, sélectionnez **par défaut**, **Optimistic**, ou **complète**.  
  
    -   Pour spécifier des paramètres personnalisés, sélectionnez ou entrez les nouveaux paramètres ou les valeurs.  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
Vous pouvez également personnaliser les paramètres pour le projet actuel. Ces paramètres sont enregistrés dans le fichier de projet actuel.  
  
**Pour personnaliser les paramètres pour le projet actuel**  
  
1.  Sur le **outils** menu, cliquez sur **paramètres du projet**.  
  
2.  Dans le **paramètres du projet** boîte de dialogue, utilisez une des procédures suivantes :  
  
    -   Pour sélectionner un mode prédéfini, dans le **Mode** zone de liste déroulante, sélectionnez **par défaut**, **Optimistic**, ou **complète**.  
  
    -   Pour spécifier un mode personnalisé, dans le **Mode** boîte, sélectionnez **personnalisé**, puis sélectionnez les paramètres de projet approprié.  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
## <a name="next-steps"></a>Étapes suivantes  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage des types de données source et cible, consultez [DB2 de mappage et les Types de données SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   Sinon, vous pouvez convertir les définitions d’objets de base de données DB2 dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définitions d’objets. Pour plus d’informations, consultez [conversion des schémas DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Mappage de DB2 et SQL Server Data Types &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)  
  
