---
title: RECONFIGURE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/20/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RECONFIGURE
- RECONFIGURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- reconfiguring configuration options
- configuration options [SQL Server], reconfiguring
- updating configuration options
- RECONFIGURE, RECONFIGURE statement
- RECONFIGURE
- RECONFIGURE, WITH OVERRIDE statement
ms.assetid: 2e6e4eeb-b70b-4f45-a253-28ac4e595d75
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32039a4077f028a078e9265c6d18f5cbb6187e3f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="reconfigure-transact-sql"></a>RECONFIGURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Met à jour la valeur actuellement configurée (la **config_value** colonne dans la **sp_configure** jeu de résultats) d’une option de configuration modifié avec la **sp_configure** procédure stockée système. Certaines options de configuration nécessitant un arrêt du serveur et le redémarrer pour mettre à jour la valeur en cours d’exécution, RECONFIGURE n’actualise pas toujours la valeur en cours d’exécution (la **run_value** colonne dans la **sp_configure** jeu de résultats) pour une valeur de configuration a changé.    
    
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Syntaxe    
    
```    
    
RECONFIGURE [ WITH OVERRIDE ]    
```    
    
## <a name="arguments"></a>Arguments    
 RECONFIGURE    
 Indique que, si un paramètre de configuration n'exige pas l'arrêt puis le redémarrage du serveur, la valeur en cours d'exécution doit être mise à jour. RECONFIGURE vérifie également que les nouvelles valeurs de configuration de valeurs qui ne sont pas valides (par exemple, une valeur d’ordre de tri qui n’existe pas dans **syscharsets**) ou non recommandées. Dans le cas d'options de configuration n'exigeant pas l'arrêt et le redémarrage du serveur, la valeur en cours d'exécution et les valeurs actuellement configurées de l'option de configuration doivent être identiques après la spécification de RECONFIGURE.    
    
 WITH OVERRIDE    
 Désactive la vérification (pour les valeurs qui ne sont pas valides ou déconseillées) pour des valeurs de configuration le **l’intervalle de récupération** option de configuration avancée.    
    
 Presque toute option de configuration peut être reconfigurée en utilisant l’option WITH OVERRIDE, toutefois certains irrécupérables erreurs ne peuvent pas toujours. Par exemple, le **options min server memory** option de configuration ne peut pas être configurée avec une valeur supérieure à la valeur spécifiée dans le **mémoire maximum du serveur** option de configuration.
      
## <a name="remarks"></a>Notes    
 **sp_configure** n’accepte pas les nouvelles valeurs d’option de configuration en dehors du documentées plages valides pour chaque option de configuration.    
    
 RECONFIGURE n'est pas autorisée dans une transaction explicite ou implicite. Lorsque vous reconfigurez plusieurs options simultanément, si l'une des opérations de reconfiguration échoue, aucune des opérations de reconfiguration ne prend effet.    
    
 Lors de la reconfiguration du gouverneur de ressources, consultez l’option de reconfiguration de [ALTER RESOURCE GOVERNOR &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-resource-governor-transact-sql.md).    
    
## <a name="permissions"></a>Permissions    
 Par défaut, les autorisations RECONFIGURE sont accordées aux personnes qui bénéficient de l'autorisation ALTER SETTINGS. Le **sysadmin** et **serveradmin** rôles serveur fixes détiennent implicitement cette autorisation.    
    
## <a name="examples"></a>Exemples    
 L'exemple suivant affecte la valeur `recovery interval` minutes à la limite supérieure de l'option de configuration `75` et utilise `RECONFIGURE WITH OVERRIDE` pour l'installer. Les intervalles de récupération supérieurs à 60 minutes sont déconseillés et désactivés par défaut. Toutefois, étant donné que l'option `WITH OVERRIDE` est spécifiée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne vérifie pas si la valeur spécifiée (`90`) est valide pour l'option de configuration `recovery interval`.    
    
```    
EXEC sp_configure 'recovery interval', 75'    
RECONFIGURE WITH OVERRIDE;    
GO    
```    
    
## <a name="see-also"></a>Voir aussi    
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)     
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)    
    
  

