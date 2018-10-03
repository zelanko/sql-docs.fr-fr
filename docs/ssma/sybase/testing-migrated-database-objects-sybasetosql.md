---
title: Test des objets de base de données (SybaseToSQL) migrés | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e29fac8b9cdb955ddaff6643eacae352e9c39bf6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47749179"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>Test des objets de base de données migrés (SybaseToSQL)
Microsoft SQL Server Migration Assistant pour Sybase testeur (SSMA testeur) teste automatiquement la conversion des objets de base de données et la migration des données effectuées par SSMA. Une fois que toutes les étapes de migration de SSMA sont terminées, utilisez SSMA testeur pour vérifier que les objets convertis fonctionnent de manière identique et que toutes les données a été correctement transféré.  
  
> [!NOTE]  
> Composant de testeur est désactivée dans le cas de connectivité Azure.  
  
Vous pouvez tester les types d’objet suivants avec SSMA testeur :  
  
-   Tables  
  
-   Procédures stockées  
  
-   Vues.  
  
-   Instructions autonomes.  
  
SSMA testeur exécute les objets sélectionnés pour le test sur Sybase et leurs équivalents dans SQL Server. Après cela, il compare les résultats selon les critères suivants :  
  
-   Sont les modifications dans les données de la table identiques ?  
  
-   Les valeurs des paramètres de sortie pour les procédures et fonctions sont identiques ?  
  
-   Les fonctions retournent les mêmes résultats ?  
  
-   Sont que les jeux de résultats identique ?  
  
> [!NOTE]  
> Attention ! N’utilisez jamais de SSMA testeur sur les systèmes de production. Pendant l’exécution du testeur le schéma source et les données sont modifiées. Pendant ce temps, la restauration complète de l’état d’origine est parfois impossible pour certains types de code testé.  
  
## <a name="prerequisites"></a>Prérequis  
Si vous souhaitez utiliser le testeur de SSMA, installer le Pack d’Extension SSMA Sybase avec la **installer la base de données testeur** option activée.  
  
En outre, vérifiez les éléments suivants :  
  
-   Fournisseur OLE DB pour Sybase est installé sur l’ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute.  
  
-   Intégration du Common Language Runtime (CLR) a été activée sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données.  
  
Notez que la version actuelle du testeur de SSMA ne prend pas en charge l’exécution en parallèle par différents utilisateurs sur le même serveur source ou cible.  
  
## <a name="getting-started"></a>Mise en route  
[Création de cas de Test &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Installation des composants SSMA sur SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Paramètres du projet &#40;Conversion&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
