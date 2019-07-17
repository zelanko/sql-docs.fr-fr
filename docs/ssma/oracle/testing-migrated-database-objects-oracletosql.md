---
title: Test des objets de base de données (OracleToSQL) migrés | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f03ef5e1-66e6-4c84-ada2-252dd5ada82f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 858c564c965fe7105c86a3087923887097e4ddac
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266481"
---
# <a name="testing-migrated-database-objects-oracletosql"></a>Test des objets de base de données migrés (OracleToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant de migration pour Oracle testeur (SSMA testeur) teste automatiquement la conversion des objets de base de données et la migration des données effectuées par SSMA. Une fois que toutes les étapes de migration de SSMA sont terminées, utilisez SSMA testeur pour vérifier que les objets convertis fonctionnent de manière identique et que toutes les données a été correctement transféré.  
  
Vous pouvez tester les types d’objet suivants avec SSMA testeur :  
  
-   Tables  
  
-   Procédures stockées, y compris les procédures empaquetées.  
  
-   Fonctions utilisateur, y compris les fonctions empaquetées.  
  
-   Vues.  
  
-   Instructions autonomes.  
  
SSMA testeur exécute les objets sélectionnés pour le test sur Oracle et leurs équivalents dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Après cela, il compare les résultats selon les critères suivants :  
  
-   Sont les modifications dans les données de la table identiques ?  
  
-   Les valeurs des paramètres de sortie pour les procédures et fonctions sont identiques ?  
  
-   Les fonctions retournent les mêmes résultats ?  
  
-   Sont que les jeux de résultats identique ?  
  
> [!NOTE]  
> Attention ! N’utilisez jamais de SSMA testeur sur les systèmes de production. Pendant l’exécution du testeur le schéma source et les données sont modifiées. Pendant ce temps, la restauration complète de l’état d’origine est parfois impossible pour certains types de code testé.  
  
## <a name="prerequisites"></a>Prérequis  
Si vous souhaitez utiliser le testeur de SSMA, installez le Pack d’Extension SSMA Oracle avec le **installer la base de données testeur** option activée.  
  
Pour permettre de comparer les données de table qui en résulte, définissez le **colonne ROWID générer** option **Oui** avant le démarrage de la conversion de schéma. SSMA ajoutera une colonne ROWID à toutes les tables pendant l’exécution de la **convertir le schéma** commande.  
  
En outre, vérifiez les éléments suivants :  
  
-   Outils clients Oracle sont installés sur l’ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute.  
  
-   Intégration du Common Language Runtime (CLR) a été activée sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données.  
  
Notez que la version actuelle du testeur de SSMA ne prend pas en charge l’exécution en parallèle par différents utilisateurs sur le même serveur source ou cible.  
  
## <a name="getting-started"></a>Prise en main  
[Création de cas de Test &#40;OracleToSQL&#41;](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Installation des composants SSMA sur SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Paramètres du projet &#40;Conversion&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
