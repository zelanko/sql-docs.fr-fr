---
title: Définition des Options de projet (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Setting project options,configuration options
ms.assetid: 08820d88-e157-4d49-9401-38580dd7ec2d
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 56e7a30725a4fcad36ffa2df869ecc559056a29e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819227"
---
# <a name="setting-project-options-mysqltosql"></a>Définition des options du projet (MySQLToSQL)
Pour chaque projet SSMA, vous pouvez définir les options au niveau du projet. Ces options spécifient la façon dont les objets sont convertis, la migration des données, et la correspondance entre les types de sources de données et les types de données cible.  Avant de convertir les objets dans SQL Server ou SQL Azure ou migrer des données dans SQL Server ou SQL Azure, vérifiez que les options de configuration sont appropriées pour le projet.  
  
SSMA vous permet de configurer les options par défaut pour tous les projets. Ces options sont appliquées à tout nouveau projet que vous créez. Vous pouvez ensuite personnaliser les options pour chaque projet.  
  
## <a name="configuration-options-and-modes"></a>Modes et les Options de configuration  
SSMA a cinq jeux de paramètres de projet :  
  
-   Informations sur le projet  
  
-   Général (Conversion, Migration et SQL Azure)  
  
-   Synchronization  
  
-   INTERFACE GRAPHIQUE UTILISATEUR  
  
-   Mappage de type  
  
Les paramètres du projet peuvent être configurés de quatre manières :  
  
-   Valeur par défaut  
  
-   Optimistic  
  
-   Complète  
  
-   Custom  
  
Le mode par défaut est recommandé pour la plupart des utilisateurs. Le mode optimiste permet de maintenir davantage de la syntaxe de MySQL actuelle et est plus facile à lire. Toutefois, en conservant la syntaxe actuelle peut manquer de précision. Si la syntaxe de MySQL doit être convertie en syntaxe équivalente de SQL Server ou SQL Azure, le mode effectue la conversion la plus complète. Le code résultant, toutefois, peut être plus difficile à lire. Dans le mode personnalisé, vous pouvez définir les options.  
  
Pour plus d’informations sur les paramètres et la façon dont les paramètres sont appliqués dans chaque mode, consultez les rubriques suivantes :  
  
-   [Paramètres du projet &#40;Conversion&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
  
-   [Paramètres du projet &#40;Migration&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md)  
  
-   [Paramètres du projet (GUI) (SSMA commun)](http://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [Paramètres du projet &#40;mappage de Type&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md)  
  
-   [Paramètres du projet &#40;synchronisation&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
-   [Paramètres du projet &#40;Azure SQL DB&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md)  
  
## <a name="setting-project-options"></a>Définition des options du projet  
Dans SSMA, vous pouvez configurer les paramètres par défaut pour tous les projets. Ces paramètres sont enregistrés dans le fichier de configuration de SSMA et appliqués à tout nouveau projet que vous créez.  
  
**Pour définir les options de projet par défaut**  
  
1.  Sur le **outils** menu, cliquez sur **par défaut des paramètres de projet**.  
  
2.  Dans le **par défaut des paramètres de projet** boîte de dialogue, utilisez une des procédures suivantes :  
  
    1.  Sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affiché / a été remplacée par **Version cible de Migration** liste déroulante, cliquez sur **général** en bas de la partie gauche, puis sélectionnez **Conversion ou de Migration ou de SQL Azure** option.  
  
    2.  Pour sélectionner un mode prédéfini, sélectionnez **par défaut**, **Optimistic**, ou **complète** à partir de la **Mode** zone de liste déroulante.  
  
    3.  Pour spécifier des paramètres personnalisés, sélectionnez ou entrez les nouveaux paramètres ou les valeurs.  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
Vous pouvez également personnaliser les paramètres pour le projet actuel. Les paramètres sont enregistrés dans le fichier de projet actuel.  
  
**Pour personnaliser les paramètres pour le projet actuel**  
  
1.  Sur le **outils** menu, cliquez sur **ProjectSettings**.  
  
2.  Dans le **ProjectSettings** boîte de dialogue, utilisez une des procédures suivantes :  
  
    1.  Pour sélectionner un mode prédéfini, sélectionnez **par défaut**, **Optimistic**, ou **complète** à partir de la **Mode** zone de liste déroulante.  
  
    2.  Pour spécifier un mode personnalisé, sélectionnez **personnalisé** à partir de la **Mode** zone de liste déroulante. Puis sélectionnez les paramètres de projet approprié.  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage des types de données source et cible, consultez [MySQL de mappage et les Types de données SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Sinon, vous pouvez convertir les définitions d’objets de base de données MySQL dans SQL Server ou les définitions d’objets SQL Azure. Pour plus d’informations, consultez [conversion de bases de données MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Mappage de MySQL et les Types de données SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
