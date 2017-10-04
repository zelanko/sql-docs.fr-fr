---
title: Planifier des packages SSIS sur Linux avec cron | Documents Microsoft
description: Cet article explique comment planifier des packages SQL Server Integration Services sur Linux avec le service cron.
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.date: 09/26/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 31d5fb63a9c2a4d8825aa39c6fa7e3377ddc8d91
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>L’exécution sur Linux avec cron du package de planification SQL Server Integration Services

Lorsque vous exécutez SQL Server Integration Services (SSIS) et SQL Server sur Windows, vous pouvez automatiser l’exécution de packages SSIS à l’aide de l’Agent SQL Server. Lorsque vous exécutez SQL Server et SSIS sur Linux, toutefois, l’utilitaire SQL Server Agent n’est pas disponible pour planifier des travaux sur Linux. Au lieu de cela, vous utilisez **Cron** service qui est largement utilisé sur les plateformes Linux pour automatiser l’exécution du package.

Cet article fournit des exemples qui montrent comment automatiser l’exécution des packages SSIS. Les exemples ont été écrites pour s’exécuter sur Red Hat Enterprise. Le code est identique pour les autres distributions de Linux telles que Ubuntu.

## <a name="prerequisites"></a>Conditions préalables

Avant de pouvoir utiliser le service Cron pour exécuter des travaux, vous devez vérifier si le service Cron s’exécute sur votre ordinateur.

Utilisez la commande suivante pour vérifier l’état du service Cron.

`systemctl status crond.service`

Si le service n’est pas actif (autrement dit, pas en cours d’exécution), consultez votre administrateur pour installer et configurer le service Cron correctement.

## <a name="create-jobs"></a>Créer des travaux

Une tâche Cron est une tâche que vous pouvez configurer pour s’exécuter régulièrement à un intervalle spécifié. La tâche peut être aussi simple qu’une commande qui vous permet de taper directement dans la console ou d’exécuter en tant qu’un script shell normalement.

Pour faciliter la gestion et à des fins de maintenance, il est recommandé de placer vos commandes de l’exécution du package dans un script avec un nom descriptif.

Voici un exemple simple d’un script shell qui contient uniquement les commandes unique pour exécuter un package. Vous pouvez ajouter des commandes supplémentaires en fonction des besoins.

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Planifier des tâches avec le Service Cron

Après avoir défini vos tâches, vous pouvez planifier elles s’exécutent automatiquement à l’aide du service Cron.

Pour ajouter votre travail pour Cron à exécuter, vous devez ajouter le travail dans le `crontab` fichier. Pour ouvrir le `crontab` fichier dans un éditeur, où vous pouvez ajouter ou mettre à jour le travail, utilisez la commande suivante :

`crontab -e`

Pour planifier le travail décrit précédemment pour exécuter tous les jours à 2 h 10, ajoutez suivant la ligne à la `crontab` fichier :

```
# run SSIS package Name at 2:10AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Enregistrer le `crontab` de fichier et quittez l’éditeur.

Pour comprendre le format de l’exemple de commande, passez en revue les informations contenues dans la section suivante.
 
## <a name="format-of-a-crontab-file"></a>Format d’un fichier Crontab

L’illustration suivante montre la description du format de la ligne de tâche ajoutée à la `crontab` fichier.

![Description du format pour l’entrée dans le fichier crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Pour obtenir une description plus détaillée de la `crontab` format de fichier, utilisez la commande suivante :

`man 5 crontab`

Voici un exemple partiels de la sortie qui permet d’expliquer l’exemple dans cet article :

![Description partielle détaillée du format de crontab](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

