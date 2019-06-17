---
title: Paramètres de Migration de données (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1191a29fa3988b85548578e8a38efc12d9fce41c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63297432"
---
# <a name="data-migration-settings-sybasetosql"></a>Paramètres de migration de données (SybaseToSQL)
  
## <a name="data-migration-settings"></a>Paramètres de migration de données  
**Paramètres de Migration de données** permet à l’utilisateur d’écrire des requêtes personnalisées pour la migration de données.  
  
-   Cet onglet est disponible lorsque **étendu d’options de migration de données** a la valeur **afficher** et est masqué lorsque le paramètre est défini sur **masquer** dans Paramètres du projet. Pour plus d’informations sur les paramètres de Migration de projet, consultez [paramètres du projet (Migration)](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924) .  
  
-   L’analyse des instructions SQL de personnalisé sera implémenté dans **les paramètres de migration de données** onglet du nœud de la Table.  
  
-   Voici les deux cases à cocher disponibles dans le **les paramètres de Migration de données** reportages. :  
  
    1.  TRUNCATE table SQL Server  
  
    2.  Sélectionnez utilisation personnalisée  
  
1.  **TRUNCATE table SQL Server :**  
     Cette option permet à l’utilisateur d’avoir une vue claire des données migrées à la base de données cible.  
  
    -   Par défaut, cette zone de texte est activée.  
  
    -   Si cette zone de texte est désactivée, puis les données qui sont migrées figurera sur les données existantes à la base de données cible.  
  
2.  **Utilisation personnalisée sélectionnez :**  
     Cette option permet à l’utilisateur de modifier le **sélectionnez** instruction présente (**sélectionnez** instruction permet aux utilisateurs de sélectionner les données à afficher à la base de données cible).  
  
    1.  Par défaut, cette zone de texte est désactivée.  
  
    2.  Si cette zone de texte est activée, elle permet aux utilisateurs de modifier le **sélectionnez** instruction présents.  
  
Il existe deux boutons présents reportages. :  
  
-   **S’appliquent :** Cliquez sur **appliquer** pour appliquer les paramètres qui ont été modifiés.  
  
-   **Annuler :** Cliquez sur **Annuler** pour restaurer les paramètres présents avant que les modifications sont apportées.  
  
## <a name="see-also"></a>Voir aussi  
[Migration de données Sybase vers SQL Server/SQL Azure](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811)  
  
