---
title: "Paramètres de Migration de données (DB2ToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 573e673e-a194-4cb2-9aba-aaac6e1a225c
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b1800689474a5ae525dedfff24bab2e60459caba
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="data-migration-settings-db2tosql"></a>Paramètres de Migration de données (DB2ToSQL)
  
## <a name="data-migration-settings"></a>Paramètres de Migration de données  
**Les paramètres de Migration de données** permet à l’utilisateur d’écrire des requêtes personnalisées pour la migration de données.  
  
-   Cet onglet est disponible lorsque **étendue des options de migration de données** a la valeur **afficher** et est masqué lorsque le paramètre est défini sur **masquer** dans Paramètres du projet. Pour plus d’informations sur les paramètres de Migration de projet, consultez [paramètres du projet (Migration)](http://msdn.microsoft.com/en-us/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae) .  
  
-   L’analyse des instructions SQL de personnalisée sera implémenté dans **les paramètres de migration de données** onglet de nœud de la Table.  
  
-   Voici les deux cases à cocher disponibles dans le **les paramètres de Migration de données** au dixième. :  
  
    1.  TRUNCATE table SQL Server  
  
    2.  Sélectionnez d’utilisation personnalisée  
  
1.  **TRUNCATE table SQL Server :**  
     Cette option permet à l’utilisateur d’avoir une vue claire des données migrées à la base de données cible.  
  
    -   Par défaut, cette zone de texte est vérifiée.  
  
    -   Si cette zone de texte est désactivée, les données migrées sont ajoutés sur les données existantes à la base de données cible.  
  
2.  **Sélectionner l’utilisation personnalisé :**  
     Cette option permet à l’utilisateur de modifier le **sélectionnez** instruction présente (**sélectionnez** instruction permet aux utilisateurs de sélectionner les données à afficher à la base de données cible).  
  
    1.  Par défaut, cette zone de texte est désactivée.  
  
    2.  Si cette zone de texte est activée, elle permet aux utilisateurs de modifier le **sélectionnez** instruction présente.  
  
Il existe deux boutons présents au dixième. :  
  
-   **Appliquer :** cliquez sur **appliquer** pour appliquer les paramètres qui ont été modifiés.  
  
-   **Annuler :** cliquez sur **Annuler** pour restaurer les paramètres présents avant les modifications en cours.  
  
## <a name="see-also"></a>Voir aussi  
[Migration de données DB2 à SQL Server](http://msdn.microsoft.com/en-us/86cbd39f-6dac-409a-9ce1-7dd54403f84b)  
  

