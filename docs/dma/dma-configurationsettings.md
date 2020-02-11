---
title: Configurer les paramètres de Assistant Migration de données
description: Découvrez comment configurer les paramètres du Assistant Migration de données en mettant à jour les valeurs dans le fichier de configuration.
ms.custom: seo-lt-2019
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: fc280fa541e2a6b5ea984086d694ffdd3f7c39a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74056539"
---
# <a name="configure-settings-for-data-migration-assistant"></a>Configurer les paramètres de Assistant Migration de données

Vous pouvez ajuster certains comportements de Assistant Migration de données en définissant les valeurs de configuration dans le fichier DMA. exe. config. Cet article décrit les valeurs de configuration de clé.

Vous pouvez trouver le fichier DMA. exe. config pour l’application de bureau Assistant Migration de données et l’utilitaire de ligne de commande, dans les dossiers suivants sur votre ordinateur.

- Application de bureau

  % ProgramFiles%\\Assistant Migration de données Microsoft\\DMA. exe. config

- Utilitaire de ligne de commande

  % ProgramFiles%\\Assistant Migration de données Microsoft\\dmacmd. exe. config 

Veillez à enregistrer une copie du fichier de configuration d’origine avant d’apporter des modifications. Après avoir apporté des modifications, redémarrez Assistant Migration de données pour que les nouvelles valeurs de configuration prennent effet.

## <a name="number-of-databases-to-assess-in-parallel"></a>Nombre de bases de données à évaluer en parallèle

Assistant Migration de données évalue plusieurs bases de données en parallèle. Pendant l’évaluation Assistant Migration de données extrait l’application de la couche données (dacpac) pour comprendre le schéma de la base de données.Cette opération peut expirer si plusieurs bases de données sur le même serveur sont évaluées en parallèle. 

À partir de Assistant Migration de données v 2.0, vous pouvez contrôler cela en définissant la valeur de configuration parallelDatabases. La valeur par défaut est 8.

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>Nombre de bases de données à migrer en parallèle

Assistant Migration de données migre plusieurs bases de données en parallèle avant de migrer les connexions. Pendant la migration, Assistant Migration de données effectue une sauvegarde de la base de données source, copie éventuellement la sauvegarde, puis la restaure sur le serveur cible. Vous pouvez rencontrer des échecs de délai d’attente lorsque plusieurs bases de données sont sélectionnées pour la migration. 

À compter de Assistant Migration de données v 2.0, si vous rencontrez ce problème, vous pouvez réduire la valeur de configuration de parallelDatabases. Vous pouvez augmenter la valeur pour réduire l’heure globale de la migration.

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases="8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>Paramètres DacFX

Pendant l’évaluation, Assistant Migration de données extrait l’application de la couche données (dacpac) pour comprendre le schéma de la base de données. Cette opération peut échouer avec des délais d’attente pour les bases de données très volumineuses, ou si le serveur est en cours de chargement. À partir de la migration de données v 1.0, vous pouvez modifier les valeurs de configuration suivantes pour éviter les erreurs. 

> [!NOTE]
> La totalité &lt;de&gt; l’entrée dacfx est commentée par défaut. Supprimez les commentaires, puis modifiez la valeur si nécessaire.

- commandTimeout

   Ce paramètre définit la propriété IDbCommand. CommandTimeout en *secondes*.(Valeur par défaut = 60)

- databaseLockTimeout

   Ce paramètre équivaut à définir le délai d’expiration du délai d’attente du [verrou\_\_](../t-sql/statements/set-lock-timeout-transact-sql.md) en *millisecondes*.(Valeur par défaut = 5000)

- maxDataReaderDegreeOfParallelism

  Ce paramètre définit le nombre de connexions du pool de connexions SQL à utiliser.(Valeur par défaut = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```

## <a name="stretch-database-recommendation-threshold"></a>Stretch Database : seuil de recommandation

Avec [SQL Server Stretch Database](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database), vous pouvez étendre dynamiquement les données transactionnelles à chaud et à froid de Microsoft SQL Server 2016 vers Azure. Stretch Database cible les bases de données transactionnelles avec de grandes quantités de données à froid. La recommandation Stretch Database, sous recommandation relative aux fonctionnalités de stockage, identifie d’abord les tables qu’elle estime tirera parti de cette fonctionnalité, puis identifie les modifications qui doivent être apportées pour activer la table pour cette fonctionnalité.

À partir de Assistant Migration de données v 2.0, vous pouvez contrôler ce seuil pour qu’une table qualifie la fonctionnalité de Stretch Database à l’aide de la valeur de configuration recommendedNumberOfRows. La valeur par défaut est 100 000 lignes. Si vous souhaitez analyser les capacités d’étirement pour des tables encore plus petites, diminuez la valeur en conséquence.

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>Délai de connexion SQL

Vous pouvez contrôler le délai d’expiration de la [connexion SQL](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx) pour les instances source et cible lors de l’exécution d’une évaluation ou d’une migration, en définissant la valeur du délai d’attente de la connexion sur un nombre de secondes spécifié. La valeur par défaut est 15 secondes.

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```

## <a name="ignore-error-codes"></a>Ignorer les codes d’erreur

Chaque règle contient un code d’erreur dans son titre. Si vous n’avez pas besoin de règles et que vous souhaitez les ignorer, utilisez la propriété ignoreErrorCodes. Vous pouvez spécifier qu’il faut ignorer une seule erreur ou plusieurs erreurs. Pour ignorer plusieurs erreurs, utilisez un point-virgule, par exemple ignoreErrorCodes = "46010 ; 71501". La valeur par défaut est 71501, qui est associée à des références non résolues identifiées lorsqu’un objet fait référence à des objets système tels que des procédures, des vues, etc.

```
<workflowSettings>

<assessment parallelDatabases="8" ignoreErrorCodes="71501" />

</workflowSettings>
```

## <a name="see-also"></a>Voir aussi

[Télécharger Assistant Migration de données](https://www.microsoft.com/download/details.aspx?id=53595)
