---
title: Paramètres de migration des données (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9c396df4-5676-4f32-9c57-70d4f15f9b7a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c2c903ef29ab1a103bc9aa4f7b061e83ee7f2a95
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67896372"
---
# <a name="data-migration-settings-mysqltosql"></a>Paramètres de migration de données (MySQLToSQL)
  
## <a name="data-migration-settings"></a>Paramètres de migration de données  
Les **paramètres de migration des données** permettent à l’utilisateur d’écrire des requêtes personnalisées pour la migration des données.  
  
-   Cet onglet est disponible lorsque l' **option options de migration étendue des données** est définie sur **Afficher** et est masquée lorsque le paramètre est défini sur **Masquer** dans les paramètres du projet. Pour plus d’informations sur les paramètres de migration de projet, consultez [paramètres du projet (migration)](https://msdn.microsoft.com/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9) .  
  
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
[Migration des données MySQL vers SQL Server/SQL Azure](https://msdn.microsoft.com/a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82)  
  
