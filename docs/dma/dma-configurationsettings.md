---
title: Configurer les paramètres de l’Assistant Migration de données (SQL Server) | Microsoft Docs
description: Découvrez comment configurer les paramètres de l’Assistant Migration de données en mettant à jour les valeurs dans le fichier de configuration
ms.custom: ''
ms.date: 10/20/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: pochiraju
ms.author: rajpo
manager: craigg
ms.openlocfilehash: ceca358e47a2cabbe01e64498d61603717a0d370
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52419250"
---
# <a name="configure-settings-for-data-migration-assistant"></a>Configurer les paramètres de l’Assistant Migration des données

Vous pouvez affiner certain comportement de l’Assistant Migration de données en définissant les valeurs de configuration dans le fichier dma.exe.config. Cet article décrit les valeurs de configuration de la clé.

Vous trouverez le fichier dma.exe.config pour l’application de bureau Data Migration Assistant et l’utilitaire de ligne de commande, dans les dossiers suivants sur votre ordinateur.

- Application de bureau

  % ProgramFiles%\\Microsoft Data Migration Assistant\\dma.exe.config

- Utilitaire de ligne de commande

  % ProgramFiles%\\Microsoft Data Migration Assistant\\dmacmd.exe.config 

Veillez à enregistrer une copie du fichier de configuration d’origine avant d’apporter des modifications. Après avoir apporté les modifications, redémarrez Data Migration Assistant pour les nouvelles valeurs de configuration prenne effet.

## <a name="number-of-databases-to-assess-in-parallel"></a>Nombre de bases de données à évaluer en parallèle

Assistant Migration de données évalue plusieurs bases de données en parallèle. Pendant l’évaluation Data Migration Assistant extrait l’application de la couche données (dacpac) pour comprendre le schéma de base de données. Cette opération peut expirer si plusieurs bases de données sur le même serveur sont évaluées en parallèle. 

À partir de Data Migration Assistant v2.0, vous pouvez contrôler cela en définissant le parallelDatabases valeur de configuration. Valeur par défaut est 8.

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>Nombre de bases de données à migrer en parallèle

Data Migration Assistant migre plusieurs bases de données en parallèle, avant migration de connexions. Pendant la migration, Data Migration Assistant sera effectuer une sauvegarde de la base de données source, copiez éventuellement la sauvegarde et sa restauration sur le serveur cible. Vous pouvez rencontrer des échecs de délai d’attente lorsque plusieurs bases de données sont sélectionnés pour la migration. 

En commençant par v2.0 Data Migration Assistant, si vous rencontrez ce problème, vous pouvez réduire la valeur de configuration parallelDatabases. Vous pouvez augmenter la valeur pour réduire la durée globale de la migration.

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases="8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>Paramètres de DacFX

Pendant l’évaluation, Data Migration Assistant extrait l’application de la couche données (dacpac) pour comprendre le schéma de base de données. Cette opération peut échouer avec des délais d’attente de bases de données extrêmement volumineux, ou si le serveur est sous charge. À compter de la Migration des données v1.0, vous pouvez modifier les valeurs de configuration suivantes pour éviter les erreurs. 

> [!NOTE]
> L’intégralité de &lt;dacfx&gt; entrée est commentée par défaut. Supprimez les commentaires et modifiez la valeur en fonction des besoins.

- commandTimeout

   Ce paramètre définit la propriété IDbCommand.CommandTimeout *secondes*. (Par défaut = 60)

- databaseLockTimeout

   Ce paramètre équivaut à [verrou définir\_délai d’expiration du délai d’attente\_période](../t-sql/statements/set-lock-timeout-transact-sql.md) dans *millisecondes*. (Par défaut = 5000)

- maxDataReaderDegreeOfParallelism

  Ce paramètre définit le nombre de connexions de pool de connexion SQL à utiliser. (Par défaut = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```

## <a name="stretch-database-recommendation-threshold"></a>Stretch Database : Seuil de recommandation

Avec [SQL Server Stretch Database](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database), vous pouvez étendre dynamiquement les données transactionnelles froides et à chaudes de Microsoft SQL Server 2016 vers Azure. Stretch Database cibles bases de données transactionnelles comportant de grandes quantités de données à froid. La recommandation de Stretch Database, sous la recommandation de fonctionnalité de stockage, identifie tout d’abord les tables qu’elle croit appartenir bénéficieront de cette fonctionnalité, et puis elle identifie les modifications devant être apportées afin de bénéficier de la table pour cette fonctionnalité.

À partir de Data Migration Assistant v2.0, vous pouvez contrôler ce seuil pour une table être éligible pour la fonctionnalité Stretch Database à l’aide de la valeur de configuration recommendedNumberOfRows. Valeur par défaut est 100 000 lignes. Si vous souhaitez analyser les fonctionnalités de stretch pour encore plus petites tables, puis que vous réduisez la valeur en conséquence.

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>Délai de connexion SQL

Vous pouvez contrôler le [délai de connexion SQL](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx) pour les instances source et cible lors de l’exécution d’une évaluation ou migration, en définissant la valeur de délai d’expiration de connexion à un nombre spécifié de secondes. La valeur par défaut est 15 secondes.

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```


## <a name="see-also"></a>Voir aussi

[Télécharger l’Assistant de Migration de données](https://www.microsoft.com/download/details.aspx?id=53595)
