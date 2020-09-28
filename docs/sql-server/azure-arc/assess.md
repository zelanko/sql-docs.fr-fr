---
title: Configurer SQL Assessment pour SQL Server avec Azure Arc
titleSuffix: ''
description: Configurer SQL Assessment à la demande pour l’instance avec Azure Arc de SQL Server
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: f3d2051e7003407a4ba7cbb3fb2ff8682ec6ee8f
ms.sourcegitcommit: 8f062015c2a033f5a0d805ee4adabbe15e7c8f94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91227322"
---
# <a name="configure-on-demand-sql-assessment-for-azure-arc-enabled-sql-server-instance"></a>Configurer SQL Assessment à la demande pour l’instance SQL Server avec Azure Arc

Vous pouvez activer SQL Assessment pour vos instances SQL Server en procédant comme suit.

## <a name="prerequisites"></a>Prérequis

* Votre instance SQL Server est connectée à Azure Arc. Suivez ces instructions pour [intégrer votre instance SQL Server à SQL Server avec Azure Arc](connect.md).

* L’extension MMA est installée et configurée sur la machine. Suivez ces instructions pour [Installer Microsoft Monitoring Agent (MMA)](configure-advanced-data-security.md#install-microsoft-monitoring-agent-mma). Pour plus d’informations, consultez [Agent Log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/log-analytics-agent).

* Le [protocole TCP/IP est activé](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) sur votre SQL Server.

* Le [navigateur SQL Server](../../tools/configuration-manager/sql-server-browser-service.md) est en cours d’exécution si vous utilisez une instance nommée de SQL Server.

* Vous avez consulté la section [Prérequis des évaluations à la demande du hub de services](https://docs.microsoft.com/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents) du document SQL Server.

## <a name="enable-on-demand-sql-assessment"></a>Activer SQL Assessment à la demande

1. Ouvrez votre ressource Azure Arc SQL Server et sélectionnez __Intégrité de l’environnement__ dans le menu de gauche.

   ![Sélection de SQL Assessment](media/assess/sql-assessment-heading-sql-server-arc.png)

1. Spécifiez un répertoire de travail sur la machine de collecte de données. `C:\sql_assessment\work_dir` est utilisé par défaut. Pendant la collecte et l’analyse, les données sont stockées temporairement dans ce dossier. Si le dossier n’existe pas, il est créé automatiquement.

1. Cliquez sur __Télécharger le script de configuration__ et copiez le script téléchargé sur la machine cible.

1. Lancez une instance d’administration de __powershell.exe__ et effectuez l’une des opérations suivantes : 
   * Si vous utilisez un compte de domaine, exécutez les commandes suivantes. Vous êtes invité à entrer le compte d’utilisateur et le mot de passe. 

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1'
      ```

    * Si vous utilisez un compte MSA, exécutez les commandes suivantes.

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1' -ManagedServiceAccountName <MSA account name>
      ```

   > [!NOTE]
   > Le script planifie une tâche nommée *SQLAssessment* pour s’exécuter dans l’heure suivant l’exécution du script précédent, puis tous les 7 jours. La tâche peut être modifiée pour s’exécuter à une date et une heure différentes, voire s’exécuter immédiatement à partir de la bibliothèque du Planificateur de tâches > Microsoft > Operations Management Suite > AOI*** > Évaluations > SQLAssessment. Cette tâche déclenche la collecte de données.

## <a name="view-the-assessment-results"></a>Afficher les résultats de l’évaluation

Le bouton __Afficher le résultat de SQL Assessment__ sur le panneau _Intégrité de l’environnement_ est désactivé jusqu’à ce que les résultats soient prêts dans Log Analytics. Lorsque le bouton est activé, vous pouvez cliquer dessus pour afficher les résultats. Une fois que les fichiers de données sont traités sur la machine cible, l’affichage des résultats dans Log Analytics peut prendre jusqu’à 2 heures.

![Résultats de l’évaluation SQL](media/assess/sql-assessment-results.png)

Vous pouvez voir l’état du traitement de données sur la machine de collecte en vérifiant les fichiers dans le dossier de travail. Une fois la tâche planifiée terminée, vous devez voir plusieurs fichiers avec le préfixe _new._ dans le répertoire de travail :

![Fichiers de données prêts](media/assess/sql-assessment-data-files-ready.png)

Microsoft Monitoring Agent analyse le dossier de travail toutes les 15 minutes en recherchant les fichiers _new.*_ et envoie les données à l’espace de travail Log Analytics. Une fois le fichier chargé, le préfixe passe de _new._ à _processed._ :

![Fichiers de données traités](media/assess/sql-assessment-data-files-processed.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez la section [Prérequis des évaluations à la demande du hub de services](https://docs.microsoft.com/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents) du document SQL Server.

Pour bénéficier d’une prise en charge complète pour SQL Assessment à la demande, un abonnement au support Premier ou Unified est requis. Pour plus d’informations, consultez [Support Premier Azure](https://azure.microsoft.com/support/plans/premier).
