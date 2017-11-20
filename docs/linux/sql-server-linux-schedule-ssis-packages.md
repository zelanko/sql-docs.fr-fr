---
title: Planifier des packages SSIS sur Linux avec cron | Documents Microsoft
description: "Cet article décrit comment planifier des packages SQL Server Integration Services (SSIS) sur Linux avec le service cron."
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 84ee0eaf4743cc4a3b188dd700b1ccbdc4ca42cc
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>L’exécution sur Linux avec cron du package de planification SQL Server Integration Services

Lorsque vous exécutez SQL Server Integration Services (SSIS) et SQL Server sur Windows, vous pouvez automatiser l’exécution de packages SSIS à l’aide de l’Agent SQL Server. Lorsque vous exécutez SQL Server et SSIS sur Linux, toutefois, l’utilitaire SQL Server Agent n’est pas disponible pour planifier des travaux sur Linux. Au lieu de cela, vous utilisez le service cron, qui est largement utilisé sur les plateformes Linux pour automatiser l’exécution du package.

Cet article fournit des exemples qui montrent comment automatiser l’exécution des packages SSIS. Les exemples sont écrits pour s’exécuter sur Red Hat Enterprise. Le code est identique pour les autres distributions Linux, telles que Ubuntu.

## <a name="prerequisites"></a>Conditions préalables

Avant d’utiliser le service cron pour exécuter des tâches, vérifiez si elle est en cours d’exécution sur votre ordinateur.

Pour vérifier l’état du service cron, utilisez la commande suivante : `systemctl status crond.service`.

Si le service n’est pas actif (autrement dit, il ne fonctionne pas), consultez votre administrateur pour installer et configurer le service cron correctement.

## <a name="create-jobs"></a>Créer des travaux

Une tâche cron est une tâche que vous pouvez configurer pour s’exécuter régulièrement à un intervalle spécifié. La tâche peut être aussi simple qu’une commande qui vous permet de taper directement dans la console ou d’exécuter en tant qu’un script shell normalement.

Pour faciliter la gestion et à des fins de maintenance, nous vous recommandons de placer vos commandes de l’exécution du package dans un script qui contient un nom descriptif.

Voici un exemple d’un script shell simple pour l’exécution d’un package. Il contient uniquement une commande unique, mais vous pouvez ajouter davantage de commandes en fonction des besoins.

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Planifier des tâches avec le service cron

Après avoir défini vos tâches, vous pouvez planifier elles s’exécutent automatiquement à l’aide du service cron.

Pour ajouter votre travail pour cron à exécuter, d’ajouter le travail dans le fichier crontab. Pour ouvrir le fichier crontab dans un éditeur, où vous pouvez ajouter ou mettre à jour le travail, utilisez la commande suivante : `crontab -e`.

Pour planifier le travail décrit précédemment pour exécuter tous les jours à 2 h 10, ajoutez la ligne suivante au fichier crontab :

```
# run <SSIS package name> at 2:10 AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Enregistrez le fichier crontab, puis quittez l’éditeur.

Pour comprendre le format de l’exemple de commande, passez en revue les informations contenues dans la section suivante.
 
## <a name="format-of-a-crontab-file"></a>Format d’un fichier crontab

L’illustration suivante montre la description du format de la ligne de tâche qui est ajoutée au fichier crontab.

![Description du format pour l’entrée dans le fichier crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Pour obtenir une description plus détaillée du format de fichier crontab, utilisez la commande suivante : `man 5 crontab`.

Voici un exemple partiels de la sortie qui permet d’expliquer l’exemple dans cet article :

![Description partielle détaillée du format de crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

