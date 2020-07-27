---
title: Supprimer les erreurs de mode de récupération - option de configuration de serveur | Microsoft Docs
ms.custom: ''
ms.date: 07/20/2020
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a59ff201edb153487640b4c5781d38a2df3756f9
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942223"
---
# <a name="suppress-recovery-model-errors-server-configuration-option"></a>Supprimer les erreurs de mode de récupération (option de configuration de serveur)

[!INCLUDE[tsql-appliesto-xxxxxx-asdbmi-xxxx-xxx-md.md](../../includes/tsql-appliesto-xxxxxx-asdbmi-xxxx-xxx-md.md)]

Les [modes de récupération](https://docs.microsoft.com/sql/relational-databases/backup-restore/recovery-models-sql-server) de SQL Server contrôlent la maintenance du journal des transactions. Le mode de récupération complète garantit qu’aucun travail n’est perdu suite à la perte ou à l’endommagement d’un fichier de données, et il prend en charge la récupération à un point arbitraire dans le temps dans la stratégie de conservation de sauvegarde. Le mode de récupération complète est le mode par défaut et le seul mode de récupération pris en charge dans SQL Managed Instance. Toute tentative de modification du mode de récupération dans SQL Managed Instance retourne un message d’erreur.

Utilisez l’option de configuration avancée **Supprimer les erreurs de mode de récupération** pour spécifier si les commandes de modification du mode de récupération de base de données, exécutées sur SQL Managed Instance, renvoient des erreurs ou des avertissements uniquement. Lorsque cette option a la valeur 1 (activé) sur SQL Managed Instance, l’exécution de la commande ALTER DATABASE SET RECOVERY ne change pas le mode de récupération de la base de données, et ne retourne pas d’erreur mais un message d’avertissement. Lorsque cette option a la valeur 0 (désactivé) sur SQL Managed Instance, l’exécution de la commande ALTER DATABASE SET RECOVERY retourne un message d’erreur.

L’option **Supprimer les erreurs de mode de récupération** est utile dans les cas où des applications héritées ou tierces tentent de définir le mode de récupération sur Simple ou Journalisé en bloc, même s’il ne s’agit pas d’une condition requise ou critique. Lorsque le changement du mode de récupération est le seul facteur bloquant pour utiliser SQL Managed Instance, l’activation de l’option Supprimer les erreurs de mode de récupération supprime ce facteur bloquant. Cette option est particulièrement utile si une autre solution de changement du code d’application n’est pas faisable ou abordable.

## <a name="examples"></a>Exemples

L’exemple suivant active la suppression des messages d’erreur liés au changement du mode de récupération de base de données, puis exécute la commande pour changer le mode de récupération de base de données, en retournant uniquement un avertissement. Le mode de récupération n’est pas réellement changé. Veillez à remplacer *my_database* par le nom réel de la base de données.

```sql
-- Turn advanced configuration options on:
sp_configure 'show advanced options', 1 ;  
GO
RECONFIGURE ;  
GO

-- Enable suppression of error messages for recovery model change:
sp_configure 'suppress recovery model errors', 1 ;  
GO
RECONFIGURE ;  
GO

-- Execute command for changing recovery model to Simple:
ALTER DATABASE my_database SET RECOVERY SIMPLE;
GO
```

## <a name="see-also"></a>Voir aussi

[Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)

[sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)

[RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)
