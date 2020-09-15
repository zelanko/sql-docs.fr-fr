---
title: Configuration de l’exécution de scripts R et Python parallèles ou simultanés
description: Configurez l’exécution parallèle ou simultanée de scripts R et Python dans un pool de comptes d’utilisateur pour mettre à l’échelle SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 09/25/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: cc6a081be3d3dd410d43ab36cde98ce6ff47eca1
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88173305"
---
# <a name="scale-concurrent-execution-of-external-scripts-in-sql-server-machine-learning-services"></a>Mettre à l’échelle l’exécution simultanée de scripts externes dans SQL Server Machine Learning Services
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

En savoir plus sur les comptes de travail pour SQL Server Machine Learning Services et sur la manière de modifier la configuration par défaut pour mettre à l’échelle le nombre d’exécutions simultanées de scripts externes.

Dans le cadre du processus d’installation de Machine Learning Services, un *pool de comptes d’utilisateurs* Windows est créé pour prendre en charge l’exécution de tâches par le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]. L’objectif de ces comptes de travail est d’isoler l’exécution simultanée des scripts externes par différents utilisateurs SQL Server.

> [!Note]
> Dans SQL Server 2019, **SQLRUserGroup** ne possède qu’un seul membre qui est maintenant le seul compte de service SQL Server Launchpad (au lieu de plusieurs comptes de travail). Cet article décrit les comptes de travail pour SQL Server 2016 et 2017.

## <a name="worker-account-group"></a>Groupe de comptes de travail

Le groupe de comptes Windows est créé par l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour chaque instance sur laquelle le Machine Learning est installé.

- Dans une instance par défaut, le nom du groupe est **SQLRUserGroup**. Le nom est le même que vous utilisiez Python, R ou les deux.
- Dans une instance nommée, le nom du groupe par défaut a pour suffixe le nom de l’instance (par exemple, **SQLRUserGroupMyInstanceName**).

Par défaut, le pool de comptes d’utilisateurs contient 20 comptes d’utilisateurs. Dans la plupart des cas, ce nombre de comptes suffit largement pour prendre en charge les tâches de Machine Learning, mais vous pouvez le revoir à la hausse. Le nombre maximal de comptes d’utilisateur est de 100.

- Dans une instance par défaut, les comptes individuels sont nommés **MSSQLSERVER01** à **MSSQLSERVER20**.
- Pour une instance nommée, les comptes individuels sont nommés en fonction du nom de l’instance (par exemple, **MyInstanceName01** à **MyInstanceName20**).

Si plusieurs instances utilisent le Machine Learning, l’ordinateur aura plusieurs groupes d’utilisateurs. Il n’est pas possible de partager un groupe entre les instances.

<a name = "HowToChangeGroup"> </a>

## <a name="number-of-worker-accounts"></a>Nombre de comptes de travail

Pour modifier le nombre d’utilisateurs dans le pool de comptes, vous devez modifier les propriétés du service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], comme décrit ci-dessous.

Les mots de passe associés à chaque compte d’utilisateur sont générés de manière aléatoire, mais vous pouvez les modifier une fois les comptes créés.

1. Ouvrez le Gestionnaire de configuration SQL Server, puis sélectionnez **SQL Server Services**.
2. Double-cliquez sur le service SQL Server Launchpad et arrêtez-le s’il est en cours d’exécution.
3.  Sous l’onglet **Service**, vérifiez que le mode de démarrage Automatique est sélectionné. Les scripts externes ne peuvent pas démarrer lorsque le Launchpad n’est pas en cours d’exécution.
4.  Cliquez sur l’onglet **Avancé** et, si nécessaire, modifiez le **Nombre d’utilisateurs externes**. Ce paramètre contrôle le nombre d’utilisateurs SQL pouvant exécuter simultanément des sessions de scripts externes. La valeur par défaut est 20 comptes. Le nombre maximal d’utilisateurs est 100.
5. Vous pouvez éventuellement affecter à l’option **Réinitialiser le mot de passe des utilisateurs externes** la valeur _Oui_ si une stratégie exigeant le changement périodique des mots de passe est en place dans votre organisation. Cette opération regénère les mots de passe chiffrés que gère Launchpad pour les comptes d’utilisateurs. Pour plus d’informations, consultez [Appliquer la stratégie des mots de passe](../security/sql-server-launchpad-service-account.md#bkmk_EnforcePolicy).
6.  Redémarrez le service Launchpad.

## <a name="managing-workloads"></a>Gestion des charges de travail

Le nombre de comptes figurant dans ce pool détermine le nombre de sessions de scripts externes qui peuvent être actives simultanément.  Par défaut, 20 comptes sont créés, ce qui signifie que 20 utilisateurs peuvent avoir des sessions Python ou R actives à un moment donné. Vous pouvez augmenter le nombre de comptes de travail, si vous prévoyez d’exécuter simultanément plus de 20 scripts.

Quand le même utilisateur exécute simultanément plusieurs scripts externes, toutes les sessions exécutées par l’utilisateur utilisent le même compte de travail. Par exemple, un utilisateur unique peut exécuter simultanément 100 scripts Python ou R différents, dans la limite des ressources, avec un seul compte de travail.

Les ressources du serveur sont les seules à limiter le nombre de comptes de travail que vous pouvez prendre en charge et le nombre de sessions simultanées qu’un utilisateur peut exécuter. En général, la mémoire est le premier goulot d’étranglement que vous rencontrez quand vous utilisez le runtime Python ou R.

Les ressources qui peuvent être utilisées par les scripts Python ou R sont régies par SQL Server. Nous vous recommandons de surveiller l’utilisation des ressources à l’aide de vues de gestion dynamique de SQL Server, ou d’examiner les compteurs de performances sur l’objet de traitement Windows associé, puis d’ajuster l’utilisation de la mémoire du serveur en conséquence. Si vous avez SQL Server Entreprise Edition, vous pouvez allouer les ressources utilisées pour l’exécution de scripts externes en configurant un [pool de ressources externes](create-external-resource-pool.md).

## <a name="next-steps"></a>Étapes suivantes

- [Surveiller l’exécution de scripts Python et R à l’aide de rapports personnalisés dans SQL Server Management Studio](../../machine-learning/administration/monitor-sql-server-machine-learning-services-using-custom-reports-management-studio.md)
- [Surveiller SQL Server Machine Learning Services à l’aide de vues de gestion dynamique (DMV)](../../machine-learning/administration/monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)