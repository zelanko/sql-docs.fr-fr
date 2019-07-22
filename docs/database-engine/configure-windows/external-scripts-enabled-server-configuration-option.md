---
title: External scripts enabled (option de configuration de serveur) | Microsoft Docs
ms.date: 11/13/2017
ms.prod: sql
ms.technology: configuration
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords:
- external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 424268eb32eb3430e2e4eb8450abfb3471f51701
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68011759"
---
# <a name="external-scripts-enabled-server-configuration-option"></a>External scripts enabled (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**S’applique à** : [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] et [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Utilisez l’option **external scripts enabled** pour activer l’exécution de scripts avec certaines extensions de langage à distance. Cette propriété est désactivée par défaut. Quand **Advanced Analytics Services** est installé, le programme d’installation peut éventuellement définir cette propriété sur True.

## <a name="remarks"></a>Notes

Vous devez activer l’option de scripts externes activés avant de pouvoir exécuter un script externe à l’aide de la procédure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) . Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans un langage pris en charge comme R ou Python. 

+ Pour [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]

    [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] prend en charge le langage R dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], ainsi qu’un ensemble d’outils de station de travail R et de bibliothèques de connectivité.

    Installez la fonction **Extensions analytiques avancées** pendant l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre l’exécution de scripts R. Le langage R est installé par défaut.

+ Pour [[!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]

    [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] utilise la même architecture que dans SQL Server 2016, mais prend en charge le langage Python.

    Installez la fonctionnalité **Extensions analytiques avancées** pendant l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre l’exécution de scripts externes. Veillez à sélectionner au moins un langage lors de l’installation initiale : R ou Python, ou les deux. 

## <a name="additional-requirements"></a>Autres conditions requises

Après l’installation, exécutez le script suivant pour activer les scripts externes :

```sql
sp_configure 'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE;  
```

Vous devez redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour que ce changement soit effectif.

Pour plus d’informations, consultez [Configurer SQL Server Machine Learning Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).

## <a name="see-also"></a>Voir aussi

[sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)

[RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)

[sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

[SQL Server Machine Learning Services](../../advanced-analytics/r/sql-server-r-services.md)
