---
title: Exécution simultanée de mise à l’échelle de scripts externes, SQL Server Machine Learning Services
description: Configurer parallèle ou simultanée R et Python l’exécution du script dans un pool de comptes d’utilisateur à l’échelle de SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: b672ce067d5d1f10754f346c77967b4e3fbe34ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963166"
---
# <a name="scale-concurrent-execution-of-external-scripts-in-sql-server-machine-learning-services"></a>Exécution simultanée de mise à l’échelle de scripts externes dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans le cadre du processus d’installation de [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)], un *pool de comptes d’utilisateurs* Windows est créé pour prendre en charge l’exécution de tâches par le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]. L’objectif de ces comptes de travail consiste à isoler l’exécution simultanée de scripts externes par différents utilisateurs SQL.

Cet article décrit la configuration par défaut et la capacité pour les comptes de travail et comment modifier la configuration par défaut pour augmenter le nombre de l’exécution simultanée de scripts externes dans SQL Server Machine Learning Services.

## <a name="worker-account-group"></a>Groupe de comptes de travail

Un groupe de compte Windows est créé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation pour chaque instance sur lequel machine learning est installé et activé.

- Dans une instance par défaut, le nom du groupe est **SQLRUserGroup**. Le nom est le même que vous utilisiez R ou Python.
- Dans une instance nommée, le nom du groupe par défaut a pour suffixe le nom de l’instance (par exemple, **SQLRUserGroupMyInstanceName**).

Par défaut, le pool de comptes d’utilisateurs contient 20 comptes d’utilisateurs. Dans la plupart des cas, 20 est largement suffisante pour prendre en charge les tâches d’apprentissage automatique, mais vous pouvez modifier le nombre de comptes. Le nombre maximal de comptes est 100.

- Dans une instance par défaut, les comptes individuels sont nommés **MSSQLSERVER01** à **MSSQLSERVER20**.
- Pour une instance nommée, les comptes individuels sont nommés en fonction du nom de l’instance (par exemple, **MyInstanceName01** à **MyInstanceName20**).

Si plusieurs instances utilise machine learning, l’ordinateur a plusieurs groupes d’utilisateurs. Un groupe ne peut pas être partagé entre les instances.

> [!Note]
> Dans SQL Server 2019, **SQLRUserGroup** a uniquement un membre qui est maintenant le compte de service SQL Server Launchpad unique au lieu de plusieurs comptes de travail.

<a name = "HowToChangeGroup"> </a>

## <a name="number-of-worker-accounts"></a>Nombre de comptes de travail

Pour modifier le nombre d’utilisateurs dans le pool de comptes, vous devez modifier les propriétés du service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], comme décrit ci-dessous.

Les mots de passe associés à chaque compte d’utilisateur sont générés de manière aléatoire, mais vous pouvez les modifier une fois les comptes créés.

1. Ouvrez le Gestionnaire de configuration SQL Server, puis sélectionnez **SQL Server Services**.
2. Double-cliquez sur le service SQL Server Launchpad et arrêtez-le s’il est en cours d’exécution.
3.  Sous l’onglet **Service**, vérifiez que le mode de démarrage Automatique est sélectionné. Impossible de démarrer des scripts externes lorsque la zone de lancement n’est pas en cours d’exécution.
4.  Cliquez sur l’onglet **Avancé** et, si nécessaire, modifiez le **Nombre d’utilisateurs externes**. Ce paramètre contrôle combien d’utilisateurs SQL peut exécuter script externe sessions simultanément. La valeur par défaut est 20 comptes. Le nombre maximal d’utilisateurs est 100.
5. Vous pouvez éventuellement affecter à l’option **Réinitialiser le mot de passe des utilisateurs externes** la valeur _Oui_ si une stratégie exigeant le changement périodique des mots de passe est en place dans votre organisation. Cette opération regénère les mots de passe chiffrés que gère Launchpad pour les comptes d’utilisateurs. Pour plus d’informations, consultez [Appliquer la stratégie des mots de passe](../security/sql-server-launchpad-service-account.md#bkmk_EnforcePolicy).
6.  Redémarrez le service Launchpad.

## <a name="managing-workloads"></a>La gestion des charges de travail

Le nombre de comptes dans ce pool détermine le nombre de sessions de script externe peut être actif simultanément.  Par défaut, 20 comptes sont créés, ce qui signifie que 20 utilisateurs peuvent avoir R ou Python sessions actives en même temps. Vous pouvez augmenter le nombre de comptes de travail, si vous prévoyez d’exécuter des scripts simultanés plus de 20.

Lorsque le même utilisateur exécute simultanément plusieurs scripts externes, toutes les sessions exécutées par l’utilisateur utilisent le même compte de travail. Par exemple, un utilisateur unique peut avoir des 100 scripts R différents qui s’exécutent simultanément, tant que permettent les ressources, mais tous les scripts seraient exécute à l’aide d’un compte de travail unique.

Le nombre de comptes de travail que vous pouvez prendre en charge et le nombre de sessions simultanées autorisées par n’importe quel utilisateur peut exécuter, est limitée uniquement par les ressources du serveur. En général, la mémoire est le premier goulot d’étranglement que vous rencontrez quand vous utilisez le runtime R.

Les ressources qui peuvent être utilisées par les scripts Python ou R sont régies par SQL Server. Nous vous recommandons de surveiller l’utilisation des ressources à l’aide de vues de gestion dynamique de SQL Server, ou d’examiner les compteurs de performances sur l’objet de traitement Windows associé, puis d’ajuster l’utilisation de la mémoire du serveur en conséquence. Si vous avez SQL Server Enterprise Edition, vous pouvez allouer les ressources utilisées pour l’exécution de scripts externes en configurant un [pool de ressources externes](how-to-create-a-resource-pool.md).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur la configuration de capacité, consultez ces articles :

- [Configuration de SQL Server pour R Services](../../advanced-analytics/r/sql-server-configuration-r-services.md)
- [Étude de cas de performances pour R Services](../../advanced-analytics/r/performance-case-study-r-services.md)