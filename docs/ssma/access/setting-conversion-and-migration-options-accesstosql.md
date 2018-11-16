---
title: Définition des Options de Migration (AccessToSQL) et de Conversion | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- conversion, setting options
- migration options
- modes
- options, conversion settings
- project settings
- schemas
ms.assetid: 0a7304df-2f35-4453-96ef-7ac83dea1167
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2cf8e07b15db7f4c2c7807c75a9862c26a92edcb
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677288"
---
# <a name="setting-conversion-and-migration-options-accesstosql"></a>Définition des Options de Migration (AccessToSQL) et de Conversion
Pour chaque projet SSMA, vous pouvez définir les options au niveau du projet. Ces options spécifient la façon dont les objets sont convertis, la migration des données, et la correspondance entre les types de sources de données et les types de données cible. Avant de convertir des objets à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure ou migrer des données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vérifiez que les options de configuration sont appropriées pour le projet.  
  
## <a name="configuration-options-and-modes"></a>Modes et les Options de configuration  
SSMA a quatre ensembles de paramètres de configuration et les quatre modes de configuration de ces paramètres : par défaut, Optimistic, complète et personnalisée. Le mode par défaut est recommandé pour la plupart des utilisateurs. Utiliser le mode optimiste pour les conversions simples. Utilisez le mode complet si vous souhaitez afficher tous les messages. Dans le mode personnalisé, vous définissez les options.  
  
Les paramètres sont décrits dans la section « Référence de l’Interface utilisateur » de cette documentation. Pour plus d’informations sur les paramètres et la façon dont les paramètres sont appliqués dans chaque mode, consultez les rubriques suivantes :  
  
-   [Paramètres du projet (Conversion)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
-   [Paramètres du projet (Migration)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)  
  
-   [Paramètres du projet (GUI)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)  
  
-   [Paramètres du projet (Mappage de type)](https://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655)  
  
-   [Paramètres du projet (SQL Azure)](https://msdn.microsoft.com/bbb8a204-d0e4-4f0b-9709-271feb1f136e)  
  
## <a name="setting-project-options"></a>Définition des options du projet  
Dans SSMA, vous pouvez configurer les paramètres par défaut pour tous les projets. Ces paramètres sont enregistrés dans le fichier de configuration de SSMA et appliqués à tout nouveau projet que vous créez.  
  
**Pour définir les options de projet par défaut**  
  
1.  Sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**.  
  
2.  Dans le **par défaut des paramètres de projet** boîte de dialogue, effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affiché / a été remplacée par **Version cible de Migration** liste déroulante, cliquez sur **général** en bas de la partie gauche, puis sélectionnez **Conversion ou de Migration ou de SQL Azure**.  
  
        > [!NOTE]  
        > Option de SQL Azure est disponible dans le **général** onglet uniquement si le type de projet créé est SQL Azure.  
  
    -   Pour sélectionner un mode prédéfini, sélectionnez **par défaut**, **Optimistic**, ou **complète** dans le **Mode** zone de liste déroulante.  
  
    -   Pour spécifier un mode personnalisé, sélectionnez **personnalisé** dans le **Mode** zone, sélectionnez une option dans le volet gauche, cliquez sur le paramètre ou une valeur dans le volet droit, puis sélectionnez ou entrez le nouveau paramètre ou la valeur.  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
Vous pouvez également personnaliser les paramètres pour le projet actuel. Ces paramètres sont enregistrés dans le fichier de projet actuel.  
  
**Pour personnaliser les paramètres pour le projet actuel**  
  
1.  Sur le **outils** menu, sélectionnez **paramètres du projet**.  
  
2.  Dans le **paramètres du projet** boîte de dialogue, effectuez l’une des opérations suivantes :  
  
    -   Pour sélectionner un mode prédéfini, sélectionnez **par défaut**, **Optimistic**, ou **complète** dans le **Mode** zone de liste déroulante.  
  
    -   Pour spécifier un mode personnalisé, sélectionnez **personnalisé** dans le **Mode** zone, sélectionnez une option dans le volet gauche, cliquez sur le paramètre ou une valeur dans le volet droit, puis sélectionnez ou entrez le nouveau paramètre ou la valeur.  
  
3.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
## <a name="next-steps"></a>Étapes suivantes  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage des types de données source et cible, consultez [Source de mappage et les Types de données cible](mapping-source-and-target-data-types-accesstosql.md)  
  
-   Pour personnaliser le mappage des bases de données source et cible, consultez [Source de mappage et de bases de données cible](mapping-source-and-target-databases-accesstosql.md)  
  
-   Sinon, vous pouvez convertir les définitions d’objets de base de données Access dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou définitions d’objets SQL Azure. Pour plus d’informations, consultez [conversion des objets de base de données Access](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
