---
title: Paramètres de migration des données (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 9fcf6142a0df913c33782b4c65e8e95d4fcf91ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029380"
---
# <a name="data-migration-settings-sybasetosql"></a>Paramètres de migration de données (SybaseToSQL)
  
## <a name="data-migration-settings"></a>Paramètres de migration de données  
Les **paramètres de migration des données** permettent à l’utilisateur d’écrire des requêtes personnalisées pour la migration des données.  
  
-   Cet onglet est disponible lorsque l' **option options de migration étendue des données** est définie sur **Afficher** et est masquée lorsque le paramètre est défini sur **Masquer** dans les paramètres du projet. Pour plus d’informations sur les paramètres de migration de projet, consultez [paramètres du projet (migration)](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924) .  
  
-   L’analyse des instructions SQL personnalisées sera implémentée dans l’onglet **paramètres de migration de données** du nœud de la table.  
  
-   Voici les deux cases à cocher disponibles dans les **paramètres de migration de données** , à savoir :  
  
    1.  Tronquer la table SQL Server  
  
    2.  Utiliser une sélection personnalisée  
  
1.  **Tronquer la table SQL Server :**  
     Cette option permet à l’utilisateur de disposer d’une vue claire des données migrées au niveau de la base de données cible.  
  
    -   Par défaut, cette zone de texte est cochée.  
  
    -   Si cette zone de texte est désactivée, les données qui sont migrées seront ajoutées aux données existantes dans la base de données cible.  
  
2.  **Utiliser la sélection personnalisée :**  
     Cette option permet à l’utilisateur de modifier l’instruction **Select** présente (l’instruction**Select** permet aux utilisateurs de sélectionner les données à afficher dans la base de données cible).  
  
    1.  Par défaut, cette zone de texte est désactivée.  
  
    2.  Si cette zone de texte est cochée, elle permet aux utilisateurs de modifier l’instruction **Select** présente.  
  
Deux boutons sont présents, à savoir :  
  
-   **Appliquer :** Cliquez sur **appliquer** pour appliquer les paramètres qui ont été modifiés.  
  
-   **Annuler :** Cliquez sur **Annuler** pour restaurer les paramètres présents avant l’établissement des modifications.  
  
## <a name="see-also"></a>Voir aussi  
[Migration de données Sybase vers SQL Server/SQL Azure](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811)  
  
